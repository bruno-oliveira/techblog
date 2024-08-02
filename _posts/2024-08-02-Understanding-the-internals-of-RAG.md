In a [previous](https://dev.to/brunooliveira/basic-rag-app-with-spring-ai-docker-and-ollama-1i7j) blog post, I detailed a possible technical setup for having a solid foundation for doing RAG within the Springboot ecosystem, using docker to leverage locally downloaded LLMs and Postgres, configured with the `PGVector` extension to be able to manipulate and store embeddings and work with similarity search from a Postgres DB. If you haven't yet, go read that one, as it will greatly help with digesting this upcoming content, even if I'll try to make this as self-contained as possible.

## Recap - what are embeddings after all?

What are embedding models?
Embedding models are models that are trained specifically to generate vector embeddings: long arrays of numbers that represent semantic meaning for a given sequence of text:

![embeddings.jpg]({{site.baseurl}}/images/embeddings.jpg)

The resulting vector embedding arrays can then be stored in a database, which will compare them as a way to search for data that is similar in meaning. 
