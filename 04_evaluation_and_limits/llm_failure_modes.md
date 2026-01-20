# Applied NLP + LLM Systems (with Evaluation)

This repository contains **small, applied NLP and LLM projects** that turn unstructured text into **reliable, testable systems**.

The focus is not on “cool demos,” but on **problem framing, evaluation discipline, and practical trade-offs** — the parts that matter in real products and **high-stakes, regulated environments**.

---

## What this repository demonstrates

**This repository demonstrates:**
- Realistic framing of NLP problems under uncertainty
- Comfort working with incomplete, ambiguous, and weakly labeled text data
- Awareness of evaluation pitfalls in small-data settings
- Understanding of NLP behavior in regulated contexts
- Preference for **decision support** over automation theater

**This repository does *not* claim:**
- Production-ready systems
- State-of-the-art benchmarks
- Generalizable performance metrics
- Automation without human oversight

These omissions are intentional.

---

## What this repository is (and is not)

This is **not** a collection of AI demos.

It is a set of **small, inspectable experiments** designed to show how NLP systems behave under realistic constraints:
- limited data,
- ambiguous categories,
- legally and economically meaningful language,
- strict requirements on traceability.

The emphasis is on:
- framing problems *before* automating them,
- understanding retrieval and classification failure modes,
- evaluating models honestly rather than optimizing metrics,
- documenting limits instead of hiding them.

The methods used here are common in production.  
What is uncommon is examining **where and why they fail**.

---

## Methods overview & rationale

This repository applies a small set of **foundational NLP methods** that appear repeatedly in real-world information systems: **retrieval, classification, and generation**.

The focus is on **method choice, evaluation discipline, and failure awareness**, not model novelty.

---

### 1. Retrieval-Augmented Generation (RAG)

**Location:** `01_rag/`

**Purpose**  
RAG is used here not as a chatbot pattern, but as a **controlled document analysis tool**.  
Answers must be grounded in retrieved text, and every factual statement must be traceable to a source.

**Why RAG**  
In regulated and high-stakes domains (finance, law, compliance), generative models are only useful when constrained by:
- document-level grounding,
- explicit citations,
- retrieval quality checks.

**What is evaluated**
- Whether relevant passages are retrieved
- Whether answers stay within retrieved context
- Whether missing information is correctly reported as *not found*

**What this shows**  
LLMs are **reasoning amplifiers, not sources of truth** — and retrieval quality is often the dominant failure mode.

---

### 2. Semantic Search (Embedding-Based Retrieval)

**Location:** `02_semantic_search/`

**Purpose**  
Semantic search is treated as an **analytical primitive**, not a product feature.  
The goal is to inspect what *similarity* actually means in practice.

**Why embeddings instead of keywords**
Keyword search fails when:
- language varies across documents,
- the same concept is expressed differently,
- queries are exploratory rather than precise.

Embeddings enable retrieval by semantic association, which is essential in research and investigative workflows.

**How it is evaluated**
- Similarity scores are exposed
- Retrieved passages are manually inspected
- Relevance is assessed qualitatively, not assumed

**What this shows**  
Semantic similarity is probabilistic, context-dependent, and prone to spurious matches — especially in legal and financial text.

---

### 3. Text Classification (Baseline → Transformer)

**Location:** `03_text_classification/`

**Purpose**  
To compare **simple, interpretable baselines** with **more expressive models** under realistic data constraints.

**Why start with a baseline**  
TF-IDF + Logistic Regression:
- is fast,
- transparent,
- often competitive in small or noisy datasets.

**Why introduce a transformer**  
Transformers capture:
- contextual meaning,
- implicit signals,
- cross-sentence dependencies,

but introduce:
- higher variance,
- stronger data requirements,
- reduced interpretability.

**What is evaluated**
- Class imbalance effects
- Model instability on small datasets
- Precision/recall trade-offs
- Cases where a “better” model performs worse

**What this shows**  
Model choice is a **decision under constraints**, not a leaderboard exercise.

---

### 4. Evaluation & limits

**Location:** `04_evaluation_and_limits/`

Evaluation is treated as a **first-class concern**, not an afterthought.

This includes:
- explicit acknowledgment of weak or missing labels,
- avoidance of misleading metrics,
- documentation of known failure modes,
- refusal to over-interpret results.

Failures are surfaced deliberately, because they are the dominant source of risk in applied NLP systems.

---

## Projects

1. **RAG over Documents (PDF QA with citations)**  
   *Goal:* Answer questions using provided documents only, with traceable sources.

2. **Semantic Search (Sentence Transformers)**  
   *Goal:* Retrieve relevant passages using embeddings and similarity metrics.

3. **Text Classification (Baseline → Transformer)**  
   *Goal:* Compare interpretable baselines and transformer models under realistic constraints.

---

## Author & perspective

This repository reflects my work at the intersection of:
- applied NLP and data science,
- financial analysis, accounting, and audit,
- research-driven evaluation.

I have worked across academic research, financial and sustainability analytics, industry-facing data science roles, and startup environments.  
This informs the perspective taken here: an emphasis on **traceability, explainability, and decision relevance**, rather than purely generative output.

The projects are designed with **regulated and high-stakes domains** in mind (finance, audit, ESG, compliance), where language is legally and economically consequential and model failure has real costs.

> Each project lives in its own folder with a short README describing the approach, evaluation, and limitations.

---

## Quick start

- Create an environment from `environment.yml`
- Run notebooks locally or in Colab

---

## Example industry & freelance use-cases

- Build a **RAG prototype** over internal PDFs (policy, legal, ESG, product docs)
- Implement **semantic search** for investigative or research workflows
- Create **classification pipelines** for routing, tagging, or triage
- Audit existing LLM workflows: **evaluation, failure modes, and risk analysis**

---

## Contact

If you’d like to collaborate on document search, RAG, or applied NLP systems — especially in regulated or high-stakes contexts — feel free to reach out.