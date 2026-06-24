# AIF-C01 - Domain 3: Foundation Model Design

#aws #ai

> Part of Domain 3 (28% of exam — highest weight). Covers model selection, inference parameters, RAG, vector databases, GenAI agents, and customization cost trade-offs.

---

## Pre-trained Model Selection Criteria

|Criteria|What to evaluate|
|---|---|
|**Cost**|Licensing fees + compute cost to run the model|
|**Modality**|What input/output types does the model support? (text, image, audio, video)|
|**Latency**|Does it respond fast enough for real-time use?|
|**Multilingual support**|Can it handle multiple languages or do you need a separate translation model?|
|**Model size**|Larger = more accurate but slower and more resource-intensive|
|**Complexity**|More complex = better accuracy but harder to tune and deploy|
|**Customization**|Can you fine-tune it on your own data?|
|**Input/output length**|Can it handle long documents or conversations without cutting off? (context window)|

> Exam tip: When a question lists multiple constraints — balance them. A "mid-sized, moderately complex, text-only, multilingual, low-latency, customizable" model is often the right answer for a chatbot scenario.

---

## Model Inference Parameters

These are settings you pass to the model at runtime to control the output.

|Parameter|What it controls|Low value|High value|
|---|---|---|---|
|**Temperature**|Randomness/creativity of output|More deterministic, predictable|More diverse, creative, unexpected|
|**Top K**|Number of candidate tokens considered|Limits to most likely tokens only|Includes less likely tokens|
|**Top P**|Percentage of likely candidates considered|Less diversity|More diversity|
|**Output length**|Min/max tokens in the response|Shorter output|Longer output|

### Temperature Quick Reference

|Temperature|Output style|Use case|
|---|---|---|
|Low|Predictable, consistent, deterministic|Legal docs, factual Q&A, customer support|
|High|Creative, diverse, non-deterministic|Creative writing, brainstorming, art|

> Exam tip: High temperature = diverse/creative output. Low temperature = predictable/consistent output. "Only the most likely responses" = low temperature.

### Example

Prompt: "The sky is filled with ___"

- Candidates: stars (0.6), clouds (0.3), dragons (0.1)
- High temperature → dragons has a higher chance (more creative)
- Top K = 2 → only stars and clouds considered (dragons eliminated)
- Top P = 0.8 → stars and clouds likely, dragons still possible

---

## RAG (Retrieval Augmented Generation)

**Definition:** Augmenting LLM output by retrieving relevant information from an external knowledge base and injecting it into the prompt at inference time — without retraining the model.

### RAG Knowledge Base Types

|Type|How it works|Best for|
|---|---|---|
|**Relational DB / Elasticsearch**|Documents indexed by keywords; retrieval via keyword search|Structured data, simple queries|
|**Vector database**|Text chunked → embedded into vectors → similarity search|Unstructured text, semantic search|
|**Hybrid**|Combines keyword + similarity search; re-ranks results|Best accuracy, most complex|
|**Graph RAG**|Vector search + graph database; returns related chunks via knowledge graph|Context-rich retrieval|

### RAG Benefits

- Improved accuracy — model answers from your actual documents
- Source attribution — can identify where the answer came from (transparency)
- Contextual relevance — you control which documents are in scope
- No retraining required — cheaper and faster than fine-tuning

### RAG Challenges

- Increased pipeline complexity
- Added latency (vector search + LLM query)
- Quality depends on the retrieval set
- Extra infrastructure cost (vector database)
- Harder to tune and maintain

---

## Vector Databases

**What they do:** Store, index, and retrieve high-dimensional vector embeddings to enable fast similarity searches.

### Key Terms

|Term|Definition|
|---|---|
|**Vector embedding**|Dense numerical representation of a chunk of text that captures semantic meaning|
|**Chunking**|Breaking a large document into smaller pieces (chunks) measured in tokens|
|**Chunk size**|Number of tokens per chunk — critical tuning parameter|
|**Chunk overlap**|How much consecutive chunks share — prevents context being cut off at boundaries|
|**Similarity search**|Finding vectors closest to a query vector — not keyword matching|

### AWS Vector Database Options

|Service|Type|Serverless option|Generates embeddings?|
|---|---|---|---|
|**OpenSearch**|Search/text index|Yes|Yes (externally) — only one that can|
|**Aurora (Postgres)**|Relational (cloud-native)|Yes|No — uses pgvector plugin|
|**RDS (Postgres)**|Relational (PaaS)|No|No — uses pgvector plugin|
|**Neptune**|Graph database (NoSQL)|Yes|No|
|**DocumentDB**|Document store (NoSQL/MongoDB)|No|No|

> Exam tip: Only **OpenSearch** can generate vector embeddings (externally). All others require you to generate embeddings before inserting data.

