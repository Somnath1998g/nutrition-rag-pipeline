# nutrition-rag-pipeline
A high-performance RAG pipeline for semantic search in nutrition textbooks. Uses Sentence-Transformers, PyMuPDF, and FAISS for 10x faster vector retrieval.
# 🥗 Nutrition RAG Pipeline

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?style=for-the-badge&logo=python&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)
![FAISS](https://img.shields.io/badge/FAISS-Vector_Search-green?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)

A comprehensive **Retrieval-Augmented Generation (RAG)** pipeline designed to ingest, chunk, embed, and retrieve knowledge from the *Human Nutrition (2020 Edition)* textbook.

This project demonstrates how to build a semantic search engine from scratch using **Sentence Transformers** for embedding and compares the performance of **PyTorch** brute-force search against **Facebook AI Similarity Search (FAISS)**.

---

## 🏗️ Project Architecture

The pipeline follows these distinct stages:

1.  **Ingestion:** Loading raw PDF documents using `PyMuPDF`.
2.  **Preprocessing:** Cleaning text and performing sentence-level splitting using `spaCy`.
3.  **Chunking:** Grouping sentences into fixed-size context windows (10 sentences) to optimize embedding context.
4.  **Embedding:** Encoding text chunks into 768-dimensional vectors using the `all-mpnet-base-v2` model.
5.  **Retrieval:** Performing similarity search to find the most relevant textbook passages for a user query.

---

## 📂 Repository Structure

```text
.
├── data/
│   └── Human-Nutrition-2020.pdf   # Source PDF (place your file here)
├── notebooks/
│   └── RAG_application.ipynb      # Main pipeline logic
├── output/
│   ├── text_chunks.csv            # Processed text data
│   └── embeddings.index           # Saved FAISS index
├── requirements.txt               # Dependencies
└── README.md                      # Project documentation
```
## ⚡ Quick Start
### 1. Clone the Repository
```bash
git clone [https://github.com/your-username/nutrition-rag-pipeline.git](https://github.com/your-username/nutrition-rag-pipeline.git)
cd nutrition-rag-pipeline
```
### 2. Set Up Virtual Environment
```bash
python -m venv venv

# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate
```
### 3. Install Dependencies
```bash
pip install -r requirements.txt
```
### 4. Run the Pipeline
Ensure you have the PDF file in the root or data directory, then launch Jupyter:
```bash
jupyter notebook notebooks/RAG_application.ipynb
```
## 🔍 Usage & Examples

### 🧠 Semantic Search
Unlike traditional keyword search, this system understands the context of your question. It uses vector embeddings to find the most conceptually relevant passages from the textbook.

**Example Query:**
> "What are the functions of macronutrients?"

**Top Retrieved Result:**
> 📖 *"Macronutrients: Nutrients that are needed in large amounts are called macronutrients. There are three classes of macronutrients: carbohydrates, lipids, and proteins. These can be metabolically processed into cellular energy. The energy from macronutrients comes from their chemical bonds. This chemical energy is converted into cellular energy that is then utilized to perform work..."*

---

### 🚀 Performance Benchmark
The pipeline evaluates two different methods of retrieval. While brute-force search is accurate, **FAISS** provides the industrial-scale speed required for large datasets.

| Search Method | Technical Description | Avg. Search Time |
| :--- | :--- | :--- |
| **PyTorch (Dot Product)** | Brute-force tensor calculation on GPU | `~4.5 ms` |
| **FAISS (IndexFlatIP)** | Optimized Vector Indexing & Retrieval | **`~0.5 ms`** |

> **Result:** Using FAISS provides a **10x speed improvement**, making it the ideal choice for production-level RAG applications.

---

### 🛠️ Key Components


- **Sentence Splitting:** Powered by `spaCy` to ensure context remains intact.
- **Vector Engine:** `all-mpnet-base-v2` (HuggingFace) for high-accuracy embeddings.
- **Indexing:** `FAISS` for lightning-fast similarity searching.
