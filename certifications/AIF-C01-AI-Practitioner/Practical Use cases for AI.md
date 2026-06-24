# AIF-C01 - Domain 1: Practical Use Cases for AI

#aws #ai

> Part of Domain 1 (20% of exam). Covers where AI works, where it doesn't, ML techniques, real-world applications, and key AWS services.

---

## AI Patterns (Where AI Works)

|Pattern|Scenario|Why AI fits|
|---|---|---|
|**Content extraction**|Pull revenue, net income, EPS from an earnings report|AI can parse both text and tabular formats|
|**Text summarization**|Summarize a legal contract into key clauses, risks, obligations|Core LLM use case|
|**Medical image annotation**|Analyze chest X-ray for pneumonia, lung cancer, enlarged heart|Computer vision + pattern recognition|
|**Drug design**|Model protein-drug interactions from 3D structures|AI identifies candidate compounds for testing|

> Note: Medical AI should always have a human overseeing results — expect this to show up in responsible AI questions too.

---

## AI Anti-Patterns (Where AI Does NOT Work)

|Anti-Pattern|Scenario|Why AI fails|
|---|---|---|
|**Financial audit**|Regulatory compliance audit|Accuracy issues, no accountability, GenAI gives different answers to the same input (nondeterminism)|
|**Pharmaceutical regulatory compliance**|R&D → clinical trials → regulatory submission|Requires complex human judgment, legal review, strict accountability|
|**Legal judgment**|Judge interpreting a contract dispute|Needs nuanced understanding, unwritten social norms, ethical/moral weighing, accountability|

### Key reasons AI fails in these scenarios — memorize these:

- **Accuracy** — GenAI hallucinates and is nondeterministic
- **Accountability** — who is responsible when AI is wrong?
- **Reproducibility** — same input can produce different outputs
- **Nuance** — unwritten rules, emotions, moral implications
- **Compliance** — regulated industries require deterministic, auditable outcomes

> Exam tip: If a question involves regulation, law, audits, or moral judgment → AI is likely the wrong tool. Look for these keywords.

---

## ML Techniques

### Regression (Supervised)

Models relationships between variables to make numeric predictions.

|Type|What it does|Example|
|---|---|---|
|**Linear regression**|One dependent variable vs one independent variable|Predict weight from height|
|**Multiple regression**|One dependent variable vs multiple independent variables|Predict house price from size, location, bedrooms|
|**Polynomial regression**|Models a curved (nth degree) relationship|Predict trajectory of a ball thrown in the air|
|**Logistic regression**|Binary classification — predicts probability of two outcomes|Spam or not spam|

> Exam tip: House prices + multiple features = **multiple regression**. Binary yes/no outcome = **logistic regression**. Don't confuse logistic regression with clustering.

---

### Classification (Supervised)

Categorizes data into predefined classes using labeled data.

**Use cases:** Email filtering, image recognition, sentiment analysis, medical diagnosis, credit scoring

> Classification = supervised + predefined labels + categorizing new data

---

### Clustering (Unsupervised)

Groups data points by similarity without predefined labels.

|Type|What it does|Example|
|---|---|---|
|**K-means**|Partitions data into K distinct clusters|Customer segmentation by purchase behavior|
|**Hierarchical**|Builds a tree of clusters|Grouping documents by text similarity|
|**DBSCAN**|Groups dense points, flags sparse ones as outliers|Anomaly detection|

> Exam tip: Clustering = unsupervised + unlabeled data + grouping. Anomaly detection = DBSCAN. Customer segmentation = K-means.

---

## Real-World AI Applications

|Application|AI type used|Key detail|
|---|---|---|
|**Autonomous vehicles**|Computer vision|Sensors + cameras + AI for perception, navigation, decision-making|
|**Virtual assistants**|NLP + speech recognition|Voice input → speech recognition → NLP → response → text-to-speech|
|**E-commerce recommendations**|ML recommendation systems|Analyzes user behavior and preferences to suggest products|
|**Fraud detection**|Pattern recognition + ML|Flags suspicious transactions in real time using anomaly detection|
|**Supply chain forecasting**|Forecasting models|Predicts demand to maintain optimal inventory levels|

---

## AWS Managed AI/ML Services

