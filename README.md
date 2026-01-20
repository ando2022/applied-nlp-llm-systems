# Applied NLP + LLM Systems  
### From “it runs” to “it can be trusted”

This repository documents a series of **small, applied experiments** in Natural Language Processing (NLP) and Large Language Models (LLMs), focused on one core question:

> **When do NLP systems help real decision-making — and when do they quietly mislead?**

Instead of optimizing for impressive demos, this work focuses on **grounding, evaluation, and failure awareness** — the parts that matter in regulated, financial, and high-stakes environments.

---

## Why this repository exists

Many NLP projects look convincing:
- fluent answers,
- confident predictions,
- clean notebooks.

But in domains like **finance, regulation, accounting, ESG, and compliance**, those qualities are not enough.

Here, *being wrong confidently is worse than being unsure*.

This repository exists to explore:
- what actually happens when NLP systems are applied to **real documents**,
- how they fail under **data scarcity and ambiguity**,
- and how to detect those failures early.

---

## What I actually did (in plain language)

I built and tested **three core NLP patterns** that appear repeatedly in real products:

1. **Document Question Answering (RAG)**
2. **Semantic Search**
3. **Text Classification**

For each, I deliberately:
- used *small or imperfect data*,
- exposed intermediate outputs,
- and documented where results became unreliable.

The goal was **understanding behavior**, not maximizing scores.

---

## 01 — RAG over Documents (PDF QA with citations)

### Purpose
To test whether a Retrieval-Augmented Generation (RAG) system can answer questions  
**only from source documents**, with **explicit page-level citations**.

This mirrors real requirements in legal, financial, and regulatory work, where:
- hallucinations are unacceptable,
- sources must be traceable,
- and “I don’t know” is a valid outcome.

### What was done
- Extracted text from selected pages of a real annual report  
- Chunked text with page references  
- Embedded chunks and retrieved top-k passages  
- Generated answers **strictly constrained** to retrieved text  
- Required every factual claim to cite a page number  

### Result (what worked)
- Produced **grounded, traceable answers** to questions about:
  - regulatory fragmentation,
  - post-merger risks,
  - litigation exposure,
  - accounting judgments.
- When information was present, it was surfaced with citations.

### What didn’t work (and why it matters)
- Retrieval scores were sometimes close across unrelated passages  
- Tables and dense disclosures degraded retrieval quality  
- Some answers required manual inspection to verify relevance  

**Key insight:**  
In RAG systems, **retrieval quality dominates answer quality**.  
LLMs amplify what you retrieve — they do not fix it.

---

## 02 — Semantic Search (Embedding-based retrieval)

### Purpose
To understand what “semantic similarity” actually means in financial and regulatory language — and where it breaks.

### What was done
- Embedded short document passages  
- Queried them using natural-language questions  
- Inspected similarity scores and retrieved text manually  

### Result
- The most relevant passage was usually ranked first  
- Secondary results often reflected **thematic similarity**, not factual relevance  

Example:
A query about *Credit Suisse acquisition risk* retrieved:
- a litigation-risk passage (correct),
- an accounting-judgment passage (semantically related, but irrelevant),
- a regulatory-outlook passage (topically adjacent).

### Why this matters
Semantic search is powerful — but **not precise**.

In investigative or compliance settings:
- similarity ≠ correctness,
- ranking ≠ truth,
- and human review remains essential.

---

## 03 — Text Classification (when not to classify)

### Purpose
To test whether short regulatory or financial statements can be reliably classified with:
- small datasets,
- fuzzy categories,
- and minimal labels.

This reflects how classification is often proposed in practice.

### What was done

**Baseline model**
- TF-IDF features + Logistic Regression  
- Two broad classes: `regulation` vs `financial_performance`  
- Very small dataset  

**Transformer model**
- Pretrained sentiment classifier applied to the same text  
- Used intentionally to test **model–task mismatch**

### Result (and why it’s important)
- The baseline model produced unstable, near-random results  
  → *Correct failure due to insufficient data*

- The transformer produced **confident but meaningless outputs**  
  → High confidence, wrong task, misleading signal  

**Key insight:**  
Classification without sufficient data and domain-specific labels is not just weak — it is actively misleading.

---

## What this repository demonstrates

- How NLP systems behave under **real constraints**
- Why baselines matter more than complex models
- How confidence can hide incorrect assumptions
- When *not* to automate
- How to reason about model failure, not just success

---

## What this repository does *not* claim

- Production-ready systems  
- State-of-the-art benchmarks  
- Generalizable performance metrics  
- Automation without human judgment  

---

## Who this work is for

This work is relevant for teams working with:
- legal and regulatory text,
- financial disclosures,
- ESG and compliance documents,
- internal policy and governance material.

Especially where:
- traceability matters,
- errors are costly,
- and evaluation must be explicit.

---

## Author perspective

My background spans:
- applied NLP and data science,
- financial analysis, accounting, and audit,
- research-driven evaluation,
- and startup environments.

That combination informs the approach taken here:  
**decision support over automation theater**.

---

## Why this matters for real work

Most failures in applied NLP do not come from bad models.  
They come from **misframed problems** and **unevaluated assumptions**.

This repository is a record of learning how to spot those issues early.