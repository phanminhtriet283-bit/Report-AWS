---
title: "Worklog Tuần 11"
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

---

### Mục tiêu tuần 11:

**Phần 1 – Triển khai Front-end Serverless (S3 + CloudFront)**

* Hiểu kiến trúc hosting website tĩnh trên AWS.
* Tạo S3 bucket để lưu trữ file build frontend.
* Cấu hình CloudFront làm CDN phân phối nội dung toàn cầu.
* Bật HTTPS thông qua ACM Certificate.
* Cấu hình Origin Access Control (OAC) để CloudFront truy cập S3 an toàn.
* Chặn public access và áp dụng bucket policy chuẩn bảo mật.

**Phần 2 – Tích hợp Cognito Authentication vào Frontend**

* Sử dụng User Pool & App Client được tạo từ Tuần 8.
* Tạo UI đăng nhập/đăng ký hoặc dùng Hosted UI.
* Lấy JWT token (Access/ID Token) sau đăng nhập.
* Lưu token vào localStorage/sessionStorage.
* Tạo logic logout, token checking & expiration.

**Phần 3 – Frontend gọi API Gateway bằng JWT**

* Gửi Authorization header dạng: `Bearer <JWT>`.
* Test các API private yêu cầu Cognito Authorizer.
* Xử lý lỗi 401 (Unauthorized), 403 (Forbidden).
* Hiển thị dữ liệu trả về từ Backend trên UI.

**Phần 4 – Monitoring & Debug**

* Bật CloudFront Access Logs.
* Kiểm tra API Gateway logs qua CloudWatch.
* Debug lỗi Lambda và xem end-to-end flow.
* Dọn dẹp resource test giảm chi phí.

---

### Các công việc trong tuần:

| Thứ | Công việc | Bắt đầu | Hoàn thành | Nguồn tài liệu |
| --- | -------- | -------- | ---------- | -------------- |
| 2 | **Hosting Frontend lên S3** <br>• Tạo bucket. <br>• Upload file build. <br>• Cấu hình index/error. | 17/11/2025 | 17/11/2025 | cloudjourney.awsstudygroup.com |
| 3 | **Tạo CloudFront Distribution** <br>• Trỏ origin về S3. <br>• Thêm HTTPS (ACM). <br>• Bật OAC & update bucket policy. | 18/11/2025 | 18/11/2025 | cloudjourney.awsstudygroup.com |
| 4 | **Tích hợp Cognito vào Frontend** <br>• Lấy token từ User Pool (tuần 8). <br>• Lưu token vào trình duyệt. <br>• Tạo UI login/logout. | 19/11/2025 | 19/11/2025 | cloudjourney.awsstudygroup.com |
| 5 | **Frontend gọi API Gateway bằng JWT** <br>• Gửi Authorization header. <br>• Test API private. <br>• Xử lý lỗi 401/403. | 20/11/2025 | 20/11/2025 | cloudjourney.awsstudygroup.com |
| 6 | **Monitoring & Debug** <br>• Review CloudFront logs. <br>• Debug API Gateway. <br>• Kiểm tra Lambda logs. | 21/11/2025 | 21/11/2025 | cloudjourney.awsstudygroup.com |
| 7 | **Cleanup tài nguyên** <br>• Xóa CloudFront test. <br>• Xóa bucket test. <br>• Kiểm tra Billing. | 22/11/2025 | 22/11/2025 | cloudjourney.awsstudygroup.com |

---

### Kết quả đạt được:

#### 1. Hoàn thiện hosting Frontend serverless
* Triển khai web tĩnh bằng S3 + CloudFront hoàn chỉnh.
* Website chạy HTTPS và bảo mật bằng OAC.
* Tối ưu tốc độ nhờ global CDN.

#### 2. Tích hợp Cognito Authentication vào UI
* Tái sử dụng User Pool cấu hình từ tuần 8.
* Lấy và lưu JWT token đúng chuẩn.
* Cài đặt login/logout & token expiration logic.

#### 3. Gọi API Gateway từ Frontend bằng JWT
* API private xác thực thành công bằng Cognito.
* UI xử lý lỗi 401/403 đúng logic.
* Data flow hoạt động mượt từ Frontend → API → Lambda.

#### 4. Debug & Monitoring hiệu quả
* Theo dõi chi tiết request qua CloudFront logs.
* Debug API & Lambda bằng CloudWatch.
* Tối ưu chi phí bằng cleanup resource test.

---

### Tóm tắt kiến thức đạt được:

* S3 + CloudFront hosting mô hình serverless chuẩn AWS.
* Tích hợp Cognito Authentication không cần Amplify.
* Gọi API Gateway bằng JWT và xử lý lỗi bảo mật.
* Debug hệ thống toàn diện từ Edge → API → Backend.

---
