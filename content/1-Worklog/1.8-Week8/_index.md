---
title: "Week 8 Worklog"

weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---

---

### Week 8 Objectives:

**Amazon API Gateway – API Layer**

* Understand REST API architecture and components.
* Build REST API with multiple resources and methods.
* Configure Integration Requests/Responses with Lambda.
* Enable CORS following best practices.
* Configure Custom Domain Name with ACM SSL.
* Enable execution logging and access logging.
* Test API using Postman and frontend clients.

**Amazon Cognito – Authentication & Authorization**

* Learn Cognito User Pool vs Identity Pool.
* Create User Pool, App Client, and Hosted UI domain.
* Configure password policy and email verification.
* Create Identity Pool for AWS credentials.
* Integrate Cognito with API Gateway using JWT Authorizer.
* Test end-to-end login → token → protected API.

---

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | ---------------- | ------------------ |
| 2 | **API Gateway – Architecture & REST API Setup** <br>• Study REST API. <br>• Create resources `/auth`, `/users`, `/items`. <br>• Configure CRUD methods. | 27/10/2025 | 27/10/2025 | cloudjourney.awsstudygroup.com |
| 3 | **Lambda Integration** <br>• Create Lambda handlers. <br>• Configure IAM roles. <br>• Enable Proxy Integration. <br>• Test API with Postman. | 28/10/2025 | 28/10/2025 | cloudjourney.awsstudygroup.com |
| 4 | **Cognito User Pool & Identity Pool Setup** <br>• Create User Pool. <br>• Configure password/email policies. <br>• Create App Client & Hosted UI. <br>• Test signup/login. | 29/10/2025 | 29/10/2025 | cloudjourney.awsstudygroup.com |
| 5 | **JWT Authorization with Cognito** <br>• Create JWT Authorizer. <br>• Attach to `/users/*` route. <br>• Test Access & ID Tokens. <br>• Configure 401/403 responses. | 30/10/2025 | 30/10/2025 | cloudjourney.awsstudygroup.com |
| 6 | **Custom Domain + Logging Setup** <br>• Create custom API domain with ACM SSL. <br>• Map domain to API stage. <br>• Enable execution & access logs. <br>• Analyze logs in CloudWatch Insights. | 31/10/2025 | 31/10/2025 | cloudjourney.awsstudygroup.com |
| 7 | **End-to-End Testing & Cleanup** <br>• Test full login-to-API flow. <br>• Remove unused Lambda/API test resources. <br>• Delete test users. <br>• Review Billing. | 01/11/2025 | 01/11/2025 | cloudjourney.awsstudygroup.com |

---

### Achievements in Week 8:

#### 1. Built a complete REST API backend with API Gateway

* Configured multiple routes and methods.
* Implemented CORS and Lambda Proxy Integration.
* Successfully tested using Postman.

#### 2. Implemented full authentication system using Cognito

* Created User Pool and Identity Pool.
* Enabled secure signup & login flows.
* Understood JWT token structure and validation.

#### 3. Secured API using JWT Authorizer

* Protected sensitive routes (`/users/*`).
* Tested access with valid, expired, and invalid tokens.

#### 4. Set up monitoring and logging for API Gateway

* Enabled CloudWatch Logs for debugging.
* Queried logs using Logs Insights.
* Investigated 4XX/5XX errors.

---

### Summary of Knowledge Gained:

* Strong understanding of API Gateway operation.
* Deep knowledge of Cognito authentication flows.
* Ability to secure APIs using JWT-based authorization.
* Experience integrating API Gateway + Lambda + Cognito.
* Familiarity with CloudWatch monitoring and API logging.

---
