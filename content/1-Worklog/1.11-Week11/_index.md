---
title: "Week 11 Worklog"
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

---

### Week 11 Objectives:

**Part 1 – Front-end Serverless Deployment (S3 + CloudFront)**

* Understand static website hosting architecture on AWS.
* Create an S3 bucket to store the frontend build.
* Configure CloudFront as a global CDN.
* Enable HTTPS using ACM certificates.
* Implement Origin Access Control (OAC) for secure S3 access.
* Block all public access and apply secure bucket policies.

**Part 2 – Integrating Cognito Authentication into the Frontend**

* Reuse User Pool & App Client configured in Week 8.
* Build login/signup UI or use Hosted UI.
* Retrieve ID/Access Tokens after authentication.
* Store tokens securely (localStorage/sessionStorage).
* Implement logout and token expiration handling.

**Part 3 – Calling API Gateway from the Frontend**

* Send Authorization header: `Bearer <JWT>`.
* Test protected API routes using Cognito Authorizer.
* Handle 401 (Unauthorized) and 403 (Forbidden).
* Render API responses on the UI.

**Part 4 – Monitoring & Debugging**

* Enable and review CloudFront Access Logs.
* Check API Gateway logs via CloudWatch.
* Debug Lambda flow end-to-end.
* Clean up unused resources to reduce costs.

---

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | ---------------- | ------------------ |
| 2 | **Deploy Frontend to S3** <br>• Create bucket. <br>• Upload build files. <br>• Configure index/error pages. | 17/11/2025 | 17/11/2025 | cloudjourney.awsstudygroup.com |
| 3 | **Create CloudFront Distribution** <br>• Add S3 origin. <br>• Configure HTTPS with ACM. <br>• Enable OAC + update bucket policy. | 18/11/2025 | 18/11/2025 | cloudjourney.awsstudygroup.com |
| 4 | **Integrate Cognito into Frontend** <br>• Retrieve JWT tokens from Week 8 User Pool. <br>• Store tokens securely. <br>• Build login/logout UI. | 19/11/2025 | 19/11/2025 | cloudjourney.awsstudygroup.com |
| 5 | **Frontend → API Gateway Integration** <br>• Send Authorization header. <br>• Test protected endpoints. <br>• Handle 401/403. | 20/11/2025 | 20/11/2025 | cloudjourney.awsstudygroup.com |
| 6 | **Monitoring & Debugging** <br>• Review CloudFront logs. <br>• Debug API Gateway. <br>• Check Lambda logs. | 21/11/2025 | 21/11/2025 | cloudjourney.awsstudygroup.com |
| 7 | **Cleanup Resources** <br>• Delete test CloudFront. <br>• Delete test S3 bucket. <br>• Review Billing. | 22/11/2025 | 22/11/2025 | cloudjourney.awsstudygroup.com |

---

### Achievements in Week 11:

#### 1. Fully deployed serverless frontend
* Frontend hosted on S3 + distributed globally via CloudFront.
* HTTPS enabled and S3 protected using OAC.
* Fast and secure static web delivery.

#### 2. Cognito Authentication integrated successfully
* Reused Week 8 User Pool.
* JWT retrieval and storage working correctly.
* Login/logout features implemented with token handling.

#### 3. Secure API Gateway calls from the frontend
* JWT-based Authorization header validated by API Gateway.
* Smooth flow from Frontend → API → Lambda backend.
* Clear error handling for authentication failures.

#### 4. Effective debugging and monitoring
* CloudFront logs used to trace user requests.
* API Gateway + Lambda logs analyzed through CloudWatch.
* Reduced cost by cleaning unused test resources.

---

### Summary of Knowledge Gained:

* Hosting serverless frontend via S3 + CloudFront.
* Practical Cognito Authentication integration without Amplify.
* Making secure API calls with JWT tokens.
* Debugging across CloudFront, API Gateway, and Lambda.
* Understanding full serverless stack behavior on AWS.

---
