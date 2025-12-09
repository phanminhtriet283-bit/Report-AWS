---
title: "Week 12 Worklog"
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

---

### Week 12 Objectives:

**Part 1 – Building AI API using Amazon Bedrock**

* Understand Bedrock architecture, pricing, throttling.
* Invoke Claude/Titan models from Lambda via Interface Endpoint.
* Apply prompt engineering for better model performance.
* Create API Gateway endpoint for external AI calls.
* Handle errors such as timeouts and throttling.

**Part 2 – Building automated workflows using Step Functions**

* Design multi-step workflows:  
  Lambda → Bedrock → Data Storage → SES Email.
* Use Task, Choice, Wait, Retry, and Catch states.
* Connect Lambda tasks to create an AI pipeline.
* Log execution history and debug errors.

**Part 3 – Email notifications using Amazon SES**

* Verify email identities.
* Build Lambda function to send emails via SES.
* Integrate SES into Step Functions workflow.
* Handle bounce and complaint notifications.

**Part 4 – Workflow Monitoring**

* Monitor Bedrock and Lambda logs with CloudWatch.
* Review Step Functions execution history.
* Track workflow metric success/failure.
* Optimize Bedrock cost (max tokens, batching, etc.).

---

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | ---------------- | ------------------ |
| 2 | **Bedrock model invocation** <br>• Call Bedrock from Lambda. <br>• Improve prompt. <br>• Debug endpoint issues. | 24/11/2025 | 24/11/2025 | cloudjourney.awsstudygroup.com |
| 3 | **AI API Development** <br>• Create /ai/generate endpoint. <br>• Return model response. <br>• Validate input. | 25/11/2025 | 25/11/2025 | cloudjourney.awsstudygroup.com |
| 4 | **Step Functions Workflow** <br>• Build State Machine. <br>• Lambda → Bedrock → Store Output. <br>• Add error handling. | 26/11/2025 | 26/11/2025 | cloudjourney.awsstudygroup.com |
| 5 | **SES Integration** <br>• Verify sender identity. <br>• Lambda send email. <br>• Add SES to workflow. | 27/11/2025 | 27/11/2025 | cloudjourney.awsstudygroup.com |
| 6 | **Monitoring & Optimization** <br>• Review logs. <br>• Analyze Step Functions map. <br>• Optimize cost. | 28/11/2025 | 28/11/2025 | cloudjourney.awsstudygroup.com |
| 7 | **Cleanup & Final Review** <br>• Remove test resources. <br>• Review billing. <br>• Validate full workflow. | 29/11/2025 | 29/11/2025 | cloudjourney.awsstudygroup.com |

---

### Achievements in Week 12:

#### 1. Successfully built a Bedrock-powered AI API
* Lambda in private subnet calls Bedrock models.
* Stable API responses via API Gateway.
* Effective prompt engineering implemented.

#### 2. Completed AI workflow using Step Functions
* Multi-step automation pipeline works end-to-end.
* Error handling & retries implemented properly.
* Clean execution flow: Input → AI → Save → Notify.

#### 3. SES email notifications integrated
* AI summary sent automatically after workflow.
* Email templates working.
* Improved automation experience.

#### 4. Full monitoring and debugging implemented
* CloudWatch logs for Lambda, Bedrock, API Gateway.
* Detailed Step Functions Execution Map.
* Cost and performance optimization.

---

### Summary of Knowledge Gained:

* Practical usage of Amazon Bedrock for AI inference.
* Building serverless AI APIs using Lambda + API Gateway.
* Workflow orchestration using Step Functions.
* Email automation with Amazon SES.
* Complete understanding of production-level AI agent architecture.

---
