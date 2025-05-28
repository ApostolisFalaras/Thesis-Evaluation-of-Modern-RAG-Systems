# Evaluating Modern Retrieval-Augmented Generation (RAG) Systems 

**Author:** Apostolos Falaras
**Thesis:** Undergraduate Thesis in Electrical & Computer Engineering
**University:** University of Thessaly
**Supervisor:** Prof. Manolis Vavalis
**Thesis Conducted:** October 2024 - February 2025

## 📚 Overview

This repository contains the code and evaluation results of my Undergraduate Thesis on **Retrieval-Augmented Generation (RAG)** systems. The project investigates how effectively modern RAG frameworks evaluate Generative AI systems across both **general-purpose** and **legal** domains.

## 🎯 Objective

The goal of this thesis was:
- Analyze and compare state-of-the-art RAG evaluation frameworks: **RAGChecker**, **RAGAs**, **ARES**, and **AutoRAG**
- Apply them to a RAG pipeline combining retriever and generator components
- Evaluate performance on two datasets:
    -  **MS MARCO** (generic knowledge)
    -  **LegalBench-RAG** (domain-specific legal data)
- Use **Chroma** and **SQLiteVec** as both the **vector store and retriever**, depending on the dataset:
    - **Chroma** was used for the MS MARCO pipeline
    - **SQLiteVec** was used for the LegalBench-RAG pipeline

## 🧠 Background

LLMs are increasingly being deployed in knowledge-intensive domains, yet they often face:
- Outdated or incomplete training data
- Inability to ground responses in real-time information

RAG systems solve this by combining:
- **Retrievers**: Find relevant external passages based on the query
- **Generators**: Answer the query using retrieved context and model knowledge

## ⚙️ Project Structure

- `RAG_Evaluation_MS_MARCO.ipynb` — evaluation on general dataset (MS MARCO)
- `RAG_Evaluation_LegalBench-RAG.ipynb` — evaluation on legal dataset
- `Falaras_Apostolos_Thesis_Report.pdf` — full thesis report detailing architecture, literature review, evaluation, and results
- `requirements.txt` — list of Python packages required

## 🧪 Evaluation Frameworks Used

| Framework    | Focus Area                                                          | Open Source  |
| ---------------- | ------------------------------------------------ | ----------------- |
| RAGChecker | Fine-grained claim-based retrieval and generation evaluation    |  ✅ |  
| RAGAs             | LLM-based faithfulness, context and answer relevance scores | ✅ |
| ARES                | Automated evaluation with synthetic data and LLM judges of faithfulness, context and answer relevance | ✅ |
| AutoRAG        | Modular pipeline evaluation with built-in retrievers, rerankers and generators | ✅ | 

Each notebook demonstrates how these tools were used and compares their effectiveness.









