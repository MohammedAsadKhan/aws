# AIF-C01 - Domain 1: Fundamentals of AI and ML

#aws #ai

> 20% of the exam. Covers core terminology, use cases, and the ML development lifecycle.

---

## Core Terminology

|Term|Definition|
|---|---|
|**Artificial Intelligence (AI)**|Systems that perform tasks normally requiring human intelligence (perception, reasoning, decision-making)|
|**Machine Learning (ML)**|Subset of AI that learns from data to improve at specific tasks|
|**Neural Network**|Computational model inspired by the brain — layers of nodes that process data from input to output|
|**Deep Learning**|Subset of ML using multi-layered neural networks to auto-extract features from large datasets|
|**Computer Vision**|AI field for interpreting visual info (images/video)|
|**NLP (Natural Language Processing)**|AI subset for human language — translation, generation, sentiment analysis|
|**AI Model**|Algorithm trained on data to classify, predict, or recognize patterns|
|**ML Algorithm**|Set of procedures for analyzing data and making predictions|
|**Training**|Teaching a model by feeding it large amounts of data|
|**Inferencing**|Using a trained model to generate predictions on new data|
|**Model Fairness**|Ensuring a model's decisions don't bias or disadvantage any group|
|**Model Fit**|How well a model's predictions match its training data|
|**LLM (Large Language Model)**|AI model trained on vast text data — handles conversations, summaries, predictions, sentiment|
|**GenAI**|AI that generates new content (text, images, audio)|
|**Agentic AI**|AI that takes autonomous actions to complete multi-step tasks|

---

## Types of Data

|Data Type|Description|Example|
|---|---|---|
|**Labeled**|Data tagged with categories/descriptors|Images tagged "cat" or "dog"|
|**Unlabeled**|No tags — model finds patterns itself|Raw social media posts|
|**Tabular**|Rows and columns (spreadsheet/CSV)|Sales database|
|**Time-series**|Observations collected sequentially at regular intervals|IoT sensor readings, stock prices|
|**Image**|Visual data for computer vision tasks|Photos, video frames|
|**Structured text**|Text in predefined format with fields/tags|CSV, XML|
|**Unstructured**|Freeform text — needs NLP to process|PDFs, social media posts|

> **Exam tip:** IoT device metrics collected frequently = **time-series data** (not tabular, not structured — time-series is most specific)

---

## Types of Learning

|Learning Type|How it works|Use case|
|---|---|---|
|**Supervised**|Trained on labeled data (input + output pairs)|Spam detection, image classification|
|**Unsupervised**|Trained on unlabeled data — finds patterns itself|Customer segmentation, anomaly detection|
|**Reinforcement**|Learns by trial and error — rewards for correct, penalties for wrong|Self-driving cars, game-playing AI|

> **Exam tip:** Reinforcement learning = agent + environment + rewards/penalties. Not rules-based, not labeled data.

---

## Common ML Algorithms

|Algorithm|What it does|Example|
|---|---|---|
|**Linear Regression**|Models relationship between variables|Predicting house prices|
|**Logistic Regression**|Binary classification|Spam or not spam|
|**KNN (K-Nearest Neighbors)**|Classifies based on closest neighbors|Recommendation engines|
|**PCA (Principal Component Analysis)**|Reduces large datasets while keeping key features|Facial recognition preprocessing|

---

## ML Development Lifecycle

1. **Data Collection & Preparation** — most critical step; identify and clean usable data
2. **Algorithm Selection** — pick the right algorithm for the task
3. **Model Training** — most time/resource intensive step
4. **Model Evaluation** — validate output quality; results feed back into step 1

---

## Types of Inferencing

| Type             | Description                                    | Priority         |
| ---------------- | ---------------------------------------------- | ---------------- |
| **Batch**        | Large dataset processed all at once            | Accuracy > Speed |
| **Real-time**    | Instant response to each input                 | Speed > Accuracy |
| **Asynchronous** | Request sent, response retrieved later         | Background tasks |
| **Serverless**   | Runs on-demand without managing infrastructure | Cost efficiency  |

