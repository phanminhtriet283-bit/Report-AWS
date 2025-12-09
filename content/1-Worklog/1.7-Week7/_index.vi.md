---
title: "Worklog Tuần 7"
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---

---

### Mục tiêu tuần 7:

**Route 53 – Quản lý Domain & DNS**

* Hiểu kiến trúc DNS và vai trò của Route 53 trong hệ thống AWS.
* Tạo Public Hosted Zone và quản lý các bản ghi A/AAAA/CNAME.
* Tích hợp domain với CloudFront và API Gateway.
* Hiểu các Routing Policy: Simple, Latency, Failover, Weighted.

**AWS WAF – Web Application Firewall**

* Hiểu cách WAF bảo vệ ứng dụng khỏi SQLi, XSS và bot attack.
* Tạo Web ACL, bật Managed Rule Groups.
* Cấu hình IP block list & rate limiting.
* Gắn WAF vào CloudFront để bảo vệ API/website.

**Amazon CloudFront – CDN & Edge Security**

* Tạo CloudFront Distribution cho S3 và API.
* Cấu hình Cache Behaviors & TTL.
* Bật HTTPS, Origin Access Control (OAC).
* Theo dõi truy cập và phân tích log.

**AWS CloudWatch – Logging & Monitoring**

* Tạo Dashboard giám sát Traffic Edge.
* Phân tích log CloudFront & WAF bằng Logs Insights.
* Tạo Alarm khi phát hiện request bất thường.

---

### Các công việc thực hiện trong tuần:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | ---------- | ------------ | ---------------- | -------------- |
| 2 | **Route 53 – Domain & DNS Setup** <br>• Tạo Hosted Zone. <br>• Tạo bản ghi A/AAAA alias về CloudFront. <br>• Kiểm tra DNS propagation bằng `dig/nslookup`. | 20/10/2025 | 20/10/2025 | cloudjourney.awsstudygroup.com |
| 3 | **CloudFront – CDN Distribution Setup** <br>• Tạo Distribution cho website/API. <br>• Bật OAC để bảo mật S3. <br>• Cấu hình Cache Behavior. <br>• Bật Access Logs. | 21/10/2025 | 21/10/2025 | cloudjourney.awsstudygroup.com |
| 4 | **AWS WAF – Web ACL Configuration** <br>• Tạo Web ACL. <br>• Bật Managed Rules (SQLi, XSS, Bot Control). <br>• Block IP/geo thử nghiệm. <br>• Gắn WAF vào CloudFront. | 22/10/2025 | 22/10/2025 | cloudjourney.awsstudygroup.com |
| 5 | **CloudWatch – Log & Metrics Analysis** <br>• Tạo Log Group cho CloudFront/WAF. <br>• Query bằng Logs Insights. <br>• Tạo Metric Filter cho request bị chặn. <br>• Tạo Alarm khi traffic tăng đột biến. | 23/10/2025 | 23/10/2025 | cloudjourney.awsstudygroup.com |
| 6 | **Security Hardening** <br>• Bật HTTPS redirect. <br>• Tối ưu TTL của CloudFront. <br>• Phân tích Access Logs tìm tấn công bot. <br>• Bật AWS Shield Standard (free). | 24/10/2025 | 24/10/2025 | cloudjourney.awsstudygroup.com |
| 7 | **Dọn dẹp tài nguyên** <br>• Xóa Web ACL test. <br>• Xóa Log Group không dùng. <br>• Xóa Distribution test. <br>• Kiểm tra Billing phần Edge Services. | 25/10/2025 | 25/10/2025 | cloudjourney.awsstudygroup.com |

---

### Kết quả đạt được tuần 7:

#### 1. Làm chủ Route 53 và kiến trúc DNS

* Tạo và cấu hình domain trỏ về CloudFront.
* Hiểu luồng phân giải DNS → CloudFront → API.
* Nắm routing policies phục vụ high availability.

#### 2. Triển khai CloudFront làm CDN toàn cầu

* Tối ưu tốc độ truy cập bằng edge caching.
* Bảo vệ S3 bằng Origin Access Control.
* Giảm latency đáng kể khi truy cập website/API.

#### 3. Triển khai AWS WAF bảo vệ Layer 7

* Ngăn chặn SQLi, XSS, Bad Bot.
* Tạo rule block IP và rate limit.
* Giám sát log WAF và phân tích threat patterns.

#### 4. Xây dựng hệ thống giám sát với CloudWatch

* Tạo Dashboard theo dõi Traffic Edge Layer.
* Sử dụng Logs Insights tìm request bất thường.
* Tạo Alarm cảnh báo tấn công layer 7.

---

### Tóm tắt kiến thức đạt được:

* Kiến trúc DNS & Edge Security thực tế với Route 53 + CloudFront + WAF.
* Cấu hình CDN hiệu quả với Cache Behavior & TTL Strategy.
* Phân tích log tấn công, truy cập bất thường bằng CloudWatch.
* Xây dựng lớp bảo mật đầu vào (front-door security) theo chuẩn AWS Well-Architected Framework.

---
