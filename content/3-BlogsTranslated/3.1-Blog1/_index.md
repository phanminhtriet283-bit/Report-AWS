---
title: "Blog 1"
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Building Resilience by Design: Developing Effective Recovery Strategies Against Ransomware

Ransomware incidents have become a priority topic in leadership discussions across modern organizations. Data shows a clear trend: the number of ransomware events has more than doubled since the beginning of the pandemic, with the financial services sector being one of the most heavily targeted. At AWS, our cross-industry collaboration with global financial institutions, regulators, operational bodies, and ecosystem partners has resulted in a certified architecture for the **Cloud Hosted Data Vault (CHDV)**—commonly referred to simply as a *vault*.

A vault is a critical component in strengthening **operational resilience** against large-scale cyber incidents. It acts as a fully isolated final line of defense, protecting the most mission-critical digital assets of an organization. It allows the business to recover even when traditional mechanisms such as High Availability (HA), Business Continuity (BC), Disaster Recovery (DR), or backups can no longer guarantee recovery. Integrating a vault into your existing resilience practices requires careful planning across multiple dimensions. In this article, we explore the key considerations for planning a vault, how it enhances existing HA, BC/DR, and backup strategies, and the people, process, and operational elements required for an effective cyber vaulting solution.

---

## **1. What Should Go Into the Vault?**

Every business unit owner might instinctively say that “everything, everywhere” needs protection. In reality, that’s not true — at least not immediately. During a large-scale cyber incident, it is easy to fall into the mindset that every dataset, application, and service is mission-critical and must be vaulted. While it is tempting to assume that anything running in the production environment is essential, attempting to vault everything without an initial assessment can lead to:

- massive vault sizes  
- excessive costs  
- recovery delays  

During a real cyber crisis, you must ask:

> **Which core IT functions and operational services are necessary to restart the business within the next 12, 24, or 48 hours — and which ones are not?**

These core services are called the **Minimum Viable Business (MVB)** — the minimum foundation required for business survival. They include not only customer-facing services but also dependencies across second-, third-, and fourth-party ecosystems.

![Figure 1: What belongs in the vault? – Focus on core IT functions and essential operational services.](images/hinh1.png)

**Figure 1: What belongs in the vault? – Focus on core IT functions and essential operational services.**

Identifying the MVB cannot be done in isolation. A vault is not just a technical solution — it requires collaboration across:

- IT  
- Security  
- Legal  
- Business unit owners  
- Application owners  
- Senior leadership  

---

## **2. What Will Recovery Look Like?**

Modern cyberattacks are intentionally designed to make system or service recovery as difficult—or nearly impossible—as possible. They aim to break traditional recovery mechanisms such as HA, BC, DR, and Backup.

Because attackers want **maximum disruption with minimal recoverability**, organizations must prepare for several critical elements:

### **Decision Time Objective (DTO)**  
How long does it take to decide to initiate recovery from the vault?

In a cyber incident, automated recovery workflows may no longer be trustworthy because adversaries may have tampered with them. Therefore, human decision-making becomes essential.

### **Cyber-Recovery Time Objective (C-RTO) & Cyber-Recovery Point Objective (C-RPO)**  
Recovery timelines must be recalibrated.  
Processes that normally take seconds may take **days** during a cyber event.

### **Minimum Acceptable Service Offering (MASO)**  
MASO asks:

> “What is the minimum level of service we can still offer customers and third-party partners during recovery?”

This may involve:
- limited functionality of the primary service  
- a temporary fallback system  
- alternative access mechanisms  

![Figure 2: What recovery looks like – What normally takes seconds may take days during a cyber crisis.](images/hinh2.png)

**Figure 2: What recovery looks like – What normally takes seconds may take days during a cyber crisis.**

---

## **3. How Will the Vault Be Segmented?**

Whether you use a single enterprise-wide vault or multiple vaults per service, the goal is always to balance:

- manageability  
- practicality  
- security  

Core vault-design principles include:

### ✔ **Simplicity**  
The vault must be easy to understand and operate.  
Complexity delays recovery.

### ✔ **Independence**  
Each vault should function autonomously, enabling parallel recovery.

### ✔ **Service mapping**  
Determine where recovery begins and the optimal restoration sequence.

### ✔ **Roles & responsibilities**  
Clearly define ownership for:
- applications  
- infrastructure  
- recovery workflows  

### ✔ **Maintenance**  
A vault is not static: applications and business needs evolve, and so must the vault.

![Figure 3: How the vault is segmented – Balancing manageability, content, and recovery workflows.](images/hinh3.png)

**Figure 3: How the vault is segmented – Balancing manageability, content, and recovery workflows.**

AWS provides the flexibility to experiment, fail fast, and iterate without building up technical debt. What seems perfect on paper may fail in testing — and those lessons shape the next vault design.

---

## **4. How Should the Vault Be Managed?**

A vault must be isolated from the operational plane so that any expanding cyber incident in production cannot cross into the vault. Without this separation, the vault itself might be compromised.

Traditional air-gapped solutions rely on physical isolation (e.g., unplugging cables, removing media), creating a literal gap.  
In the cloud, equivalent controls are implemented using:

- **Access zones:** ephemeral environments with limited access windows  
- **Strong MFA:** hardware security tokens for vault operators  
- **Zero Trust:** authenticate every step; trust nothing by default  
- **IAM controls:** enforce strict least-privilege boundaries  
- **Change management:** access only via formal approval workflows  

