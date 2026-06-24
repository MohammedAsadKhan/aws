# AIF-C01 - Domain 2: AWS Generative AI Offerings

#aws #ai

> Part of Domain 2 (24% of exam). Covers AWS GenAI services, their advantages, benefits, and cost trade-offs.

---

## AWS GenAI Services — Who Does What

|Service|What it does|Who uses it|Key detail|
|---|---|---|---|
|**Amazon Bedrock**|Access to foundation models from AWS and third parties via single API|Developers building GenAI apps|Serverless, supports fine-tuning and RAG, private customization|
|**SageMaker JumpStart**|Pre-trained models for summarization, image generation, etc.|Data scientists|Models stay in your VPC — encrypted, private, shareable across org|
|**Amazon Q Developer**|AI assistant for coding — generates, explains, debugs code|Developers / IT teams|Aware of your AWS resource inventory for customized answers|
|**Amazon Q Business**|AI assistant for business intelligence using company data|Business analysts / employees|Connects to enterprise data repositories (inventory, sales, feedback)|
|**PartyRock**|No-code playground for building GenAI apps|Non-developers / marketing teams|Built on Bedrock; chain prompts, create apps without writing code|
|**Amazon QuickSight**|Business intelligence and data visualization|Business / management|Integrates with Q for AI-powered insight queries|

### Service → Use Case Map

|Need|Service|
|---|---|
|Build and deploy AI models with full control|SageMaker JumpStart|
|Access foundation models via API, no infrastructure|Amazon Bedrock|
|Generate and debug code with AI|Q Developer|
|Query company data for business insights|Q Business|
|Create AI apps without writing code|PartyRock|
|Visualize business performance data|QuickSight|
|Fine-tune a model on your own private data|Bedrock|
|Understand and mitigate model bias|SageMaker Clarify|

---

## AWS GenAI Advantages

|Advantage|What it means|
|---|---|
|**Accessibility**|Pre-built models and APIs — developers of all skill levels can use them|
|**Lower barrier to entry**|Pre-trained models + integrated infrastructure = no need to build from scratch|
|**Efficiency**|Managed services handle scaling, load balancing, security automatically|
|**Cost effectiveness**|Pay-as-you-go — no static resource provisioning|
|**Speed to market**|Less time on infrastructure = faster development lifecycle|
|**Business alignment**|Services are customizable enough to align with any business goal|

## AWS GenAI Benefits (Security & Compliance)

|Benefit|What it means|
|---|---|
|**Security**|Encryption in transit and at rest, IAM permissions management built-in|
|**Compliance**|AWS is pre-certified with many frameworks — reduces compliance heavy lifting|
|**Shared responsibility**|AWS manages data centers, hypervisors, API endpoints — you manage workloads and data|
|**Safety**|SageMaker Clarify helps detect and mitigate bias, toxicity, hallucinations|

---

## AWS GenAI Cost Trade-offs

|Factor|What drives cost up|
|---|---|
|**Responsiveness**|Lower latency = more powerful model/resources = higher cost|
|**Availability**|High availability across AZs = more provisioned resources = higher cost|
|**Redundancy**|Cross-region replication, disaster recovery = multiple resources = higher cost|
|**Performance**|More GPU power or throughput = higher cost|
|**Regional coverage**|Using multiple regions = cross-region data transfer costs|
|**Token-based pricing**|More/longer interactions with LLMs = more tokens = more cost|
|**Provisioned throughput**|Pay for what you provision whether you use it or not|
|**Custom models**|Most expensive — managed GPU compute costs more than on-prem equivalent|

> Exam tip: Token-based pricing = you pay per token sent and received. Sending a full document as context every time = very expensive. Chunk and retrieve only what's needed (RAG).

---

## Key Concepts: RAG and Fine-tuning in Bedrock

|Technique|What it does|When to use|
|---|---|---|
|**Fine-tuning**|Retrain the model on your own labeled data to specialize it|When you need the model to behave differently in a specific domain|
|**RAG (Retrieval Augmented Generation)**|Retrieve relevant data at inference time and inject it into the prompt|When you need the model to answer from current or private data without retraining|

> RAG = cheaper and faster than fine-tuning. Fine-tuning = better for deep domain specialization.

---

## Retail Company Use Case — Full Service Map

|Business need|AWS Service|
|---|---|
|Predict stock demand / optimize inventory|SageMaker JumpStart|
|Personalize customer recommendations|Bedrock (fine-tuned on purchase history)|
|Marketing team builds AI apps without code|PartyRock|
|IT team generates and debugs code|Q Developer|
|Query enterprise data (inventory, sales, feedback)|Q Business|
|Visualize business performance|QuickSight|

---

## Practice Questions

---

### Q1 — Identifying the Right AWS GenAI Advantage

**Question:** A retail company wants to build a customer support chatbot using AWS GenAI services. They need to deploy quickly, scale with demand, minimize operational overhead, have a small team with limited AI expertise, and prefer a cost-effective solution. Which is the most appropriate advantage of using AWS GenAI services?

**A.** Custom model development from scratch allows full control and customization **B.** Manually managing infrastructure ensures the AI service is fully optimized **C.** Pre-built models and easy-to-use APIs reduce the need for in-depth AI expertise, accelerating time to market **D.** Requiring a large development team ensures the AI solution can be properly maintained and scaled

**Correct Answer: C**

|Option|Why it's wrong/right|
|---|---|
|A|Building from scratch requires expertise, time, and resources the company doesn't have|
|B|AWS managed services handle optimization automatically — manual management defeats the purpose|
|C|Correct — pre-built models + easy APIs = small team can deploy fast without deep AI expertise|
|D|AWS GenAI services are designed for lean teams — a large team is not required|

**Tips & Tricks:**

- Map the question constraints to the answer: small team + limited expertise + fast time to market = pre-built models and APIs
- Any answer that says "manual", "from scratch", or "large team" is almost always wrong when the question mentions managed services or limited resources
- The pattern: AWS managed services exist to reduce operational burden — answers that increase burden are wrong
- "Fast time to market" is always linked to pre-built models and managed services, not custom builds

---

### Q2 — Matching AWS Services to Business Requirements

**Question:** A retail company wants to use AWS GenAI services to: build AI apps, manage code development, leverage company data for insights, and visualize business performance. Which combination of AWS services best meets their needs?

**A.** Bedrock, Lambda, Q Business, SageMaker JumpStart **B.** Q Developer, Q Business, SageMaker JumpStart, QuickSight **C.** PartyRock, Bedrock, RDS, Lambda **D.** Q Developer, PartyRock, Bedrock, QuickSight

**Correct Answer: D**

|Option|Why it's wrong/right|
|---|---|
|A|Lambda is not an AI service — eliminates this option|
|B|SageMaker JumpStart doesn't let non-developers build apps — PartyRock does|
|C|RDS and Lambda are not GenAI services — eliminates this option|
|D|Correct — Q Developer (code), PartyRock (no-code AI apps), Bedrock (foundation models), QuickSight (visualization)|

**Tips & Tricks:**

- Eliminate answers containing non-AI services first: Lambda, RDS, EC2 → wrong answers
- Map each requirement to a service before reading the options:
    - Build AI apps without code → PartyRock
    - Code development → Q Developer
    - Company data insights → Q Business
    - Visualization → QuickSight
    - Foundation models → Bedrock
- If an answer is missing PartyRock for "no-code AI apps" → eliminate it
- SageMaker JumpStart trap: it's for data scientists, not no-code app builders — PartyRock is the no-code tool