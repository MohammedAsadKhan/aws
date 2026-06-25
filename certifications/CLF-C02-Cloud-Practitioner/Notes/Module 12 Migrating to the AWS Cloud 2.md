#aws #cloud 
# Introduction
## 1. The Three-Phase Cloud Migration Process
AWS structures large-scale cloud migrations into a continuous, iterative three-phase framework. Moving systematically through these phases reduces operational risk, aligns stakeholders, and ensures financial viability.
### Ⅰ. Assess (The Baseline Readiness)
- **Definition:** Evaluating an organization's current operational, technical, and cultural readiness to operate efficiently in the cloud.
- **Core Activities:**
    - Identifying foundational business outcomes, overarching migration drivers, and strategic milestones.
    - Formulating a comprehensive, data-driven **business case** for cloud adoption.
    - Mapping existing assets to discover what resources currently run on-premises or in other cloud environments.
- **Cybersecurity Boundary:** Establishing initial landing zone security postures, discovering asset inventories, and identifying legacy compliance requirements that must be accounted for in the target cloud architecture.
### Ⅱ. Mobilize (The Blueprint Phase)
- **Definition:** Addressing the readiness gaps discovered in the Assess phase, building a detailed operational plan, and refining your target environment architectures.
- **Core Activities:**
    - Map and analyze the complex **interdependencies** across application components, networks, and databases in your current infrastructure.
    - Formulate specific migration strategies (e.g., the 7 Rs) tailored to meet distinct business objectives.
    - Set up an initial operational environment in AWS (frequently a Landing Zone) with foundational access controls and billing boundaries.
### Ⅲ. Migrate & Modernize (The Execution Tier)
- **Definition:** Actively transferring workloads into the cloud, verifying performance, and adapting cloud-native structures.
- **Core Activities:**
    - Designing, migrating, testing, and validating every isolated workload or application tier.
    - Utilizing AWS migration specialists, professional services, or verified AWS Competency Partners to offset skills shortages or accelerate time-to-market.
    - Shifting applications from simple lift-and-shift patterns toward modernized architecture frameworks (e.g., refactoring toward serverless or microservices) to maximize cloud value.
## 2. Centralized Governance: AWS Migration Hub
- **Unified Management:** Actively bridges the execution gaps between phases. While primarily utilized to orchestrate and **mobilize** foundational tracking data, it functions as a single pane of glass to discover, plan, track, and manage migrations during the **Migrate & Modernize** phase.
- **Telemetry Aggregation:** Consolidates status metrics from various AWS tools (such as AWS Application Migration Service or AWS Database Migration Service) alongside third-party tools, eliminating fragmented visibility across complex application migrations.
⚠️ EXAM FLAGS: Scenario Triggers
- **If an exam scenario asks** for the step where an organization evaluates its structural readiness for cloud adoption, defines its overarching business case, and identifies initial outcomes: **Select the Assess Phase**.
- **If a question outlines a scenario** where a company needs a central, single dashboard to track the status of multiple moving applications across various migration tools: **Select AWS Migration Hub**.
- **If a question states** that a company is evaluating application interdependencies and selecting appropriate migration paths to close technical readiness gaps: **Select the Mobilize Phase**.
💡 Cybersecurity & Technical Pass Tips
- **Discovering Dependencies Early to Prevent Breach Vectors:** Legacy application footprints often rely on undocumented, hardcoded internal connections, legacy protocols, or implicit network trust boundaries. During the **Mobilize** phase, mapping these interdependencies is critical. Failing to discover a hidden backend database dependency before migration can disrupt application availability or lead to misconfigured security groups that accidentally expose legacy interfaces to the internet.
- **Applying the Principle of Least Privilege During Transition:** Migration requires highly privileged service accounts to read and duplicate local disks or databases. Ensure these migration credentials are distinct, fully audited via AWS CloudTrail, and strictly isolated from standard production roles. Once the **Migrate & Modernize** phase finishes, these migration-specific IAM roles should be instantly revoked to eliminate residual access risks.
# Migration Frameworks and Strategies
## The AWS Cloud Adoption Framework (AWS CAF)
The AWS Cloud Adoption Framework (CAF) is a structured framework developed by AWS Professional Services. It leverages AWS experience and historical best practices to help organizations systematically map out, accelerate, and de-risk their cloud transformation journey.

Rather than treating a cloud migration solely as a technical IT infrastructure update, AWS CAF enforces comprehensive organizational change by grouping strategic guidance into **six distinct perspectives**. These six perspectives are split evenly into two overarching capabilities: **Business Capabilities** and **Technical Capabilities**.

