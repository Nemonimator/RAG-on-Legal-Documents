# ⚖️ Legal RAG Pipeline for Document Analysis

This repository contains a robust Retrieval-Augmented Generation (RAG) pipeline designed to analyze legal documents and answer domain-specific questions with clause-level precision. Built using LangChain, OpenAI embeddings, and Chroma vector store, the system enables scalable semantic search and grounded generation for legal NLP tasks.

---

## 🚀 Project Overview

- **Domain**: Legal document analysis (e.g., NDAs, merger agreements)
- **Goal**: Build a reproducible RAG pipeline that retrieves relevant clauses and generates context-aware answers
- **Tech Stack**: Python, LangChain, OpenAI, ChromaDB, Jupyter Notebook

---

## 🧠 Pipeline Architecture

1. **Preprocessing**  
   - Ingested 694 legal documents  
   - Chunked into 112,433 semantic units using recursive character splitting with overlap

2. **Embedding**  
   - Used `text-embedding-ada-002` via OpenAI  
   - Rate-aware batching to respect token-per-minute limits

3. **Vector Store**  
   - Persisted embeddings using ChromaDB  
   - Supports similarity-based retrieval

4. **RAG Chain**  
   - Connected retriever to `gpt-3.5-turbo` using LangChain's `RetrievalQA`  
   - Modular function returns both generated answers and supporting source documents

---

## 📊 Evaluation Results

### Full Benchmark Evaluation
| Metric     | Score   |
|------------|---------|
| ROUGE-1    | 0.4105  |
| ROUGE-2    | 0.2715  |
| ROUGE-L    | 0.4105  |
| BLEU       | 4.3282  |

### First 100 Questions Evaluation
| Metric     | Score   |
|------------|---------|
| ROUGE-1    | 0.3087  |
| ROUGE-2    | 0.1656  |
| ROUGE-L    | 0.2784  |
| BLEU       | 9.1715  |

---

## 🔍 Key Insights

- The pipeline retrieves semantically relevant clauses and generates legally coherent answers.
- ROUGE scores confirm structural and conceptual alignment with benchmark ground truths.
- BLEU scores reflect moderate phrasing fidelity, with room for improvement in exact clause quoting.
- Performance improves on shorter, clause-focused queries—highlighting the importance of chunk granularity and retrieval precision.

---

## 🧪 Recommendations

- Try `"refine"` or `"map_reduce"` chain types for longer contexts
- Run RAGAS for deeper metrics like faithfulness and context precision
- Use semantic similarity scoring for softer evaluation
- Add metadata filtering for document-type-specific retrieval

---

## 📁 Repository Structure