> **Exam tip:** LLMs use real-time inferencing. Self-driving cars need real-time. Batch = when accuracy matters more than speed.

---

## Deep Learning: Neural Network Structure

```
Input Layer → Hidden Layers → Output Layer
```

- **Input layer** — raw features enter here (pixels, measurements, key-value pairs)
- **Hidden layers** — neurons apply transformations (edge detection, shape recognition, etc.)
- **Output layer** — final result (classification, prediction)

> Analogy: Input = loading dock, Hidden = assembly workers, Output = packaging and shipping

---

## Key AWS Services (Domain 1 Preview)

|Service|What it does|
|---|---|
|**Amazon SageMaker AI**|Build, train, and deploy ML models|
|**Amazon Transcribe**|Speech to text|
|**Amazon Translate**|Language translation|
|**Amazon Comprehend**|NLP — sentiment, entities, key phrases|
|**Amazon Lex**|Conversational AI / chatbots|
|**Amazon Polly**|Text to speech|
|**Amazon Bedrock**|Access to foundation models via API|
|**Amazon Q**|AI assistant for business and dev tasks|

---

## Practice Questions

---

### Q1 — Reinforcement Learning Definition

**Question:** A company is developing self-driving car technology. They want to determine the best machine learning workflow. They believe reinforcement learning is appropriate. Which of the following is the best definition of reinforcement learning?

**A.** Reinforcement learning involves training a model to make decisions by providing it with a fixed set of rules. For example, a chess program follows predefined strategies to win.
**B.** Reinforcement learning is a type of ML where an agent learns to make decisions by interacting with an environment, receiving feedback in the form of rewards or penalties — similar to training a dog. 
**C.** Reinforcement learning is about creating a model that can process large amounts of data without human intervention. An example is a computer that sorts emails into spam or not spam based on predefined filters. 
**D.** Reinforcement learning is the process of using labeled data to train models for classification tasks.

**Correct Answer: B**

|Option|Why it's wrong|
|---|---|
|A|Describes a rule-based/expert system — not ML at all|
|C|Describes logistic regression (spam filtering = binary classification)|
|D|Describes supervised learning (labeled data + classification)|
|B|Correct — agent + environment + rewards/penalties = reinforcement learning|

**Tips & Tricks:**

- The word "rules" in an answer = rule-based system, eliminate it
- "Labeled data" + "classification" in the same answer = supervised learning, eliminate it
- "Without human intervention" + "predefined filters" = that's logistic regression disguised as RL
- RL keyword chain to memorize: **agent → environment → reward/penalty → decision**
- Self-driving cars are the classic RL use case on AWS exams — lock that in

---

### Q2 — Identifying Data Type

**Question:** A company's application runs on remote devices and uses IoT technology to deliver metric values on a frequent schedule. The company wants to perform anomaly detection on that data using machine learning. Which of the following best describes the data?

**A.** Tabular data **B.** Unlabeled data **C.** Structured data **D.** Time-series data

**Correct Answer: D**

|Option|Why it's wrong/right|
|---|---|
|A|Tabular is about structure (rows/columns) — doesn't capture the time element|
|B|Unlabeled is about missing tags — completely unrelated to the delivery format|
|C|Structured is too broad — tabular and time-series are both structured|
|D|Correct — IoT metrics collected frequently at regular intervals = time-series by definition|

**Tips & Tricks:**

- When you see **IoT + frequent schedule + anomaly detection** → always time-series
- The trap here is tabular and structured — both are partially true but not the _most specific_ answer
- AWS exams always want the most specific correct answer, not just a correct one
- Anomaly detection is a classic time-series use case — if you see it, think time-series first
- Memory trick: **time-series = timestamps + regular intervals + sequential**

---

## Quick Hierarchy Cheat Sheet

```
AI
└── Machine Learning
    └── Deep Learning
        └── Neural Networks

AI
└── NLP
└── Computer Vision
└── GenAI
    └── LLMs
        └── Agentic AI
```