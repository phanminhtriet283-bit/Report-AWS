---
title: "Worklog Tuần 9"
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---

---

### Mục tiêu tuần 9:

**AWS Lambda – Serverless Compute**

* Hiểu kiến trúc và vòng đời thực thi của Lambda.
* Tạo các Lambda function phục vụ backend.
* Tích hợp Lambda với API Gateway bằng Lambda Proxy Integration.
* Cấu hình IAM Role cho Lambda để truy cập RDS, S3 và Bedrock.
* Sử dụng Secrets Manager để quản lý thông tin kết nối cơ sở dữ liệu.
* Giám sát Lambda bằng CloudWatch Logs & Metrics.

**Lambda trong VPC & VPC Endpoint**

* Đưa Lambda vào private subnet để kết nối tài nguyên nội bộ.
* Cấu hình Security Group cho Lambda ↔ RDS.
* Tạo VPC Endpoints:
  * S3 Gateway Endpoint để truy cập S3 không cần NAT.
  * Bedrock Interface Endpoint để gọi AI model từ private subnet.
* Kiểm thử Lambda truy cập RDS và Bedrock.

**Tối ưu & Kiểm soát chi phí**

* Hiểu Cold Start & áp dụng chiến lược giảm độ trễ.
* Tối ưu Memory / Timeout của Lambda.
* Giảm chi phí NAT Gateway bằng cách chuyển sang VPC Endpoints.
* Áp dụng Connection Pooling cho RDS.

---

### Các công việc trong tuần:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | -------- | ------------ | ---------------- | -------------- |
| 2 | **Lambda – Tổng quan & tạo function** <br>• Tìm hiểu vòng đời Lambda. <br>• Tạo function (Node.js/Python). <br>• Cấu hình IAM Role. <br>• Test trên Lambda Console. | 03/11/2025 | 03/11/2025 | cloudjourney.awsstudygroup.com |
| 3 | **Tích hợp Lambda với API Gateway** <br>• Tạo REST API. <br>• Gắn Lambda vào các routes. <br>• Bật CORS. <br>• Test qua Postman. | 04/11/2025 | 04/11/2025 | cloudjourney.awsstudygroup.com |
| 4 | **Đưa Lambda vào VPC (Private Subnet)** <br>• Chọn subnet & security group. <br>• Test kết nối RDS. <br>• Fix lỗi timeout/networking. | 05/11/2025 | 05/11/2025 | cloudjourney.awsstudygroup.com |
| 5 | **Tạo VPC Endpoints** <br>• Tạo S3 Gateway Endpoint. <br>• Tạo Bedrock Interface Endpoint. <br>• Test gọi Bedrock từ Lambda. | 06/11/2025 | 06/11/2025 | cloudjourney.awsstudygroup.com |
| 6 | **Tích hợp Secrets Manager** <br>• Tạo Secret cho RDS. <br>• Truy xuất bằng AWS SDK. <br>• Cấu hình IAM Resource Policy. | 07/11/2025 | 07/11/2025 | cloudjourney.awsstudygroup.com |
| 7 | **Tối ưu hiệu năng & chi phí** <br>• Điều chỉnh memory/timeouts. <br>• Connection pooling. <br>• So sánh chi phí NAT Gateway vs VPC Endpoint. | 08/11/2025 | 08/11/2025 | cloudjourney.awsstudygroup.com |

---

### Kết quả đạt được tuần 9:

#### 1. Xây dựng backend serverless bằng AWS Lambda

* Tạo nhiều hàm Lambda hỗ trợ API Gateway.
* Hiểu rõ cold start và cách tối ưu.
* Quản lý quyền truy cập tài nguyên bằng IAM Role.

#### 2. Lambda chạy trong VPC kết nối được với RDS

* Thiết lập thành công Lambda trong private subnet.
* Fix lỗi SG, route table, NACL gây timeout.
* Kết nối query RDS ổn định.

#### 3. Tạo VPC Endpoints phục vụ truy cập nội bộ

* S3 Gateway Endpoint giúp truy cập S3 mà không cần Internet.
* Bedrock Endpoint cho phép gọi AI model từ private subnet.
* Giảm chi phí vận hành NAT Gateway.

#### 4. Bảo mật thông tin DB bằng Secrets Manager

* Không lưu password trong code.
* Tất cả function Lambda truy xuất secret an toàn qua SDK.

#### 5. Tối ưu hiệu năng & chi phí

* Giảm cold start nhờ tối ưu cấu hình.
* Giảm tải RDS bằng connection pooling.
* Hiểu rõ cách tối ưu chi phí cho Lambda & networking.

---

### Tóm tắt kiến thức đạt được:

* Kiến trúc Lambda & mô hình serverless.
* Networking trong VPC và truy cập tài nguyên private.
* VPC Endpoint (S3 & Bedrock) – Khi nào nên dùng.
* Secrets Manager – Best practices cho bảo mật.
* Tối ưu hiệu năng, chi phí và hạn chế cold start.

---