### A. Business Capabilities (Organizational & Strategic)
These perspectives focus on aligning the cloud migration with overall corporate strategy, managing organizational talent shifts, and maintaining institutional control.
#### Ⅰ. Business Perspective
- **Core Focus:** Ensuring that the cloud transformation aligns tightly with organizational business goals, financial targets, and strategic models.
- **Key Activities:** Formulating the financial business case, tracking return on investment (ROI), evaluating budget impacts, and monitoring value realization.
- **Target Roles/Stakeholders:** Business Analysts, Financial Analysts, Procurement Managers, and Executive Leadership.
#### Ⅱ. People Perspective
- **Core Focus:** Managing the human capital component of the transformation, shifting corporate culture, and bridging technical capability deficits.
- **Key Activities:** Uncovering structural skills gaps, creating comprehensive training programs, optimizing talent recruitment, and managing organizational change management (OCM).
- **Target Roles/Stakeholders:** Human Resources (HR), Training Directors, and Talent Managers.
#### Ⅲ. Governance Perspective
- **Core Focus:** Managing and minimizing the business risks associated with cloud transformation while optimizing project execution.
- **Key Activities:** Managing cloud portfolios, updating enterprise risk management matrices, conducting benefits management, and enforcing program governance.
- **Target Roles/Stakeholders:** Chief Information Officers (CIOs), Program Managers, Project Managers, and Enterprise Risk Managers.
### B. Technical Capabilities (Engineering & Execution)
These perspectives focus on the actual design, technical security perimeters, and ongoing infrastructure operations inside the cloud environment.
#### Ⅳ. Platform Perspective
- **Core Focus:** Designing, building, and structurally optimizing cloud-native architectures and infrastructure patterns.
- **Key Activities:** Designing target landing zones, provisioning compute and storage architectures, establishing application patterns, and automating infrastructure deployments.
- **Target Roles/Stakeholders:** Cloud Architects, Developers, and Systems Engineers.
#### Ⅴ. Security Perspective
- **Core Focus:** Enforcing structural data privacy, identity control, and continuous regulatory compliance across cloud workloads.
- **Key Activities:** Designing identity and access management (IAM) perimeters, building data encryption-at-rest and in-transit strategies, establishing incident response playbooks, and automating vulnerability screening.
- **Target Roles/Stakeholders:** Chief Information Security Officers (CISOs), Security Architects, and Application Security Engineers.
#### Ⅵ. Operations Perspective
- **Core Focus:** Enabling, running, monitoring, and recovering IT workloads to the precise service level agreements (SLAs) agreed upon with business stakeholders.
- **Key Activities:** Defining day-to-day and quarter-to-quarter operating procedures, configuring performance telemetry monitoring, coordinating application logging, and executing disaster recovery (DR) protocols.
- **Target Roles/Stakeholders:** IT Operations Managers, IT Support Managers, and Site Reliability Engineers (SREs).
## 3. The AWS CAF Deliverable: The Action Plan
- **Process Flow:** Organizations use the six perspectives to methodically evaluate their current state, which allows them to pinpoint precise technical and operational gaps in their skills and legacy processes.
- **The Action Plan:** These discovered gaps are documented as structured inputs to generate a tailored **AWS CAF Action Plan**. This action plan serves as the definitive engineering and change-management roadmap used to guide the entire organization safely through its cloud journey.
⚠️ EXAM FLAGS: Scenario Triggers
- **If an exam scenario asks** for a framework created by AWS Professional Services that provides comprehensive guidance to reduce business risk, organize stakeholders, and identify process/skills gaps prior to migration: **Select AWS Cloud Adoption Framework (AWS CAF)**.
- **If a question asks** which AWS CAF perspective an HR manager or corporate trainer falls under when addressing cloud-skills training and organizational restructuring: **Select the People Perspective**.
- **If a question asks** which AWS CAF perspective is explicitly responsible for defining daily operating procedures, managing system monitoring alerts, and recovering IT workloads to agreed-upon service levels: **Select the Operations Perspective**.
- **If a scenario asks** to identify the primary business-focused capabilities versus technical-focused capabilities:
    - **Business Capabilities:** Business, People, Governance.
    - **Technical Capabilities:** Platform, Security, Operations.
💡 Cybersecurity & Technical Pass Tips
- **Securing the "Operations" Interface:** During a migration, legacy operational workflows (like manual server patching or static configuration sheets) are replaced by cloud-native operations (such as automated patching pipelines via AWS Systems Manager). From a security perspective, ensuring your **Operations Perspective** stakeholders understand cloud-native telemetry is critical. If your operational teams do not update their incident response and logging procedures to ingest automated cloud alerts, a technical breach or architecture failure could go unnoticed for days.
- **Treating the CAF Action Plan as an Attack-Surface Blueprint:** The gaps identified during a CAF evaluation frequently highlight severe organizational vulnerabilities (e.g., "Lack of centralized encryption standards" under Security, or "No automated infrastructure provisioning" under Platform). Treat the resulting **AWS CAF Action Plan** as highly confidential, internal documentation. If a malicious actor compromises these assessment files, they gain an immediate, high-fidelity roadmap detailing your organization's exact architectural weaknesses and un-trained personnel sectors.
## Seven Migration Strategies
## The 7 Rs Migration Strategies
When transitioning workloads to the cloud, every application in an enterprise IT portfolio maps to one of seven distinct migration pathways known as the **7 Rs**. Selecting the appropriate path requires a balance between speed, cost, migration complexity, and target-state performance requirements.
### A. The Migration Pathways (Workloads Transferred)
#### Ⅰ. Rehost ("Lift and Shift")
- **Mechanism:** Moving applications from an on-premises ecosystem to AWS without altering the application architecture or code configuration. Legacy physical or virtual servers are typically converted straight into Amazon EC2 Virtual Machines (VMs).
- **Strategic Value:** Provides the fastest path to the cloud. While it fails to exploit cloud-native scaling out of the gate, companies frequently save up to 30% in total infrastructure operational costs through raw resource virtualization.
- **Key Risk:** Inherits all legacy engineering flaws, technical debt, and inefficiencies from the on-premises deployment.
#### Ⅱ. Relocate ("Hypervisor Shift")
- **Mechanism:** Transferring virtualized environments or containerized software platforms directly to a cloud-equivalent hosting zone without changing configuration patterns or code base.
- **Strategic Value:** Specifically used when the application is already decoupled inside on-premises hypervisors or standard container registries, allowing operations to smoothly shift the hosting endpoint to an AWS-managed platform (e.g., VMware Cloud on AWS).
#### Ⅲ. Replatform ("Lift, Tinker, and Shift")
- **Mechanism:** Moving workloads to the cloud while implementing target, high-value optimizations to infrastructure components, **without modifying the application's underlying source code**.
- **Canonical Example:** Migrating a legacy, self-managed on-premises MySQL database onto a fully managed platform like **Amazon RDS** or **Amazon Aurora** without changing the core application logic.
- **Strategic Value:** Offloads heavy operational infrastructure management tasks (backups, patching, scaling) to AWS with minimal development cycles.
#### Ⅳ. Refactor / Rearchitect ("Cloud-Native Redesign")
- **Mechanism:** Completely re-engineering and rewriting the application's source code to exploit cloud-native features, modern architectures, and serverless technology platforms.
- **Canonical Example:** Breaking a monolithic application apart into microservices or serverless functions using **AWS Lambda** and **Amazon ECS/EKS**.
- **Strategic Value:** Yields the highest long-term agility, feature velocity, performance scalability, and cost optimization metrics.
- **Trade-Off:** Incurs the highest initial upfront planning, financial investment, development cycles, and human engineering effort.
#### Ⅴ. Repurchase ("Drop and Shop")
- **Mechanism:** Abandoning a legacy internal application or commercial licensing agreement completely and transitioning to a fresh product tier, typically a cloud-native Software-as-a-Service (SaaS) architecture or alternative cloud vendor.
- **Canonical Example:** Dropping a proprietary on-premises customer relationship management (CRM) database software package to shop for a cloud-delivered SaaS package.
- **Trade-Off:** Upfront procurement and training costs increase, and the data-migration pipeline between incompatible schema packages can become complex.
### B. The Non-Migration Pathways (Workloads Left Behind)
#### Ⅵ. Retain ("Stays Where It Lays")
- **Mechanism:** Keeping applications running in their current on-premises or existing facility state rather than executing a migration sequence.
- **Strategic Value:** Applied to workloads that are slated for deprecation within a few months, require massive legacy compliance overhead, or face rigid business dependencies. Migrating them introduces zero net-positive business value.
#### Ⅶ. Retire ("Turn off the Lights")
- **Mechanism:** Systematically identifying, shutting down, and decommissioning workloads that are no longer actively used by the enterprise.
- **Strategic Value:** Portfolio reviews often reveal that **more than 10%** of enterprise IT workloads are completely idle or obsolete. Identifying and retiring these assets immediately claws back operational budget, eliminates support cycles, and reduces corporate technical overhead.
## 5. Architectural Strategy Decision Matrix

