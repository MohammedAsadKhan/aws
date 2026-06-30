# AWS Certified Cloud Practitioner (CLF-C02)

**Status:** ✅ Passed

---

## About This Certification

The AWS Certified Cloud Practitioner validates foundational cloud knowledge and core AWS services. It covers cloud concepts, security and compliance, cloud technology and services, and billing/pricing/support.

**Passing score:** 700/1000
**Exam format:** 65 questions, 90 minutes

---

## Domain Breakdown

| Domain | Weight |
|--------|--------|
| Domain 1: Cloud Concepts | 24% |
| Domain 2: Security and Compliance | 30% |
| Domain 3: Cloud Technology and Services | 34% |
| Domain 4: Billing, Pricing and Support | 12% |

---

## Study Approach

Notes for this certification are built from two sources, cross-referenced for completeness:

- **AWS Skill Builder** — primary source notes (13 modules, Obsidian-formatted with exam flags and cybersecurity tie-ins)
- **Pluralsight (CLF-C02 Path)** — used for video review at 1.75x speed and hands-on labs (S3 static hosting, EventBridge automation, IAM least-privilege configuration)
- **LinkedIn Learning (Student Account)** — used for additional practice exams

Each module note follows a consistent format:
- Core concept breakdown
- ⚠️ **Exam Flags** — scenario triggers and common trick questions
- 💡 **Cybersecurity Pass Tips** — security-focused angle tying concepts back to a Cyber concentration

---

## Module Notes

| # | Module | Topics Covered |
|---|--------|----------------|
| 1 | [Introduction to Cloud](./Module_1.md) | Cloud history, CapEx vs. OpEx, 6 Advantages of Cloud, Shared Responsibility Model, HA/Fault Tolerance basics |
| 2 | [Compute in the Cloud](./Module_2_Compute_in_the_Cloud.md) | EC2 fundamentals, instance families, vertical/horizontal scaling, Elastic Load Balancing, SQS vs. SNS |
| 3 | [Exploring Compute Services](./Module_3_Exploring_Compute_Services.md) | Serverless philosophy, AWS Lambda, containers (ECS/EKS/ECR/Fargate), Elastic Beanstalk, Batch, Lightsail, Outposts |
| 4 | [Going Global](./Module_4_Going_Global.md) | AWS Regions, Availability Zones, Edge Locations, CloudFront, Global Accelerator |
| 5 | [Intro to Networking](./Module_5_Intro_to_Networking.md) | Amazon VPC, public vs. private subnets, network segmentation and security boundaries |
| 6 | [Storage](./Module_6_Storage.md) | S3, EBS, EFS, storage classes and use case mapping |
| 7 | [Databases](./Module_7_Databases.md) | RDS, DynamoDB, Aurora, relational vs. non-relational use cases |
| 8 | [AI/ML and Data Analytics](./Module_8_-_AI_ML_and_Data_Analytics.md) | Core AI/ML services, data analytics tooling overview |
| 9 | [Security](./Module_9_Security_3.md) | AuthN/AuthZ, IAM structure, root user, PoLP, KMS, GuardDuty, Inspector, Detective, Security Hub |
| 10 | [Monitoring, Compliance & Governance](./Module_10_-_Monitoring__Compliance_and_Governance_in_the_AWS_Cloud.md) | CloudWatch, CloudTrail, Config, compliance programs |
| 11 | [Pricing and Support](./Module_11_Pricing_and_Support.md) | Pricing principles, cost drivers, Billing Dashboard, Budgets, Cost Explorer, Support Plans |
| 12 | [Migrating to the AWS Cloud](./Module_12_Migrating_to_the_AWS_Cloud_2.md) | Cloud Adoption Framework (CAF), migration strategies (the 6 R's) |
| 13 | [Well-Architected Solutions](./Module_13_Well_Architected_Solutions_3.md) | 6 Pillars of the Well-Architected Framework, WA Tool, specialized services, real-world architecture blueprints |

---


## Key Exam Watch-Outs

- **6 Pillars, not 5** — Well-Architected Framework now includes **Sustainability** as of recent exam updates
- **SQS (pull) vs. SNS (push)** — frequently tested distinction
- **Inspector (proactive scanning) vs. GuardDuty (active threat detection) vs. Detective (root cause investigation)** — high-yield security service mapping
- **Shared Responsibility shifts by service model** (IaaS → PaaS → SaaS) — boundary is not fixed
- **Service launch order**: SQS (2004) → S3 & EC2 (2006) — common trick-question detail

---
