# applied-nlp-llm-systems
# Applied NLP + LLM Systems (with evaluation)

This repository contains small, applied projects that turn unstructured text into reliable, testable systems.
The focus is not “cool demos”, but **problem framing, evaluation, and practical trade-offs**—the parts that matter in real products.

## What I build here
- **Semantic search**: retrieve relevant items from large text corpora using sentence embeddings
- **RAG over documents**: question answering grounded in PDFs with source citations
- **Text classification**: strong baselines (TF-IDF) + transformer improvements, compared transparently
- **Evaluation & limits**: failure cases, error analysis, and when LLMs are the wrong tool

## Why this isn’t “just ChatGPT”
ChatGPT can generate text and code.
This repo demonstrates the parts that require engineering judgment:
- choosing the right problem and scope
- building baselines before using LLMs
- designing evaluation (not just eyeballing outputs)
- controlling failure modes (hallucinations, retrieval errors, leakage)
- making systems reproducible and explainable

## Projects
1. **RAG over Documents (PDF QA with citations)**  
   Goal: answer questions using the provided documents only, and show sources.
2. **Semantic Search (Sentence Transformers)**  
   Goal: retrieve similar questions/documents with embeddings + similarity search.
3. **Text Classification (Baseline → Transformer)**  
   Goal: compare a simple baseline against a transformer approach with clear metrics.

> Each project has its own folder with a short README explaining the approach, evaluation, and limits.

## Quick start
- Create an environment from `environment.yml` (or follow each project’s instructions).
- Run notebooks locally or in Colab.

## Freelance use-cases this maps to
- Build a **RAG prototype** over internal PDFs (policy, legal, ESG, product docs)
- Implement **semantic search** for a knowledge base or ticket system
- Create **classification pipelines** for routing, tagging, triage
- Audit an existing LLM workflow: **evaluation + failure-case analysis**

## Contact
If you want to collaborate on document search / RAG / applied NLP systems, feel free to reach out.