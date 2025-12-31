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
