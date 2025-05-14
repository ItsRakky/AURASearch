# AuraSearch: A Hierarchical RAG System with Interactive Knowledge Visualization

[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)  

## Overview

AuraSearch is a novel Retrieval Augmented Generation (RAG) system designed to enhance the relevance, explainability, and user control of knowledge retrieval compared to traditional RAG approaches. It leverages a hierarchical semantic structure ("AuraGrid") built from embedding-based clustering to organize data, enabling efficient traversal and targeted context aggregation for Large Language Models (LLMs).  The core innovation lies in its interactive 2D/3D visualization, allowing users to trace the retrieval path and explore the knowledge base visually.

## Key Features

*   **Hierarchical Semantic Structure ("AuraGrid"):** Data is organized into a multi-level hierarchy of "Sectors," "Regions," "Zones," and “Families” based on semantic similarity determined by vector embeddings.
*   **Configurable S-Level Traversal:** Users (or administrators) can control the depth of search within the AuraGrid hierarchy using configurable "S-Levels" – thresholds for similarity scores at each level, allowing a balance between speed, comprehensiveness, and computational cost.
*   **Multipath Exploration:**  When queries are ambiguous or span multiple topics, the system explores multiple branches of the AuraGrid simultaneously ("multipath traversal") to retrieve diverse perspectives.
*   **Interactive "Trace Trail" Visualization (2D/3D):** The retrieval process is visualized as a path ("Trace Trail") through the AuraGrid, providing users with a clear understanding of how the system arrived at its results.  This visualization can be in 2D or 3D for enhanced spatial comprehension.
*   **LLM-Augmented Answers:** Context retrieved from activated zones within the AuraGrid is used to prompt an LLM for generating answers grounded in specific knowledge sources.
*   **Interactive Curation & Feedback Loop:** Users can provide feedback on retrieved content and potentially edit data associated with individual zones, contributing directly to the accuracy and quality of the knowledge base.

## Architecture & Components

1.  **Data Ingestion & Processing:** Loads documents, chunks them into manageable segments, and extracts metadata.
2.  **Embedding Module:** Generates vector embeddings for each text chunk using pre-trained sentence transformer models or LLM embedding APIs (e.g., OpenAI's `text-embedding-ada-002`).
3.  **AuraGrid Indexing:**
    *   Clustering: Recursively clusters embedded chunks to define hierarchical levels (Sectors, Regions, Zones, Families).
    *   Prototype Vectors: Calculates prototype vectors for each level based on cluster centroids.
    *   Metadata Storage: Stores chunk IDs and their assigned AuraGrid path.  Optionally stores vector embeddings in a Vector Database.
4.  **Query Processing Engine:**
    *   Embeds user query.
    *   Traverses the AuraGrid hierarchy, applying S-level thresholds to identify activated zones/families.
    *   Performs fine-grained similarity search within activated families (using a Vector Database or direct comparison).
5.  **Context Aggregation Module:** Formats retrieved chunks and metadata into prompts for the LLM.
6.  **LLM Augmentation Module:** Sends aggregated context to an LLM API to generate answers.
7.  **Visualization & Interaction Layer:** Renders the AuraGrid (2D or 3D), visualizes the “Trace Trail,” displays retrieved results, and provides user interaction controls.

## Technologies Used (Prototype Implementation)

*   **Programming Language:** Python
*   **Frontend Framework:** React (or Vue/Svelte)
*   **Embedding Models:** Sentence Transformers library (`sentence-transformers`), OpenAI API, Cohere Embed models
*   **Vector Database (Optional):** ChromaDB, FAISS, Weaviate, Pinecone
*   **LLM APIs:** ANY
*   **3D Visualization Library (for 3D Prototype):** Three.js

## Getting Started (Code yet to be published)

*  **Data Preparation:** Gather and preprocess your knowledge base documents.
*   **0 Data setup:** Use database as is, allow for dynamic addition of information to database during runtime.

## Future Enhancements

*   **Self-Optimizing S-Levels:** Use machine learning to dynamically learn and adjust the AuraGrid structure based on query patterns.
*   **Proactive Contextualization:** Suggest relevant zones before a full query is typed.
*   **Personalized AuraGrids:** Adapt the hierarchy based on user profiles or roles.
*   **Cross-Lingual Retrieval:** Extend to multi-lingual knowledge bases.

## License

This project is licensed under the [MIT License](LICENSE).

---
