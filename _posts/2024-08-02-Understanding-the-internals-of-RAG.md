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
