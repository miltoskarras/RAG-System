#  Langflow RAG System – AI-Powered Q&A on Graphic Design

This project demonstrates a lightweight, Retrieval-Augmented Generation (RAG) system built using [Langflow](https://github.com/logspace-ai/langflow). It allows users to query a document and receive accurate, context-aware answers, using embeddings and a vector database.

---

##  Project Overview

The system processes a PDF document titled **“Graphic Designer and His Subject”** by Angeliki Athanasiadi and provides natural language responses to user questions based on that document.

It uses:

-  **Langflow** as a flow-based interface
-  **OpenAI GPT-4o Mini** for answer generation
-  **Astra DB** as a vector store (via [DataStax Astra](https://www.datastax.com/astra))
-  **OpenAI Embeddings** for semantic chunk retrieval

---

##  How It Works

1. **Document Upload** – A PDF is loaded via the `File` node in Langflow.
2. **Text Splitting** – The content is broken into overlapping chunks using the `Split Text` node.
3. **Embedding Generation** – Chunks are encoded using `text-embedding-3-small`.
4. **Astra DB Storage** – Embeddings are stored in a custom `rag_03_collection` inside `Assig01` DB.
5. **Semantic Search** – User queries are converted to embeddings and matched to document chunks.
6. **Prompt Assembly** – Retrieved context is injected into a prompt template.
7. **Answer Generation** – GPT-4o mini generates a natural language response.
8. **Display** – Output is shown in the `Chat Output` node.

---

##  Flow Screenshot

![Langflow Full Pipeline](docs/screenshot-flow.png)

> *(See full report in the `/docs` folder for step-by-step screenshots.)*

---

##  Setup Instructions

> You don’t need to install Langflow locally—this project runs on Langflow’s **Playground (Astra-integrated)**.

### Prerequisites

- OpenAI API key
- Astra DB account (free tier available)
- Langflow Playground access: [https://astra.datastax.com/langflow](https://astra.datastax.com/langflow)

### Run the Flow

1. Fork this repository and download the `.json` Langflow file.
2. Go to [Langflow Playground](https://astra.datastax.com/langflow).
3. Upload the flow under `My Projects`.
4. Paste your OpenAI and Astra API keys.
5. Upload your document in the flow and click "Play".

---

##  Files

| File | Description |
|------|-------------|
| `RAG System.json` | Langflow export file |
| `RAG System Report.pdf` | Final assignment report |
| `README.md` | Project documentation |

---

## ⚠ Known Issues

- Langflow Playground may crash or lag under large document loads.
- PDF conversion may require size optimization.
- Embedding consistency is crucial between ingestion and querying.

---

##  Future Improvements

-  Add citation references to retrieved answers
- 📊 Integrate feedback/rating loop for answer accuracy

---

## Author

**Miltiades Karras**  
Course: *Multi-Agent Systems & Game Theory*  
University Assignment – 2025

---

##  License

This project is for educational purposes. Contact the author for reuse permissions.
