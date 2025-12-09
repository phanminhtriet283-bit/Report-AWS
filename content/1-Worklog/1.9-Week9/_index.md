---
title: "Week 9 Worklog"

weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---

---

### Week 9 Objectives:

**AWS Lambda – Serverless Compute**

* Understand Lambda execution lifecycle (init, invoke, freeze).
* Build backend Lambda functions.
* Integrate Lambda with API Gateway using Lambda Proxy.
* Configure IAM roles for RDS, S3, and Bedrock access.
* Use AWS Secrets Manager for secure credential storage.
* Monitor Lambda via CloudWatch Logs and Metrics.

**Lambda in VPC & VPC Endpoints**

* Deploy Lambda inside private subnets for secure backend operations.
* Configure Security Groups for Lambda → RDS communication.
* Create VPC Endpoints:
  * **S3 Gateway Endpoint** for internal S3 access  
  * **Bedrock Interface Endpoint** for private AI API calls  
* Test Lambda connectivity to both RDS and Bedrock.

**Performance & Cost Optimization**

* Learn cold start behaviors and mitigation strategies.
* Tune memory & timeout settings for best performance.
* Reduce NAT Gateway traffic using VPC Endpoints.
* Apply database connection pooling to reduce overhead.

---

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | ---------------- | ------------------ |
| 2 | **Lambda – Overview & Function Creation** <br>• Study lifecycle. <br>• Create first function. <br>• Configure IAM execution role. <br>• Run test. | 03/11/2025 | 03/11/2025 | cloudjourney.awsstudygroup.com |
| 3 | **Lambda Integration with API Gateway** <br>• Attach Lambda to REST API. <br>• Enable Proxy Integration. <br>• Enable CORS. <br>• Test with Postman. | 04/11/2025 | 04/11/2025 | cloudjourney.awsstudygroup.com |
| 4 | **Lambda in VPC – Private Deployment** <br>• Attach Lambda to private subnets. <br>• Configure SG rules. <br>• Fix timeout issues. <br>• Validate DB queries. | 05/11/2025 | 05/11/2025 | cloudjourney.awsstudygroup.com |
| 5 | **VPC Endpoints Setup** <br>• Create S3 Gateway Endpoint. <br>• Create Bedrock Interface Endpoint. <br>• Test inference from Lambda. | 06/11/2025 | 06/11/2025 | cloudjourney.awsstudygroup.com |
| 6 | **Secrets Manager Integration** <br>• Store DB credentials. <br>• Retrieve via SDK. <br>• Apply IAM policies. <br>• Test secure DB connection. | 07/11/2025 | 07/11/2025 | cloudjourney.awsstudygroup.com |
| 7 | **Performance & Cost Optimization** <br>• Tune memory/timeouts. <br>• Implement pooling. <br>• Analyze NAT vs Endpoint cost. <br>• Review Billing. | 08/11/2025 | 08/11/2025 | cloudjourney.awsstudygroup.com |

---

### Achievements in Week 9:

#### 1. Built a functional serverless backend with AWS Lambda

* Multiple Lambda functions handling API operations.
* Understood cold starts and how to optimize them.
* IAM roles configured securely for resource access.

#### 2. Lambda successfully deployed inside VPC

* Stable connection to RDS from private subnets.
* Resolved networking issues (SG, routing, NACL).
* Verified smooth query execution.

#### 3. Implemented VPC Endpoints for secure & cost-efficient networking

* S3 Gateway Endpoint removed NAT dependency.
* Bedrock Endpoint enabled secure AI inference.
* Overall networking cost reduced significantly.

#### 4. Improved security with Secrets Manager

* No credentials stored in environment variables.
* Lambda fetches secrets securely using AWS SDK.

#### 5. Performance & cost improvements

* Better performance through memory tuning.
* Reduced DB overload via connection pooling.
* Lower NAT Gateway costs using VPC Endpoint.

---

### Summary of Knowledge Gained:

* Deep understanding of Lambda serverless architecture.
* Working knowledge of VPC networking for private workloads.
* Practical usage of VPC Endpoints (S3, Bedrock).
* Strong experience using Secrets Manager securely.
* Ability to optimize Lambda performance & cost for production systems.

---
