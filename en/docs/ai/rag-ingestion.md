# RAG Ingestion

## Introduction

Retrieval-Augmented Generation (RAG) is an AI framework that improves how Large Language Models (LLMs) answer questions by giving them access to additional, relevant information.

RAG works through two main processes, which are ingestion and retrieval.

## RAG ingestion
To make use of RAG effectively, data must be systematically ingested into vector databases. This process, known as RAG ingestion, involves setting up a vector database, utilizing embedding models, processing source files and chunking data.
Devant offers a platform to efficiently ingest and manage unstructured documents for RAG.
This guide walks through the key steps of RAG ingestion in Devant.
Devant RAG ingestion supports multiple file types including PDFs (including scanned PDFs), DOCX, PPTX, XLSX, CSV, HTML, MD, images, and audio files (MP3, WAV, M4A, FLAC, OGG).

Navigate to your organization using the **Organization** dropdown in the top left of the Devant console header. In the left navigation menu, click **RAG**, then select **Ingestion**.

### Step 1: Initialize vector store

LLMs receive contextual information as numerical vectors (embeddings). A vector database stores these embeddings for efficient retrieval.
Devant supports a wide range of vector databases like Pinecone, Weaviate, Chroma, and so on. 

1. Select `Pinecone` as the vector database.
2. Enter the API key in the **API Key** field.

    ???+ info "Info"
        To create an API key, refer to the [Pinecone API key documentation](https://docs.pinecone.io/guides/projects/manage-api-keys#create-an-api-key).

3. Enter the **Collection Name**. The collection will be automatically created if it does not exist.
4. Click **Next**.

### Step 2: Configure the embedding model

1. Select `text-embedding-ada-002` embedding model from the **Open AI** dropdown.
2. Enter the API key in the **Embedding Model API Key** field.

    ???+ info "Info"
        To create an API key, refer to the [OpenAI platform documentation](https://platform.openai.com/docs/guides/embeddings).

3. Click **Next**.

### Step 3: Configure chunking

Chunking is used to break large documents into manageable parts because processing them all at once is not feasible.
**Chunking strategy**, **Max segment size**, and **Max overlap size** are automatically populated with default values. You can modify them if needed.

???+ info "Info"
    - **Chunking strategy** defines how text is split into smaller, manageable pieces (chunks).
    - **Max segment size** determines the maximum length of tokens for each chunk.
    - **Max overlap size** defines how many tokens repeat between consecutive chunks.

 ![RAG ingestion](../assets/img/ai/rag-application/rag-ingestion1.gif)

### Step 4: Choose ingestion mode


Choose how you want to perform RAG ingestion:

- **Upload Now**: Instantly upload and ingest files into your vector store. The steps below will guide you through the **Upload Now** workflow for immediate ingestion.
- **Schedule RAG Ingestion**: Set up automated, scheduled ingestion from a selected data source. For step-by-step instructions, refer to the [Schedule Automation](schedule-rag-automation.md) guide.
    
### Step 5: Upload source files

Next, upload your source files (e.g., PDFs, CSVs, or text documents) for processing.

1. Click **Select Files**. This will open the file explorer on your local machine.
2. Select the files you want to upload.
3. Click **Upload**.

    !!! note
        When you click **Upload** it will generate embeddings for the uploaded files and store them in the vector database.

 ![RAG ingestion](../assets/img/ai/rag-application/rag-ingestion2.gif)

### Step 6: Verify

Once processing is complete, execute test queries to ensure proper data retrieval.

1. Enter a query according to the content of the files uploaded in the previous step in the  **Query** field.
2. **Maximum chunks to retrieve** and **Minimum similarity threshold** are automatically populated with default values. You can modify them if needed.

    ???+ info "Info"
        - **Maximum chunks to retrieve** defines the number of matching chunks to retrieve against the query.
        - **Minimum similarity threshold** determines whether a chunk is relevant enough to be considered a match for a given query. Expressed as a value between 0 and 1 (for example, 0.7 or 70% similarity).

3. Click **Retrieve**. The search results will display the chunks that match your query.

 ![RAG ingestion](../assets/img/ai/rag-application/rag-ingestion3.gif)
       

!!! note
    Follow this detailed tutorial [video](https://www.youtube.com/watch?v=8GlrHYS-EYI&list=PLp0TUr0bmhX4colDnjhEKAnZ3RmjCv5y2&ab_channel=WSO2) to understand how to set up the RAG ingestion and create your vector index.
