# Why Annual Reports Are a Poor Target for RAG Systems

Annual reports are often used as example documents for Retrieval-Augmented Generation (RAG) demos.
They are long, public, well-structured, and easy to obtain.

However, after implementing and testing a RAG pipeline on a large financial annual report, this project deliberately documents **why annual reports are a weak target for meaningful RAG applications**, especially in high-stakes domains such as finance and regulation.

This document explains **what works, what doesn’t, and why**.

---

## 1. Annual Reports Are Already Optimized for Reading, Not Decision Support

Annual reports are written to:
- comply with regulatory disclosure requirements,
- present a controlled narrative to investors and regulators,
- minimize legal exposure.

They are **not written to support operational or strategic decisions**.

As a result:
- Key uncertainties are softened by legal language.
- Risks are disclosed but rarely quantified.
- Forward-looking statements are intentionally vague.

A RAG system can retrieve these passages, but it cannot **create new insight** from language that is already optimized to avoid precision.

---

## 2. Most Questions Have Trivial or Pre-Packaged Answers

Many questions asked of annual reports fall into one of these categories:
- “What risks does the company mention?”
- “What does the company say about regulation?”
- “What are the key accounting judgments?”

The answers:
- already exist verbatim in the document,
- are structured under clear section headers,
- are written to be safely reusable.

In practice, this means:
- Simple keyword search often performs as well as semantic retrieval.
- RAG adds technical complexity without improving decision quality.
- The system retrieves text, but no interpretation or trade-off is required.

This makes annual reports **low-signal targets** for demonstrating the value of RAG.

---

## 3. There Is No Decision Boundary

RAG is most valuable when:
- information is fragmented,
- trade-offs are unclear,
- incorrect answers have consequences.

Annual reports do not create such boundaries.

They do not answer questions like:
- “What should we do?”
- “Which option is better?”
- “What changes if assumptions break?”

Instead, they document what has already happened under carefully controlled wording.

Without a decision boundary, RAG becomes:
> a sophisticated way to re-read a document that already explains itself.

---

## 4. Time Relevance Is Weak

Annual reports are backward-looking by design.

Using a report from year *t* to answer questions in year *t+2*:
- does not reflect current regulatory reality,
- does not capture evolving market conditions,
- does not support forward-looking decisions.

A technically correct answer may still be **economically irrelevant**.

This limits the practical value of RAG over annual reports outside of:
- compliance audits,
- academic demonstrations,
- internal training materials.

---

## 5. Legal Language Limits Interpretability

Financial and regulatory disclosures rely heavily on:
- conditional phrasing,
- disclaimers,
- legal qualifiers.

Examples include:
- “may,” “could,” “subject to,” “we believe,” “we cannot assure.”

While legally necessary, this language:
- prevents strong conclusions,
- limits model-driven synthesis,
- makes confident answers misleading.

A responsible RAG system must either:
- repeat the same hedging language, or
- risk hallucinating certainty where none exists.

Neither outcome produces actionable insight.

---

## 6. Where Annual Reports *Can* Be Useful

This does not mean annual reports are useless.

They can be appropriate for:
- internal onboarding and training,
- locating disclosures for compliance review,
- verifying whether a topic is mentioned at all.

In these cases, RAG acts as a **navigation aid**, not an analytical engine.

That distinction matters.

---

## 7. Better RAG Targets in Financial and Regulatory Domains

RAG systems deliver more value when applied to documents that:
- precede decisions, not follow them,
- contain unresolved ambiguity,
- require interpretation or comparison.

Examples include:
- draft regulations and consultation papers,
- internal policy drafts,
- tender documents and RFPs,
- transaction documents and term sheets,
- multi-document regulatory guidance sets.

These texts create **real uncertainty**, where retrieval quality and citation discipline directly affect outcomes.

---

## Conclusion

Annual reports are attractive RAG demos because they are safe, public, and structured.
They are weak RAG targets because they lack:
- decision pressure,
- informational asymmetry,
- interpretive tension.

This project intentionally documents this limitation to emphasize an important point:

> **Good RAG systems start with good problem selection.**

Technical correctness without decision relevance is not value.

Understanding *where not to apply RAG* is as important as knowing how to build it.