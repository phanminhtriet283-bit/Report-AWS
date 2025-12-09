---
title: "Blog 3"
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

## [Networking & Content Delivery](https://aws.amazon.com/blogs/networking-and-content-delivery/)

Amazon CloudFront hiện hỗ trợ nguồn IPv6 để phân phối IPv6 toàn diện

Viết bởi Sagar Desarda và Ravi Avula on 04 SEP 2025 in [Các phương pháp hay nhất](https://aws.amazon.com/blogs/networking-and-content-delivery/category/post-types/best-practices/), [Mạng & Phân phối nội dung](https://aws.amazon.com/blogs/networking-and-content-delivery/category/networking-content-delivery/), [Hướng dẫn kỹ thuật](https://aws.amazon.com/blogs/networking-and-content-delivery/category/post-types/technical-how-to/) [Permalink](https://aws.amazon.com/blogs/networking-and-content-delivery/amazon-cloudfront-now-supports-ipv6-origins-for-end-to-end-ipv6-delivery/)  [Chia sẻ](https://aws.amazon.com/vi/blogs/networking-and-content-delivery/amazon-cloudfront-now-supports-ipv6-origins-for-end-to-end-ipv6-delivery/)

Việc áp dụng IPv6 tiếp tục tăng tốc trên toàn thế giới khi các tổ chức vượt ra ngoài giới hạn của không gian địa chỉ IPv4. Tại Amazon Web Services (AWS), từ lâu chúng tôi đã hỗ trợ IPv6 từ người dùng cuối đến [ mạng Amazon CloudFront của mình](https://aws.amazon.com/cloudfront/)  , giúp người dùng cuối giảm độ trễ, cải thiện hiệu suất và phạm vi tiếp cận trên các mạng di động hiện đại. Bây giờ, chúng tôi rất vui mừng được tiến thêm một bước nữa. Bắt đầu từ hôm nay, CloudFront hiện hỗ trợ kết nối IPv6 từ biên đến nguồn – cho phép đường dẫn phân phối IPv6 thực sự từ đầu đến cuối. Điều này cho phép người dùng cuối sử dụng CloudFront làm cổng internet ngăn xếp kép IPv6 và IPv4 cho các ứng dụng web của họ để cung cấp khả năng tăng tốc nội dung.

**Tại sao điều này lại quan trọng?**

IPv6 là giao thức truyền tải cơ bản cho hầu hết các mạng di động hiện đại và tỷ lệ lưu lượng băng thông rộng ngày càng tăng. Kích hoạt IPv6 đến nguồn cho phép bạn duy trì tính nhất quán của giao thức trong chuỗi phân phối, giảm chi phí vận hành từ sự phức tạp của ngăn xếp kép và đạt được các luồng lưu lượng xác định, có thể quan sát và hiệu quả hơn. Đối với người dùng cuối CloudFront, những lợi thế này chuyển trực tiếp thành tải trang nhanh hơn, phát trực tuyến ổn định hơn và kiến trúc phân phối tiếp tục hoạt động khi tài nguyên IPv4 giảm dần.

**Lợi ích của IPv6 đối với các ứng dụng hỗ trợ CloudFront**

CloudFront hiện hỗ trợ nguồn gốc qua IPv6, do đó bạn có thể kích hoạt kết nối IPv6 đầu cuối – từ người dùng cuối đến máy chủ gốc của bạn. Điều này mở ra một loạt các lợi ích kỹ thuật và vận hành so với phân phối dựa trên IPv4 truyền thống.

1\. Loại bỏ chi phí NAT và cải thiện hiệu suấtMạng IPv4 phụ thuộc nhiều vào Dịch địa chỉ mạng (NAT), đặc biệt là NAT cấp nhà cung cấp dịch vụ được sử dụng bởi các ISP và nhà khai thác di động. Các lớp NAT này gây ra sự chậm trễ trong thiết lập kết nối, giới hạn tính khả dụng của cổng và có thể gây ra sự cố rớt gói. IPv6 loại bỏ nhu cầu về NAT, cho phép kết nối trực tiếp từ đầu đến cuối giữa người dùng cuối, CloudFront và nguồn gốc. Kết quả là độ trễ thấp hơn, tải trang nhanh hơn và trải nghiệm người dùng tốt hơn – đặc biệt là ở các thị trường ưu tiên thiết bị di động, nơi mức độ áp dụng IPv6 cao nhất.

2\. Xử lý gói hiệu quả hơnIPv6 giới thiệu tiêu đề và Tiêu đề mở rộng được đơn giản hóa, có độ dài cố định cho thông tin điều khiển tùy chọn. Điều này giúp phân tích cú pháp và chuyển tiếp gói hiệu quả hơn cho bộ định tuyến, tường lửa, cân bằng tải và các nút CloudFront. IPv6 giảm chi phí xử lý trên mỗi gói và loại bỏ sự mơ hồ trong quá trình chuyển tiếp hoặc kiểm tra gói, đặc biệt là trong các hệ thống thực hiện kiểm tra gói sâu hoặc định hình lưu lượng. Không giống như IPv4, cho phép phân mảnh trong đường dẫn của các bộ định tuyến, IPv6 ủy quyền hoàn toàn trách nhiệm phân mảnh cho máy chủ nguồn. Hạn chế kiến trúc này cải thiện hiệu suất truyền dẫn bằng cách giảm truyền lại và duy trì kích thước phân đoạn tối ưu trong suốt đường vận chuyển. Do đó, IPv6 cho phép các kết nối TCP ổn định và hiệu quả hơn, đặc biệt là trên các liên kết đường dài hoặc độ trễ cao giữa CloudFront và nguồn gốc. Điều này được thực hiện bằng cách giảm truyền lại và duy trì kích thước phân đoạn tối ưu trong suốt đường vận chuyển.

3\. Kiểm soát đường truyền và tắc nghẽn có thể dự đoán IPv6 thực thi Khám phá MTU đường dẫn (PMTUD) đầu cuối, ủy quyền hoàn toàn trách nhiệm phân mảnh cho máy chủ nguồn. Hạn chế kiến trúc này cải thiện khả năng dự đoán truyền tải và giảm thiểu nguy cơ các gói bị rớt hoặc phân mảnh do MTU không khớp. IPv6 cải thiện độ ổn định và thông lượng TCP – đặc biệt là trên đường dẫn đường dài hoặc độ trễ cao giữa CloudFront và nguồn không phải AWS. Điều này được thực hiện bằng cách giảm thiểu việc truyền lại và duy trì kích thước phân đoạn tối ưu từ đầu đến cuối. Đối với các nguồn AWS, ngày nay đạt được những lợi ích tương tự thông qua mạng đường trục AWS như hỗ trợ khung jumbo. Việc kích hoạt khung jumbo giữa vị trí biên AWS và điểm cuối ứng dụng trong Khu vực AWS cho phép CloudFront gửi và nhận tải trọng lớn hơn trong mỗi gói. Hỗ trợ khung Jumbo cắt giảm tổng thời gian cần thiết để truyền dữ liệu giữa người dùng cuối và ứng dụng của bạn.

4\. Khả năng mở rộng kết nối cao hơnTrong IPv4, NAT giảm số lượng cổng nguồn khả dụng trên mỗi địa chỉ IP gốc, điều này giới hạn số lượng kết nối đồng thời mà nút CloudFront có thể thiết lập với gốc. Ràng buộc này có thể trở thành vấn đề trong môi trường có lưu lượng truy cập cao, nơi hàng nghìn yêu cầu đồng thời phải được xử lý hiệu quả. Khả năng này đặc biệt có lợi khi sử dụng các giao thức như HTTP/2, trong đó ghép kênh nhiều luồng trên một kết nối duy nhất và sử dụng lại kết nối là điều cần thiết để tối đa hóa hiệu suất và giảm thiểu độ trễ.

**Bắt đầu**

Bắt đầu từ hôm nay, bạn có thể định cấu hình các nguồn được liên kết với bản phân phối CloudFront của mình để sử dụng IPv6. Tính năng mới cho phép bạn chọn giữa IPv4 (mặc định), IPv6 hoặc ngăn xếp kép (IPv4 và IPv6). Đối với các nguồn gốc hiện tại của bạn, CloudFront tiếp tục sử dụng IPv4. Khi sử dụng ngăn xếp kép, CloudFront sẽ tự động chọn giữa địa chỉ IP IPv4 và IPv6 để đảm bảo phân phối lưu lượng truy cập đồng đều về nguồn trên cả hai.

Bạn có thể sử dụng bảng điều khiển CloudFront hoặc API CloudFront để tạo hoặc cập nhật bản phân phối CloudFront nhằm định cấu hình kết nối IPv6 với nguồn của bạn. Trong bài đăng này, chúng tôi sẽ hướng dẫn bạn cách tạo nguồn có hỗ trợ IPv6 và khám phá các phương pháp hay nhất để kích hoạt IPv6 một cách an toàn trên các nguồn gốc hiện có. Trước khi bắt đầu, hãy đảm bảo nguồn của bạn hỗ trợ kết nối IPv6 hoặc ngăn xếp kép. Đây có thể là nguồn tùy chỉnh hoặc dịch vụ AWS có hỗ trợ IPv6, chẳng hạn như [Elastic Load Balancers](https://aws.amazon.com/elasticloadbalancing/), [Amazon API Gateway](https://aws.amazon.com/api-gateway/) hoặc [ URL hàm](https://aws.amazon.com/lambda/) AWS Lambda.

**Tạo bản phân phối CloudFront mới với nguồn gốc IPv6**

Trong bảng điều khiển CloudFront, chọn tùy chọn để tạo bản phân phối CloudFront.

Bước 1: Bắt đầuNhập tên phân phối và nhập các thông số tùy chọn khác trước khi chọn Tiếp theo để chuyển sang Bước 2\.

![Khởi tạo bản phân phối CloudFront của bạn][image1]

Bước 2: Chỉ định nguồn gốcTrong Bước 2, chọn loại xuất xứ và nhập thông tin xuất xứ. Để định cấu hình IPv6, hãy chọn tùy chỉnh cài đặt nguồn gốc trong bảng Cài đặt.

![Định cấu hình nguồn CloudFront của bạn][image2]

Chọn IPv6 hoặc Dualstack cho cài đặt Loại địa chỉ IP gốc và chọn Tiếp theo.

![Cài đặt loại địa chỉ IP gốc][image3]

Bước 3: Bật bảo mậtBạn có thể chọn bật [AWS WAF](https://aws.amazon.com/waf/) để bảo vệ ứng dụng của mình và chọn Tiếp theo.  
 ![Đính kèm AWS WAF vào phân phối CloudFront][image4]

Bước 4: Xem lại và tạoĐánh giá và chọn nút Tạo phân phối để tạo phân phối.

![Xác nhận cài đặt CloudFront và triển khai][image5]

Thêm nguồn IPv6 mới vào bản phân phối CloudFront hiện cóĐể thêm nguồn IPv6 mới vào bản phân phối CloudFront hiện có, hãy mở cài đặt Phân phối bằng cách chọn bản phân phối và chọn tab Nguồn để Tạo gốc.

![Đính kèm nguồn IPv6 vào bản phân phối CloudFront][image6]

Mở rộng Cài đặt bổ sung và chọn tùy chọn IPv6 hoặc Dualstack trong loại Địa chỉ IP gốc để bật kết nối IPv6 với nguồn của bạn. Khi bạn tạo nguồn gốc, hãy thêm hoặc cập nhật hành vi để trỏ đến nguồn gốc mới của bạn.

![Mở rộng cài đặt bổ sung][image7]

Bật IPv6 cho nguồn hiện có  
 Bạn có thể sử dụng [triển khai liên tục CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/continuous-deployment.html) để di chuyển các thay đổi sang cài đặt gốc một cách an toàn. Triển khai liên tục CloudFront cho phép bạn kiểm tra các thay đổi một cách an toàn bằng cách sử dụng chính sách triển khai để định tuyến các yêu cầu đến phân phối dàn dựng, cũng như xác thực và thúc đẩy các thay đổi. Để biết thêm chi tiết về cách tiếp cận này, hãy tham khảo [tài liệu về CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/working-with-staging-distribution-continuous-deployment-policy.html).

![Thiết lập nguồn gốc Dualstack][image8]

Xác thực kết nối IPv6 với nguồn Sử dụng số liệu hoặc nhật ký ứng dụng để xác thực lưu lượng IPv6 tại gốc. Trong trường hợp này, chúng tôi đã sử dụng [Cân bằng tải ứng dụng (ALB)](https://aws.amazon.com/elasticloadbalancing/application-load-balancer/) làm nguồn gốc và sử dụng chỉ số Yêu cầu IPv6 để xác thực.

![Giám sát lưu lượng gốc IPv6][image9]

**Kết thúc**

Khi việc áp dụng IPv6 ngày càng tăng trên các mạng di động và toàn cầu, việc kích hoạt IPv6 toàn diện—từ người dùng cuối đến Amazon CloudFront đến nguồn điện—sẽ mở ra những lợi thế về hiệu suất và kiến trúc mà IPv4 không thể sánh kịp. Nó loại bỏ chi phí NAT, cải thiện khả năng hiển thị định tuyến và luồng, đồng thời hợp lý hóa quá trình xử lý gói thông qua các tiêu đề cố định và khám phá MTU Đường dẫn đáng tin cậy. Mặc dù CloudFront tối ưu hóa cho cả IPv4 và IPv6, nhưng lợi ích của IPv6 rõ rệt nhất trong chặng đầu tiên và cuối cùng của quá trình phân phối. Nắm bắt IPv6 từ đầu đến cuối tạo nền tảng cho việc phân phối nội dung có thể mở rộng, hiệu suất cao và sẵn sàng cho tương lai.

Bật IPv6 toàn diện trên Amazon CloudFront không còn là tùy chọn nữa – đây là bước cơ bản để mở khóa độ trễ thấp hơn, khả năng phục hồi cao hơn và khả năng mở rộng trong tương lai. Nếu bạn chưa có, hãy bật hỗ trợ IPv6 trong [bản phân phối CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/DownloadDistValuesGeneral.html#DownloadDistValuesEnableIPv6)  của bạn ngay hôm nay.

![Một người mặc áo sơ mi đenNội dung do AI tạo ra có thể không chính xác.][image10]

Sagar Desarda

Sagar Desarda là Trưởng bộ phận Quản lý Tài khoản Kỹ thuật (TAM) và Phát triển Kinh doanh (BD) cho Dữ liệu, Phân tích và Gen AI ISV. Các nhóm của Sagar hợp tác với khách hàng để tối ưu hóa kiến trúc AWS của họ, đảm bảo hoạt động liền mạch của các ứng dụng quan trọng trong kinh doanh, đẩy nhanh quá trình áp dụng và thúc đẩy thành công trong việc tiếp cận thị trường trên khắp Bắc Mỹ. Ngoài ra, Sagar còn là lãnh đạo AMER cho nhóm Chuyên gia Dịch vụ Mạng biên, nơi ông thúc đẩy tăng trưởng kinh doanh mới, thúc đẩy các cam kết kỹ thuật và tác giả các ấn phẩm hướng tới khách hàng.

 

![Một người có ria mép và áo sơ mi sọcNội dung do AI tạo ra có thể không chính xác.][image11]

Ravi Avula

Ravi là Kiến trúc sư giải pháp cấp cao của AWS tập trung vào Kiến trúc doanh nghiệp. Ông có 20 năm kinh nghiệm trong lĩnh vực kỹ thuật phần mềm và giữ một số vai trò lãnh đạo trong lĩnh vực kỹ thuật phần mềm và kiến trúc phần mềm làm việc trong ngành thanh toán.

[image1]: /images/3-BlogsTranslated/h1.png
[image2]: /images/3-BlogsTranslated/h2.png
[image3]: /images/3-BlogsTranslated/h3.png
[image4]: /images/3-BlogsTranslated/h4.png
[image5]: /images/3-BlogsTranslated/h5.png
[image6]: /images/3-BlogsTranslated/h6.png
[image7]: /images/3-BlogsTranslated/h7.png
[image8]: /images/3-BlogsTranslated/h8.png
[image9]: /images/3-BlogsTranslated/h9.png
[image10]: /images/3-BlogsTranslated/h10.png
[image11]: /images/3-BlogsTranslated/h11.png

