---
title: "Worklog Tuần 12"
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

---

### Mục tiêu tuần 12:

**Phần 1 – Amazon Bedrock: Xây dựng API AI cho hệ thống**

* Hiểu kiến trúc Bedrock: model invocation, pricing, throttling.
* Gọi mô hình Claude/Titan từ Lambda qua Interface Endpoint.
* Tối ưu prompt để xử lý dữ liệu, phân tích nội dung.
* Tạo API Gateway endpoint để expose AI API ra ngoài.
* Xử lý lỗi: timeout, throttling, input validation.

**Phần 2 – Xây dựng Workflow tự động bằng Step Functions**

* Thiết kế quy trình nhiều bước:  
  Lambda → Bedrock → Lưu dữ liệu → Gửi email.
* Sử dụng Task State, Choice State, Wait State.
* Tích hợp Lambda vào Step Functions để tạo workflow AI.
* Bắt lỗi bằng Retry + Catch.
* Ghi log quá trình xử lý.

**Phần 3 – Gửi email thông báo bằng Amazon SES**

* Xác minh email/sender identity.
* Tạo Lambda gửi email từ template.
* Kết hợp Step Functions → SES để gửi báo cáo kết quả AI.
* Xử lý bounce/complaint nếu có.

**Phần 4 – Monitoring toàn bộ workflow**

* CloudWatch Logs cho Bedrock & Lambda.
* Xem Execution History trong Step Functions.
* Metrics theo dõi success/failure của workflow.
* Tối ưu chi phí khi dùng Bedrock (max tokens, batching…).

---

### Các công việc trong tuần:

| Thứ | Công việc | Bắt đầu | Hoàn thành | Nguồn tài liệu |
| --- | -------- | -------- | ---------- | -------------- |
| 2 | **Bedrock basic operations** <br>• Gọi model qua Lambda. <br>• Tối ưu prompt & chế độ inference. <br>• Debug lỗi connection. | 24/11/2025 | 24/11/2025 | cloudjourney.awsstudygroup.com |
| 3 | **Tạo AI API qua API Gateway + Lambda** <br>• Tạo route /ai/generate. <br>• Nhận input từ FE. <br>• Trả về kết quả từ Bedrock. | 25/11/2025 | 25/11/2025 | cloudjourney.awsstudygroup.com |
| 4 | **Thiết kế Step Functions workflow** <br>• Tạo State Machine. <br>• Lambda → Bedrock → lưu dữ liệu. <br>• Tạo nhánh xử lý lỗi. | 26/11/2025 | 26/11/2025 | cloudjourney.awsstudygroup.com |
| 5 | **Tích hợp SES vào workflow** <br>• Verify email. <br>• Lambda gửi email kết quả AI. <br>• Tích hợp vào Step Functions. | 27/11/2025 | 27/11/2025 | cloudjourney.awsstudygroup.com |
| 6 | **Monitoring & Debug** <br>• CloudWatch Logs cho Bedrock. <br>• Xem execution history Step Functions. <br>• Tối ưu chi phí. | 28/11/2025 | 28/11/2025 | cloudjourney.awsstudygroup.com |
| 7 | **Cleanup & Final Review** <br>• Xóa executions, test lambda, AI data. <br>• Kiểm tra billing Bedrock. <br>• Review output workflow. | 29/11/2025 | 29/11/2025 | cloudjourney.awsstudygroup.com |

---

### Kết quả đạt được:

#### 1. Xây dựng thành công API AI dựa trên Bedrock
* Gọi model AI từ Lambda chạy trong private subnet.
* Trả kết quả nhanh, ổn định qua API Gateway.
* Áp dụng prompt engineering để cải thiện output.

#### 2. Thiết kế workflow tự động bằng Step Functions
* Kết hợp nhiều Lambda thành một pipeline hoàn chỉnh.
* Tự động xử lý: Nhận input → Gọi AI → Lưu dữ liệu → Gửi email.
* Bắt lỗi chi tiết và retry hợp lý.

#### 3. Tích hợp SES gửi thông báo tự động
* Gửi email thành công từ Lambda.
* Gửi báo cáo AI sau mỗi workflow execution.
* Hiểu cơ chế quản lý bounce/complaint.

#### 4. Giám sát toàn diện hệ thống AI workflow
* Theo dõi log Bedrock, Lambda, API Gateway.
* Quan sát Step Functions Execution Map.
* Tối ưu chi phí AI inference & Lambda runtime.

---

### Tóm tắt kiến thức đạt được:

* Kiến thức thực chiến Amazon Bedrock & mô hình AI.
* Tạo API AI serverless bằng Lambda + API Gateway.
* Xây dựng workflow đa bước bằng Step Functions.
* Gửi email tự động bằng Amazon SES.
* Hiểu quy trình end-to-end của AI Agent Production.

---
