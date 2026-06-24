# AIF-C01 - Domain 5: AI Governance & Compliance

#aws #ai

> Part of Domain 4 (14% of exam). Covers AWS governance services, data governance strategies, compliance standards, and governance protocols.

---

## What Is GRC?

**G**overnance + **R**isk + **C**ompliance

Simple version: making sure your AI workload follows the rules, is auditable, and doesn't cause legal or ethical problems.

---

## AWS Governance & Compliance Services

|Service|What it does|Simple version|
|---|---|---|
|**AWS Config**|Records resource configurations, tracks changes over time, flags non-compliant resources|"Is my infrastructure set up correctly and staying that way?"|
|**Amazon Inspector**|Scans workloads for software vulnerabilities (CVEs) and unintended network exposure|"Does my infrastructure have known security holes?"|
|**AWS Audit Manager**|Organizes evidence and findings into compliance reports for specific frameworks|"Here's the proof we're compliant with GDPR/SOC 2"|
|**AWS Artifact**|Central place to view AWS's own compliance certifications and auditor reports|"Here's AWS's proof they're compliant"|
|**AWS CloudTrail**|Logs every API action taken across all AWS services — who did what, when|"Full audit trail of everything that happened"|
|**AWS Trusted Advisor**|Runs checks against Well-Architected Framework pillars including security, gives recommendations|"Here's how to do this better"|

### Service → Purpose Map

|Need|Service|
|---|---|
|Audit trail of all API actions|CloudTrail|
|Scan for software vulnerabilities|Inspector|
|Prove compliance with a framework|Audit Manager + Artifact|
|Monitor infrastructure config for drift|AWS Config|
|Best practice recommendations|Trusted Advisor|

---

## Data Governance Lifecycle (in order)

|Phase|What happens|
|---|---|
|**1. Data collection**|Source data from databases, sensors, web scraping, documents|
|**2. Data pre-processing**|Clean and transform data for model training|
|**3. Training**|Use data to train AI models|
|**4. Model deployment**|Model generates outputs from inputs|
|**5. Data archiving & deletion**|Manage data post-use — comply with retention and deletion policies|

---

## Data Governance Key Concepts

|Concept|What it means|
|---|---|
|**Data logging**|Record all key activities related to data usage — supports compliance, troubleshooting, transparency|
|**Data residency & sovereignty**|Where is data physically stored? Some regulations require data to stay in a specific country/region|
|**Monitoring & observation**|Continuously track data usage, model behavior, and compliance — catch anomalies early|
|**Data retention**|How long you keep data after collecting it — keep only the minimum needed|
|**Data deletion**|Securely delete data at end of lifecycle — must still be compliant after deletion|

> Exam tip: "Keep data longer just in case" = wrong. Keep only what you need for the minimum required time, then securely delete.

---

## Governance Protocol Elements

Six things every governance protocol needs:

|Element|What it is|
|---|---|
|**Policies**|Clear guidelines governing organizational behavior|
|**Review cadence**|How often governance is reviewed (answer: **quarterly**)|
|**Review strategies**|Structured approach to monitoring and adapting governance|
|**Governance frameworks**|Established model for organizing and enforcing governance|
|**Transparency standards**|Ensure decisions are open and accessible to stakeholders|
|**Team training requirements**|Continuous education so all staff follow governance standards|

---

## Compliance Standards to Know

|Standard|What it covers|Who it applies to|
|---|---|---|
|**ISO**|International standards across sectors including AI|Global — any organization|
|**SOC (SOC 2)**|Controls for service organizations around data handling and security|US-focused, financial and tech services|
|**GDPR**|Data privacy rights for individuals|EU — any company handling EU citizen data|
|**CCPA**|Consumer privacy rights|California, US — companies handling CA resident data|

> Exam tip: GDPR = EU. CCPA = California. Both are data privacy laws but different jurisdictions.

---

## Practice Questions

---

### Q1 — Prioritizing Data Governance Actions

**Question:** A GenAI system occasionally generates biased outputs based on training data, and there are concerns about long-term storage and potential misuse of sensitive data. Which action should you prioritize?

**A.** Implement robust data logging and monitoring to track model behavior and data access **B.** Increase data retention periods to ensure all training data is kept longer **C.** Store all training data in a centralized location without considering regional data residency laws **D.** Regularly assess and update model training data to mitigate bias and comply with data deletion policies

**Correct Answer: D**

|Option|Why it's wrong/right|
|---|---|
|A|Logging helps monitor but doesn't fix bias or address sensitive data misuse directly|
|B|Keeping data longer is the opposite of best practice — increases risk of misuse|
|C|Ignoring data residency laws = instant compliance violation — eliminate immediately|
|D|Correct — updating training data fixes bias; deletion policies address sensitive data misuse|

**Tips & Tricks:**

- The question has two problems: bias + sensitive data risk. The correct answer must address both
- "Increase retention" is always a trap — less data stored = less risk
- "Ignore residency laws" = automatic elimination — any answer suggesting non-compliance is wrong
- Pattern: bias in outputs → fix the training data. Long-term storage risk → enforce deletion policies. One answer that does both = correct

---

### Q2 — Governance Protocol Review Cadence

**Question:** How often should governance protocols be reviewed to remain effective and relevant in a fast-evolving regulatory environment?

**A.** Annually, with no further reviews until the next cycle **B.** Quarterly, to check compliance and evaluate effectiveness **C.** Monthly, to track small day-to-day adjustments **D.** Continuously, with reviews whenever there are external changes

**Correct Answer: B**

|Option|Why it's wrong/right|
|---|---|
|A|Annual reviews are too infrequent for a fast-changing environment|
|B|Correct — quarterly strikes the right balance: frequent enough to stay current, thorough enough to be meaningful|
|C|Monthly is too frequent for comprehensive protocol evaluation — surface-level only|
|D|Continuous review creates massive operational overhead — monitoring continuously is fine, but full reviews should be scheduled|

**Tips & Tricks:**

- Governance review cadence = **quarterly** — memorize this
- "Continuously" sounds thorough but creates unsustainable overhead — trap answer
- "Annually" sounds stable but too slow for regulatory environments — trap answer
- The key distinction: **monitor continuously, review quarterly**
- Any compliance/governance cadence question without a specific regulation → quarterly is the safe default answer