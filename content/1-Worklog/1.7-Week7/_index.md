---
title: "Week 7 Worklog"

weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---

---

### Week 7 Objectives:

**Amazon Route 53 – DNS & Domain Management**

* Understand DNS architecture and Route 53’s role in AWS.
* Create Public Hosted Zones and manage A/AAAA/CNAME records.
* Integrate Route 53 with CloudFront and API Gateway.
* Learn Simple, Weighted, Latency, and Failover routing.

**AWS WAF – Web Application Firewall**

* Understand Layer 7 protection mechanisms.
* Create Web ACL and enable AWS Managed Rules.
* Configure IP blocking and rate limiting.
* Attach WAF to CloudFront to secure API and website traffic.

**Amazon CloudFront – CDN & Edge Security**

* Create CDN distribution for S3 and API Gateway origins.
* Configure cache behaviors, TTL settings, and HTTPS.
* Use Origin Access Control for securing S3 buckets.
* Enable access logs for monitoring.

**AWS CloudWatch – Monitoring & Observability**

* Create CloudWatch Dashboard for Edge Layer.
* Analyze WAF & CloudFront logs using Logs Insights.
* Build alarms for abnormal traffic spikes.
* Understand metrics such as request count, cache hit ratio, blocked requests.

---

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ----- | ---------- | ---------------- | ------------------ |
| 2 | **Route 53 – Domain & DNS Setup** <br>• Create Hosted Zone. <br>• Add A/AAAA alias to CloudFront. <br>• Verify DNS propagation. | 20/10/2025 | 20/10/2025 | cloudjourney.awsstudygroup.com |
| 3 | **CloudFront – Distribution Setup** <br>• Create distribution for S3/API. <br>• Enable HTTPS and OAC. <br>• Configure cache behavior. <br>• Enable access logs. | 21/10/2025 | 21/10/2025 | cloudjourney.awsstudygroup.com |
| 4 | **AWS WAF – Web ACL Configuration** <br>• Create Web ACL. <br>• Enable Managed Rules. <br>• Add IP block & rate limit rules. <br>• Attach to CloudFront. | 22/10/2025 | 22/10/2025 | cloudjourney.awsstudygroup.com |
| 5 | **CloudWatch – Logs & Metrics Analysis** <br>• Create Log Groups. <br>• Query logs via Logs Insights. <br>• Create Metric Filter for blocked requests. <br>• Build alarms. | 23/10/2025 | 23/10/2025 | cloudjourney.awsstudygroup.com |
| 6 | **Security Hardening** <br>• Enforce HTTPS redirection. <br>• Optimize cache TTL. <br>• Analyze attack patterns in logs. <br>• Enable AWS Shield Standard. | 24/10/2025 | 24/10/2025 | cloudjourney.awsstudygroup.com |
| 7 | **Resource Cleanup** <br>• Remove test Web ACL. <br>• Delete unused Log Groups. <br>• Disable Distribution. <br>• Review Billing for WAF/CF logs. | 25/10/2025 | 25/10/2025 | cloudjourney.awsstudygroup.com |

---

### Achievements in Week 7:

#### 1. Strong understanding of Route 53 DNS architecture

* Configured public DNS and domain routing successfully.
* Understood traffic flow: DNS → CloudFront → API.

#### 2. Successfully deployed CloudFront CDN

* Improved global latency.
* Configured cache behavior and encryption.
* Protected S3 using OAC.

#### 3. Built a secure Layer 7 protection system using AWS WAF

* Blocked malicious traffic (SQLi, XSS, bots).
* Implemented rate limiting.
* Analyzed WAF logs for threat detection.

#### 4. Built observability with CloudWatch

* Created Edge Monitoring Dashboard.
* Queried logs using Logs Insights.
* Set alarms for suspicious activity.

---

### Summary of Knowledge Gained:

* Understanding of AWS Edge Services (Route 53, CloudFront, WAF).
* Ability to secure and accelerate applications using CDN.
* Hands-on experience in threat detection & log analysis.
* Ability to build a front-door security system following AWS best practices.

---