|**Strategy**|**Architecture Change?**|**Code Modification?**|**Upfront Effort / Cost**|**Core Driver**|
|---|---|---|---|---|
|**Rehost**|No|No|Low|Speed / Immediate cost reductions|
|**Relocate**|No (Platform shift)|No|Low|Operational continuity for existing VMs/Containers|
|**Replatform**|Minimal (Tinker infrastructure)|No|Medium|Offloading management overhead (e.g., moving to RDS)|
|**Refactor**|Total Redesign|Extensive|High|Massive scale, performance, and feature velocity requirements|
|**Repurchase**|Shift to Vendor|Total Change|Medium-High|Upgrading legacy software to modern commercial SaaS|
|**Retain**|None|None|Zero|Short-term lifecycle, dependencies, or deprecation timeline|
|**Retire**|Decommissioned|None|Zero|Eliminating wasteful, unused enterprise assets|

⚠️ EXAM FLAGS: Scenario Triggers
- **If a scenario describes** a company needing to move hundreds of local servers to AWS as fast as possible to meet a hard data-center exit deadline, without mutating application code: **Select Rehost**.
- **If a question states** an organization wants to shift a self-managed database to AWS to eliminate administrative tasks like hardware patching and automated backups, but **cannot modify the underlying application code**: **Select Replatform**.
- **If a question describes** a company rewriting a legacy monolithic platform from scratch to use a serverless, highly scalable microservices architecture on AWS Lambda: **Select Refactor (or Rearchitect)**.
- **If an enterprise discovers** that 15% of its internal tracking applications are obsolete, unutilized, and driving unnecessary operational costs: **Select Retire**.
- **If a question highlights** changing from an on-premises commercial software license package to a modern cloud-based SaaS alternative: **Select Repurchase**.

💡 Cybersecurity & Technical Pass Tips
- **Reducing the Enterprise Attack Surface via "Retire":** From a security architecture perspective, every active server, legacy database, or application framework represents an entry point for an adversary. Legacy, unused, or unpatched applications ("vampire workloads") frequently lack active monitoring telemetry. Transitioning them to **Retire** is not just an infrastructure cost optimization win—it immediately shrinks the enterprise attack surface by removing old, unmonitored software code that could otherwise be exploited.
- **Code Audits and Vulnerability Injection during "Refactor":** Re-engineering application systems down to the source code level during a **Refactor** pathway means code bases are completely opened up. Ensure that your CI/CD (Continuous Integration/Continuous Delivery) pipelines integrate automated Static Application Security Testing (SAST) tools from the start. Rewriting an application for cloud-native performance without security scanning can introduce critical flaws (like SQL injections or insecure API endpoints) into the production environment.
- **The Configuration Inheritance Hazard of "Rehost":** A pure lift-and-shift does not magically fix poor security posture. If an on-premises server is plagued with weak system configurations, hardcoded root passwords, unpatched local operating system kernels, or unnecessary open ports, **Rehosting** it simply shifts those vulnerabilities directly onto an Amazon EC2 instance. Ensure security groups are strictly configured during a rehost to prevent existing system flaws from being exposed to the public internet.
# Migrations Services and Tools
## Core Migration Services and Tools
AWS provides a structured suite of migration utilities designed to systematically advance an organization through the **Assess**, **Mobilize**, and **Migrate & Modernize** phases.
### A. The Assess Phase: Business Case Generation
#### Ⅰ. Migration Evaluator (Formerly TSO Logic)
- **Definition:** A data-driven pre-migration analysis service focused entirely on generating a directional **business case** and projecting target AWS cloud costs.
- **Core Capabilities:**
    - Captures a snapshot of the on-premises resource footprint (CPU, RAM, Storage) and analyzes real-time utilization trends.
    - Translates raw performance metrics into optimized, right-sized AWS configuration recommendations (e.g., matching local configurations to the most cost-effective Amazon EC2 or EBS tiers).
    - Automatically applies industry benchmarks and identifies opportunities to optimize and reuse existing software licenses (Bring Your Own License - BYOL).