![Figure 4: How the vault is managed – Intentional isolation while preserving observability.](images/hinh4.png)

**Figure 4: How the vault is managed – Intentional isolation while preserving observability.**

---

## **5. How Should You Plan for Logistics and Service Providers?**

Physical considerations are often overlooked when planning for cyber recovery. When focusing heavily on core applications and infrastructure, organizations frequently neglect external dependencies that are critical to restoration.

Key examples include:

### • Internal and external network access  
Even minor connectivity disruptions can halt recovery.

### • Software repositories  
Despite automation, organizations should maintain physical media (e.g., secure USB drives) for emergency distribution.

### • Supply chain resilience  
Replace destroyed hardware through pre-planned logistics:
- sourcing  
- transport  
- storage  
- deployment  

### • Physical logistics  
Where will teams work during a large-scale recovery?  
Is there backup equipment and workspace available?

![Figure 5: Logistics and service providers – Extending planning to external dependencies.](images/hinh5.png)

**Figure 5: Logistics and service providers – Extending planning to external dependencies.**

Sophisticated ransomware attacks often create multiple minor failures simultaneously. Individually, these failures may seem insignificant — but together, they can create cascading disruptions that dramatically slow recovery.

## **6. Who Is Responsible for the Vaulting Process?**

People are ultimately responsible for managing and operating the cyber vaulting process. They develop best practices and serve as the first responders during recovery. Choosing the right team is crucial — and not always simple.

Vaulting principles span protection, planning, and operations.  
Therefore, effective vault governance **requires collaboration across multiple stakeholders**, not just a single technical group.

### • Business stakeholders  
They — not the backup team — should determine recovery prioritization.  
This is based on their knowledge of:

- system dependencies  
- regulatory obligations  
- business impact  

Clear communication between technical and business teams is essential for an effective cyber recovery strategy.

![Figure 6: People and processes – Balancing both is fundamental for good practices.](images/hinh6.png)

**Figure 6: People and processes – Balancing both is fundamental for good practices.**

As a result of cross-functional collaboration, organizations form detailed recovery plans that must be followed. However, this can inadvertently create recovery scenarios that, while aligned with policy, are not operationally realistic.

Overly complex procedures can:

- slow recovery  
- cause misalignment  
- encourage operators to take shortcuts  

Although these behaviors may not immediately compromise security, **the worst time to discover gaps in your vaulting process is during an actual cyber incident**.

For effective recovery, organizations must embed good practices into daily operations. This requires a balance between:

- robust cyber recovery requirements  
- practical and sustainable operational workflows  

---

## **7. Why Is Executive Sponsorship Necessary?**

Any additional operational burden increases cost, effort, and complexity. Naturally, executives — especially CFOs — question why a solution that does not generate revenue should consume time and budget.

A vault is not part of daily business operations.  
Therefore, its **value and purpose** must be clearly understood and supported at the highest levels of the organization.

This requires:

### ⭐ **Top-down executive sponsorship**

Without leadership support, vault initiatives often stagnate, lack funding, or fail to gain organizational adoption.

![Figure 7: Executive sponsorship – A top-down approach aligns the entire organization.](images/hinh7.png)

**Figure 7: Executive sponsorship – A top-down approach aligns the entire organization.**

---

# **Getting Started with AWS**

AWS provides multiple layers of defense against ransomware.

### ✔ **Storage & Backup**
- **AWS Backup** — centralized management, immutable backups, logical air-gapping  
- **Amazon S3** — versioning + Object Lock  
- **Amazon FSx for NetApp ONTAP** — tamper-proof snapshots  

### ✔ **Threat Detection**
- **Amazon GuardDuty** — suspicious activity detection  
- **AWS Security Hub** — unified security visibility  
- **Amazon Macie** — sensitive data discovery  
- **AWS WAF & AWS Shield** — web attack and DDoS mitigation  
- **AWS Network Firewall** — network-layer protection  

Partner solutions like **Elastio** integrate with AWS Backup to verify data integrity in near real-time, enabling “clean recoveries” with minimal downtime.

### ✔ **Identity Protection & Compliance**
- **AWS IAM** — least privilege access  
- **AWS Organizations** — centralized policy governance  
- **AWS Config & AWS CloudTrail** — configuration auditing + forensic analysis  

---

# **Conclusion**

Cyber incidents — especially ransomware — continue to rise.  
Organizations must shift from defending against random failures to preparing for **intentional, targeted disruptions**.

This requires:

- a clear recovery strategy  
- detailed planning for worst-case scenarios  
- frequent testing and validation  
- coordinated action across the entire organization  

Cyber resilience goes far beyond the IT department.  
It demands commitment from:

- operations  
- finance  
- business leadership  
- engineers  
- front-line staff  

True resilience becomes possible only when it becomes **a shared responsibility across the entire organization**, from the CEO to system administrators.

---

# **About the Authors**

### **Tom Tasker**  
Storage Solution Architect – Global Financial Services, AWS  
Tom works with major global financial organizations, regulators, and partners to design secure, resilient storage architectures on AWS.

### **Danny Johnston**  
Head of Global Financial Services Storage Business Development, AWS  
Danny specializes in enterprise storage strategy and collaborates with customers and regulatory bodies to drive modernization and digital transformation initiatives.

