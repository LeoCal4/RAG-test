# RAG-test
Testing various implementations of a RAG system.

## Objectives
- [x] RAG systems research
- [x] Exploratory testing
- [ ] Generate an evaluation dataset
- [ ] Implementation without predefined libraries
- [ ] LlamaIndex implementation
- [ ] Haystack implementation

## General Pipeline
1. The user sends a question (*query*) to the system.
2. The Embedding Model creates an embedded representation of the query.
3. The Retriever finds the most similar documents stored in a Vector DB according to the generated embeddings, using a similarity metric.
4. The relevant documents retrieved this way are sorted by relevance using the scores calculated using a Reranked model.
5. The original user question and the most relevant documents are used to generated a prompt for a LLM, in order to answer using the retrieved information.
6. The answer is show to the user.

## Models
- Query LLM: [Llama 2 7B (chat version)](https://huggingface.co/meta-llama/Llama-2-7b-chat-hf)
  - 7B can easily run in its quantized form on Google Colab free GPU tier while giving decent results
- Embeddings LLM: [BGE Small EN](https://huggingface.co/BAAI/bge-small-en-v1.5)
  - Small model with great results, its family is quite high in the Huggingface leaderboard for the embeddings
- Reranking LLM: [BGE Reranker Base]()

## Dataset
As of now, the first tests are based on the [News Articles Dataset](https://www.kaggle.com/datasets/asad1m9a9h6mood/news-articles), which consists in ~2500 news articles scraped from https://www.thenews.com.pk, consisting of business and sports articles. Since these are very specific, it can be assumed that the models should not have a precise prior knowledge about the events reported in the articles, therefore they are forced to gather the knowledge needed to answer correctly from the retrieved documents.