- **Primary Deliverable: Quick Insights Report**
    - A high-fidelity, data-driven financial document shared with corporate stakeholders and executive teams to justify the total cloud investment and highlight exact cost-reduction paths
### B. The Mobilize Phase: Deep Discovery & Dependency Mapping
#### Ⅱ. AWS Application Discovery Service (ADS)
- **Definition:** The engineering toolset that scans local enterprise data centers to automatically inventory local server hardware and map technical application structures.
- **Core Capabilities:**
    - Collects static configuration details (server hostnames, IP/MAC addresses, resource allocations) along with dynamic performance telemetry.
    - **Network Dependency Mapping:** Monitors active Transmission Control Protocol (TCP) connections to visually identify which local servers and database endpoints must communicate with one another to keep an application running.
- **Deployment Vectors:**
    - **Discovery Agent:** Software installed directly onto local OS kernels (Windows/Linux) to provide deep, agent-based discovery, system utilization reports, and network connection tracing.
    - **Agentless Collector:** A lightweight virtual appliance deployed directly onto local hypervisors (e.g., VMware) to provide immediate asset discovery without local OS modification.
### C. The Central Governance Command Plane
#### Ⅲ. AWS Migration Hub
- **Definition:** A centralized operational dashboard provided at **no additional cost** that aggregates portfolio tracking metrics from discovery to final execution.
- **Core Capabilities:**
    - Combines asset inventory profiles with network diagrams built from ADS metrics, allowing engineers to group dependent servers into logical "Applications."
    - Functions as a single pane of glass that tracks the real-time status of migrations being handled by various underlying tools (like AWS Application Migration Service or AWS Database Migration Service).
    - Provides prescriptive "journey templates" and automated recommendations to orchestrate modernization and fast-track application refactoring.
### D. The Migrate & Modernize Phase: Technical Execution
#### Ⅳ. AWS Application Migration Service (AWS MGN)
- **Definition:** The definitive AWS service recommended for **mass-scale lift-and-shift (Rehost)** migrations. It converts physical, virtualized, or cloud-hosted source servers to run natively on AWS.
- **Core Technical Mechanism:**
    - Operates strictly at the **block-storage level**. It copies every block from directly attached local drives (SAN, local hard disks) and replicates them over a secure network into equivalent target Amazon EBS volumes.
    - Employs continuous data protection (CDP) synchronization, enabling non-disruptive background data replication while production workloads continue running locally.
    - **Automated Machine Conversion:** During cutover execution, MGN modifies kernel drivers and network configurations to automatically convert the replicated disks into a bootable, native Amazon EC2 instance with an RTO (Recovery Time Objective) of minutes.
    - **Post-Launch Modernization Actions:** Features a built-in automation engine that can instantly apply post-migration changes, such as upgrading Windows Server operating system versions or injecting disaster recovery parameters during launch.
## 7. Migration Tool Selection Matrix

|**Core Requirement**|**Migration Evaluator**|**Application Discovery Service (ADS)**|**Migration Hub**|**Application Migration Service (MGN)**|
|---|---|---|---|---|
|**Build a Financial Business Case**|🟩 **Primary**|🟥 No|🟨 Secondary|🟥 No|
|**Map Application Interdependencies**|🟥 No|🟩 **Primary**|🟩 **Primary**|🟥 No|
|**Group Servers into Applications**|🟥 No|🟨 Secondary|🟩 **Primary**|🟥 No|
|**Execute Server Disk Replication (Rehost)**|🟥 No|🟥 No|🟥 No|🟩 **Primary**|
|**Track Overall Migration Wave Status**|🟥 No|🟥 No|🟩 **Primary**|🟨 Secondary|

⚠️ EXAM FLAGS: Scenario Triggers

- **If a scenario asks** for a service that eliminates financial guesswork by automatically capturing utilization data to build a **business case** detailing projected AWS costs and software license optimization scenarios: **Select Migration Evaluator**.
- **If a question outlines** an environment with zero up-to-date architecture documentation, requiring a tool to map **active network dependencies** and TCP connections between local on-premises servers: **Select AWS Application Discovery Service (ADS)**.
- **If an exam question requires** a single centralized dashboard to **group discovered servers into discrete applications** and track their progress across multiple distinct migration tools at no cost: **Select AWS Migration Hub**.
- **If a company wants** to systematically move physical servers or VMware virtual machines directly onto AWS as Amazon EC2 instances with **minimal downtime** and without modifying source environment application code: **Select AWS Application Migration Service (AWS MGN)**.

