---
title: "Event 2"
date: 2026-06-11
weight: 1
chapter: false
pre: " <b> 4.2. </b> "
---

# SUMMARY REPORT: CLOUD ARCHITECT & TECH TALK EVENT (JUNE 11)

## 1. Brief Description of Event Content & Core Activities
The event consisted of two primary activity segments: The Cloud Architect Competition Finals and a Series of In-Depth Technical Presentations (Tech Talks) by 3 speakers representing tech enterprises.

### A. Activity 1: Cloud Architect Competition Finals ("Ao Lang" Award)
- **Format:** Cloud architecture scenario-based multiple-choice contest between the top competing teams (KLK AST Team vs. Ngu Dai Hiep Team).
- **Core Topics Covered:** Real-world AWS engineering challenges including:
  - Selecting IaaS models (EC2) and compliant storage device decommissioning processes following safety standards.
  - Enforcing the Principle of Least Privilege for S3 bucket access.
  - High-throughput UDP load balancing solutions for multiplayer gaming combined with key-value databases (NLB + DynamoDB).
  - Automated EC2 error remediation using CloudWatch Logs, Metric Filters & Alarms.
  - Secure content delivery from S3 via CloudFront using Origin Access Control (OAC).
  - Designing low-latency, high-bandwidth hybrid connectivity between On-premises data centers and multi-region VPCs (Direct Connect Gateway).
  - Migrating large-scale MySQL databases (25TB) from On-premises to AWS with minimal downtime (AWS DMS / DataSync / Aurora Replication).
  - Automating AMI/EC2 updates using CloudFormation paired with Systems Manager Parameter Store.

### B. Activity 2: Expert Sharing Series by Tech Speakers

#### Topic 1: Applying AI in Cloud Security with AWS Security Agent
*(Speaker: Mr. Thinh - DevOps/DevSecOps Engineer)*
- Analyzed the limitations of traditional Pentesting (high costs of $5,000–$20,000/run, human dependency, time-consuming).
- Introduced AWS Security Agent leveraging Multi-agent AI / Bedrock to automate: Design Security Reviews (evaluating architecture against PCI-DSS & Well-Architected Framework), Code Reviews (CI/CD integration, Pull Request auditing on GitHub/GitLab), and automated System Pentesting.
- Highlighted practical limitations: Current lack of automated support for complex MFA authentication flows (SSO, Email OTP) or specialized protocols such as mTLS.

#### Topic 2: SLA Governance & Monitoring Systems in Enterprise Practice
*(Speaker: Mr. Nam - Infrastructure/Reliability Engineer)*
- Explained the importance of SLAs (Service Level Agreements) and accountability in upholding commitments to customers.
- Clarified key perspectives: Healthy Infrastructure does not guarantee a Healthy UX if the application suffers from logical connection failures.
- Risk Governance Lifecycle: Identify Risk → Monitor Signal → Response (SOP/SNS) → Log & Improve.
- Live Demo: Building a CloudWatch Dashboard and configuring database disconnection alerts between EC2 (Back-end) and RDS PostgreSQL via AWS SNS.

#### Topic 3: Roadmap & Preparation Strategies for the AWS Certified Cloud Practitioner (CLF-C02)
*(Speaker: Mr. Huy)*
- Overview of the AWS Certification path (Foundational, Associate, Professional, Specialty).
- Structure of the CLF-C02 exam: 65 multiple-choice questions, 120 minutes (includes a 30-minute accommodation for non-native English speakers), passing score of 700/1000, 3-year validity ($100 exam fee).
- Domain weights across 4 areas: Cloud Concepts (24%), Security & Compliance (30%), Cloud Technology & Services (34%), Billing & Pricing (12%).
- Exam tactics: Process of Elimination, Keyword Mapping, hands-on practice via AWS Free Tier, and "Flag for Review" techniques.

## 2. Key Results & Value Gained

### A. Professional Knowledge & Lessons Learned
- **Cloud Architecture & Infrastructure:** Deepened understanding of orchestrating advanced AWS services (Direct Connect, CloudFront OAC, Auto Scaling, SQS, DMS) to solve large-scale infrastructure challenges requiring high availability (HA) and cost optimization.
- **Security Automation (DevSecOps):** Exposed to cutting-edge trends in applying Generative AI / Multi-agent frameworks to code vulnerability auditing and security design right from the planning phase.
- **Enterprise Operations Mindset (SRE/Reliability):** Realized that the ultimate goal of monitoring is not just keeping server indicators "green," but ensuring continuous customer journeys and maintaining strict SLA commitments.

### B. Newly Acquired Skills
- **Hands-on Monitoring Configuration:** Mastered custom Metric Alarms on CloudWatch, setting up alerting matrices via AWS SNS, and bridging connectivity health checks between EC2 and RDS tiers.
- **International Certification Preparation:** Mastered keyword analysis techniques, process-of-elimination strategies, and time allocation tactics for AWS Practitioner/Associate exams.

## 3. Practical Participation Summary & Accumulated Experience
- **Absorbing Real-World Practices:** Direct attendance helped bridge academic theory with real-world enterprise incident management (such as connection drops between back-ends and databases, faulty script executions, or financial penalty risks from SLA breaches).
- **Soft Skills Refinement:** Developed critical thinking and analytical skills when evaluating cloud architecture options during the contest; learned live troubleshooting presentation styles from senior engineers.
- **Career Path Orientation:** Clearly shaped learning roadmaps in Cloud/DevOps, setting structured milestones to earn AWS certifications to strengthen professional portfolios and enhance career competitiveness.

![Event2](/images/4-EventParticipated/event_11-6-26/1.png)
![Event2](/images/4-EventParticipated/event_11-6-26/2.png)
![Event2](/images/4-EventParticipated/event_11-6-26/3.png)
![Event2](/images/4-EventParticipated/event_11-6-26/4.png)
![Event2](/images/4-EventParticipated/event_11-6-26/5.png)
![Event2](/images/4-EventParticipated/event_11-6-26/6.png)
![Event2](/images/4-EventParticipated/event_11-6-26/7.png)
![Event2](/images/4-EventParticipated/event_11-6-26/8.png)