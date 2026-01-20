# 01 — RAG over Documents (PDF QA with citations)

This directory contains an applied **Retrieval-Augmented Generation (RAG)** project focused on answering questions from long-form documents **with strict page-level citations**.

The emphasis is not on fluent generation, but on **retrieval quality, traceability, and evaluation**—key requirements in regulated and high-stakes domains.

---

## Goal

Build a small, testable RAG pipeline that:
- answers questions **only from provided documents**
- produces **page-level citations**
- fails explicitly when information is not found

This project is intentionally **evaluation-first**: retrieval accuracy and citation discipline matter more than stylistic output.

---

## Document used (case study)

**UBS Group Annual Report 2024**  
Pages used: **41–75**  
(Strategy, regulation, risk factors, accounting and reporting excerpts)

### Why this document is interesting
- Contains real regulatory language, risk disclosures, and accounting judgments
- Hallucinations are unacceptable in this domain
- Long, structured, and legally meaningful
- Demonstrates immediate business value: rapid access to risk and regulatory statements with traceable sources

---

## Contents

- `rag_pipeline.ipynb`  
  End-to-end implementation of a document-based RAG pipeline:
  1. Extract text with page numbers  
  2. Chunk and embed text  
  3. Perform semantic retrieval (top-k)  
  4. Generate answers constrained to retrieved context  
  5. Enforce strict page-level citation requirements  

- `data/`  
  Contains the PDF used in the notebook.

---

## How it works (high level)

### Retrieval
- Sentence Transformer embeddings
- Cosine similarity search over text chunks
- Top-k chunks passed to the generation step

### Generation
- LLM prompted to answer using **only** retrieved chunks
- If information is missing, the model responds explicitly:
  > “Not found in the provided pages.”
- Every factual statement must include a citation (e.g. `(page 46)`)

---

## Example questions answered

1. Regulatory fragmentation and expected regulatory evolution in 2025  
2. Heightened risks from the Credit Suisse acquisition  
3. Risks that may only become apparent with hindsight  
4. Critical accounting estimates and judgments under IFRS  
5. Litigation risk and regulatory scrutiny related to Credit Suisse integration  

Sample answers with citations are included in the repository.

---

## Evaluation notes (manual)

- Retrieval performs best when queries align with section terminology  
  (e.g. “Risk factors”, “regulatory fragmentation”)
- Tables are partially extracted; answers relying on tables may degrade
- Citations act as a guardrail: if a sentence cannot be cited, it is considered invalid output

---

## Running locally

Dependencies can be installed via:

```bash
pip install -r requirements.txt