💡 Cybersecurity & Technical Pass Tips
- **Protecting the Discovery Footprint (ADS data integrity):** The AWS Application Discovery Service agent requires deep permissions to capture system configurations, running processes, and network sockets. Because the agent creates an un-bypassable asset inventory list, this telemetry data must be strictly isolated. Under the AWS Shared Responsibility Model, ensure that the data collected by ADS is protected via strict IAM policies and encrypted at rest using custom AWS KMS keys. If an unauthorized entity gains access to your ADS discovery exports, they obtain an exhaustive architectural map of your entire corporate data center, including hidden internal dependencies and target network boundaries.
- **Mitigating Replication Layer Risk with MGN Staging Areas:** AWS MGN works by installing a local replication agent on the source machine that continually streams block changes to a **Staging Area Subnet** inside your target AWS VPC. This staging area hosts lightweight, low-cost EC2 instances that catch and commit incoming blocks to EBS volumes. From a security architecture perspective, this staging area should be isolated from the rest of your production network via strict security groups and network ACLs. Do not allow these transient replication workers to communicate with secure internal network tiers until the final instance conversion and post-launch modernization security validation actions have been successfully executed.
# Migrating Databases to the AWS Cloud
## Database Migrations
Migrating relational databases, data warehouses, or NoSQL footprints to the cloud presents two core challenges: **Schema Structural Conversion** (transforming the data blueprint and database code) and **Data Ingestion/Replication** (transferring the actual data records). AWS provides two highly specialized utilities to execute these functions safely with minimal operational disruption.
### A. AWS Schema Conversion Tool (AWS SCT)
- **Definition:** A pre-migration application designed to analyze, evaluate, and transform database structures and code objects from one engine flavor to another.
- **Core Technical Functions:**
    - **Schema Mapping:** Translates database blueprints, including table structures, indexing properties, data field constraints, and relationships.
    - **Code Refactoring:** Automatically refactors internal database logic—such as stored procedures, views, triggers, and functions—to align with the target engine's dialect.
    - **Effort Assessment Reporting:** Scans the source database and outputs a high-fidelity assessment report detailing conversion complexity, automated success probabilities, and exact blocks of incompatible code requiring manual engineering review.
- **Primary Paradigm:** **Heterogeneous Planning**. It does not move raw tabular data; it maps the structural tracks so that data can be cleanly received by a different type of engine.
### B. AWS Database Migration Service (AWS DMS)
- **Definition:** A fully managed, highly resilient service designed to quickly, securely, and cost-effectively transfer actual data records and warehouses into AWS.
- **Core Technical Mechanism:**
    - Operates via a dedicated replication engine running specialized synchronization software.
    - Establishes a persistent, dual-ended network connection linking a defined **Source Endpoint** to a target cloud **Target Endpoint**.
- **Key Features & Capabilities:**
    - **Zero-Downtime Migration:** Replicates data changes dynamically while the source database remains completely live and actively serving production application traffic.
    - **Continuous Change Data Capture (CDC):** Captures ongoing local modifications in real time, caching and committing them to the target AWS database until cutover.
    - **Failback Resiliency:** Maintains data synchronization in a state that permits operations to seamlessly abort and fall back to the legacy on-premises database if validation criteria fail.
    - **Cross-Geographic Replication:** Natively supports shipping records across disparate AWS Regions or Availability Zones (AZs).
## 9. Structural Topologies: Homogeneous vs. Heterogeneous

Database migrations are architecturally classified based on whether the underlying software engine shifts during transition.

```
[Homogeneous Migration]
On-Premises MySQL ─────────────( Natively Via AWS DMS )────────────> Amazon RDS MySQL
                              *No Engine Change, One-Step Process*

[Heterogeneous Migration]
On-Premises Oracle ──> [ AWS SCT: Converts Schema ] ──> [ AWS DMS: Moves Data ] ──> Amazon Aurora PostgreSQL
                            *Engine Changes, Two-Step Process*
```

### Ⅰ. Homogeneous Migrations (Like-for-Like)
- **Definition:** The source engine and target engine are identical or fully compatible.
- **Canonical Examples:** * On-premises Microsoft SQL Server $\rightarrow$ Amazon RDS for SQL Server
    - Local self-managed MySQL Hypervisor $\rightarrow$ Amazon Aurora MySQL-Compatible Edition
- **Execution Pattern:** Simple, one-step execution. Because data types, structural constraints, and schema code are natively compatible, engineers link endpoints straight to **AWS DMS** and begin replication without an intermediate abstraction step.
### Ⅱ. Heterogeneous Migrations (Cross-Engine Shift)
- **Definition:** The source engine type and the target cloud engine type are completely different.
- **Canonical Examples:** * Legacy Commercial Oracle Database $\rightarrow$ Amazon Aurora PostgreSQL-Compatible Edition
    - On-premises Microsoft SQL Server $\rightarrow$ Amazon RDS for MySQL
- **Execution Pattern:** Complex, **two-step execution pipeline**. Because data schemas and underlying database code dialects conflict, engineers must chain services sequentially:
    1. **Step 1:** Run **AWS SCT** to evaluate compatibility, convert the local structural schema blueprint, and deploy the new tables onto the target AWS instance.
    2. **Step 2:** Fire up **AWS DMS** to stream the actual data records across the active endpoints.
## 10. Database Migration Service Decision Matrix

|**Requirement / Scenario Objective**|**AWS Database Migration Service (DMS)**|**AWS Schema Conversion Tool (SCT)**|
|---|---|---|
|Move actual data records from an on-premises engine to AWS|🟩 **Primary**|🟥 No|
|Convert views, triggers, and stored procedures to a new SQL dialect|🟥 No|🟩 **Primary**|
|Perform a live migration with minimal downtime to production|🟩 **Primary**|🟥 No|
|Generate an assessment report detailing structural migration complexity|🟥 No|🟩 **Primary**|
|Execute a one-step, like-for-like (Homogeneous) database copy|🟩 **Primary**|🟥 No (Unnecessary)|
|Execute a two-step, cross-engine (Heterogeneous) database transition|🟩 **Active Data Carrier**|🟩 **Structural Pre-requisite**|

