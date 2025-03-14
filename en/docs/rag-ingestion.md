## Introduction

Retrieval-Augmented Generation (RAG) is a powerful approach that enhances Large Language Models (LLM) accuracy by providing contextual data sources.
To effectively use RAG, we need a structured way to ingest and store data. 
This process, known as RAG Ingestion, involves configuring a vector database, embedding models, chunking, and processing source files.
This guide walks through the key steps of RAG Ingestion in Devant.

Go to your Organization by selecting the organization from the **Organization** dropdown in the top left corner. Select **RAG Ingestion** from the **Admin** dropdown in the bottom of the left navigation. 

## Step 1: Initialize Vector Store

Contextual information is provided as numerical vectors (embeddings) to LLMs. These embeddings are stored in a vector database for efficient retrieval.
Devant supports a wide range of vector databases like Pinecone, Weaviate, Chroma, and so on. 

1. Select `Pinecone` as the vector database.
2. Enter the API key in the **API Key** field.

    ???+ info "Info"
        Refer to the [Pinecone API Key documentation](https://docs.pinecone.io/guides/projects/manage-api-keys#create-an-api-key) to create an API key.

3. Enter the **Collection Name**. The collection will be automatically created if it does not exist.
4. Click **Next**.

## Step 2: Configure the Embedding Model

1. Select `text-embedding-ada-002` embedding model from the **Open AI** dropdown.
2. Enter the API key in the **Embedding Model API Key** field.

    ???+ info "Info"
        Refer to the [OpenAI Platform documentation](https://platform.openai.com/docs/guides/embeddings) to create an API key.

3. Click **Next**.

## Step 3: Configure Chunking

Since large documents cannot be processed at once, we use chunking to break them into manageable parts.
**Chunking strategy**, **Max segment size**, and **Max overlap size** are automatically populated with default values. You can modify them if needed.

???+ info "Info"
    - **Chunking strategy** defines how text is split into smaller, manageable pieces (chunks).
    - **Max segment size** determines the maximum length of tokens for each chunk.
    - **Max overlap size** defines how many tokens are repeated between consecutive chunks.

## Step 4: Upload Source Files

Next, upload your source files (e.g., PDFs, CSVs, or text documents) for processing.

1. Click **Select Files**. This will open the file explorer on your local machine.
2. Select the files you want to upload.
3. Click **Upload**.

    !!! note
        When you click **Upload** it will also generate embeddings for the uploaded files and store them in the vector database.

## Step 5: Verify

Once processing is complete, execute test queries to ensure proper data retrieval.

1. Enter a query according to the content of the files uploaded in the previous step in the  **Query** field.
2. **Maximum chunks to retrieve** and **Minimum similarity threshold** are automatically populated with default values. You can modify them if needed.

    ???+ info "Info"
        - **Maximum chunks to retrieve** defines the number of matching chunks to retrieve against the query.
        - **Minimum similarity threshold** determines whether a chunk is relevant enough to be considered a match for a given query. Expressed as a value between 0 and 1 (for example, 0.7 or 70% similarity).

3. Click **Retrieve**. The search results will display the chunks that match the query.
   
<a href="{{base_path}}/assets/img/rag-ingestion.gif"><img src="{{base_path}}/assets/img/rag-ingestion.gif" alt="RAG Ingestion" width="80%"></a>
