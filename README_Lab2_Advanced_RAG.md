# Lab 2 — Advanced RAG Results (CS 5542)

> **Course:** CS 5542 — Big Data Analytics and Apps  
> **Lab:** Advanced RAG Systems Engineering  
> **Student Name:**  Ruixuan Hou
> **GitHub Username:**  RHou02
> **Date:**  Jan 29 2026

---

## 1. Project Dataset
- **Query:** Q1: What are the core principles for processing personal data under GDPR Article 5?
  - **Relevant Evidence (keywords / entities / constraints):** GDPR Article 5, lawfulness, fairness, transparency, purpose limitation, data minimisation, accuracy, storage limitation, integrity, confidentiality, accountability
  - **Correct Answer Criteria (1–2 bullets):**
    - Lists at least 4+ principles correctly
    - Notes controller responsibility ("accountability")

- **Query:** Q2: According to GDPR Article 13, what information must a controller provide when collecting personal data from the data subject?
  - **Relevant Evidence (keywords / entities / constraints):** Controller identity, purpose, legal basis, recipients, transfers, retention, rights, complaints, automated decision-making
  - **Correct Answer Criteria (1–2 bullets):**
    - Lists key categories clearly
    - Notes info must be provided at time of collection

- **Query:** Q3: If a landlord collects tenant personal data in a lease application, do they need to explain the retention period and whether automated decision-making is used?
  - **Relevant Evidence (keywords / entities / constraints):** GDPR Article 13(2)(a), Article 13(2)(f), storage period, automated decision-making
  - **Correct Answer Criteria (1–2 bullets):**
    - Answer 'Yes' with justification citing Article 13
    - Optionally refer to Article 5 storage limitation principle

---

## 3. System Design
- **Chunking Strategy:** Semantic  
- **Chunk Size / Overlap:** 1200 / 200 characters  
- **Embedding Model:** sentence-transformers/all-MiniLM-L6-v2  
- **Vector Store / Index:** FAISS  
- **Keyword Retriever:** TF-IDF + BM25  
- **Hybrid α Value(s):** 0.2, 0.5, 0.8  
- **Re-ranking Method:** Cross-Encoder (ms-marco-MiniLM-L-6-v2)

### Design Rationale
We chose semantic chunking to preserve context across sentences. FAISS allows fast vector search, while TF-IDF + BM25 captures keyword signals. Hybrid retrieval balances semantic and keyword matches using α. Cross-encoder reranking improves precision by reordering retrieved chunks but adds extra compute.

---

## 4. Results
v


*Replace numbers with your actual results.*

---

## 5. Failure Case
- **What failed?** One chunk missed key clause for GDPR Article 13  
- **Which layer failed?** Chunking  
- **Proposed system-level fix:** Use smaller chunk size or semantic overlap increase to capture entire sentence context

---

## 6. Evidence of Grounding
Provide one example of a **RAG-grounded answer with citations**:
> **Answer:** The controller must provide the data subject with information including identity, purpose, legal basis, recipients, rights, and retention period at the time of collection.  
> **Citations:** [Chunk 3], [Chunk 7]

---

## 7. Reflection (3–5 Sentences)
Building this RAG system taught us that semantic chunking improves context retention. Hybrid retrieval balances semantic and keyword matP@5_keywordR@10_keywordP@5_vectorR@10_vectorP@5_hybridR@10_hybridqueryalpha_usednum_relevant_labeled00.00.00.00.00.00.0Q1: What are the core principles for processin...0.2010.00.00.00.00.00.0Q2: According to GDPR Article 13, what informa...0.2020.00.00.00.00.00.0Q3: If a landlord collects tenant personal dat...0.20￼ches. Cross-encoder reranking increases Precision@K but slows computation. Failures often come from chunking too coarsely. Adjusting chunk size or overlap is a concrete fix.

---

## Reproducibility Checklist
- [x] Project dataset included or linked  
- [x] Queries + rubric filled  
- [x] Results table completed  
- [ ] Screenshots included in repo  
- [x] Notebook runs end-to-end
