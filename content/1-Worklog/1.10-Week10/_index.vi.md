---
title: "Worklog Tuần 10"
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

---

### Mục tiêu tuần 10:

**Amazon RDS – Quản trị & Tối ưu hóa**

* Ôn lại kiến trúc RDS: Multi-AZ, Read Replica, Backup, Monitoring.
* Quản lý Parameter Group và Option Group.
* Tối ưu hóa kết nối RDS cho Lambda.
* Sử dụng Query Plan & Performance Insights để phân tích hiệu năng.
* Sao lưu – phục hồi – tạo snapshot thủ công và tự động.

**Amazon S3 – Lưu trữ & tích hợp backend**

* Hiểu cơ chế bucket, folder, object.
* Cấu hình bucket policy & IAM policy cho Lambda.
* Tải file, xử lý file từ Lambda.
* Quản lý Lifecycle rule để tối ưu phí.

**VPC Interface Endpoint cho Amazon Bedrock**

* Tạo Interface Endpoint để truy cập Bedrock trong private subnet.
* Cấu hình bảo mật (SG, route table).
* Gọi Bedrock model (Claude, Titan...) từ Lambda.

**Lambda Integration – Xây dựng API xử lý dữ liệu**

* Lambda truy vấn dữ liệu từ RDS.
* Lambda lưu hoặc đọc dữ liệu từ S3.
* Lambda gọi Bedrock để xử lý AI logic.
* Theo dõi hoạt động bằng CloudWatch Logs & Metrics.

---

### Các công việc thực hiện trong tuần:

| Thứ | Công việc | Bắt đầu | Hoàn thành | Nguồn tài liệu |
| --- | -------- | -------- | ---------- | -------------- |
| 2 | **RDS Advanced Operations** <br>• Xem lại Parameter Group & Option Group. <br>• Theo dõi Performance Insights. <br>• Tạo snapshot & restore test. | 10/11/2025 | 10/11/2025 | cloudjourney.awsstudygroup.com |
| 3 | **Lambda → RDS Integration** <br>• Tạo IAM Role cho Lambda. <br>• Kết nối RDS qua private subnet. <br>• Tối ưu connection pooling. <br>• Debug lỗi timeout/conn limit. | 11/11/2025 | 11/11/2025 | cloudjourney.awsstudygroup.com |
| 4 | **S3 Integration** <br>• Tạo bucket backend. <br>• Tạo Bucket Policy an toàn. <br>• Lambda tải lên/đọc file từ S3. <br>• Thử nghiệm Lifecycle để tiết kiệm phí. | 12/11/2025 | 12/11/2025 | cloudjourney.awsstudygroup.com |
| 5 | **Tạo Bedrock Interface Endpoint** <br>• Tạo Interface Endpoint trong private subnet. <br>• Gán SG cho phép HTTPS. <br>• Test gọi Bedrock model từ Lambda. | 13/11/2025 | 13/11/2025 | cloudjourney.awsstudygroup.com |
| 6 | **API Lambda sử dụng RDS + S3 + Bedrock** <br>• Xây API lambda xử lý dữ liệu từ DB. <br>• Lưu output vào S3. <br>• Gọi Bedrock để tạo nội dung AI. <br>• Giám sát qua CloudWatch. | 14/11/2025 | 14/11/2025 | cloudjourney.awsstudygroup.com |
| 7 | **Dọn dẹp tài nguyên & tối ưu chi phí** <br>• Xóa snapshot & test DB. <br>• Dọn bucket rác. <br>• Kiểm tra chi phí Endpoint, RDS, S3. | 15/11/2025 | 15/11/2025 | cloudjourney.awsstudygroup.com |

---

### Kết quả đạt được tuần 10:

#### 1. Làm chủ RDS nâng cao

* Hiểu rõ vai trò Parameter Group và Option Group.
* Phân tích hiệu suất RDS qua Performance Insights.
* Tối ưu số lượng kết nối từ Lambda vào Database.
* Thực hiện backup/restore thành thạo.

#### 2. Tích hợp S3 với backend

* Tạo bucket an toàn theo chuẩn IAM.
* Upload/download file thành công từ Lambda.
* Quản lý vòng đời dữ liệu bằng Lifecycle Rule.

#### 3. Tạo và sử dụng Bedrock Interface Endpoint

* Kết nối thành công từ Lambda trong private subnet.
* Thực hiện gọi mô hình AI (Claude/Titan).
* Hiểu quy trình inference trong môi trường private networking.

#### 4. Xây dựng API backend AI-driven

* Lambda truy vấn DB + S3 + Bedrock.
* Tạo workflow xử lý dữ liệu + phân tích AI.
* Theo dõi log và phòng lỗi bằng CloudWatch.

---

### Tóm tắt kiến thức đạt được:

* RDS nâng cao: hiệu năng, bảo trì, backup.
* Kết nối Lambda ↔ RDS an toàn trong private subnet.
* Tích hợp S3 lưu trữ backend.
* Sử dụng Bedrock Endpoint để chạy AI private.
* Xây dựng API serverless hoàn chỉnh với nhiều dịch vụ AWS.

---
