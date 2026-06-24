# AIF-C01 - Domain 5: AI Security

#aws #ai

> Part of Domain 4 (14% of exam). Covers AWS security services, data origin tracking, secure data engineering, and AI-specific security practices.

---

## Shared Responsibility Model (Quick Recap)

The more managed the service, the less security responsibility you have.

|Service Type|AWS Responsible For|Customer Responsible For|
|---|---|---|
|**IaaS** (EC2)|Hardware, global infra, compute, storage, network, API endpoints|OS, network security, encryption, platform management, data|
|**PaaS** (managed services)|Above + OS + platform management + server-side encryption|Applications, data, access control|
|**SaaS** (fully managed)|Almost everything|Data and user access|

> Exam tip: More managed = AWS takes more responsibility. Customer always owns their data regardless of service type.

---

## Encryption in AWS AI Workloads

|Layer|In Transit|At Rest|
|---|---|---|
|CloudFront (CDN)|TLS/SSL|N/A (caching)|
|Load balancer|TLS|N/A (no disc storage)|
|EC2 app runtime|TLS (self-signed cert)|Block storage + customer keys|
|Shared file system|TLS|Customer configurable keys|
|RDS database|TLS|Block storage + customer keys|
|Data warehouse|TLS|CloudHSM (single-tenant hardware encryption)|
|S3 object storage|TLS|KMS (customer configurable keys)|

### Key AWS Encryption Services

- **AWS Certificate Manager (ACM)** — manages TLS certs for in-transit encryption
- **AWS KMS (Key Management Service)** — symmetric and asymmetric at-rest encryption, customer configurable
- **AWS CloudHSM** — dedicated hardware-backed encryption for highest security requirements

---

## Data Security AWS Services

|Service|What it does|
|---|---|
|**Amazon Macie**|Classifies sensitive data, identifies PII, analyzes access permissions, generates findings by severity|
|**AWS PrivateLink**|Connects VPC privately to AWS services or on-prem — traffic never crosses the public internet|

---

## Data Origin & Tracking

### Source Citation

Documenting where data came from and how it was gathered.

- Who created it, how it was collected, timestamps
- Builds trust, enables traceability, supports regulatory compliance

### Data Lineage

Tracing the full journey of data from source → transformation → destination.

- Helps identify errors or inconsistencies in the pipeline
- Shows impact if something breaks — you know what's affected downstream

### Data Cataloguing

A central repository of metadata about all data sources.

- Makes data discoverable across teams
- Enforces governance and data standards
- Reduces redundancy — people stop recreating datasets that already exist

---

## Secure Data Engineering Best Practices

|Problem|Risk|Solution|
|---|---|---|
|Poor quality raw data (missing values, duplicates)|Inaccurate predictions, patient harm|Validate and clean incoming data at ingestion|
|Sensitive patient data exposure|Privacy violation, legal consequences|**Homomorphic encryption** — process encrypted data without decrypting it|
|Unauthorized access by internal staff|Data misuse or leakage|**ABAC (Attribute-Based Access Control)** — permissions based on user identity + data properties + request context|
|Data corruption during transmission|Lower data quality, bad predictions|**Encryption + checksums** — generate checksum at ingestion, verify before every processing step|

---

## AI Security Practices

|Practice|What it means|Example|
|---|---|---|
|**Application security**|Keep AI apps and models free from vulnerabilities|Quarterly security audits of trading algorithms|
|**Threat detection**|Monitor AI systems for unusual behavior or anomalies|AI-powered detection of abnormal trading patterns|
|**Vulnerability management**|Identify and fix weaknesses, including AI-specific ones (adversarial attacks, model inversion)|Vulnerability scans to prevent reverse-engineering of predictions|
|**Infrastructure protection**|Secure the cloud infrastructure hosting AI models|Encrypted storage, IAM roles, automated failover|
|**Prompt injection prevention**|Validate and sanitize inputs to prevent malicious prompts from altering AI behavior|Input validation + output monitoring on NLP models|
|**Encryption at rest and in transit**|Protect data stored and transmitted|AES-256 at rest, TLS/SSL in transit|

---

## Key Security Techniques to Know

|Technique|Simple explanation|When to use|
|---|---|---|
|**Homomorphic encryption**|Encrypt data AND still process it — no one can see the raw data, even admins|When data must be used for training but must stay private throughout|
|**ABAC**|Permissions based on user identity + data properties + request context — more granular than RBAC|When different roles need very specific, context-aware access levels|
|**Federated learning**|Train models across decentralized sources without moving the raw data|When data can't leave its source (hospitals, clinics)|
|**Data anonymization**|Remove or mask PII from datasets|When sharing data externally but accuracy impact is acceptable|
|**Checksums**|Generate a hash of data at ingestion, verify before every processing step|When data integrity during transmission and storage is critical|
|**Prompt injection prevention**|Validate all inputs, sanitize before passing to the model|When AI accepts user input that could be manipulated|

---

## Practice Questions

---

### Q1 — Protecting Data During Processing

**Question:** A healthcare AI company handles sensitive patient data. The main concern is how to secure the data **during processing** without exposing it to unauthorized parties. Which technique is most effective?

**A.** Federated learning **B.** Attribute-based access control (ABAC) **C.** Homomorphic encryption **D.** Data anonymization

**Correct Answer: C**

|Option|Why it's wrong/right|
|---|---|
|A|Federated learning protects data by keeping it at the source — doesn't protect it during processing|
|B|ABAC controls who can access data — doesn't protect data during the processing step itself|
|C|Correct — homomorphic encryption allows processing of data while it stays encrypted throughout|
|D|Anonymization removes PII but doesn't protect data during processing, and can reduce model accuracy|

**Tips & Tricks:**

- Key phrase: "**during processing**" → homomorphic encryption, every time
- Federated learning trap: it's privacy-preserving but the protection is about not moving data, not about encrypting it during processing
- ABAC trap: access control ≠ processing security
- Memory trick: **Homomorphic = process without decrypting. Federated = train without moving. ABAC = access without oversharing.**

---

### Q2 — Preventing Malicious Alteration of AI Behavior

**Question:** Which of the following is a key consideration when managing security for AI systems, specifically to **prevent malicious alterations to AI behavior or outputs**?

**A.** Prompt injection prevention **B.** Infrastructure protection **C.** Encryption at rest **D.** Application security

**Correct Answer: A**

|Option|Why it's wrong/right|
|---|---|
|A|Correct — prompt injection = malicious input designed to alter AI behavior/outputs. Preventing it directly answers the question|
|B|Infrastructure protection secures physical/virtual resources — not specifically about output manipulation|
|C|Encryption at rest protects stored data — doesn't prevent output manipulation|
|D|Application security overlaps slightly but is broader — prompt injection is the more specific and correct answer|

**Tips & Tricks:**

- "Malicious alteration of AI behavior or outputs" = **prompt injection** — lock this in
- The question is very specific — map the exact threat to the exact defense
- Application security trap: it sounds right because it's about securing AI models, but it's too broad. Prompt injection is the precise answer for this exact attack type
- Whenever you see "malicious prompts", "alter behavior", "manipulate outputs" → prompt injection prevention