|Service|What it does|Key detail|
|---|---|---|
|**Amazon SageMaker**|Build, train, deploy ML models|Works no-code or fully custom; scales to any size|
|**Amazon Transcribe**|Speech/audio/video → text|Supports domain-specific models + data masking|
|**Amazon Translate**|Language translation|Real-time and batch; supports custom terminology|
|**Amazon Comprehend**|Extract insights from text|Keywords, phrases, sentiment, document classification — no ML experience needed|
|**Amazon Lex**|Conversational chatbot|Voice + text; used for customer service, sales, support|
|**Amazon Polly**|Text → speech|Multiple languages, adjustable voice, style, speed, pitch|

### Architecture Example: Multilingual Chatbot

```
User (voice) → Transcribe (speech-to-text)
                       ↓
                      Lex (conversation flow)
                       ↓
                  Translate (customer language → processing language)
                       ↓
                  Comprehend (sentiment, key phrases, tone)
                  [model trained in SageMaker]
                       ↓
                  Translate (back to customer language)
                       ↓
                      Lex (conversational tone)
                       ↓
         Text user ←——         ——→ Polly (text-to-speech) → Voice user
```

> Exam tip: Know which service does what in this chain. Comprehend = insight extraction. Lex = conversation management. Polly = text to speech (not speech to text — that's Transcribe).

---

## When to Use Traditional ML vs Foundation Models

|Use Traditional ML|Use Foundation Models (FMs)|
|---|---|
|Strict regulatory/compliance requirements|General-purpose language tasks|
|Need full explainability of decisions|Content generation, summarization|
|Operational constraints (cost, latency)|When adaptability matters more than explainability|
|Labeled data available and task is specific|Little labeled data, broad task scope|

---

## Practice Questions

---

### Q1 — Identifying the Right ML Technique

**Question:** A company has a requirement to build an application which predicts house prices based on multiple features such as square footage, number of bathrooms, and whether it has a basement. Which machine learning technique would be appropriate?

**A.** Clustering **B.** Classification **C.** Regression **D.** Unsupervised learning

**Correct Answer: C**

|Option|Why it's wrong/right|
|---|---|
|A|Clustering is unsupervised — groups similar data, doesn't predict a numeric value|
|B|Classification predicts a category/label, not a numeric price|
|C|Correct — regression models relationships between variables to predict a numeric outcome|
|D|Unsupervised is a superset of techniques using unlabeled data — too broad and doesn't fit a prediction task|

**Tips & Tricks:**

- Any time you see **predicting a number** (price, weight, temperature) → **regression**
- Any time you see **predicting a category** (spam/not spam, cat/dog) → **classification**
- Any time you see **grouping without labels** → **clustering**
- "Multiple features" + "predict price" is the textbook multiple regression scenario — memorize it
- Unsupervised learning as an answer choice is almost always a trap — it's too vague to be the best answer

---

### Q2 — Identifying AI-Appropriate Workflow Steps (Select Two)

**Question:** An equity investment firm is responsible for choosing new companies to add to their portfolio. This process involves an in-depth analysis of that company. Which workflow steps would be appropriate to apply AI and ML techniques? (Select two)

**A.** Ingesting quarterly financial filing figures from a CSV file **B.** Performing financial sentiment analysis on company press releases **C.** Summarizing the critical points in an earnings call transcript **D.** Calculating commonly unreported metrics such as EBITDA from other available metrics **E.** Initiating a keyword search for company-related news articles

**Correct Answer: B and C**

|Option|Why it's wrong/right|
|---|---|
|A|Simple data ingestion from CSV — rule-driven, no AI needed|
|B|Correct — financial sentiment analysis on unstructured text is a strong AI/NLP use case|
|C|Correct — summarizing a transcript is a core LLM use case|
|D|Calculating EBITDA from other metrics is just math/formulas — no AI needed|
|E|Keyword search is deterministic — no AI required (AI would only be needed to evaluate relevance, not search)|

**Tips & Tricks:**

- The pattern for "AI is NOT needed": simple math, rule-based logic, keyword search, CSV ingestion, formulas
- The pattern for "AI IS needed": unstructured text analysis, summarization, sentiment, image recognition, predictions
- On select-two questions, eliminate the obvious non-AI tasks first (formulas, simple queries) and you'll find the AI tasks left standing
- "Sentiment analysis" = always an AI/NLP task
- "Summarizing a transcript" = always an LLM task — lock this in