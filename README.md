# Applied NLP + LLM Systems (with Evaluation)

This repository contains **small, applied NLP and LLM projects** that turn unstructured text into **reliable, testable systems**.

The focus is not on “cool demos,” but on **problem framing, evaluation, and practical trade-offs**—the parts that actually matter in real products and high-stakes environments.

---

## What I build here

- **Semantic search**  
  Retrieve relevant items from large text corpora using sentence embeddings and similarity search.

- **RAG over documents**  
  Question answering grounded strictly in source documents (PDFs), with explicit citations.

- **Text classification**  
  Transparent comparisons between strong classical baselines (TF-IDF) and transformer-based models.

- **Evaluation & limits**  
  Error analysis, failure modes, and clear discussion of when LLMs are *not* the right tool.

---

## What this repository is (and is not)

This repository is **not** a collection of AI demos or production-ready tools.  
It is a working surface for exploring how ideas, assumptions, and narratives can be turned into **testable systems**.

The emphasis is on:
- structuring ambiguous problems,
- making implicit assumptions explicit,
- designing evaluation *before* automation,
- understanding where models help — and where they do not.

If you are looking for end-to-end automation, this repo will likely feel incomplete.  
If you are interested in **making decisions more grounded and less illusory**, this repository reflects how I approach that work.

---

## Projects

1. **RAG over Documents (PDF QA with citations)**  
   *Goal:* Answer questions using provided documents only, with traceable sources.

2. **Semantic Search (Sentence Transformers)**  
   *Goal:* Retrieve similar questions or documents using embeddings and similarity metrics.

3. **Text Classification (Baseline → Transformer)**  
   *Goal:* Compare simple baselines and transformer models using clear, interpretable metrics.

---

## Focus on Financial & Regulatory Text

A subset of projects applies the same NLP and LLM pipelines to **financial, audit, and regulatory documents**, including annual reports, risk disclosures, and ESG statements.

These domains impose constraints that generic LLM demos often ignore:
- hallucinations are unacceptable,
- traceability and citations are mandatory,
- language carries legal and financial meaning,
- evaluation matters more than fluency.

My background in **financial analysis, accounting, and audit** informs how problems are framed, which signals are extracted, and how outputs are evaluated.  
The goal is not automation for its own sake, but **decision support that can be trusted**.

---

## Author & Perspective

This repository reflects my work at the intersection of:
- applied NLP and data science,
- financial analysis, accounting, and audit,
- research-driven evaluation.

I have worked across academic research, financial and sustainability analytics, industry-facing data science roles, and startup environments.  
This informs the perspective taken here: an emphasis on **traceability, explainability, and decision relevance**, rather than purely generative output.

The projects are designed with **regulated and high-stakes domains** in mind (finance, audit, ESG, compliance), where language is economically and legally consequential and model failure has real costs.

> Each project lives in its own folder with a short README describing the approach, evaluation, and limitations.

---

## Quick start

- Create an environment from `environment.yml` (or follow individual project instructions).
- Run notebooks locally or in Colab.

---

## Example freelance use-cases this maps to

- Build a **RAG prototype** over internal PDFs (policy, legal, ESG, product documentation)
- Implement **semantic search** for a knowledge base or support/ticketing system
- Create **classification pipelines** for routing, tagging, or triage
- Audit an existing LLM workflow: **evaluation, failure modes, and risk analysis**

---

## Contact

If you’d like to collaborate on document search, RAG, or applied NLP systems—especially in regulated or high-stakes contexts—feel free to reach out.