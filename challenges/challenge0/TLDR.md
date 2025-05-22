# TL;DR

## Key Concepts

- **Large Language Models (LLMs)**: AI models that generate human-like text based on input. Key attributes include:
  - **Parameters**: Indicate model size and complexity.
  - **Tokens**: Measure the number of unique words the model can process.

- **Retrieval-Augmented Generation (RAG)**: A technique that combines LLMs with a retrieval system to enhance text generation by pulling in relevant external information.

## RAG Architecture Components

1. **Vector Database**: Stores embeddings of documents for retrieval.
2. **Ingestion Service**: Handles data feeding, chunking, and embedding.
3. **Chat API**: Facilitates user interaction and response generation.
4. **Chat Website**: User interface for querying documents.
5. **AI Model**: Generates responses based on retrieved information.

## RAG Process Phases

- **Index**: Load, split (chunk), and embed documents.
- **Retrieve**: Fetch relevant documents based on user queries.
- **Generate**: Produce responses using the retrieved context.

## Technologies Used

- **Vector Databases**: Azure AI Search, Azure Cosmos DB, Milvus.
- **Ingestion Services**: Azure AI Document Intelligence, unstructured.io.
- **Frameworks**: LangChain, Semantic Kernel.
- **AI Models**: Azure OpenAI GPT4o, Microsoft Phi-3.5.

## Considerations

- The quality of answers is influenced by the underlying data's quality and organization.
- Chunking strategies affect the relevance and accuracy of responses.
- RAG is not universally applicable; it excels in scenarios requiring up-to-date information but may fall short in cases needing deep contextual understanding.
- RAG can be compared to fine-tuning LLMs, with each having its strengths and weaknesses based on use cases.