⚠️ EXAM FLAGS: Scenario Triggers
- **If an exam question mentions** migrating data from an on-premises database to an AWS database while ensuring **the source database remains fully operational and online** during the process: **Select AWS Database Migration Service (AWS DMS)**.
- **If a scenario asks** how to migrate a commercial database to an open-source engine on AWS (such as Oracle to Amazon Aurora) and specifically highlights the need to convert database code objects like **stored procedures, views, and functions**: **Select AWS Schema Conversion Tool (AWS SCT)**.
- **If a question outlines a "Homogeneous Migration"** (e.g., MySQL to RDS MySQL) and asks for the fastest tool to move the database: **Select AWS DMS alone** (SCT is not required when the engines match).
- **If a question outlines a "Heterogeneous Migration"** (e.g., Microsoft SQL Server to Amazon Aurora PostgreSQL) and asks for the required combination of tools to achieve this: **Select both AWS SCT and AWS DMS**.

💡 Cybersecurity & Technical Pass Tips
- **Data Masking and Flight Ingestion Security:** Under the AWS Shared Responsibility Model, executing database migrations exposes high-value transactional customer profiles to transit risks. When configuring your DMS Replication Instance, **always enforce SSL/TLS encryption in transit** on both your source and target endpoints. Furthermore, if you are migrating production datasets down to a staging or testing cloud environment for validation, ensure that sensitive identifiers (like SSNs, passwords, or credit card arrays) are dynamically masked or anonymized via DMS transformation rules at the replication instance layer before the data hits the target environment.
- **Isolating the DMS Replication Engine in Your VPC Architecture:** A DMS replication instance is fundamentally a specialized Amazon EC2 instance deployed inside your target network. To protect it from external exploit vectors, it should **never be provisioned with a public IP address or placed in a public subnet**. Instead, position the replication instance inside a private subnet. Establish network private connectivity to your on-premises facility using an encrypted site-to-site VPN or AWS Direct Connect, and configure security groups to lock down traffic interfaces so that only authorized database administrators and designated source database ports can speak to the replication node.
# Migrating to the AWS Cloud
## Transferring Data Online
Moving bulk unstructured data, transactional datasets, or legacy file systems over live network architectures requires balancing security constraints, data validation mechanics, scheduling windows, and bandwidth footprints. AWS provides distinct, purpose-built tools to orchestrate online network ingestion based on the underlying data delivery mechanism.
### A. AWS DataSync (Automated Bulk Ingestion)
- **Definition:** A highly accelerated, secure data-transfer service designed to automate and optimize the movement of massive datasets between on-premises storage architectures and AWS.
- **Underlying Technical Mechanics:**
    - Requires deploying a lightweight software **DataSync Agent** as a virtual machine (VM) in your local infrastructure close to your Network Attached Storage (NAS) or Storage Area Network (SAN).
    - Uses a proprietary, multi-threaded network protocol to parallelize data streams and maximize the utilization of your available network pipe.
    - **Built-In Data Validation:** Performs inline cryptographic verification via MD5/SHA checksum validations both in-transit and at-rest, ensuring the files arrive safely with no packet corruption.
- **Core Governance Features:**
    - **Bandwidth Throttling:** Allows engineers to establish maximum network consumption caps so data migration streams do not starve production internet traffic.
    - **Task Scheduling & Filtering:** Supports configuring execution cron schedules (e.g., run only during off-peak windows from 02:00 to 05:00) along with prefix/suffix exclusions.
- **Target AWS Storage Endpoints:** Streams directly to **Amazon S3**, **Amazon EFS**, or **Amazon FSx**.
- **Primary Use Cases:** Executing active mass migrations, routine archiving of cold data layers, and automating continuous hybrid-cloud storage synchronization loops.
### B. AWS Transfer Family (Legacy Protocol Modernization)
- **Definition:** A fully managed, highly scalable cloud gateway that enables seamless, direct file transfer interactions using legacy industry-standard protocols straight into cloud-native storage backends.
- **Supported Protocols:**
    - **SFTP** (Secure File Transfer Protocol - SSH-based)
    - **FTPS** (File Transfer Protocol Secure - TLS/SSL encrypted)
    - **FTP** (File Transfer Protocol - unencrypted, legacy boundary)
    - **AS2** (Applicability Statement 2 - often used for B2B transactional data)
- **Underlying Technical Advantage:**
    - Eliminates the operational overhead of spinning up, maintaining, patching, and scaling standard Linux/Windows FTP virtual machine servers in public subnets.
    - Seamlessly abstracts the file transfer endpoint. External customers, suppliers, internal business units, or legacy automation scripts continue running their normal file transmission routines without altering their application code or client software.
- **Target Storage Integration:** Files uploaded through the Transfer Family are dynamically backed by **Amazon S3** or **Amazon EFS** as standard objects/files, allowing immediate downstream application ingestion.
### C. AWS Direct Connect (The Private Physical Highway)
- **Definition:** A network service that establishes a dedicated, private physical fiber-optic connection bypassing the public internet entirely to link an organization's on-premises corporate data center or co-location facility directly into AWS.
- **Data Migration Value Layer:**
    - While classified under the Global Network Engineering domain, it functions as the structural highway used by both **AWS DataSync** and **AWS DMS** to move immense scale datasets online.
- **Core Strengths:**
    - Drastically **reduces network egress costs** compared to data shipped over the standard public internet.
    - Maximizes available data throughput by substituting volatile public internet routes with predictable, deterministic network performance and massively increased bandwidth capacities (available in configurations up to 100 Gbps).
## 12. Online Ingestion Technology Selection Matrix