---

## Foundation Model Customization — Cost Trade-offs

|Method|Cost|Data needed|Speed|Risk|Best when|
|---|---|---|---|---|---|
|**Pre-training**|Very high (GPUs/TPUs + time)|Massive, high-quality dataset|Slowest|High|Need a fully custom model from scratch|
|**Fine-tuning**|Moderate (GPU/TPU access)|Small targeted dataset|Fast (15-20 min)|Overfitting risk if dataset too small|Need deep domain specialization|
|**In-context learning**|Low (no training)|None|Instant|Limited customization|Rapid deployment, flexibility, low cost|
|**RAG**|Moderate-high (vector store + latency)|Document corpus|Moderate|Retrieval quality dependency|Private/current data without retraining|

### Overfitting (Fine-tuning Risk)

When the fine-tuning dataset is too small or not representative, the model **memorizes** the dataset instead of learning from it — fails on new unseen data.

### Customization Decision Guide

|Requirement|Choose|
|---|---|
|Minimize cost, rapid deployment, flexibility|In-context learning|
|Deep domain specialization, have labeled data|Fine-tuning|
|Answer from private/current documents, no retraining|RAG|
|Full control, unique use case, large budget|Pre-training|
|Regulated industry, must keep data private|Fine-tuning or RAG with private deployment|

---

## GenAI Agents

**Regular agent:** Software that performs specific actions based on rigid, predefined rules — static.

**GenAI agent:** Uses an LLM to perform tasks that can't be handled by rigid rules — dynamic, context-aware.

### News Curation Agent Example (AWS Architecture)

```
Scheduler (hourly/daily)
  → Job Initiator (Python function)
      → Pulls company list + deny list from Parameter Store
      → Loops through companies, fetches articles
      → Filters deny list, checks article length
      → Submits valid articles to Queue 1

Queue 1
  → Relevancy function
      → LLM evaluates article relevance (0-1 score)
      → Articles below threshold are dropped
      → Passes valid articles to Queue 2

Queue 2
  → Summary/Sentiment function
      → LLM generates article summary
      → LLM calculates sentiment score
      → Stores results in NoSQL DB (DynamoDB)

UI reads from NoSQL DB
```

> Key note: LLMs are nondeterministic — same article fed multiple times will get different relevancy scores. Account for this with threshold ranges, not exact values.

---

## Practice Questions

---

### Q1 — Inference Parameter Effect

**Question:** You are tasked with generating creative text using an AI model and need to set the inference parameters to encourage diverse outputs. If you choose a high temperature setting, what is the expected effect on the generated response?

**A.** The model will produce repetitive and predictable responses **B.** The model will generate diverse and creative responses **C.** The model will ignore the prompt entirely **D.** The model will only provide the most likely responses based on input

**Correct Answer: B**

|Option|Why it's wrong/right|
|---|---|
|A|Repetitive and predictable = low temperature, not high|
|B|Correct — high temperature increases randomness and diversity|
|C|The model always processes the prompt regardless of temperature|
|D|Only most likely responses = low temperature behavior|

**Tips & Tricks:**

- High temperature = high creativity = high diversity — all three go together
- Low temperature = predictable = deterministic = "most likely" — all four go together
- "Diverse and creative outputs" in the question = high temperature in the answer, every time
- Option D is the most common trap — it describes low temperature using different words

---

### Q2 — Choosing the Right Customization Approach

**Question:** A tech startup wants to deploy an NLP model for customer support. They want to minimize costs, allow rapid implementation, and need flexibility to adjust responses based on specific queries. Which customization approach should they choose?

**A.** Pre-training **B.** Fine-tuning **C.** In-context learning **D.** RAG

**Correct Answer: C**

|Option|Why it's wrong/right|
|---|---|
|A|Pre-training = very high cost + very slow — eliminates immediately|
|B|Fine-tuning = moderate cost + needs a dataset + not instant — doesn't meet "rapid" or "minimize cost"|
|C|Correct — no extra training, zero extra cost, adjust on the fly, instant deployment|
|D|RAG = adds infrastructure complexity and cost — not designed for rapid, low-cost deployment|

**Tips & Tricks:**

- Map the three constraints before reading options: minimize cost + rapid + flexible
    - Minimize cost → eliminates pre-training (very high) and RAG (moderate-high)
    - Rapid implementation → eliminates pre-training and fine-tuning
    - Flexible adjustments → in-context learning wins (adjust mid-conversation)
- In-context learning is the answer whenever you see: no budget, no time, needs flexibility
- RAG trap: it improves accuracy but adds complexity and cost — not the "cheap and fast" option
- Fine-tuning trap: it's better than pre-training but still needs data, compute, and time