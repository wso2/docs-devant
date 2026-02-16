## Introduction

Retrieval-Augmented Generation (RAG) is an AI framework that improves how Large Language Models (LLMs) answer questions by giving them access to additional, relevant information.

RAG works through two main processes, which are ingestion and retrieval.

## RAG ingestion
To make use of RAG effectively, data must be systematically ingested into vector databases. This process, known as RAG Ingestion, involves setting up a vector database, utilizing embedding models, processing source files and chunking data.
Devant offers a platform to efficiently ingest and manage unstructured documents for RAG.
This guide walks through the key steps of RAG Ingestion in Devant.
Devant RAG ingestion has support for multiple file types including PDFS, DOCX, PPTX, XLSX, HTML as well as audio support (MP3, WAV, OGG) 

Go to your Organization by selecting the organization from the **Organization** dropdown in the top left corner. Select **Ingestion** from the **RAG** dropdown at the bottom of the left navigation. 

### Step 1: Initialize Vector Store

LLMs receive contextual information as numerical vectors (embeddings). A vector database stores these embeddings for efficient retrieval.
Devant supports a wide range of vector databases like Pinecone, Weaviate, Chroma, and so on. 

1. Select `Pinecone` as the vector database.
2. Enter the API key in the **API Key** field.

    ???+ info "Info"
        To create an API key, refer to the [Pinecone API Key documentation](https://docs.pinecone.io/guides/projects/manage-api-keys#create-an-api-key).

3. Enter the **Collection Name**. The collection will be automatically created if it does not exist.
4. Click **Next**.

### Step 2: Configure the Embedding Model

1. Select `text-embedding-ada-002` embedding model from the **Open AI** dropdown.
2. Enter the API key in the **Embedding Model API Key** field.

    ???+ info "Info"
        To create an API key, refer to the [OpenAI Platform documentation](https://platform.openai.com/docs/guides/embeddings).

3. Click **Next**.

### Step 3: Configure Chunking

Chunking is used to break large documents into manageable parts because processing them all at once is not feasible.
**Chunking strategy**, **Max segment size**, and **Max overlap size** are automatically populated with default values. You can modify them if needed.

???+ info "Info"
    - **Chunking strategy** defines how text is split into smaller, manageable pieces (chunks).
    - **Max segment size** determines the maximum length of tokens for each chunk.
    - **Max overlap size** defines how many tokens repeat between consecutive chunks.

### Step 4: Choose Ingestion Mode

Select the method for performing RAG ingestion:

- **Upload Now**: Upload and ingest files immediately. This page describes the Upload Now workflow.
- **Schedule RAG Ingestion**: Configure automated, scheduled ingestion from a selected datasource. For detailed instructions, see the [Schedule RAG Ingestion](schedule-rag-ingestion.md) guide.
    
### Step 5: Upload Source Files

Next, upload your source files (e.g., PDFs, CSVs, or text documents) for processing.

1. Click **Select Files**. This will open the file explorer on your local machine.
2. Select the files you want to upload.
3. Click **Upload**.

    !!! note
        When you click **Upload** it will generate embeddings for the uploaded files and store them in the vector database.

### Step 6: Verify

Once processing is complete, execute test queries to ensure proper data retrieval.

1. Enter a query according to the content of the files uploaded in the previous step in the  **Query** field.
2. **Maximum chunks to retrieve** and **Minimum similarity threshold** are automatically populated with default values. You can modify them if needed.

    ???+ info "Info"
        - **Maximum chunks to retrieve** defines the number of matching chunks to retrieve against the query.
        - **Minimum similarity threshold** determines whether a chunk is relevant enough to be considered a match for a given query. Expressed as a value between 0 and 1 (for example, 0.7 or 70% similarity).

3. Click **Retrieve**. The search results will display the chunks that match the query.

       <a href="{{base_path}}/assets/img/ai/rag-application/rag-ingestion.gif"><img src="{{base_path}}/assets/img/ai/rag-application/rag-ingestion.gif" alt="RAG Ingestion" width="80%"></a>

!!! note
    Follow this detailed tutorial [video](https://www.youtube.com/watch?v=8GlrHYS-EYI&list=PLp0TUr0bmhX4colDnjhEKAnZ3RmjCv5y2&ab_channel=WSO2) to understand how to set up the RAG ingestion and create your vector index.

## RAG retrieval

To retrieve chunks that have already been ingested (without uploading new files), navigate to the **Retrieve** tab under the **RAG** menu. Enter the necessary connection details for your vector database, select the embedding model, and submit your query. The system will return the most relevant chunks based on your query.

Devant's retrieval process uses a reranking model to ensure that only the most accurate and contextually relevant chunks are returned.

After completing the RAG ingestion process, you can implement a rag retrieval to connect your vector database with user queries and generate responses.

For detailed implementation steps and configuration, refer to the [RAG retrieval](https://bi.docs.wso2.com/integration-guides/ai/rag/build-a-rag-application/#rag-retrieval) tutorial in the WSO2 Integrator: BI documentation.