|**Core Use Case Scenario Requirement**|**AWS DataSync**|**AWS Transfer Family**|**AWS Direct Connect**|
|---|---|---|---|
|Need an automated, multi-threaded tool to lift-and-shift on-premises NAS filesystems to S3|🟩 **Primary**|🟥 No|🟥 No|
|Third-party vendor mandates shipping daily CSV transactions using **SFTP** protocols|🟥 No|🟩 **Primary**|🟥 No|
|Enterprise demands a completely **private physical connection** that bypasses the public internet|🟥 No|🟥 No|🟩 **Primary**|
|Requires dynamic **bandwidth throttling** and execution tasks mapped to off-peak schedules|🟩 **Primary**|🟥 No|🟥 No|
|Need a fully managed service to replace legacy on-premises FTP server hardware|🟥 No|🟩 **Primary**|🟥 No|

⚠️ EXAM FLAGS: Scenario Triggers
- **If a question outlines a scenario** where an engineer needs to automate and accelerate bulk file migrations between on-premises storage and Amazon S3 with built-in **bandwidth throttling, task scheduling, and data integrity verification**: **Select AWS DataSync**.
- **If an exam question mentions** migrating or modernizing business workflows where external partners or internal applications are hardcoded to upload files using **SFTP, FTPS, or FTP** directly into AWS storage without managing server infrastructure: **Select AWS Transfer Family**.
- **If a scenario requires** a high-throughput, consistent network migration pipeline that completely **bypasses the public internet** to reduce outbound network transfer costs and achieve maximum bandwidth predictability: **Select AWS Direct Connect**.
💡 Cybersecurity & Technical Pass Tips
- **Mitigating FTP Exploitation via the Transfer Family Perimeter:** Standard FTP transmits data payloads and authentication credentials in completely unencrypted cleartext. If an exam scenario presents a legacy architecture bound to FTP, migrating it to **AWS Transfer Family** allows security architects to inject technical validation controls. You can enforce a migration transition path toward **SFTP**, integrate AWS Transfer Family natively with **AWS Secrets Manager** for robust authentication lifecycle rotation, and leverage **Amazon GuardDuty** to run behavioral analytics across incoming connection requests to isolate unauthorized source IPs.
- **Enforcing End-to-End Cryptographic Isolation over Direct Connect:** A common cybersecurity misconception is that an AWS Direct Connect link is automatically encrypted by default. Because it is a raw physical circuit bypassing the public internet, data streams over standard Direct Connect travel unencrypted. To fulfill strict regulatory compliance requirements (such as HIPAA or PCI-DSS), security engineers must layer cryptographic security protocols on top of the connection. This is achieved by provisioning an **AWS Site-to-Site VPN connection inside the Direct Connect private virtual interface (VIF)**, wrapping all active DataSync or database migration streams inside an IPsec encrypted tunnel.
- **Validating Data Ingestion Integrity via Checksums:** When using AWS DataSync to migrate transactional datasets, always ensure the verification option is fully enabled. DataSync calculates the SHA-256 or MD5 hashing signature of the local file before transport, streams it, and cross-references it against the object metadata hash inside Amazon S3. If an attacker executes a malicious Man-in-the-Middle (MitM) packet manipulation attempt or a system error clips a data block mid-flight, the signatures mismatch, DataSync immediately flags validation failure, halts task reporting, and triggers an automated re-transfer loop to guarantee absolute data confidentiality and integrity.
## Transferring Data Offline
## Offline Data Transfer: The AWS Snow Family
When network-based online ingestion frameworks (like AWS DataSync or AWS Direct Connect) become mathematically unviable due to restricted bandwidth, remote physical locations, or extreme multi-petabyte datasets, organizations must pivot to **Offline Data Migration**.
The **AWS Snow Family** is a suite of physical, ruggedized, hardware appliances shipped directly to local data centers or remote operational field zones to capture data locally and transport it to AWS via a physical shipping carrier.

```
                  [ The Data Center Offline Ingestion Pipeline ]
  
  Step 1: Order Device ──> Step 2: Connect Local LAN ──> Step 3: Copy Data (S3/NFS)
        │                                                               │
        ▼                                                               ▼
  Step 6: Verified in S3 <── Step 5: Secure AWS Ingest <── Step 4: Carrier Shipping
```

