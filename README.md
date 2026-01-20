# Applied NLP + LLM Systems  
### Understanding how text systems help — and where they fail

This repository documents a small set of **applied NLP experiments** built to understand a very practical question:

> **How can we find, explain, and organize information in large text documents — and when do NLP systems quietly break?**

Instead of building polished demos, this work focuses on **clarity, limits, and decision-making**.  
The goal is not automation for its own sake, but understanding **which tools answer which questions**, and which ones should *not* be used at all.

---

## The core problem this repo explores

When working with long documents (financial reports, regulatory texts, policies, disclosures), people usually want to do one or more of the following:

1. **Find where relevant information is**
2. **Understand what a document says about a specific question**
3. **Organize text into categories for easier navigation**

These are **three different problems**.

This repository explores **one method for each**, using simple, inspectable implementations:

| Human question | NLP method |
|---------------|-----------|
| Where should I look? | Semantic Search |
| What does it say? | RAG (Retrieval-Augmented Generation) |
| How should this be organized? | Text Classification |

The projects are intentionally small so that **behavior and failure modes are visible**.

---

## 01 — Semantic Search  
### *“Where should I look?”*

### What problem this solves

Semantic search is about **finding relevant text**, not answering questions.

Given:
- a set of document passages
- a query or topic

The system returns the passages that are **closest in meaning**, even if they do not share exact words.

### How it works (conceptually)

- Each text passage is converted into a numerical vector using an **embedding model**
- The query is embedded the same way
- Similarity (cosine similarity) is computed between vectors
- Passages are ranked by closeness

There is **no generation**, no reasoning, no summarization.

### What this experiment showed

- The most relevant passage was often ranked first
- Secondary results were thematically related but sometimes irrelevant
- Similarity scores exposed uncertainty rather than hiding it

### Why this matters

Semantic search is a **foundation**:
- RAG depends on it
- Classification pipelines often start with it
- Human review is still required

**Key insight:**  
Semantic similarity is probabilistic, not factual.  
It helps you *look in the right place*, but it does not tell you what is true.

---

## 02 — RAG over Documents (PDF QA with citations)  
### *“Answer — but only from the document”*

### What problem this solves

RAG (Retrieval-Augmented Generation) is used when you want:
- answers to questions
- grounded strictly in source documents
- with traceable citations

This is critical in financial, legal, and regulatory contexts where:
- hallucinations are unacceptable
- sources must be explicit
- “not found” is a valid answer

### How it works

RAG combines two steps:

1. **Semantic search** retrieves relevant passages  
2. An **LLM** generates an answer **only from those passages**

The model is constrained:
- it cannot use outside knowledge
- every factual claim must be traceable to retrieved text

### What this experiment showed

- When retrieval worked well, answers were accurate and traceable
- When retrieval was weak, answers degraded accordingly
- The LLM never “fixed” bad retrieval — it amplified it

### Why this matters

RAG systems are often described as “LLMs over documents”.

This experiment shows the reality:

> **RAG quality is determined more by retrieval than by generation.**

LLMs do not create truth — they rearrange what they are given.

---

## 03 — Text Classification  
### *“How should this text be labeled?”*

### What problem this solves

Classification does **not answer questions**.

It assigns labels to text so that:
- content can be filtered,
- routed,
- grouped,
- or prioritized.

Example:
- regulation vs financial performance
- risk vs strategy
- legal vs operational

### What was tested

Two approaches were intentionally compared:

#### 1. Baseline model
- TF-IDF features + Logistic Regression
- Very small dataset
- Two broad, overlapping categories

#### 2. Pretrained transformer
- A sentiment classifier applied to regulatory text
- Used intentionally to demonstrate **model–task mismatch**

### What happened (and why it matters)

- The baseline model produced unstable, near-random results  
  → Correct behavior given insufficient data

- The transformer produced confident predictions  
  → But they were meaningless for the task

The transformer answered a **different question** (“positive vs negative sentiment”) while appearing highly confident.

### Key insight

> **Confidence is not correctness.**

Classification without:
- sufficient data,
- clear labels,
- domain-specific training

is not just weak — it is misleading.

---

## What this repository demonstrates

- How different NLP methods answer **different human questions**
- Why semantic search, RAG, and classification are not interchangeable
- How failure modes appear in realistic, small-data settings
- Why evaluation matters more than fluent output
- When automation should *not* be applied

---

## What this repository does *not* claim

- Production-ready systems  
- State-of-the-art performance  
- Generalizable benchmarks  
- Automation without human oversight  

---

## Why this work matters

Most problems in applied NLP do not come from bad models.

They come from:
- unclear problem framing,
- wrong tool selection,
- and unexamined assumptions.

This repository is a record of **learning how to ask the right questions before deploying models**.

---

## Perspective

This work is informed by experience across:
- applied NLP and data science,
- financial analysis, accounting, and audit,
- research-driven evaluation,
- and startup environments.

The guiding principle throughout is:

> **Decision support over automation theater.**