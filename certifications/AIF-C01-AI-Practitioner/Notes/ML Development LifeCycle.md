# AIF-C01 - Domain 1: ML Development Lifecycle

#aws #ai

> Part of Domain 1 (20% of exam). Covers the full ML pipeline, MLOps, AWS SageMaker services, deployment types, and model performance metrics.

---

## ML Lifecycle Phases (in order)

|Phase|What happens|
|---|---|
|**1. Business Goal**|Define what you're optimizing, is ML the right tool, cost/feasibility review|
|**2. Problem Framing**|Define what is observed vs what should be predicted; identify inputs/outputs and variables|
|**3. Data Collection**|Labeling, ingestion (streaming or batch), aggregation into storage|
|**4. Pre-processing**|Clean, partition, scale, balance, and augment data; remove bias|
|**5. Feature Engineering**|Select, transform, create, and extract features (inputs used during training and inference)|
|**6. Train, Tune, Evaluate**|Train model on data, tune hyperparameters, evaluate on held-out data never used in training|
|**7. Deployment**|Make model available to applications via API endpoint|
|**8. Monitoring**|Track explainability, detect data/concept drift, trigger automated model updates|

> Exam tip: Feature engineering = managing inputs (song ratings, demographics, listening duration). Don't confuse it with data collection or pre-processing.

---

## Feature Engineering Subtasks

|Subtask|What it does|
|---|---|
|**Feature selection**|Pick the subset of features that minimize error|
|**Feature transformation**|Replace missing or invalid features|
|**Feature creation**|Create new features from existing data|
|**Feature extraction**|Reduce data dimensionality|

---

## ML Model Sources

|Source|Examples|
|---|---|
|**Open source pre-trained**|Meta, Hugging Face, TensorFlow models|
|**Custom (built-in algorithms)**|Supervised (regression), unsupervised (clustering), image processing, text analysis|

---

## Deployment Types

|Type|How it works|When to use|
|---|---|---|
|**Self-hosted API**|API Gateway → Load Balancer → EC2/Container hosting the model locally|Full control, custom infrastructure|
|**Managed API**|API Gateway → Load Balancer → Compute → SageMaker inference endpoint|Reduced operational overhead, managed scaling|

---

## MLOps
MLOps applies DevOps principles to ML — but extends them to cover data and models too.

|Principle|What it means in MLOps|
|---|---|
|**Version control**|Separate repos for data, code, and models|
|**Automation**|Anything without human oversight should be automated|
|**CI/CD**|Continuous integration/deployment extended to include data and models|
|**Model governance**|Evaluation and transparency to check for fairness, bias, and ethics|

### MLOps Benefits
- **Productivity** — automated self-service for faster evaluation
- **Reliability** — consistent, high-quality automation; less troubleshooting
- **Repeatability** — automation ensures predictable, consistent output
- **Auditability** — all inputs and outputs are versioned
- **Data and model quality** — automated guardrails and validation run frequently
### MLOps Pipeline Structure

```
Data Pipeline       → Data Repo (version controlled)
Build & Test        → Code Repo (model build + evaluate + select)
Deployment Pipeline → Model Repo (model selection + deployment)
Monitoring Pipeline → Ongoing quality evaluation
```

---
## AWS SageMaker Features (ML Pipeline Services)

|Feature|What it does|
|---|---|
|**Data Wrangler / Canvas**|Low/no-code data preparation and analysis via web interface|
|**Feature Store**|Store, share, manage features for training and inference; supports time travel|
|**Training**|Train models at scale using built-in or custom algorithms; manages compute and storage|
|**MLflow / Experiments**|Track metrics during fine-tuning, test with sample data, evaluate outputs|
|**Processing**|Run scripts/notebooks to process, transform, analyze datasets and evaluate models|
|**Model Registry**|Catalog models, manage versions and approval status, trigger deployments|
|**Deployment**|Deploy models for inference with optimal performance/cost instance selection|
|**Model Monitor**|Continuous monitoring of deployed model quality; supports real-time and batch|
|**Pipelines**|Orchestrate the full ML pipeline; purpose-built for MLOps|

### SageMaker Pipeline Flow

```
Data Wrangler (prepare) 
→ Feature Store (curate features) 
→ Training (train model) 
→ MLflow (track experiments) 
→ Processing (evaluate model) 
→ Model Registry (register) 
→ Deployment (deploy) 
→ Model Monitor (monitor)
```

---

## Model Performance Metrics

|Metric|Used for|Key detail|
|---|---|---|
|**Accuracy**|Classification|Correct predictions / total predictions|
|**Precision**|Classification|Of all positive predictions, how many were actually correct (penalizes false positives)|
|**Recall**|Classification|Of all actual positives, how many did we catch (penalizes false negatives)|
|**F1 Score**|Classification|Harmonic mean of precision and recall — best when class distribution is imbalanced|
|**AUC-ROC**|Classification|Measures ability to distinguish between classes; higher = better; never below 0.5; 0.9+ = optimal|
|**MSE (Mean Squared Error)**|Regression|Average squared difference between predicted and actual values; closer to 0 = better|
|**R-Squared**|Regression|Proportion of variance in dependent variable explained by independent variables; measures model fit|

### When to use which metric

|Scenario|Use|
|---|---|
|Predicting a number (price, weight)|MSE or R-Squared|
|Binary classification (spam/not spam)|AUC-ROC|
|Imbalanced classes (rare event detection)|F1 Score|
|General classification accuracy|Accuracy|

> Exam tip: MSE and R-Squared = regression only. AUC-ROC and F1 = classification only. If the question says "binary classification" → AUC-ROC is almost always the answer over F1.

---

## Practice Questions

---

### Q1 — Identifying the ML Lifecycle Step

