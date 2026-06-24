# AIF-C01 - Domain 2: Fundamentals of Generative AI

#aws #ai

> 24% of the exam. Covers GenAI terminology, foundation model types, use cases, lifecycle, and AWS GenAI services.

---
## Core GenAI Terminology

|Term|Definition|
|---|---|
|**Transformer-based LLM**|Large language model that understands and generates human-like text by learning patterns and relationships between words (e.g. GPT)|
|**Token**|The smallest unit of text a model processes — could be a word, phrase, character, or punctuation|
|**Chunking**|Breaking large text into smaller pieces (chunks) measured in tokens — critical parameter for vector databases|
|**Vector**|Mathematical representation of data as a series of numerical values — used for similarity/relationship searching|
|**Embedding**|Dense vector representation of text or data that captures semantic meaning — similarity searches run against embeddings, not raw vectors|
|**Prompt**|Input text given to a model to generate a response|
|**Inference**|Using a trained model to generate output from a new input|
|**Hallucination**|When a model generates confident but factually incorrect output|
|**Context window**|Maximum amount of text (in tokens) a model can process at once|

> Exam tip: Vectors vs Embeddings — vectors are the raw math, embeddings are the semantic-meaning version of vectors. Similarity search = embeddings.

---

## Foundation Model Types

|Model|What it does|Best for|Avoid when|
|---|---|---|---|
|**LLM**|Understands and generates text|Text generation, translation, summarization, chatbots|Image generation|
|**Diffusion Model**|Starts with noise, gradually refines into output|High-quality image generation, audio generation|Quick/simple outputs|
|**Multimodal**|Trained on multiple data types (text, audio, video, images)|Tasks requiring multiple input/output types|Single-modality tasks|
|**GAN (Generative Adversarial Network)**|Two neural networks compete — one generates, one discriminates|Basic image/video generation|Complex, highly detailed images|
|**VAE (Variational AutoEncoder)**|Combines neural network + probabilistic modeling|Anomaly detection in large time-series datasets|High-quality image generation|

### Model Selection Cheat Sheet

|Scenario|Model|
|---|---|
|High-quality image generation, fine detail control|Diffusion Model|
|Text generation, chatbot, summarization|LLM|
|Input is text + image + audio combined|Multimodal|
|Anomaly detection in time-series data|VAE|
|Two networks competing to generate realistic content|GAN|
|Marketing artwork, logos, custom visuals|Diffusion Model|

> Exam tip: GAN = two competing neural networks (generator vs discriminator). VAE = anomaly detection. Diffusion = best image quality. LLM = text only.

---

## Foundation Model Lifecycle (in order)

|Step|What happens|
|---|---|
|**1. Data Selection**|Massive dataset — labeled/unlabeled, structured/unstructured, text/images/video/audio|
|**2. Model Selection**|Choose model type based on intended use (LLM, diffusion, GAN, VAE, multimodal)|
|**3. Pre-training**|Self-supervised training — model learns meaning, context, relationships in data; works with unlabeled data|
|**4. Fine-tuning**|Supervised process — take pre-trained model, adapt it for a specific domain or task using targeted dataset|
|**5. Evaluation**|Measure accuracy and speed using objective metrics|
|**6. Deployment**|Integrate model with applications/APIs using MLOps principles|
|**7. Feedback**|Continuous post-deployment monitoring — identifies bias, drift, and other issues|

> Exam tip: Pre-training = general learning on massive data (self-supervised). Fine-tuning = specializing the model for a specific task (supervised). These are two different steps.

---

## Pre-training vs Fine-tuning

||Pre-training|Fine-tuning|
|---|---|---|
|**When**|Before deployment|After pre-training|
|**Data**|Massive, general, often unlabeled|Smaller, targeted, labeled|
|**Supervision**|Self-supervised|Supervised|
|**Goal**|Learn general language/patterns|Specialize for a specific task|
|**Example**|GPT trained on the entire internet|GPT fine-tuned on customer service conversations|

---

## GenAI Use Cases

