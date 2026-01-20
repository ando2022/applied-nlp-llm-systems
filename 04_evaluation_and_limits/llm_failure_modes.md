# Applied NLP + LLM Systems for High-Stakes Text

This repository shows **how to turn complex, high-risk text into usable decision support**  
using NLP and LLMs — *without* relying on blind automation.

It focuses on **documents where being wrong is costly**:
regulatory disclosures, financial reporting, audit language, ESG statements, and policy text.

The goal is not to build chatbots.  
The goal is to build **systems that help humans reason over text they must be able to trust**.

---

## Why this repository exists

Most NLP and LLM demos assume:
- clean data,
- clear labels,
- forgiving use-cases,
- and unlimited tolerance for hallucinations.

Real organizations do not operate under those assumptions.

This repository exists to show:
- how retrieval, classification, and generation behave **when the text is ambiguous**,
- what breaks first when data is small or weakly labeled,
- where LLMs help — and where they should *not* be used.

If you work with **regulated, financial, legal, or policy-relevant text**, this is the reality.

---

## What this repository demonstrates

**This repository demonstrates:**
- How to frame NLP problems where *accuracy is secondary to traceability*
- How to evaluate systems when metrics are misleading or unavailable
- How retrieval quality dominates downstream LLM behavior
- How simple baselines often outperform complex models in constrained settings
- How to design NLP systems as **decision support**, not automation

**This repository deliberately avoids:**
- production hype,
- leaderboard optimization,
- black-box claims,
- automation without accountability.

---

## What this repository is (and is not)

This is **not** a collection of AI demos.

It is a set of **small, inspectable systems** designed to answer one question:

> *Can a human rely on this output when the consequences matter?*

The emphasis is on:
- framing the problem before choosing the model,
- exposing assumptions instead of hiding them,
- surfacing failure modes early,
- documenting limits clearly.

---

## Methods used — and why they matter

This repository uses **methods that are already common in production**.
The value is not novelty — it is **how these methods are constrained, evaluated, and interpreted**.

---

### 1. Retrieval-Augmented Generation (RAG)

**Location:** `01_rag/`

**What it is here**  
RAG is used as a **document analysis discipline**, not a conversational interface.

Answers:
- must be grounded in retrieved text,
- must include page-level citations,
- must explicitly report when information is missing.

**Why this matters**  
In finance, law, audit, and compliance:
- fluent answers without sources are worse than no answer,
- hallucinations are operational risk,
- retrieval errors are the dominant failure mode.

This project makes those constraints explicit.

---

### 2. Semantic Search (Embedding-Based Retrieval)

**Location:** `02_semantic_search/`

**What it is here**  
Semantic search is treated as an **analytical tool**, not a UX feature.

Instead of asking “does it work?”, the project asks:
- *what kinds of associations does the model make?*
- *when does similarity stop meaning relevance?*

**Why this matters**  
Investigative and research workflows depend on recall and context —  
but false semantic proximity can mislead analysis.

This module exposes similarity scores and forces human inspection.

---

### 3. Text Classification (Baseline → Transformer)

**Location:** `03_text_classification/`

**What it is here**  
A controlled comparison between:
- interpretable classical baselines (TF-IDF + Logistic Regression),
- and transformer-based models.

**Why this matters**  
In small or weakly labeled datasets:
- complex models are unstable,
- metrics fluctuate wildly,
- interpretability matters more than marginal accuracy.

This project shows **when simpler models are the safer choice**.

---

### 4. Evaluation & limits

**Location:** `04_evaluation_and_limits/`

Evaluation is treated as a **design requirement**, not an afterthought.

This includes:
- explicit acknowledgment of weak labels,
- refusal to over-interpret metrics,
- documentation of failure cases,
- and clear statements of *what this system should not be used for*.

---

## Who this repository is for

This work is relevant if you:
- work with financial, regulatory, ESG, legal, or policy text,
- build or evaluate NLP systems used by analysts, researchers, or professionals,
- care more about **trust and traceability** than novelty,
- need to justify *why* a model is used — not just *that* it works.

---

## Author & perspective

This repository reflects work at the intersection of:
- applied NLP and data science,
- financial analysis, accounting, and audit,
- research-driven evaluation.

The perspective throughout is shaped by experience in:
academia, financial and sustainability analytics, industry data science, and startup environments.

The common thread:  
**language is economically and legally consequential**, and models must be treated accordingly.

---

## Quick start

- Create an environment from `environment.yml`
- Run notebooks locally or in Colab
- Each project folder contains a focused README

---

## Example professional use-cases

- Prototype **RAG over internal regulatory or policy documents**
- Implement **semantic search for investigative research**
- Build **classification pipelines** for triage or routing
- Audit existing LLM systems for **risk, failure modes, and evaluation gaps**

---

## Contact

If you work with high-stakes text and want systems that support judgment
instead of replacing it, feel free to reach out.