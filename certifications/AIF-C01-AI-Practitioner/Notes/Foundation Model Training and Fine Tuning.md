# AIF-C01 - Domain 3: Foundation Model Training & Fine-Tuning

#aws #ai

> Part of Domain 3 (28% of exam). Covers when to build vs use a pre-trained model, the four fine-tuning methods, and data preparation.

---

## Build From Scratch vs Use Pre-trained — Simple Version

Think of it like cooking:

- **Build from scratch** = grow your own vegetables, mill your own flour, make everything yourself. Maximum control, maximum effort, maximum cost.
- **Pre-trained model** = buy ingredients from the store. Someone already did the hard work. You just cook the meal.
- **Fine-tuning** = take a meal kit and adjust the seasoning to your taste. Fast, cheap, works great.

---

## Decision Guide: Scratch vs Pre-trained vs Fine-tuned

|Question|If YES →|
|---|---|
|Does a pre-trained model already exist for this task?|Use pre-trained|
|Do you need deep specialization but have limited data?|Fine-tune|
|Do you need something completely unique with no existing model?|Build from scratch|
|Do you have a small team with limited AI expertise?|Pre-trained or fine-tune|
|Do you have massive budget, huge dataset, and deep expertise?|Build from scratch|

---

## The Four Fine-Tuning Methods

### 1. Instruction Tuning

**Simple version:** You give the model a list of "if someone says X, respond with Y" examples and retrain it on those.

- Format: JSON file with prompt → desired output pairs
- Best for: making a model better at following commands and instructions
- Example: Amazon trained Alexa on thousands of voice commands ("play my playlist", "set a timer") so it understands user instructions better

---

### 2. Adapting for a Specific Domain

**Simple version:** You take a general model and feed it a ton of documents from one specific field (law, medicine, finance) so it becomes an expert in that area.

- Best for: industries with unique language and concepts
- Example: ROSS Intelligence trained a model on case law, statutes, and legal opinions → it could now answer legal questions and find relevant cases
- Pro tip: Combining domain adaptation + RAG makes it even more powerful

---

### 3. Transfer Learning

**Simple version:** Take a model trained for one thing and apply it to a related but different task — without retraining from scratch.

- Think of it like: you learned to drive a car, now you're learning to drive a truck. You don't start from zero.
- Example: BERT was trained on general text → transferred to do sentiment analysis without starting over
- Best for: when you have a general model and want to apply it to a narrower task efficiently

---

### 4. Continuous Pre-training

**Simple version:** Keep feeding the model new data regularly over time so it never gets outdated.

- Best for: fast-moving topics where information changes constantly
- Example: X (Twitter) feeds its recommendation model new tweets and trending topics continuously so content suggestions stay relevant
- Also helps gradually reduce bias and toxicity over time

---

## Fine-Tuning Methods — Cheat Sheet

|Method|What you do|Best when|Real-world example|
|---|---|---|---|
|**Instruction tuning**|Train on prompt → output pairs|Model needs to follow commands better|Alexa voice commands|
|**Domain adaptation**|Train on domain-specific corpus|Need deep expertise in one field|Legal AI, medical AI|
|**Transfer learning**|Apply existing model to new related task|Efficient repurposing, narrow scope|BERT → sentiment analysis|
|**Continuous pre-training**|Keep adding new data over time|Model needs to stay current|Twitter/X recommendations|

---

## Data Preparation — Why It Matters

**Garbage in = garbage out.** The model is only as good as the data you train it on.

The most critical step before fine-tuning is **data curation** — making sure your training data is:

- Relevant to the specific domain or task
- High quality (accurate, clean, well-formatted)
- Representative of what the model will actually see in production

> Quality beats quantity in fine-tuning. A small, clean, relevant dataset beats a huge messy one.

### Common data prep mistakes:

- **Too little data** → underfitting (model doesn't learn enough)
- **Too small AND not representative** → overfitting (model memorizes instead of learning)
- **Unstructured/noisy data** → model learns the wrong patterns

---

## Practice Questions

---

### Q1 — Identifying the Fine-Tuning Method

**Question:** A legal AI system was trained specifically on legal texts such as case law and statutes to improve its understanding of complex legal language. Which method of fine-tuning was primarily used?

**A.** Instruction Tuning **B.** Adapting Models for Specific Domains **C.** Transfer Learning **D.** Continuous Pre-training

**Correct Answer: B**

|Option|Why it's wrong/right|
|---|---|
|A|Instruction tuning = training on prompt/output pairs — not what happened here|
|B|Correct — training on domain-specific texts (legal corpus) = domain adaptation|
|C|Transfer learning = applying a general model to a related task — not deep domain training|
|D|Continuous pre-training = ongoing updates over time — not what was done initially|

**Tips & Tricks:**

- "Trained on legal/medical/financial texts" → **domain adaptation**, every time
- Instruction tuning trap: sounds like it could apply to legal AI, but instruction tuning is about commands and prompts, not domain knowledge
- Transfer learning trap: a general model being used for legal work sounds like transfer learning, but the key is they specifically trained on legal texts — that's domain adaptation
- Memory trick: **Domain adaptation = becoming an expert. Transfer learning = switching careers.**

---

### Q2 — Most Critical Data Step for Fine-Tuning

**Question:** You are fine-tuning a foundation model for customer support interactions. The success relies heavily on the quality of data used. Which step is most critical to ensure the model effectively learns from the provided data?

**A.** Data curation **B.** Data size increase **C.** Initial training with diverse data **D.** Unstructured feedback collection

**Correct Answer: A**

|Option|Why it's wrong/right|
|---|---|
|A|Correct — relevant, high-quality, domain-specific examples = model learns the right things|
|B|More data helps but quality beats quantity in fine-tuning — wrong emphasis|
|C|Diverse training already happened during pre-training — fine-tuning needs targeted data, not broad diversity|
|D|Feedback collection happens after fine-tuning is done — not during|

**Tips & Tricks:**

- For fine-tuning questions: **quality of data > quantity of data**
- "Most critical step" for fine-tuning = data curation (making sure data is clean, relevant, representative)
- Data size increase is a trap — it implies more is always better, but a small high-quality dataset beats a large noisy one
- Feedback collection is always a post-deployment step — eliminate it for any question about the training/fine-tuning process
- The order is: curate data → fine-tune → deploy → collect feedback. Feedback is last.