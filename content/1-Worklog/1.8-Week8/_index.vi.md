---
title: "Worklog Tuần 8"
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---

---

### Mục tiêu tuần 8:

**Amazon API Gateway – Xây dựng tầng API**

* Hiểu kiến trúc API Gateway: REST API, HTTP API, WebSocket API.
* Tạo REST API phục vụ backend Lambda.
* Cấu hình Resource, Method, Integration Request/Response.
* Bật CORS theo chuẩn.
* Tạo Custom Domain Name cho API.
* Thu thập log API qua CloudWatch Logs.
* Test API bằng Postman và công cụ frontend.

**Amazon Cognito – Authentication & Authorization**

* Hiểu kiến trúc User Pool và Identity Pool.
* Tạo User Pool, cấu hình password policy & email verification.
* Tạo App Client và domain Cognito Hosted UI.
* Tạo Identity Pool để cấp AWS Credentials.
* Tích hợp Cognito với API Gateway bằng JWT Authorizer.
* Test quy trình Login → Token → Gọi API bảo vệ.

---

### Các công việc thực hiện trong tuần:

| Thứ | Công việc | Bắt đầu | Hoàn thành | Nguồn tài liệu |
| --- | -------- | -------- | ---------- | -------------- |
| 2 | **API Gateway – Kiến trúc & tạo REST API** <br>• Nghiên cứu REST/HTTP API. <br>• Tạo API, resource `/auth`, `/users`, `/items`. <br>• Cấu hình GET/POST/PUT/DELETE. | 27/10/2025 | 27/10/2025 | cloudjourney.awsstudygroup.com |
| 3 | **Tích hợp API Gateway ↔ Lambda** <br>• Tạo Lambda handlers. <br>• Gán IAM Role cho Lambda. <br>• Tạo Integration Proxy. <br>• Kích hoạt CORS. <br>• Test API bằng Postman. | 28/10/2025 | 28/10/2025 | cloudjourney.awsstudygroup.com |
| 4 | **Cognito – Tạo User Pool & Identity Pool** <br>• Tạo User Pool và App Client. <br>• Cấu hình password policy & verification. <br>• Tạo Identity Pool để lấy AWS credentials. <br>• Test đăng ký & đăng nhập. | 29/10/2025 | 29/10/2025 | cloudjourney.awsstudygroup.com |
| 5 | **JWT Authorization – Bảo vệ API bằng Cognito** <br>• Tạo JWT Authorizer trong API Gateway. <br>• Gắn authorizer vào `/users/*`. <br>• Test Access Token & ID Token. <br>• Cấu hình lỗi 401/403. | 30/10/2025 | 30/10/2025 | cloudjourney.awsstudygroup.com |
| 6 | **Custom Domain Name + Logging** <br>• Tạo domain API bằng ACM Certificate. <br>• Map domain với API Gateway stage. <br>• Bật Access Logging & Execution Logging. <br>• Query log bằng CloudWatch Insights. | 31/10/2025 | 31/10/2025 | cloudjourney.awsstudygroup.com |
| 7 | **Kiểm thử end-to-end & dọn tài nguyên** <br>• Flow: Register → Login → Token → Call Protected API. <br>• Xóa API/Lambda test. <br>• Xóa users test. <br>• Kiểm tra Billing. | 1/11/2025 | 1/11/2025 | cloudjourney.awsstudygroup.com |

---

### Kết quả đạt được tuần 8:

#### 1. Xây dựng hệ thống API backend sử dụng API Gateway

* Tạo REST API đầy đủ resource & method.
* Thực hiện CORS đúng chuẩn cho frontend.
* Tích hợp API Gateway ↔ Lambda theo mô hình serverless.

#### 2. Hoàn thiện hệ thống xác thực bằng Amazon Cognito

* Tạo User Pool & Identity Pool.
* Test đầy đủ signup / login / token flow.
* Nắm rõ JWT token structure và authorization.

#### 3. Triển khai bảo vệ API bằng JWT Authorizer

* Chỉ người dùng đã đăng nhập mới truy cập được `/users/*`.
* Test phân quyền thành công với token hợp lệ/hết hạn/sai.

#### 4. Logging & Monitoring bằng CloudWatch

* Theo dõi request/response của API Gateway.
* Phân tích lỗi 4XX/5XX.
* Query log để phát hiện request bất thường.

---

### Tóm tắt kiến thức đạt được:

* Kiến trúc API Gateway trong AWS.
* Mô hình Authentication/Authorization bằng Cognito.
* Cách bảo vệ API bằng JWT Authorizer.
* Luồng đăng nhập người dùng & quản lý token.
* Giám sát API bằng CloudWatch.

---