|Use Case|Description|
|---|---|
|**Text generation**|Emails, reports, articles, code|
|**Image generation**|Marketing materials, artwork, logos|
|**Summarization**|Condense long documents into key points|
|**Translation**|Convert content between languages|
|**Chatbots**|Customer service, virtual assistants|
|**Code generation**|Write, explain, and debug code|
|**Sentiment analysis**|Understand tone and emotion in text|

---

## AWS GenAI Architecture Example: Image Generation App

```
User → Route 53 (DNS)
     → CloudFront (CDN + WAF + wildcard cert)
     → ALB (load balancer)
     → EC2 / Node.js app (IAM role for permissions)
     → Amazon Bedrock (image generation via managed model)
     → S3 (store generated images)
     → DynamoDB (store image metadata)
     → CloudFront (serve image back to user via CDN)
```

Key design decisions:

- **Bedrock** = managed model, no self-hosting required
- **S3** = image storage
- **DynamoDB** = NoSQL key-value store for metadata
- **CloudFront** = CDN for fast content delivery
- **NAT Gateway** = outbound-only from private subnets
- **VPC endpoints** = EC2 talks to S3/DynamoDB without going through internet gateway

---

## Key AWS GenAI Services

|Service|What it does|
|---|---|
|**Amazon Bedrock**|Access to foundation models via API — no self-hosting; supports image and text models|
|**Amazon Q**|AI assistant for business/dev tasks; built on Bedrock|
|**SageMaker JumpStart**|Pre-built ML solutions and foundation models for quick deployment|
|**Amazon Titan**|AWS's own family of foundation models (text, embeddings, image)|
|**Amazon CodeWhisperer**|AI code generation and suggestions (now part of Amazon Q Developer)|

---

## Practice Questions

---

### Q1 — Selecting the Right Foundation Model

**Question:** A media company wants to create a tool that generates unique, high-quality images for marketing materials, including custom artwork and logos. They need a model that ensures high resolution, sharp details, and the ability to control specific attributes of generated images. Which type of generative model would be most appropriate?

**A.** LLM **B.** GAN (Generative Adversarial Network) **C.** VAE (Variational AutoEncoder) **D.** Diffusion Model

**Correct Answer: D**

|Option|Why it's wrong/right|
|---|---|
|A|LLMs are designed for text — immediately eliminate for any image task|
|B|GANs can generate images but struggle with complex, highly detailed outputs|
|C|VAEs can generate images but aren't designed for high quality — primary use is anomaly detection|
|D|Correct — diffusion models start with noise and gradually refine into high-quality, detail-controlled images|

**Tips & Tricks:**

- Any image question that mentions "high quality", "fine detail", "sharp", "control attributes" → Diffusion Model
- LLM = text only — eliminate immediately for any image/audio/video task
- VAE = anomaly detection first, image generation is a secondary and weaker use case
- GAN = two networks competing — sounds impressive but loses to diffusion on quality
- Memory trick: **Diffusion = detail**. It starts from noise and diffuses into a clean, high-quality result

---

### Q2 — Identifying the Foundation Model Lifecycle Stage

**Question:** A company is developing a customer service chatbot. They have selected a foundational language model, gathered a large dataset of conversational interactions, and completed pre-training on general language patterns. They are now working to customize the chatbot for specific customer queries. After evaluation, they will deploy the model and monitor feedback. At which stage of the foundation model lifecycle is the team currently working?

**A.** Model Selection **B.** Fine-tuning **C.** Deployment **D.** Feedback

**Correct Answer: B**

|Option|Why it's wrong/right|
|---|---|
|A|Model selection already happened — they already chose their foundation model|
|B|Correct — customizing a pre-trained model for a specific task (customer queries) = fine-tuning|
|C|Deployment hasn't happened yet — they're still building|
|D|Feedback is post-deployment — they haven't deployed yet|

**Tips & Tricks:**

- The lifecycle question trick: the scenario always tells you what they ALREADY DID — eliminate those steps first
- "Customizing for specific queries/domain" = fine-tuning, every time
- "Already selected model + already pre-trained + NOW customizing" → you are at fine-tuning
- Order to memorize: Data Selection → Model Selection → Pre-training → **Fine-tuning** → Evaluation → Deployment → Feedback
- If they say "monitoring after deployment" → Feedback. If they say "making it available" → Deployment. If they say "customizing" → Fine-tuning