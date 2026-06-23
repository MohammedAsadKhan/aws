# AWS Projects

Hands-on projects built on AWS, organized by domain. Each project demonstrates practical application of AWS services across AI/ML, security, and cloud infrastructure.

---

## AI/ML Projects

> Projects leveraging AWS AI and machine learning services.

| Project | Description | Services | Status |
|---------|-------------|----------|--------|
| RAG Document Q&A | Upload documents and query them using natural language via a RAG pipeline | Bedrock, OpenSearch, S3, Lambda | 🔄 Coming Soon |
| Image Generation App | Web app that generates images from text prompts using Amazon Bedrock | Bedrock, S3, DynamoDB, CloudFront, EC2 | 🔄 Coming Soon |
| Sentiment Analysis Pipeline | Analyze customer feedback at scale using NLP | Comprehend, S3, Lambda, DynamoDB | 🔄 Coming Soon |

---

## Security Projects

> Projects focused on cloud security, IAM auditing, and threat detection.

| Project | Description | Services | Status |
|---------|-------------|----------|--------|
| IAM Policy Auditor | Script that scans IAM policies for overly permissive rules and flags violations | IAM, Python, Boto3 | 🔄 Coming Soon |
| CloudTrail Log Analyzer | Parses CloudTrail logs to detect suspicious API activity | CloudTrail, S3, Lambda, SNS | 🔄 Coming Soon |
| S3 Security Checker | Automated scanner for misconfigured S3 buckets (public access, no encryption) | S3, Macie, Lambda | 🔄 Coming Soon |

---

## Cloud Projects

> General cloud infrastructure and serverless projects.

| Project | Description | Services | Status |
|---------|-------------|----------|--------|
| Serverless REST API | Full CRUD API with authentication | Lambda, API Gateway, DynamoDB, Cognito | 🔄 Coming Soon |
| Static Website with CDN | Secure, globally distributed static site | S3, CloudFront, Route 53, ACM | 🔄 Coming Soon |

---

## How Projects Are Structured

Each project folder contains:

```
project-name/
├── README.md          # Overview, architecture, setup instructions
├── architecture/      # Architecture diagrams
├── src/               # Source code
└── docs/              # Additional documentation
```
