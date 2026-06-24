# AIF-C01 - Domain 3: Foundation Model Performance

#aws #ai

> Part of Domain 3 (28% of exam). Covers how we measure if an AI model is doing a good job, and whether it's delivering business value.

---
## The Big Picture — Why Do We Evaluate Models?

Imagine you hired someone to write summaries for you. How do you know if they're doing a good job? You compare their summary to a good reference summary and see how close they got. That's exactly what these metrics do — they compare what the AI generated to what a human expert would have written.

---
## Performance Metrics (How Good Is the AI's Output?)
### ROUGE — For Summarization
**Full name:** Recall-Oriented Understudy for Gisting Evaluation **Simple version:** Count how many words from the AI's summary also appear in the reference summary.
**Example:**
- Original article: long, detailed text about a new cancer drug
- Reference summary: "Researchers discovered a new drug that reduces tumor size in cancer patients"
- AI summary: "Researchers at XYZ University discovered a new drug that reduces tumor size significantly in cancer patients"
- ROUGE score: how many words overlap? If 8 out of 10 words match → score = 0.8 (80%) ✅

|ROUGE Type|What it checks|
|---|---|
|**ROUGE-N**|Counts matching words (unigrams) or word pairs (bigrams)|
|**ROUGE-L**|Finds the longest sequence of matching words in order|

> Higher ROUGE score = better summary. Used for summarization and translation tasks.

---
### BLEU — For Translation
**Full name:** Bilingual Evaluation Understudy **Simple version:** Count how many words from the AI's translation match a human's correct translation.

**Example:**
- English: "The cat sits on the mat"
- Human Spanish translation: "El gato se sienta en el tapete"
- AI Spanish translation: slightly different wording
- BLEU score: how many words from the AI version match the human version?

> Higher BLEU score = better translation. Used specifically for language translation tasks.

---
### BERTScore — For Meaning (Not Just Word Matching)
**Simple version:** Instead of checking if the exact same words appear, it checks if the _meaning_ is the same — even if different words are used.

**Example:**
- Reference: "AI is improving industries by increasing efficiency"
- AI output: "Artificial intelligence enhances efficiency in different sectors"
- These don't share many exact words, but they mean the same thing
- BERTScore says ✅ — ROUGE would give a lower score because the words are different

**How it works:**
1. Converts both texts into vector embeddings (meaning-based numbers)
2. Compares how similar the vectors are
3. Calculates precision + recall → outputs an F1 score

> Use BERTScore when meaning matters more than exact wording.

---
## Metric Quick Reference

|Metric|Used for|Checks|Score means|
|---|---|---|---|
|**ROUGE**|Summarization|Word overlap with reference|Higher = better summary|
|**BLEU**|Translation|N-gram match with reference translation|Higher = better translation|
|**BERTScore**|Any text|Semantic (meaning) similarity via embeddings|Higher = closer in meaning|

---
## How Do You Actually Evaluate a Model?
### Option 1: Human Evaluation
- A real person reads the AI output and grades it
- Criteria: coherence, relevance, accuracy, quality
- ✅ Best for setting a gold standard
- ❌ Slow, expensive, hard to scale

### Option 2: Benchmark Datasets
Pre-made test sets that everyone uses so results are comparable.

|Benchmark|Tests|
|---|---|
|**GLUE**|General language understanding|
|**SuperGLUE**|Harder version of GLUE|
|**SQuAD**|Question answering|
|**WMT**|Machine translation|

✅ Objective, standardized, trackable over time ❌ Doesn't always reflect real-world use cases

---
## Business Value Metrics (Is the AI Actually Helping?)
The point isn't just that the AI scores well on a test — it needs to actually help the business. Here's how you measure that:

|Business Goal|Example|Metrics to track|
|---|---|---|
|**Productivity**|Customer support chatbot|Average response time, ticket resolution rate|
|**User engagement**|Product recommendation engine|Click-through rate, session duration, conversion rate|
|**Task efficiency**|Automating data entry|Time to complete task, error rate|

> The key method: compare metrics **before** AI vs **after** AI. If response time went down → AI is delivering value.

---
## GenAI Agents — Simple Explanation
A **regular agent** follows strict rules like a flowchart — if X then Y, always.

A **GenAI agent** uses an LLM to make judgment calls — it can handle things that don't fit neatly into predefined rules.

**Real example: News curation system**
- Regular agent handles: fetching articles, filtering deny list (simple rules)
- GenAI agent handles: "Is this article actually relevant to Company X?" (needs judgment)
- GenAI agent also handles: summarizing the article, analyzing sentiment (needs language understanding)

---

## Practice Questions

---

### Q1 — Identifying the Right Evaluation Metric

**Question:** During evaluation of machine-generated summaries, a new metric assesses **semantic similarity** between generated text and a reference summary using **deep contextual embeddings**. What distinguishes this metric from traditional N-gram methods?

**A.** It computes a score based on exact phrase matches **B.** It uses word embeddings that capture the meaning of words in context **C.** It focuses solely on the length of the generated text **D.** It requires multiple reference summaries for valid evaluation

**Correct Answer: B**

|Option|Why it's wrong/right|
|---|---|
|A|Exact phrase matching = ROUGE/BLEU — that's the _traditional_ method being contrasted against|
|B|Correct — BERTScore uses embeddings to compare meaning, not just matching words|
|C|Length comparison has nothing to do with semantic similarity|
|D|Multiple reference summaries isn't what makes a metric semantic|

**Tips & Tricks:**

- "Semantic similarity" + "contextual embeddings" = **BERTScore** every time
- "Exact word/phrase matching" = ROUGE or BLEU — traditional N-gram methods
- The question is basically asking: what makes BERTScore different from ROUGE/BLEU?
    - Answer: BERTScore checks _meaning_, ROUGE/BLEU check _exact words_
- Memory trick: **BERT = meaning. ROUGE = word count. BLEU = translation word count.**

---

### Q2 — Identifying the Right Business Value Metric

**Question:** A company implemented a foundation model as an AI customer support chatbot. Which metric should they primarily focus on to evaluate **productivity improvements**?

**A.** Customer satisfaction scores **B.** Number of new customer inquiries **C.** Employee training hours **D.** Average response time

**Correct Answer: D**

|Option|Why it's wrong/right|
|---|---|
|A|Satisfaction scores measure sentiment, not productivity — also affected by many other factors|
|B|Number of new inquiries has nothing to do with chatbot performance|
|C|Employee training hours is completely unrelated to the chatbot|
|D|Correct — average response time directly measures how fast the chatbot handles requests, compare before vs after AI|

**Tips & Tricks:**

- "Productivity" = how efficiently the task gets done → time-based metrics win
- For a chatbot: **average response time** and **ticket resolution rate** are the go-to productivity metrics
- Customer satisfaction is a trap — it sounds right but it's a sentiment/quality metric, not a productivity metric
- The formula for any business value question: what can you measure **before and after** that directly reflects the AI's job?
- Chatbot's job = respond to customers fast and accurately → measure response time and resolution rate