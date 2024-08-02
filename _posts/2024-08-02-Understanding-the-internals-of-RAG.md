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