### A. Core Architectural Constraints Driving Offline Migration
1. **The Bandwidth Bottleneck:** Attempting to stream multiple petabytes of data over standard corporate internet pipes can take months or years, saturating business network resources. Shifting to an offline hardware appliance is often faster than standard internet protocol transmission (_"Never underestimate the bandwidth of a station wagon full of tapes"_).
2. **Disconnected Environments (Austere Edge):** Operations executing out of remote research vessels, sub-surface mining fields, military tactical deployment lines, or geographic mapping areas frequently suffer from complete network isolation where online cloud APIs are completely out of reach.
### B. Deep-Dive: AWS Snowball Edge Devices
AWS Snowball Edge appliances represent the mid-to-high scale baseline tiers of the Snow Family, featuring industrial-grade engineering designed to bridge physical and digital infrastructure.
#### Ⅰ. Snowball Edge Storage Optimized
- **Primary Paradigm:** Mass-scale, ultra-high-velocity offline data migration.
- **Hardware Underpinnings:** Equipped with up to 210 TB of raw, high-performance NVMe block storage configurations to support gigabyte-per-second copy workflows.
- **Best Use Case:** Lifting and shifting massive historical data archives, multi-terabyte system backup layers, vast media processing libraries, or massive analytics logs directly into **Amazon S3** or **Amazon EBS**.
#### Ⅱ. Snowball Edge Compute Optimized
- **Primary Paradigm:** Delivering high-performance compute capacity straight to disconnected field edges.
- **Hardware Underpinnings:** Packed with up to 104 vCPUs, 416 GB of RAM, and optional hardware **Graphics Processing Units (GPUs)** for dense floating-point processing, balanced with a lower local storage footprint (e.g., 28 TB NVMe).
- **Best Use Case:** Executing advanced computer vision modeling, real-time machine learning inference, localized video parsing, or processing industrial IoT telemetry variables on-site before shipping any assets back to civilization.
### C. Advanced Structural Features of the Snow Family
- **Logistical Automation via E-Ink Display:** Snowball Edge appliances feature a built-in Electronic Ink (E-Ink) status panel. When a local backup task terminates and the unit is powered down, the E-Ink display automatically switches to display the return carrier shipping manifest—eliminating manual paperwork, mislabeling risks, and routing human errors.
- **Edge Virtualization Layer:** Both device variants allow engineers to host and run local virtual machine instances via **Amazon EC2 AMIs** or container execution tiers natively on the physical device while it resides completely offline.
- **Localized Storage Abstraction:** Exposes localized endpoints that allow local infrastructure systems to mount the physical appliance as a standard Network File System (NFS) target or communicate via S3-compatible API expressions.
## 14. The Extended Snow Family Hierarchy (Exam Reference Model)
To pass foundational cloud architecture checkpoints, understand where Snowball Edge fits among its sibling appliances:

|**Device Class**|**Physical Form Factor**|**Usable Ingestion Capacity**|**Core Target Workload**|
|---|---|---|---|
|**AWS Snowcone**|Ultra-Portable (4.5 lbs)|~8 TB|Hand-carried tactical edge collection; can migrate data **online via built-in AWS DataSync** or offline via shipping.|
|**AWS Snowball Edge**|Rugged Industrial Suitcase|Up to 210 TB|Multi-petabyte enterprise database/archive migration, complex localized edge computing, and GPU inference.|
|**AWS Snowmobile**|45-foot Ruggedized Semi-Trailer|Up to 100 PB|Exabyte-scale complete data center exit migrations, massive digital media studio transitions.|

⚠️ EXAM FLAGS: Scenario Triggers
- **If a scenario describes** an environment lacking consistent internet connectivity (such as a cruise ship or remote research facility) that needs to collect and process large amounts of data on-site using local virtual machines before transferring it to AWS: **Select AWS Snowball Edge (Compute Optimized)**.
- **If a question states** that a company must migrate 400 Terabytes of historical data archives from an on-premises datacenter with an unstable, low-speed internet connection to Amazon S3 as quickly as possible: **Select AWS Snowball Edge (Storage Optimized)**.
- **If a scenario mentions** a physical device where the return shipping label **automatically updates on a built-in E-Ink screen** upon completion of local tasks: **Select AWS Snowball Edge**.
- **If an exam choice asks** to choose between online and offline transfer tools for moving hundreds of petabytes under tight network constraints: Remember that **AWS DataSync/Direct Connect = Online**, while **AWS Snow Family = Offline**.
💡 Cybersecurity & Technical Pass Tips
- **Enforcing Absolute Cryptographic Isolation at Rest:** Data security over physical carrier pathways is tightly controlled under the AWS Shared Responsibility Model. The moment a Snowball Edge unit boots inside a local facility, **all written data is automatically encrypted with 256-bit encryption keys** generated and managed via **AWS Key Management Service (KMS)**. This encryption is enforced at the hardware controller layer. If a malicious actor hijacks the physical shipping truck mid-transit and attempts to extract the internal NVMe storage drives, the data payloads are completely unreadable without the corresponding cloud-side KMS permissions.
- **Physical Tamper Detection and Hardware Lifecycle Protection:** Every device in the Snow Family is built with an internal **Trusted Platform Module (TPM)** and custom tamper-evident enclosures. If an adversary attempts to open the chassis or splice physical interception lines into the system boards during shipping, the internal security card detects the physical state change. Upon arrival at the AWS ingestion loading dock, engineers run structural telemetry validations. If tamper flags register, the device is immediately quarantined, the ingestion task is aborted, and the physical media is securely wiped to protect corporate confidentiality and data integrity.
- **Post-Ingestion Zero-Trace Sanitization:** Once data is successfully migrated from a Snowball Edge into your target Amazon S3 buckets and cryptographically validated via automated checksum verifications, the physical device enters an automated multi-pass sanitization loop. AWS executes a comprehensive, forensic hardware wipe conforming to **NIST SP 800-88 National Security Guidelines for Media Sanitization**. This guarantees that the next customer renting that exact same physical hardware box can never extract residual data blocks from your enterprise footprint.

This completes your master Obsidian study notes system for **Module 12: Migrating to the AWS Cloud**!
### Master Vault Index for Module 12:
1. **The Three-Phase Migration Process** (_Assess, Mobilize, Migrate & Modernize_)
2. **Centralized Governance Frameworks** (_AWS Migration Hub_)
3. **The AWS Cloud Adoption Framework** (_AWS CAF: 6 Perspectives / Action Plan_)
4. **The 7 Rs Migration Strategies** (_Rehost, Relocate, Replatform, Refactor, Repurchase, Retain, Retire_)
5. **Core Application Tracking Utilities** (_Migration Evaluator, Application Discovery Service, AWS MGN_)
6. **Database Modernization Engines** (_AWS SCT, AWS DMS_)
7. **Online Network Ingestion Paths** (_AWS DataSync, AWS Transfer Family, Direct Connect_)
8. **Offline Data Transport Hardware** (_AWS Snow Family: Snowcone, Snowball Edge, Snowmobile_)