**Question:** An ML model is used for an application which recommends music playlists to its users. Part of this application includes a workflow of managing song ratings, listening duration, and listener demographics for use by the model. Which ML lifecycle step describes this process?

**A.** Feature Engineering **B.** Train, Tune, and Evaluate **C.** Collect Data **D.** Pre-process Data

**Correct Answer: A**

|Option|Why it's wrong/right|
|---|---|
|A|Correct — song ratings, listening duration, and demographics are inputs (features) being managed for model use|
|B|Train, Tune, Evaluate is about building and testing the model — not managing inputs|
|C|Data collection is about ingestion and labeling — close but not specific enough|
|D|Pre-processing is about cleaning and transforming data — not managing feature inputs|

**Tips & Tricks:**

- Features = inputs used during training AND inference
- If the question mentions managing, storing, or organizing inputs for a model → Feature Engineering
- "Song ratings, listening duration, demographics" are classic features — structured inputs the model uses to make predictions
- The trap here is Collect Data — collecting and managing are different things; managing implies feature engineering
- Memory trick: Feature Engineering = everything you do to the inputs before they go into the model

---

### Q2 — Choosing the Right Performance Metric

**Question:** A company is building a machine learning model to predict whether an email is spam. They want to evaluate the performance of the model. Which of the following metrics is most appropriate for evaluating the performance of this classification model?

**A.** F1 Score **B.** AUC-ROC **C.** MSE (Mean Squared Error) **D.** R-Squared

**Correct Answer: B**

|Option|Why it's wrong/right|
|---|---|
|A|F1 Score works for classification but doesn't show how well the model discriminates between the two classes overall|
|B|Correct — AUC-ROC evaluates a model's ability to distinguish between classes (spam vs not spam); ideal for binary classification|
|C|MSE is for regression (predicts numbers) — immediately eliminate for any classification question|
|D|R-Squared is for regression — immediately eliminate for any classification question|

**Tips & Tricks:**

- First thing to do: is this regression or classification? Regression → MSE/R-Squared. Classification → F1/AUC-ROC
- "Spam or not spam" = binary classification → eliminate C and D immediately
- AUC-ROC vs F1: AUC-ROC is better when you want to know how well the model separates the two classes overall; F1 is better when class imbalance is the main concern
- If the question says "predict whether" or "classify as" → binary classification → AUC-ROC
- Never pick MSE or R-Squared for classification — they measure error on numeric predictions, not class labels

### Model Performance Metrics — Tips & Tricks

#### The Golden Rule

**Regression** (predicting a number) → MSE, RMSE, MAE, R-Squared  
**Classification** (predicting a category) → AUC-ROC, F1, Accuracy, Precision, Recall

See "regression" or "numeric prediction" in the question → eliminate all classification metrics instantly. See "binary", "classify", "spam/not spam", "yes/no" → eliminate all regression metrics instantly.

---

#### Metric-by-Metric Triggers

|Metric|Keyword triggers in the question|Eliminate when you see|
|---|---|---|
|**AUC-ROC**|binary classification, spam, fraud detection, distinguish between two classes, true positive vs false positive|regression, predicting a number|
|**F1 Score**|imbalanced classes, rare event detection, false positives AND false negatives both matter, medical diagnosis (rare disease)|regression, balanced dataset where accuracy is fine|
|**Accuracy**|balanced classes, simple classification, overall correctness|imbalanced classes (accuracy becomes misleading)|
|**Precision**|false positives are costly (e.g. flagging innocent people as fraud)|regression|
|**Recall**|false negatives are costly (e.g. missing a cancer diagnosis)|regression|
|**MSE**|regression, predicting a number, minimize error, penalizes large errors more|classification, binary|
|**RMSE**|same as MSE but result is in same unit as prediction|classification, binary|
|**MAE**|regression, average error, treats all errors equally (no squaring)|classification, binary|
|**R-Squared**|model fit, variance explained, how well variables predict outcome|classification, binary|

---

#### Scenarios Mapped to Metrics

|Scenario|Answer|
|---|---|
|Spam vs not spam|AUC-ROC|
|Fraud detection (rare fraud events)|F1 Score|
|Cancer diagnosis (missing one is deadly)|Recall|
|Flagging innocent people as criminals|Precision|
|Predicting house prices|MSE or RMSE|
|How well square footage predicts price|R-Squared|
|Self-driving car object detection|F1 Score|
|Email classification, balanced dataset|Accuracy|
|IoT anomaly detection (rare anomalies)|F1 Score|
|Model that distinguishes two classes|AUC-ROC|

---

#### AUC-ROC Number Line (memorize this)

```
0.5 ←— random guessing (straight line, useless)
0.67 ←— breakeven point
0.7-0.8 ←— acceptable
0.8-0.9 ←— good
0.9+ ←— optimal
1.0 ←— perfect (too good = likely overfitting)
```

---

#### Precision vs Recall — How to Never Mix Them Up

- **Precision** = "Of everything I flagged, how many were actually correct?" → false positives hurt you
- **Recall** = "Of everything that was actually correct, how many did I catch?" → false negatives hurt you

Memory trick:

- **P**recision = **P**olice — you don't want to arrest innocent people (false positives)
- **R**ecall = **R**escue — you don't want to miss anyone who needs saving (false negatives)

---

#### F1 vs AUC-ROC — How to Pick Between Them

|F1 Score|AUC-ROC|
|---|---|
|Imbalanced classes|Overall class separation ability|
|You care about both precision AND recall|You care about true positive vs false positive tradeoff|
|Rare events (fraud, disease)|Binary classification in general|
|Single threshold evaluation|Threshold-independent evaluation|

If the question just says "binary classification" with no other context → **AUC-ROC**  
If the question mentions "rare", "imbalanced", or "few positive cases" → **F1**