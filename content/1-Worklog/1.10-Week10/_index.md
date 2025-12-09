---
title: "Week 10 Worklog"

weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

---

### Week 10 Objectives:

**Amazon RDS – Advanced Operations**

* Review RDS architecture: Multi-AZ, Read Replica, backup lifecycle.
* Understand Parameter Groups and Option Groups.
* Optimize Lambda → RDS connections.
* Analyze database performance with Performance Insights.
* Perform backup, restore, manual snapshot management.

**Amazon S3 – Backend Storage Integration**

* Understand buckets, objects, permissions.
* Configure secure Bucket Policies & IAM roles.
* Upload/download files via Lambda.
* Implement Lifecycle rules for cost optimization.

**Amazon Bedrock – VPC Interface Endpoint**

* Create Interface Endpoint inside private subnets.
* Configure SG and routing for private access.
* Invoke Bedrock models (Claude, Titan…) from Lambda.

**Lambda Integration – Full Backend Workflow**

* Lambda performs database queries on RDS.
* Lambda stores and reads data from S3.
* Lambda invokes Bedrock for AI processing.
* Monitor execution using CloudWatch.

---

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | ---------------- | ------------------ |
| 2 | **RDS Advanced Operations** <br>• Review Parameter/Option Groups. <br>• Analyze Performance Insights. <br>• Create snapshots & restore. | 10/11/2025 | 10/11/2025 | cloudjourney.awsstudygroup.com |
| 3 | **Lambda → RDS Integration** <br>• Configure IAM Role. <br>• Connect Lambda to RDS in private subnet. <br>• Implement connection pooling. <br>• Debug timeout issues. | 11/11/2025 | 11/11/2025 | cloudjourney.awsstudygroup.com |
| 4 | **S3 Integration** <br>• Create bucket. <br>• Configure policies. <br>• Upload/download from Lambda. <br>• Apply Lifecycle rules. | 12/11/2025 | 12/11/2025 | cloudjourney.awsstudygroup.com |
| 5 | **Create Bedrock Interface Endpoint** <br>• Deploy endpoint in private subnet. <br>• Configure security groups. <br>• Test Bedrock inference from Lambda. | 13/11/2025 | 13/11/2025 | cloudjourney.awsstudygroup.com |
| 6 | **AI-Driven Lambda API** <br>• Query RDS. <br>• Store output in S3. <br>• Invoke Bedrock model. <br>• Monitor logs in CloudWatch. | 14/11/2025 | 14/11/2025 | cloudjourney.awsstudygroup.com |
| 7 | **Cleanup & Cost Optimization** <br>• Delete snapshots and test DB. <br>• Clean S3 bucket. <br>• Review Endpoint/RDS/S3 costs. | 15/11/2025 | 15/11/2025 | cloudjourney.awsstudygroup.com |

---

### Achievements in Week 10:

#### 1. Mastered advanced RDS operations

* Understood Parameter Groups and Option Groups.
* Applied performance troubleshooting via Performance Insights.
* Managed backup, restore, and snapshots efficiently.

#### 2. Successfully integrated S3 with backend workflows

* Secure bucket configuration using IAM best practices.
* Lambda can upload, read, and manage data objects.
* Lifecycle rules deployed to reduce storage cost.

#### 3. Built a secure Bedrock Endpoint for private AI inference

* Lambda can call Bedrock models inside VPC without Internet.
* Understood use cases for private model inference.

#### 4. Developed AI-enhanced backend API

* Combined RDS + S3 + Bedrock in a single Lambda workflow.
* Processed structured + unstructured data.
* Built CloudWatch monitoring for debugging and optimization.

---

### Summary of Knowledge Gained:

* Strong knowledge of advanced RDS features and optimization.
* Hands-on skills integrating Lambda with RDS and S3.
* Experience deploying Bedrock Endpoint for private AI workloads.
* Ability to build multi-service backend workflows using AWS.
* Understanding of cost optimization across RDS, S3, Lambda, and VPC networking.

---
