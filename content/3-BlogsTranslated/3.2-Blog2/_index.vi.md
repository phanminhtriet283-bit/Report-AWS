---
title: "Blog 2"
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# Định tuyến động bằng Amazon VPC Route Server

AWS cung cấp dịch vụ được quản lý **Amazon VPC Route Server** để giúp khách hàng thiết lập và vận hành giao thức định tuyến động Border Gateway Protocol (BGP) trong Amazon Virtual Private Cloud (Amazon VPC).

Trước đây, để có định tuyến động trong môi trường VPC, bạn cần chạy VPC router dựa trên phần mềm của riêng mình trên Amazon EC2. Giờ đây, với Amazon VPC Route Server, bạn có thể:

- Thiết lập phiên BGP động giữa Amazon VPC Route Server và các thiết bị mạng ảo.  
- Trao đổi thông tin định tuyến dựa trên thay đổi của lưu lượng.  
- Cập nhật tự động bảng định tuyến VPC mà không cần thủ công.  
- Phát hiện sự cố nhanh hơn bằng **Bidirectional Forwarding Detection (BFD)**.  
- Thực hiện kiểm tra sâu lưu lượng qua firewall ở quy mô Multi-AZ.

Trong blog này, chúng tôi trình bày chi tiết cách Amazon VPC Route Server hoạt động, các trường hợp sử dụng và cách bạn có thể bắt đầu với định tuyến động trong Amazon VPC.

---

## Tổng quan về Amazon VPC Route Server

Khách hàng triển khai software appliance để xử lý lưu lượng thoại. Appliance yêu cầu định tuyến động và dữ liệu trạng thái định tuyến được cập nhật liên tục thông qua BGP.

Software appliance yêu cầu:

- Định tuyến động từ Route Server  
- Phiên BGP hai chiều để phát hiện trạng thái mạng  
- Chuyển đổi tuyến đường phù hợp  

![Hình 1: Kiến trúc định tuyến động với Amazon VPC Route Server](images/hinh1.png)

**Hình 1: Kiến trúc định tuyến động với Amazon VPC Route Server**

Luồng định tuyến động:

1. Route Server thiết lập phiên BGP với thiết bị mạng.  
2. Thiết bị gửi tuyến đường về Route Server.  
3. Route Server cập nhật bảng định tuyến VPC.  
4. Route Server tạo phiên BFD đến thiết bị mạng.  
5. Thiết bị phản hồi bằng phiên BFD.  
6. Cả hai thực hiện phát hiện trạng thái để duy trì session BGP.

---

## Cách định tuyến động hoạt động trong Amazon VPC

![Hình 2: Route từ Route Server vào bảng route VPC](images/hinh2.png)

**Hình 2: Route từ Route Server vào bảng route VPC**

Quy trình:

1. Thiết bị thiết lập phiên BGP với Route Server.  
2. Trao đổi route.  
3. Route Server cập nhật route table.  
4. Lưu lượng đi theo route mới.

---

## Khi nào nên sử dụng định tuyến động?

### ✔ Chuyển đổi dự phòng tự động (Failover Automation)

Failover trong cloud đòi hỏi route phải thay đổi ngay khi instance, thiết bị hoặc AZ gặp lỗi.

![Hình 3: Chuyển đổi dự phòng bằng dynamic routing](images/hinh3.png)

**Hình 3: Chuyển đổi dự phòng bằng dynamic routing**

---

### ✔ Kiến trúc Floating IP cho High Availability

Floating IP cho phép một địa chỉ IP ổn định khi backend thay đổi.

![Hình 4: Kiến trúc Floating IP uptime cao](images/hinh4.png)

**Hình 4: Kiến trúc Floating IP uptime cao**

---

### ✔ Kiểm tra lưu lượng qua firewall

Phổ biến trong:

- DMZ  
- kiểm duyệt outbound  
- chặn truy cập trái phép  

![Hình 5: Firewall inspection trong nhiều AZ](images/hinh5.png)

**Hình 5: Firewall inspection trong nhiều AZ**

---

### ✔ Phát hiện sự cố cực nhanh bằng BFD

Trước đây failover mất 10–30 giây.  
Với BFD → chỉ **dưới 1 giây**.

![Hình 6: BFD phát hiện sự cố nhanh hơn](images/hinh6.png)

**Hình 6: BFD phát hiện sự cố nhanh hơn**

---

### ✔ Cập nhật bảng định tuyến VPC tự động

Không cần update thủ công.

![Hình 7: Route cập nhật tự động](images/hinh7.png)

**Hình 7: Route cập nhật tự động**

---

## Route Consistency & Route Advertisement

![Hình 8: Route Advertisement trong Route Server](images/hinh8.png)

**Hình 8: Route Advertisement trong Route Server**

Route Server thực hiện:

- Nhận route từ thiết bị mạng  
- Xác thực route hợp lệ  
- Đẩy vào route table  
- Quản lý vòng đời route theo session BGP  

---

## BFD và vai trò trong quá trình khôi phục

BFD giúp:

- Phát hiện link-down trong mili-giây  
- Tăng tốc failover  
- Phù hợp workload yêu cầu low latency

![Hình 9: BFD hỗ trợ failover](images/hinh9.png)

**Hình 9: BFD hỗ trợ failover**

---

# Kết luận

Amazon VPC Route Server mang lại cách tiếp cận mạnh mẽ, linh hoạt và dễ vận hành cho dynamic routing:

- BGP  
- BFD  
- Firewall inspection  
- Floating IP  
- Route advertisement tự động  

→ Đây là giải pháp phù hợp cho các kiến trúc yêu cầu **High Availability** và **Resilience**.

---

# Tác giả

**Rashid Mulji – Principal Solutions Architect, AWS**  
**Ryan Umstead – Senior Solutions Architect, AWS**

