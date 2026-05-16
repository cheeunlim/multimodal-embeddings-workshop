# **Multimodal Media Search with Gemini Embedding 2 and Vector Search 2.0**

This project demonstrates how to build a state-of-the-art multimodal retrieval system using Gemini Embedding 2 and Vertex AI Vector Search 2.0 on Google Cloud. It is designed to handle mixed media types, including images and long-form videos, enabling semantic search across different modalities.

## **Workflow Overview & Architecture**

The project is structured into 6 main phases, guiding you from environment setup to advanced hybrid search implementation.

### **Phase 1: Environment Setup & Initialization**
Configure necessary environment variables and constants, including Project ID, Region, worker counts, and GCS bucket names. This phase ensures all prerequisites are met for interacting with Google Cloud services.

### **Phase 2: Data Loading & File List Generation**
Retrieve the list of files from the specified Google Cloud Storage (GCS) bucket and classify them into images and videos. This dynamic approach replaces static dataset registries.

### **Phase 3: Embedding Extraction & Video Processing**
*   **Video Chunking**: Large video files are segmented into smaller, manageable chunks (e.g., 30 seconds) to allow for granular retrieval and precise timestamp seeking.
*   **Parallel Processing**: Utilizes `ThreadPoolExecutor` to parallelize embedding extraction for both video chunks and images, significantly speeding up the process.
*   **Gemini Embedding 2**: Leverages the latest Gemini Embedding model to generate high-dimensional dense vectors capturing the semantic essence of the media content.

### **Phase 4: Vector Search 2.0 Setup**
Initialize service clients for Vertex AI Vector Search 2.0 and define the data schema. This setup enables storing media embeddings along with metadata in a managed search index.

### **Phase 5: Media Search & Rendering**
Define search functions and rendering utilities to visualize the results. This phase allows you to query the index and see the matching images or video chunks displayed directly in the notebook.

### **Phase 6: Advanced Search (Hybrid & Sparse Vectors)**
Implement hybrid search by combining dense vectors from Gemini with sparse vectors (e.g., BM25) generated from natural language descriptions. This approach enhances search accuracy by capturing both semantic meaning and specific keywords.

---

## **Key Technologies**

*   **Google Gemini Models**: For multimodal embedding generation and natural language understanding.
*   **Vertex AI Vector Search 2.0**: For scalable, low-latency vector similarity search.
*   **MoviePy**: For video processing and chunking.
*   **Google Cloud Storage**: For storing source media files.

## **How to Use**

1.  **Open Notebook**: Open `multimodal_search.ipynb`.
2.  **Configure Environment**: Update the `PROJECT_ID` and `source_bucket_name` in Cell 2.
3.  **Run Cells**: Execute the cells sequentially to process data, index embeddings, and perform searches.

> [!NOTE]
> This notebook uses Vertex AI Vector Search 2.0 in beta (`v1beta`), which supports direct data object management and search without manual index deployment in some configurations.
