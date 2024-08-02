In a [previous](https://dev.to/brunooliveira/basic-rag-app-with-spring-ai-docker-and-ollama-1i7j) blog post, I detailed a possible technical setup for having a solid foundation for doing RAG within the Springboot ecosystem, using docker to leverage locally downloaded LLMs and Postgres, configured with the `PGVector` extension to be able to manipulate and store embeddings and work with similarity search from a Postgres DB. If you haven't yet, go read that one, as it will greatly help with digesting this upcoming content, even if I'll try to make this as self-contained as possible.

## Recap - what are embeddings after all?

Note the below two paragraphs are adapted from the awesome [Ollama blog](https://ollama.com/blog/embedding-models), credits go to them! Emphasis mine.

At a very broad level, embedding models are models that are trained specifically to generate vector embeddings: long arrays of numbers that **represent semantic meaning** for a given sequence of text:

![embeddings.png]({{site.baseurl}}/images/embeddings.png)

The resulting vector embedding arrays can then be stored in a database, which will enable us to compare them as a way to search for data that is similar in meaning. 

What this means is that, essentially, we perform a domain transform: just like the Fourier Transform can map a signal from the time to the frequency domain, we are mapping long sequences of text into a "vector-domain", producing an alternative representation of the text. The main insight is that in this new "vector domain", it is simpler and easier to search for "similar enough" texts in a way that plain text doesn't allow us to.

The shift from the text domain to the vector domain needs to encode the _semantic meaning_ of the text in some way, which is the aspect that makes this work: it's not only a matter of applying a simple change from words to vectors, but, it's really about capturing the semantic meaning of the text.
Embedding models are, generally neural network algorithms that can be thought of as a checkpoint step in an LLM completion generation flow, that generates embeddings when an input is provided and stop there.

Current LLM providers like OpenAI, AWS Bedrock, Anthropic, and several other open-source projects, offer two distinct APIs: firstly, what is called an _inference_ API, which is what is known colloquially as a large language model: text goes in, in the form of a prompt, and a completion, usually in the form of human-readable text, an image, a video or even audio, comes out.
Secondly, an _embeddings_ API, which is an API whose sole responsibility is to produce embeddings from a piece of text and is arguably, the most important step in a deployed, trained, and fine-tuned LLM request flow.

Embeddings are the crucial piece of the puzzle for understanding RAG.

## Requirements for embeddings to work

Another crucial point to understand is that each provider offers different embedding models that support different context window sizes (the size, measured in tokens, of the largest chunk of text you can embed at once) as well as different dimension sizes (the number of dimensions, i.e. elements, in the "vector-representation" of the embedded text).
These two numbers mean different things and play different roles at different levels of the stack.
Online, the most looked-at numbers you'll often read about concern only the number of elements in the "vector-representation" of the text, so, when you read online that "OpenAI embeddings have 1536 dimensions" or that "the default embedding size of PGVectorStore is set to 1536", this just means that the number of elements of the vectors that encode the semantic meaning of the text is 1536.
There are many different models, from open-source to proprietary that have different dimensions, from 768 dimensions to over 3000, the flavors are quite varied here, and, a lot of the work is in testing the different trade-offs between different sizes in terms of how well the embeddings perform across a range of aspects, from size taken in the DB tables where they are stored, to the performance of using them with different distance types (we'll see what these are later).

So, what is the most important aspect when working with embeddings? Very simply, and also obviously, **the embeddings of potential documents meant to be used for RAG purposes need to be done by the same model that will embed the query** for optimal results. If the vectors would have different sizes, applying a distance metric to them wouldn't make sense. Obviously what this _also_ means is that in theory different embedding models that produce vectors of similar sizes _could_ be used, the results would be meaningless to interpret as the representations in semantic meaning would be different, even if the size of the resulting vectors would be the same. Just because we can, doesn't mean we should.

## Back to Springboot: how does this work in practice?

Now that we've seen some of the theory, let's look at some code to make it more concrete.

Springboot has a new module, Spring AI, which we can leverage to integrate embeddings (and a dedicated database to work with them) into a regular Springboot web application.

Just like there are many distinct Large Language Models and Embedding providers, we can have many distinct "vector database" providers.

In the remainder of this post, I'll focus on integrating only open-source variants of all we've been discussing so far:

- LLMs are stored and run locally, via the Ollama project, packaged as a docker container;
- Postgres will serve as our vector store, by being extended with the `PGVector` extension;
- The embedding model to be used will be [mxbai-embed-large-v1](https://www.mixedbread.ai/blog/mxbai-embed-large-v1) from Mixedbread;

All of this has been written in the previous blog post, but, in the interest of making this post fully self-contained, I'll extract the key pieces and repeat them here for reference.

Ollama is a cool new project that surfaced as a way to leverage the power of LLMs and embedding models by allowing people to run them locally on their machines. The base docker setup I used (as part of a larger docker-compose file that instantiated more services, such as the Springboot application and a Streamlit front-end) for setting up Ollama was the following:

```docker
  ollama-llm:
    image: ollama/ollama:latest
    volumes:
      - ollama_data:/root/.ollama
    ports:
      - "11434:11434"
    networks:
      - app-network

...

  prepare-models:
    image: ollama/ollama:latest
    depends_on:
      - ollama-llm
    volumes:
      - ollama_data:/root/.ollama
    environment:
      - OLLAMA_HOST=http://ollama-llm:11434
    networks:
      - app-network
    entrypoint: >
      sh -c "
        echo 'Waiting for Ollama server to start...' &&
        sleep 10 &&
        echo 'Pulling tinydolphin...' &&
        ollama pull tinydolphin &&
        echo 'Pulling tinyllama...' &&
        ollama pull tinyllama &&
      echo 'Pulling llama3.1...' &&
      ollama pull llama3.1 &&
      echo 'Pulling embedding model...' &&
      ollama pull mxbai-embed-large &&
        echo 'Model preparation complete.'"

networks:
 - app-network
```

Ollama, upon start, spins up a server that we can then pull several open-source LLM and embedding models from, so, we do this in a two-image fashion: one that "prepares the models" by pulling them into our machine, into the volume defined by `ollama_data`, that is then shared with the `ollama-llm` compose service which will be the actual "running service" that we can then connect to from our Java code, to "call the LLM" as well as for generating the embeddings.

The way this would work in a real production setting would be that the Java Springboot app would have a URL to connect itself to an LLM provider, which, in our case will be the Ollama "self-hosted" model.

Let's see how this works:

```docker
  backend:
    build: .
    ports:
      - "8080:8080"
    environment:
      - SPRING_DATASOURCE_URL=jdbc:postgresql://db:5432/ragdb
      - SPRING_DATASOURCE_USERNAME=postgres
      - SPRING_DATASOURCE_PASSWORD=password
      - SPRING_AI_OLLAMA_BASE_URL=http://ollama-llm:11434/
      - SPRING_AI_OLLAMA_CHAT_OPTIONS_MODEL=tinydolphin
      - SPRING_AI_OLLAMA_CHAT_OPTIONS_ALTERNATIVE_MODEL=tinyllama
      - SPRING_AI_OLLAMA_CHAT_OPTIONS_ALTERNATIVE_SECOND_MODEL=llama3.1
      - SPRING_AI_OLLAMA_EMBEDDING_OPTIONS_MODEL=mxbai-embed-large
      - SPRING_AI_VECTORSTORE_PGVECTOR_REMOVE_EXISTING_VECTOR_STORE_TABLE=true
      - SPRING_AI_VECTORSTORE_PGVECTOR_INDEX_TYPE=HNSW
      - SPRING_AI_VECTORSTORE_PGVECTOR_DISTANCE_TYPE=COSINE_DISTANCE
      - SPRING_AI_VECTORSTORE_PGVECTOR_DIMENSIONS=1024
    depends_on:
      - prepare-models
      - db
    volumes:
      - ollama_data:/root/.ollama
    networks:
      - app-network
```

The key properties for this sub-section are:

```
- SPRING_AI_OLLAMA_BASE_URL=http://ollama-llm:11434/
- SPRING_AI_OLLAMA_CHAT_OPTIONS_MODEL=tinydolphin
- SPRING_AI_OLLAMA_CHAT_OPTIONS_ALTERNATIVE_MODEL=tinyllama
- SPRING_AI_OLLAMA_CHAT_OPTIONS_ALTERNATIVE_SECOND_MODEL=llama3.1
- SPRING_AI_OLLAMA_EMBEDDING_OPTIONS_MODEL=mxbai-embed-large
```

We connect to the Ollama running server and configure the models we have downloaded to connect our Springboot app to them.

Let's now look at how generating embeddings work using the configured model we just downloaded into our Ollama volume.

### Generating embeddings in code with mxbai-embed-large-v1

The basic endpoint we'll use is:

```java
@PostMapping("/query-embedding")
    public String embedding(@RequestBody String query) {
        return embeddingService.computeEmbedding(query).toString();
    }
```

Inside the `EmbeddingService` we have:

```java
@Slf4j
@Service
@AllArgsConstructor
@ConditionalOnProperty("spring.datasource.url")
public class EmbeddingService {

    @Qualifier("ollamaEmbeddingModel")
    private EmbeddingModel embeddingModel;

    public List<Double> computeEmbedding(String query) {
        return embeddingModel.embed(query);
    }
...
}
```

The real link between this piece of code and the docker-compose configuration shown above is "tucked away" in the Qualifier annotation: