---
title: "Blog 2"
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---
[**AWS for SAP**](https://aws.amazon.com/blogs/awsforsap/)

## **Trợ lý AI Agentic cho SAP với AWS Generative AI**  
Viết bởi Sourav Sadhu vào ngày 04 tháng 9 năm 2025 trong [Amazon Bedrock](https://aws.amazon.com/blogs/awsforsap/category/artificial-intelligence/amazon-machine-learning/amazon-bedrock/), [Amazon Bedrock Agents](https://aws.amazon.com/blogs/awsforsap/category/artificial-intelligence/amazon-machine-learning/amazon-bedrock/amazon-bedrock-agents/), [Amazon Bedrock Knowledge Bases](https://aws.amazon.com/blogs/awsforsap/category/artificial-intelligence/amazon-machine-learning/amazon-bedrock/amazon-bedrock-knowledge-bases/), [SAP on AWS](https://aws.amazon.com/blogs/awsforsap/category/sap/), [Technical How-to](https://aws.amazon.com/blogs/awsforsap/category/post-types/technical-how-to/) [Permalink](https://aws.amazon.com/blogs/awsforsap/agentic-ai-assistant-for-sap-with-aws-genai/)  [Share](https://aws.amazon.com/blogs/awsforsap/agentic-ai-assistant-for-sap-with-aws-genai/#)

**Giới thiệu**

Hệ thống SAP là xương sống của nhiều doanh nghiệp, quản lý các quy trình kinh doanh quan trọng và tạo ra khối lượng dữ liệu giá trị lớn. Các quy trình kinh doanh và dữ liệu quan trọng này thường mở rộng ra ngoài hệ thống SAP doanh nghiệp, yêu cầu khách hàng tương tác với các hệ thống bên ngoài. Khi các tổ chức tìm cách tận dụng dữ liệu này để có được những hiểu biết sâu sắc hơn và cải thiện việc ra quyết định, nhu cầu thay đổi cách khách hàng SAP tương tác với dữ liệu và hệ thống của họ ngày càng tăng.

Khả năng xử lý ngôn ngữ tự nhiên (NLP) của trí tuệ nhân tạo tạo sinh (Generative AI) cung cấp cho người dùng SAP một công cụ mạnh mẽ để tương tác với các hệ thống ERP phức tạp bằng các câu hỏi ngôn ngữ tự nhiên, loại bỏ nhu cầu về kiến thức kỹ thuật chuyên sâu hoặc các truy vấn SQL phức tạp. Điều này dân chủ hóa việc truy cập dữ liệu trong toàn tổ chức, cho phép người dùng doanh nghiệp đặt câu hỏi, tạo báo cáo và thu thập thông tin chi tiết theo thời gian thực thông qua các giao diện hội thoại.

Việc tích hợp Generative AI với hệ thống SAP cho phép các tổ chức thu hẹp khoảng cách giữa dữ liệu ERP có cấu trúc và thông tin không có cấu trúc từ các nguồn SAP và không phải SAP, mang lại cái nhìn toàn diện hơn về bối cảnh kinh doanh của họ. Sự tích hợp này có thể dẫn đến dự báo chính xác hơn, trải nghiệm khách hàng được cá nhân hóa và ra quyết định dựa trên dữ liệu bao quát toàn bộ hệ sinh thái doanh nghiệp.

AWS và SAP trao quyền cho khách hàng ở mọi giai đoạn của hành trình áp dụng Generative AI với bộ dịch vụ AI tạo sinh tiên tiến, cơ sở hạ tầng mạnh mẽ và nguồn lực triển khai phong phú. Những dịch vụ này có thể tích hợp với hệ thống SAP và bổ sung cho hệ sinh thái dịch vụ đám mây rộng lớn của AWS và SAP.

Trong bài blog này (Phần 1 của chuỗi 2 phần), tôi sẽ mô tả và minh họa cách bạn có thể tận dụng Amazon Bedrock và các dịch vụ AWS khác để thu thập thông tin chi tiết từ các nguồn dữ liệu SAP và không phải SAP bằng ngôn ngữ tự nhiên của con người trong một giao diện thống nhất thông qua MS Teams, Slack và giao diện người dùng Streamlit.

Trong Phần 2 của chuỗi bài blog này, tôi sẽ mô tả và minh họa cách bạn có thể tận dụng các dịch vụ SAP BTP \[SAP Build Apps, SAP Generative AI Hub\] để thu thập thông tin chi tiết từ các hệ thống SAP và không phải SAP bằng ngôn ngữ tự nhiên của con người trong một giao diện thống nhất với giao diện người dùng SAP Build Apps.

**Tổng quan**

Tôi sẽ bắt đầu bằng cách phát triển logic kinh doanh cần thiết để trích xuất dữ liệu từ hệ thống SAP. Tôi sẽ tạo hai hàm AWS Lambda để thực thi logic kinh doanh, được hỗ trợ bởi các dịch vụ AWS khác nhau bao gồm Bedrock Knowledge Bases và AWS Secrets Manager. Sau đó, tôi sẽ tập trung vào việc tạo logic kinh doanh để xử lý dữ liệu từ một nguồn dữ liệu không phải SAP bổ sung, triển khai một hàm Lambda khác được thiết kế đặc biệt để trích xuất dữ liệu từ Amazon DynamoDB, nơi chứa thông tin logistics. Để nâng cao khả năng của hệ thống, tôi sẽ thiết lập một cơ sở tri thức sẽ đóng vai trò là nguồn dữ liệu thứ ba, hỗ trợ các truy vấn chung của người dùng. Tiếp theo, tôi sẽ triển khai một Amazon Bedrock Agent chịu trách nhiệm điều phối luồng giữa các nguồn dữ liệu khác nhau dựa trên truy vấn của người dùng. Ở giai đoạn cuối, tôi sẽ tạo một giao diện người dùng bằng Streamlit, đồng thời cung cấp một tùy chọn tích hợp thay thế với MS Teams và Slack để tăng khả năng truy cập.

![][image1]

**Hình 1\. Kiến trúc cấp cao**

**Hướng dẫn thực hiện**

Tôi đã cấu trúc giải pháp thành 5 bước. Hãy cùng tôi đi qua từng bước:

**Bước 1 – Tạo logic kinh doanh để lấy dữ liệu từ hệ thống SAP**  
**Bước 2 – Tạo logic kinh doanh để lấy dữ liệu từ hệ thống không phải SAP**  
**Bước 3 – Tạo cơ sở tri thức Bedrock cho các truy vấn chung**  
**Bước 4 – Tạo Bedrock Agents để điều phối giữa các nguồn dữ liệu khác nhau**  
**Bước 5 – Tạo giao diện người dùng với Microsoft Teams, Slack và Streamlit**

**Điều kiện tiên quyết**

Một tài khoản AWS với quyền IAM phù hợp để làm việc với Amazon S3, AWS Lambda, Amazon Bedrock Agents, Amazon Bedrock Knowledge Bases, Amazon Bedrock LLM (Claude), AWS Secrets Manager, Amazon DynamoDB. Nếu bạn chưa quen với các dịch vụ này, nên tìm hiểu trước khi tiếp tục.

* Một hệ thống SAP hỗ trợ dịch vụ SAP OData làm nguồn dữ liệu cho Đơn hàng Bán hàng SAP.  
* Tôi đã sử dụng dịch vụ OData tiêu chuẩn, Dịch vụ Đơn hàng Bán hàng SAP: API\_SALES\_ORDER\_SRV và Tập thực thể: A\_SalesOrder cho bản demo này, tuy nhiên bạn có thể sử dụng bất kỳ dịch vụ OData nào tùy thuộc vào trường hợp sử dụng của bạn. Tôi đã công khai OData qua internet, nhưng tùy thuộc vào vị trí hệ thống SAP của bạn, bạn có thể chọn không công khai qua internet. Tuy nhiên, chúng tôi khuyến nghị thiết lập kết nối riêng tư để có hiệu suất và bảo mật tốt hơn. Để biết thêm thông tin, xem *Cách kích hoạt dịch vụ OData trong SAP S/4HANA* và *Kết nối với RISE từ tài khoản AWS của bạn*.  
* Tài khoản Slack cho tích hợp Slack và tài khoản MS Teams cho tích hợp MS Teams \[tùy chọn\].

**Bước 1 – Tạo logic kinh doanh để lấy dữ liệu từ hệ thống SAP**

I. Tôi sẽ bắt đầu bằng cách tạo bí mật trong AWS Secrets Manager để lưu trữ thông tin đăng nhập và chi tiết kết nối của hệ thống S4.

Chọn loại bí mật là Loại bí mật khác và sau đó thêm các chi tiết dưới đây vào cặp Khóa/Giá trị. Đặt giá trị bí mật phù hợp với môi trường của bạn.

| Khóa bí mật | Giá trị bí mật |
| ----- | ----- |
| S4\_host\_details | https://\<hostname\>:\<port\> |
| S4\_username | xxxx |
| S4\_password | xxxx |

Để biết thêm thông tin, xem *Tạo bí mật trong AWS Secrets Manager*.

II. Là bước thứ hai, tôi sẽ tạo hai cơ sở tri thức Bedrock để bổ sung và hỗ trợ dữ liệu SAP khi cần thiết.

* Odata-Schema-knowledgebase: Tôi sẽ sử dụng cơ sở tri thức này để cung cấp chi tiết lược đồ cho LLM, để mô hình có đủ kiến thức về các thuộc tính cần sử dụng khi tạo URL OData dựa trên truy vấn của người dùng.  
* SAP-external-knowledgebase: Tôi sẽ sử dụng cơ sở tri thức này để cung cấp chi tiết bổ sung cho dữ liệu không phải SAP.

Tôi đã xem xét các đầu vào sau khi tạo hai cơ sở tri thức, giữ tất cả các cài đặt khác ở giá trị mặc định.

* Cung cấp chi tiết cơ sở tri thức  
  * Tên cơ sở tri thức: Chọn tên cho mỗi cơ sở tri thức với mô tả thân thiện với người dùng. Tôi đã sử dụng Odata-Schema-knowledgebase và SAP-external-knowledgebase.  
  * Mô tả cơ sở tri thức: Cung cấp mô tả xác định duy nhất cơ sở tri thức của bạn.  
* Quyền IAM: Chọn Tạo và sử dụng vai trò dịch vụ mới.  
* Cấu hình nguồn dữ liệu  
  * Nguồn dữ liệu: Chọn Amazon S3.  
  * Tên nguồn dữ liệu: Chọn tên cho mỗi nguồn dữ liệu.  
  * S3 URI: Tạo hai bucket S3, một cho mỗi cơ sở tri thức. Tải tệp Sales\_Order\_Schema.json cho Odata-Schema-knowledgebase và Shipping\_Policy.pdf cho SAP-external-knowledgebase từ kho GitHub lên các bucket S3 tương ứng và cung cấp URI S3.  
* Cấu hình lưu trữ và xử lý dữ liệu  
  * Mô hình nhúng: Amazon Titan Text Embeddings V2.  
  * Cơ sở dữ liệu vector: Phương pháp tạo vector là Tạo nhanh kho vector mới và kho vector là Amazon OpenSearch Serverless.

Để biết thêm thông tin, xem *Tạo cơ sở tri thức bằng cách kết nối với nguồn dữ liệu trong Amazon Bedrock Knowledge Bases*.

Đây là giao diện cuối cùng của tôi  
![][image2]

III. Bây giờ, tôi sẽ tạo hai hàm Lambda để trích xuất dữ liệu từ hệ thống SAP dựa trên truy vấn của người dùng.

* SAP-Odata-URL-Generation: Hàm Lambda này thực thi logic kinh doanh để tạo URL OData dựa trên truy vấn của người dùng với sự hỗ trợ của LLM, được bổ sung bởi chi tiết lược đồ từ cơ sở tri thức và chi tiết máy chủ từ AWS Secrets Manager.  
* SAP-Sales-Order-Query: Hàm Lambda này thực thi logic kinh doanh cốt lõi để truy xuất dữ liệu từ hệ thống SAP. Nó sử dụng URL OData do hàm SAP-Odata-URL-Generation cung cấp và truy cập an toàn thông tin đăng nhập hệ thống được lưu trữ trong AWS Secrets Manager. Hàm sau đó xử lý dữ liệu đã truy xuất, tận dụng LLM thông qua Bedrock, và cuối cùng trình bày thông tin có cấu trúc cho Bedrock Agent để sử dụng tiếp.

Tôi đã xem xét các đầu vào dưới đây khi tạo các hàm, giữ tất cả các cài đặt khác ở giá trị mặc định.

* Chọn Tạo từ đầu.  
* Tên hàm: Chọn tên cho mỗi hàm với mô tả thân thiện với người dùng. Tôi đã chọn SAP-Odata-URL-Generation và SAP-Sales-Order-Query.  
* Môi trường chạy: Python 3.13.  
* Kiến trúc: x86\_64.  
* Mã: Sao chép mã SAP-Odata-URL-Generation.py cho hàm SAP-Odata-URL-Generation và SAP-Sales-Order-Query.py cho SAP-Sales-Order-Query từ kho GitHub. Lưu ý: Điều chỉnh mã với các giá trị cụ thể cho triển khai của bạn như kb\_id, SecretId, v.v.  
* Cấu hình: Bộ nhớ: 1024MB, Thời gian chờ: 15 phút.  
* Lớp: Thêm lớp requests-layer.zip để thêm mô-đun requests vào hàm Lambda từ kho GitHub.  
* Quyền: Cần cấu hình các quyền dưới đây cho các hàm Lambda.  
  * SAP-Odata-URL-Generation: Vai trò thực thi – Ngoài vai trò cơ bản của Lambda, tạo một chính sách IAM mới với các hành động sau: bedrock:InvokeModel, bedrock-agent-runtime:Retrieve, secretsmanager:GetSecretValue. Tuyên bố chính sách dựa trên tài nguyên – Quyền lambda:InvokeFunction cho ARN của Bedrock Agent mà chúng ta sẽ tạo ở Bước 4\.  
  * SAP-Sales-Order-Query: Vai trò thực thi – Ngoài vai trò cơ bản của Lambda, tạo một chính sách IAM mới với các hành động sau: bedrock:InvokeModel, secretsmanager:GetSecretValue. Tuyên bố chính sách dựa trên tài nguyên – Quyền lambda:InvokeFunction cho ARN của Bedrock Agent mà chúng ta sẽ tạo ở Bước 4\.

Để biết thêm thông tin, xem *Xây dựng hàm Lambda với Python* và *Làm việc với các lớp cho hàm Lambda Python*.

**Bước 2 – Tạo logic kinh doanh để lấy dữ liệu từ hệ thống không phải SAP**

I. Tôi sẽ bắt đầu bằng cách tạo một bảng DynamoDB, với các đầu vào dưới đây.

* Tên bảng: logistics.  
* Khóa phân vùng: order\_id.

Sử dụng tệp Items.json từ kho GitHub để tạo mục trong bảng DynamoDB. Để biết thêm thông tin, xem *Tạo mục bảng Amazon DynamoDB từ tệp JSON*.

II. Bây giờ, tôi sẽ tạo một hàm Lambda để trích xuất dữ liệu từ bảng DynamoDB dựa trên truy vấn của người dùng.

* Chọn Tạo từ đầu.  
* Tên hàm: Chọn tên cho hàm với mô tả thân thiện với người dùng. Tôi đã chọn Logistics-System.  
* Môi trường chạy: Python 3.13.  
* Kiến trúc: x86\_64.  
* Cấu hình: Bộ nhớ: 1024MB, Thời gian chờ: 15 phút.  
* Mã: Sao chép mã Logistics-System.py từ kho GitHub.  
* Quyền: Thêm các quyền sau cho hàm Lambda. Vai trò thực thi – Ngoài vai trò cơ bản của Lambda, tạo một chính sách IAM mới với các hành động sau: dynamodb:Query, dynamodb:DescribeTable. Tuyên bố chính sách dựa trên tài nguyên – Quyền lambda:InvokeFunction cho ARN của Bedrock Agent mà chúng ta sẽ tạo ở Bước 4\.

**Bước 3 – Tạo cơ sở tri thức cho các truy vấn chung**

Bây giờ, tôi sẽ tạo một cơ sở tri thức thứ ba. Cơ sở tri thức này sẽ đóng vai trò là kho thông tin chung. Người dùng có thể truy cập tài nguyên này để tìm hiểu về các chủ đề khác nhau, từ thông tin tổ chức đến chuyên môn cụ thể theo chủ đề, tùy theo yêu cầu.

General-information-knowledgebase: Trong bản demo này, tôi sẽ sử dụng cơ sở tri thức này để cung cấp hướng dẫn về các quy trình kinh doanh SAP.

Tôi đã xem xét các đầu vào dưới đây khi tạo cơ sở tri thức, giữ phần còn lại ở giá trị mặc định.

* Cung cấp chi tiết cơ sở tri thức  
  * Tên cơ sở tri thức: Chọn tên cho mỗi cơ sở tri thức, tôi đã sử dụng General-information-knowledgebase với mô tả thân thiện với người dùng.  
  * Quyền IAM: Chọn Tạo và sử dụng vai trò dịch vụ mới.  
* Cấu hình nguồn dữ liệu  
  * Nguồn dữ liệu: Chọn Amazon S3.  
  * Tên nguồn dữ liệu: Chọn tên cho nguồn dữ liệu theo ý bạn.  
  * S3 URI: Tạo bucket S3, tải lên tệp “How to create SAP Sales Order pdf” từ kho GitHub và cung cấp URI S3 tương ứng.  
* Cấu hình lưu trữ và xử lý dữ liệu  
  * Mô hình nhúng: Amazon Titan Text Embeddings V2.  
  * Cơ sở dữ liệu vector: Phương pháp tạo vector là Tạo nhanh kho vector mới và kho vector là Amazon OpenSearch Serverless.

**Đây là giao diện cuối cùng của tôi**

*![][image3]*

**Bước 4 – Tạo Bedrock Agent**

Trong bước này, tôi sẽ tạo một Bedrock Agent để giúp chúng ta điều phối giữa các nguồn dữ liệu khác nhau mà chúng ta đã tạo trong các bước trước để trả lời các truy vấn của người dùng.

Tôi đã xem xét các đầu vào dưới đây khi tạo Bedrock Agent, giữ tất cả các cài đặt khác ở giá trị mặc định.

* Chi tiết Agent:  
  * Tên Agent: Chọn tên cho agent và mô tả thân thiện với người dùng. Tôi đã đặt tên là Business-Query-System.  
  * Vai trò tài nguyên Agent: Chọn Tạo và sử dụng vai trò dịch vụ mới.  
  * Chọn mô hình: Chọn Claude 3 Sonnet v1. Bạn có thể chọn một LLM khác, nhưng bạn cần sửa đổi các lời nhắc tương ứng để có phản hồi mong muốn.  
  * Hướng dẫn cho Agent: Cung cấp hướng dẫn chi tiết, từng bước, giải thích rõ ràng những gì bạn muốn Agent thực hiện.

Bạn là một trợ lý AI hỗ trợ người dùng truy vấn dữ liệu bán hàng SAP trực tiếp từ hệ thống SAP và chi tiết vận chuyển từ hệ thống logistics. Bạn cũng giúp người dùng với các truy vấn chung về quy trình kinh doanh từ cơ sở tri thức của công ty.

* Cài đặt bổ sung: Chọn đầu vào người dùng là Bật.  
* Nhóm hành động: Nhóm hành động xác định các nhiệm vụ mà agent nên hỗ trợ người dùng thực hiện.  
  * Nhóm hành động: SAP-Sales-Order. Tôi sẽ sử dụng nhóm hành động này để xử lý bất kỳ truy vấn nào liên quan đến đơn hàng bán hàng SAP.  
    * Tên nhóm hành động: Chọn tên cho nhóm hành động và đưa ra mô tả thân thiện với người dùng. Tôi đã đặt tên là SAP-Sales-Order.  
    * Loại nhóm hành động: Xác định bằng chi tiết hàm.  
    * Gọi nhóm hành động: Chọn hàm Lambda hiện có và chọn hàm Lambda đã tạo ở Bước 1, SAP-Sales-Order-Query.  
    * Tên hàm nhóm hành động 1: SalesOrder và cung cấp mô tả cho hàm.  
  * Nhóm hành động: Logistics-System. Tôi sẽ sử dụng nhóm hành động này để xử lý bất kỳ truy vấn nào liên quan đến thông tin logistics cho đơn hàng bán hàng.  
    * Tên nhóm hành động: Chọn tên cho nhóm hành động và đưa ra mô tả thân thiện với người dùng. Tôi đã đặt tên là Logistics-System.  
    * Loại nhóm hành động: Xác định bằng lược đồ API.  
    * Gọi nhóm hành động: Chọn hàm Lambda hiện có và chọn hàm Lambda đã tạo ở Bước 2, Logistics-System.  
    * Lược đồ nhóm hành động: Chọn lược đồ API hiện có.  
    * S3 URL: Tạo bucket S3 và tải tệp logistics.json từ kho GitHub lên bucket S3 và cung cấp URL S3 của bucket.  
* Bộ nhớ: Chọn Bật với thời gian bộ nhớ là 2 ngày và số phiên gần đây tối đa là 20\.  
* Cơ sở tri thức: Thêm các cơ sở tri thức đã tạo trước đó.  
  * Chọn cơ sở tri thức: SAP-external-knowledgebase.

Hướng dẫn cơ sở tri thức cho Agent: Sử dụng cơ sở tri thức này khi bạn cần thông tin bên ngoài hệ thống SAP và kết hợp với dữ liệu hệ thống SAP để hoàn thành phản hồi.

* Chọn cơ sở tri thức: General-Information-knowledgebase.

Hướng dẫn cơ sở tri thức cho Agent: Sử dụng cơ sở tri thức này để trả lời các câu hỏi kinh doanh chung từ người dùng mà không có sẵn từ hệ thống SAP.

* Chi tiết chiến lược điều phối – Điều phối mặc định. Các agent Bedrock cung cấp các mẫu lời nhắc mặc định, nhưng chúng có thể được tùy chỉnh để đáp ứng các yêu cầu cụ thể. Tôi sẽ tùy chỉnh các mẫu lời nhắc dưới đây để phù hợp với yêu cầu trường hợp sử dụng cụ thể của chúng ta.  
  * Tiền xử lý: Chọn Ghi đè mẫu tiền xử lý mặc định. Thêm phần dưới đây vào mẫu lời nhắc.

\- Danh mục F: Các câu hỏi có thể được trả lời hoặc hỗ trợ bởi agent gọi hàm của chúng ta bằng cách sử dụng các hàm đã cung cấp và các đối số từ lịch sử hội thoại hoặc các đối số liên quan mà nó có thể thu thập bằng hàm askuser VÀ cũng cần dữ liệu bên ngoài từ cơ sở tri thức để hoàn thành phản hồi. Kết hợp dữ liệu từ hệ thống SAP hoặc hệ thống Logistics không phải SAP và cơ sở tri thức bên ngoài để chuẩn bị câu trả lời cuối cùng

* Điều phối: Chọn Ghi đè mẫu điều phối mặc định. Thêm văn bản dưới đây vào các phần tương ứng trong mẫu lời nhắc.

$knowledge\_base\_guideline$

\- Nếu bất kỳ dữ liệu nào không được cập nhật trong hệ thống Logistics như ngày giao hàng, thì kiểm tra cơ sở tri thức có tên 'SAP-external-knowledgebase' để tìm thời gian giao hàng ước tính theo danh mục vận chuyển. Sau đó, xem xét thời gian đó và cộng vào ngày 'Đơn hàng Nhận được' và chia sẻ ngày giao hàng ước tính với người dùng.

\- Nếu hệ thống SAP báo lỗi do dữ liệu yêu cầu không có sẵn, kiểm tra cơ sở tri thức có tên 'SAP-external-knowledgebase' để tìm giải thích về MÃ LỖI. Chỉ trả lời người dùng với giải thích về mã lỗi.

$tools\_guidelines$ \[Phần này không tồn tại, chúng ta cần tạo nó\]

\- Chỉ gọi công cụ 'SAP-Sales-Order' cho bất kỳ câu hỏi nào liên quan đến đơn hàng bán hàng.

\- Chỉ gọi công cụ 'Logistics-System' cho bất kỳ chi tiết vận chuyển nào cho đơn hàng bán hàng.

\- KHÔNG gọi cả hai công cụ 'SAP-Sales-Order' và 'Logistics-System' trừ khi người dùng yêu cầu cả hai thông tin.

$multiple\_tools\_guidelines$ \[Phần này không tồn tại, chúng ta cần tạo nó\]

\- Nếu người dùng hỏi câu hỏi cần gọi nhiều hơn một công cụ. Gọi các công cụ từng cái một. Thu thập phản hồi từ cả hai công cụ và sau đó kết hợp chúng trước khi trả lời người dùng.

Ví dụ, nếu người dùng yêu cầu cả thông tin Đơn hàng Bán hàng và Logistics. Đầu tiên, lấy chi tiết Đơn hàng Bán hàng với công cụ Đơn hàng Bán hàng. Sau đó, lấy chi tiết logistics từ công cụ Logistics. Cuối cùng, kết hợp cả hai phản hồi thành một khi trả lời người dùng.

Sau khi nhập tất cả chi tiết, tôi sẽ Lưu và sau đó chọn Chuẩn bị để cập nhật các thay đổi mới nhất. Để điều hướng đến trang tổng quan agent, chọn Lưu và thoát.

Cuối cùng, tạo Bí danh để có một bản chụp nhanh hoặc phiên bản cụ thể của agent được sử dụng trong ứng dụng.

Chọn Tạo, cung cấp tên Bí danh với mô tả thân thiện với người dùng.

Chọn Tạo phiên bản mới và liên kết nó với bí danh này cho phiên bản với thông lượng mặc định là Theo yêu cầu.

Để biết thêm thông tin, xem *Tạo và cấu hình agent thủ công*.

**Đây là giao diện cuối cùng của tôi**

*![][image4]*

***![][image5]***

Bây giờ, tôi cần điều chỉnh các vai trò IAM cho hàm Lambda để Bedrock Agent có thể gọi chúng.

Thực hiện các bước tại *Sử dụng chính sách dựa trên tài nguyên cho Lambda* và gắn chính sách dựa trên tài nguyên sau vào hàm Lambda để cho phép Amazon Bedrock truy cập hàm Lambda cho các nhóm hành động của agent, thay thế các ${giá trị} khi cần thiết.

JSON  
{  
    "Version": "2012-10-17",  
    "Statement": \[  
        {  
            "Sid": "AccessLambdaFunction",  
            "Effect": "Allow",  
            "Principal": {  
                "Service": "bedrock.amazonaws.com"  
            },  
            "Action": "lambda:InvokeFunction",  
            "Resource": "arn:aws:lambda:${region}:${account-id}:function:function-name",  
            "Condition": {  
                "StringEquals": {  
                    "AWS:SourceAccount": "${account-id}"  
                },  
                "ArnLike": {  
                   "AWS:SourceArn": "arn:aws:bedrock:${region}:${account-id}:agent/${agent-id}"  
                }  
            }  
        }  
    \]

}

**Đây là chính sách của tôi**

*{ "Version": "2012-10-17", "Id": "default", "Statement": \[ { "Sid": "bedrock-agent-sales", "Effect": "Allow", "Principal": { "Service": "bedrock.amazonaws.com" }, "Action": "lambda:InvokeFunction", "Resource": "arn:aws:lambda:us-east-1:1234567xxxx:function:SAP-Sales-Order-Query", "Condition": { "StringEquals": { "AWS:SourceAccount": "1234567xxxx" }, "AWS:SourceArn": { "arn:aws:bedrock:us-east-1: 1234567xxxx:agent/VX5FAWE3OO" } } } \] }* 

**Bước 5 – Tạo giao diện người dùng với Microsoft Teams, Slack và Streamlit**

Bước này liên quan đến việc phát triển một giao diện người dùng cho phép người dùng tương tác với Bedrock Agent.

* **Microsoft Teams** – Tích hợp này yêu cầu truy cập vào cả MS Teams (với quyền phù hợp) và Amazon Q Developer trong ứng dụng trò chuyện. Amazon Q Developer trong ứng dụng trò chuyện (trước đây là AWS Chatbot) cho phép bạn tương tác với Bedrock Agents GenAI trong Microsoft Teams.

**Bước 1: Cấu hình truy cập ứng dụng**

Microsoft Teams được cài đặt và được quản trị viên tổ chức của bạn phê duyệt.

**Bước 2: Cấu hình kênh Teams**

Tạo một kênh chuẩn MS Teams hoặc sử dụng kênh hiện có và thêm Amazon Q Developer vào kênh. \[Lưu ý: Cần kênh chuẩn vì Microsoft Teams hiện không hỗ trợ Amazon Q Developer trong các kênh riêng tư\]

* Trong Microsoft Teams, tìm tên nhóm của bạn và chọn, sau đó chọn Quản lý nhóm.  
* Chọn Ứng dụng, sau đó chọn Thêm ứng dụng.  
* Nhập Amazon Q Developer vào thanh tìm kiếm để tìm Amazon Q Developer.  
* Chọn bot.  
* Chọn Thêm vào nhóm và hoàn thành lời nhắc.

**Bước 3: Cấu hình Amazon Q Developer cho client Teams**

Bước này cung cấp quyền truy cập cho Amazon Q Developer trong ứng dụng trò chuyện vào kênh MS Teams của bạn.

* Mở Amazon Q Developer trong ứng dụng trò chuyện trong bảng điều khiển AWS.  
* Trong Cấu hình client trò chuyện, chọn Microsoft Teams, sao chép và dán URL kênh Microsoft Teams mà chúng ta đã tạo ở bước trước, sau đó chọn Cấu hình. \[Bạn sẽ được chuyển hướng đến trang ủy quyền Teams để yêu cầu quyền truy cập thông tin của Amazon Q Developer\].  
* Trên trang ủy quyền Microsoft Teams, chọn Chấp nhận. Ở phía bên trái, giờ bạn sẽ thấy kênh Teams của bạn được liệt kê trong Microsoft Teams.

Tiếp theo, tôi sẽ liên kết kênh MS Teams với cấu hình của mình.

Trên trang chi tiết Teams trong bảng điều khiển Amazon Q Developer, chọn Cấu hình kênh mới. Tôi có các đầu vào dưới đây cho cấu hình của mình, giữ phần còn lại ở mặc định.

* Chi tiết cấu hình:  
  * Tên cấu hình: Chọn tên cho cấu hình của bạn. Tôi đã đặt tên là aws-sap-demos-team.  
* Kênh Microsoft Teams:  
  * URL kênh: Sao chép và dán URL kênh Microsoft Teams mà chúng ta đã tạo ở bước 2\.  
* Quyền:  
  * Cài đặt vai trò: Chọn Vai trò kênh.  
  * Vai trò kênh: Chọn Tạo vai trò IAM bằng mẫu.  
  * Tên vai trò: Chọn tên theo ý bạn. Tôi đã đặt tên là awschatbot-sap-genai-teams-role.  
  * Mẫu chính sách: Quyền truy cập Amazon Q Developer.  
  * Chính sách bảo vệ kênh \[Tên chính sách\]: AWSLambdaBasicExecutionRole, AmazonQDeveloperAccess. Bạn có thể điều chỉnh các chính sách IAM theo yêu cầu của mình, nhưng luôn khuyến nghị tuân theo thực tiễn quyền tối thiểu.

**Bước 4: Kết nối agent với kênh trò chuyện**

Kết nối Amazon Q Developer Bedrock Agent yêu cầu hành động IAM bedrock:InvokeAgent.

Thêm chính sách dưới đây vào vai trò IAM: awschatbot-sap-genai-teams-role đã tạo ở bước trước.

JSON  
{  
  "Sid": "AllowInvokeBedrockAgent",  
  "Effect": "Allow",  
  "Action": "bedrock:InvokeAgent",  
  "Resource": \[  
    "arn:aws:bedrock:aws-region:\<AWS Account ID\>:agent-alias/\<Bedrock Agent ID\>/\<Agent Alias ID\>/"  
  \]  
}

Để thêm Bedrock Agent vào kênh trò chuyện của bạn, nhập như sau. Chọn tên kết nối theo ý bạn.

@Amazon Q connector add connector\_name arn:aws:bedrock:aws-region:AWSAccountID:agent/AgentID AliasID

Mục nhập của tôi trông như thế này:

@Amazon Q connector add order\_assistant arn:aws:bedrock:us-east-1:xxxxxxx:agent/VX5FAWE3OO VG92WRF1JI

Để biết thêm thông tin, xem [Tutorial: Get started with Microsoft Teams](https://docs.aws.amazon.com/chatbot/latest/adminguide/teams-setup.html)

**Giao diện Teams trông như thế này**

*![][image6]*

* **Slack** – Tích hợp này yêu cầu truy cập vào cả Slack (với quyền phù hợp) và Amazon Q Developer trong ứng dụng trò chuyện. Amazon Q Developer trong ứng dụng trò chuyện (trước đây là AWS Chatbot) cho phép bạn tương tác với Bedrock Agents GenAI trong Slack.

**Bước 1: Cấu hình truy cập ứng dụng**

Quản trị viên không gian làm việc cần phê duyệt việc sử dụng ứng dụng Amazon Q Developer trong không gian làm việc.

**Bước 2: Cấu hình kênh Slack**

Tạo một kênh Slack hoặc sử dụng kênh hiện có và thêm Amazon Q Developer vào kênh Slack.

Trong kênh Slack của bạn, nhập /invite @Amazon Q và chọn Mời Họ.

**Bước 3: Cấu hình Amazon Q Developer cho client Slack**

Bước này cung cấp quyền truy cập cho Amazon Q Developer trong ứng dụng trò chuyện vào không gian làm việc Slack của bạn.

* Mở Amazon Q Developer trong ứng dụng trò chuyện trong bảng điều khiển AWS. Trong Cấu hình client trò chuyện, chọn Slack, sau đó chọn Cấu hình. \[Bạn sẽ được chuyển hướng đến trang ủy quyền Slack để yêu cầu quyền truy cập thông tin của Amazon Q Developer\].  
* Chọn không gian làm việc Slack mà bạn muốn sử dụng với Amazon Q Developer và chọn Cho phép.  
* Ở phía bên trái, giờ bạn sẽ thấy không gian làm việc Slack của bạn được liệt kê trong Slack.

Tiếp theo, tôi sẽ liên kết một kênh với cấu hình của mình.

Trên trang chi tiết Không gian làm việc trong bảng điều khiển Amazon Q Developer, chọn Cấu hình kênh mới. Tôi có các đầu vào dưới đây cho cấu hình của mình, giữ phần còn lại ở mặc định.

* Chi tiết cấu hình:  
  * Tên cấu hình: Chọn tên cho cấu hình của bạn. Tôi đã đặt tên là sap-genai-slack-chatbot.  
* Tùy chọn nội bộ Amazon:  
  * Phân loại tài khoản: Chọn Không phải sản xuất.  
* Kênh Slack:  
  * ID kênh: Cung cấp ID kênh của kênh Slack mà bạn đã cấu hình ở bước 2\.  
* Quyền:  
  * Cài đặt vai trò: Chọn Vai trò kênh.  
  * Vai trò kênh: Chọn Tạo vai trò IAM bằng mẫu.  
  * Tên vai trò: Chọn tên theo ý bạn. Tôi đã đặt tên là aws-sap-genai-chatbot-role.  
  * Mẫu chính sách: Quyền truy cập Amazon Q Developer.  
  * Chính sách bảo vệ kênh \[Tên chính sách\]: AWSLambdaBasicExecutionRole, AmazonQDeveloperAccess. Bạn có thể điều chỉnh các chính sách IAM theo yêu cầu của mình, nhưng luôn khuyến nghị tuân theo thực tiễn quyền tối thiểu.

**Bước 4: Kết nối agent với kênh trò chuyện**

Kết nối Amazon Q Developer Bedrock Agent yêu cầu hành động IAM bedrock:InvokeAgent.

Thêm chính sách dưới đây vào vai trò IAM: awschatbot-sap-genai-teams-role đã tạo ở bước trước.

JSON  
{  
  "Sid": "AllowInvokeBedrockAgent",  
  "Effect": "Allow",  
  "Action": "bedrock:InvokeAgent",  
  "Resource": \[  
    "arn:aws:bedrock:aws-region:\<AWS Account ID\>:agent-alias/\<Bedrock Agent ID\>/\<Agent Alias ID\>/"  
  \]  
}

Để thêm Bedrock Agent vào kênh trò chuyện của bạn, nhập như sau. Chọn tên kết nối theo ý bạn.

@Amazon Q connector add connector\_name arn:aws:bedrock:aws-region:AWSAccountID:agent/AgentID AliasID.

Mục nhập của tôi trông như thế này:

@Amazon Q connector add order\_assistant arn:aws:bedrock:us-east-1:xxxxxxx:agent/VX5FAWE3OO VG92WRF1JI

Để biết thêm thông tin, xem [Tutorial: Get started with Slack](https://docs.aws.amazon.com/chatbot/latest/adminguide/slack-setup.html#getting-started-prerequisites-slack)

**Giao diện Slack trông như thế này**  
**![][image7]**

* **Streamlit** – Streamlit là một khung Python mã nguồn mở thường được sử dụng để xây dựng các ứng dụng web tương tác cho các tập lệnh Python. Tôi đã thực hiện các bước dưới đây để lưu trữ ứng dụng trên một phiên bản Amazon EC2.  
* Khởi tạo một phiên bản EC2, tôi đã xem xét một phiên bản Amazon Linux t2.micro.  
* Thiết lập phiên bản EC2 với nhóm bảo mật cần thiết cho phép lưu lượng HTTP/HTTPS (cổng 80/443/8501 hoặc bất kỳ cổng nào khác bạn đã chọn sử dụng).  
* Chuẩn bị môi trường như sau:

**Cài đặt các gói cần thiết**

$sudo apt update

$sudo apt-get install python3-venv

**Thiết lập môi trường ảo**

$mkdir streamlit-demo

$cd streamlit-demo

$python3 \-m venv venv

$source venv/bin/activate

* Cài đặt Streamlit

$pip install streamlit

* Tạo một tệp có tên streamlit-app.py bằng trình chỉnh sửa Vi/Vim/nano và sao chép mã trong streamlit-app.py từ kho GitHub.  
* Chạy ứng dụng Streamlit với lệnh dưới đây

$nohup streamlit run streamlit-app.py &

* Chạy ứng dụng Streamlit ở chế độ nền với lệnh dưới đây

$nohup streamlit run streamlit-app.py &

* Streamlit gán cổng có sẵn từ 8501 tăng dần lên 1\. Nếu bạn muốn Streamlit sử dụng một cổng cụ thể, bạn có thể sử dụng lệnh dưới đây

$streamlit run streamlit-app.py \--server.port XXXX 

Sau khi chạy các lệnh trên, tôi có thể thấy URL để mở ứng dụng Streamlit trong trình duyệt của mình, như được hiển thị dưới đây.

**![][image8]**  
**Ứng dụng Streamlit trông như thế này**  
**![][image9]**

**Chi phí**

Việc vận hành các Mô hình Ngôn ngữ Lớn (LLMs) đòi hỏi cơ sở hạ tầng, phát triển và chi phí bảo trì đáng kể. Tuy nhiên, các dịch vụ AWS như Amazon Bedrock có thể giảm chi phí đáng kể thông qua quản lý cơ sở hạ tầng đơn giản hóa, quy trình phát triển được tối ưu, mô hình định giá linh hoạt và các tùy chọn tối ưu hóa chi phí khác nhau để truy cập các LLM theo lựa chọn của bạn.

| Dịch vụ AWS – US East (N. Virginia) | Chi phí | Ước tính \[chạy trong một giờ\] |
| ----- | ----- | ----- |
| Bedrock – Suy luận Mô hình Nền tảng LLM \[Claude 3.5 Sonnet\] | 100K Đầu vào, 200K Đầu ra | $3.3 |
| Bedrock – Suy luận Mô hình Nhúng \[Amazon Titan Text Embeddings v2\] | 100 tài liệu, trung bình 500 từ mỗi tài liệu | $0.10 |
| Đơn vị Tính toán OpenSearch (OCU) – Lập chỉ mục | 2 OCU \[tối thiểu 2 OCU\] | $0.48 |
| Đơn vị Tính toán OpenSearch (OCU) – Tìm kiếm và Truy vấn | 2 OCU \[tối thiểu 2 OCU\] | $0.48 |
| Lưu trữ Quản lý OpenSearch | 10GB | $0.24 |
| Phiên bản EC2 \[Ứng dụng Streamlit\] | t2.micro | $0.0116 |
| Lambda, Secrets Manager, DynamoDB |  | $0.2 |
| **Chi phí ước tính để sử dụng ứng dụng trong một giờ – $4.8116** |  |  |

Để biết thêm thông tin, xem *Giá [Amazon Bedrock pricing](https://aws.amazon.com/bedrock/pricing/), [Amazon OpenSearch Service Pricing](https://aws.amazon.com/opensearch-service/pricing/), [Amazon EC2 On-Demand Pricing](https://aws.amazon.com/ec2/pricing/on-demand/), [AWS Lambda pricing](https://aws.amazon.com/lambda/pricing/?trk=73f686c8-9606-40ad-852f-7b2bcafa68fe&sc_channel=ps&s_kwcid=AL!4422!3!651212652669!p!!g!!amazon%20lambda&ef_id=Cj0KCQjwxdXBBhDEARIsAAUkP6hN9YpfOSDCv7S4eeGxIrgdufbFC5HA-qPaLU19nhD4HLRN1LlWolwaApckEALw_wcB:G:s&s_kwcid=AL!4422!3!651212652669!p!!g!!amazon%20lambda!909122559!45462426916&gad_campaignid=909122559&gclid=Cj0KCQjwxdXBBhDEARIsAAUkP6hN9YpfOSDCv7S4eeGxIrgdufbFC5HA-qPaLU19nhD4HLRN1LlWolwaApckEALw_wcB), [AWS Secrets Manager pricing](https://aws.amazon.com/secrets-manager/pricing/), [Amazon DynamoDB pricing](https://aws.amazon.com/dynamodb/pricing/)*

**Kết luận**

Bài blog này thể hiện cách tạo một trợ lý ảo thông minh tương tác liền mạch với cả hệ thống SAP và không phải SAP bằng cách sử dụng các dịch vụ AWS, tập trung vào Amazon Bedrock. Giải pháp tích hợp các hệ thống SAP cho dữ liệu đơn hàng bán hàng, các hệ thống không phải SAP cho thông tin logistics, và cơ sở tri thức cho các chi tiết bổ sung, tất cả đều có thể truy cập thông qua nhiều giao diện người dùng bao gồm Streamlit, Microsoft Teams và Slack. Bằng cách tận dụng bộ dịch vụ AWS như Lambda, Bedrock, Secrets Manager và DynamoDB, việc triển khai cho phép tương tác ngôn ngữ tự nhiên với các hệ thống doanh nghiệp phức tạp, cung cấp quyền truy cập thống nhất vào các nguồn dữ liệu đa dạng trong khi duy trì bảo mật mạnh mẽ. Kiến trúc không máy chủ và mô hình định giá trả theo sử dụng làm cho giải pháp này trở nên dễ tiếp cận và hiệu quả về chi phí cho các tổ chức muốn nâng cao khả năng truy cập dữ liệu thông qua các giao diện AI hội thoại. Bài blog cung cấp một hướng dẫn chi tiết, từng bước để triển khai giải pháp này, mở đường cho các doanh nghiệp tận dụng AI tạo sinh trong môi trường SAP và không phải SAP của họ.

Hãy trải nghiệm thực tế trong việc chuyển đổi cách bạn tương tác với dữ liệu doanh nghiệp bằng cách triển khai giải pháp này. Đẩy nhanh quá trình chuyển đổi số của bạn bằng cách khám phá bộ dịch vụ học máy toàn diện của chúng tôi, bao gồm Amazon AgentCore (Xem trước) để triển khai và vận hành các agent AI an toàn ở quy mô lớn, Amazon Forecast cho phân tích dự đoán, Amazon Textract cho xử lý tài liệu thông minh, Amazon Translate cho dịch ngôn ngữ, và Amazon Comprehend cho xử lý ngôn ngữ tự nhiên. Những dịch vụ này tích hợp liền mạch với SAP để đáp ứng các nhu cầu kinh doanh khác nhau và mở ra những khả năng mới cho tổ chức của bạn.

Truy cập trang [AWS for SAP](https://aws.amazon.com/sap/) để tìm hiểu lý do tại sao hàng ngàn khách hàng tin tưởng AWS để di chuyển và đổi mới với SAP.

TAGS: [\#saponaws](https://aws.amazon.com/blogs/awsforsap/tag/saponaws/), [RISE with SAP](https://aws.amazon.com/blogs/awsforsap/tag/rise-with-sap/), [S/4HANA](https://aws.amazon.com/blogs/awsforsap/tag/s-4hana/), [SAP applications](https://aws.amazon.com/blogs/awsforsap/tag/sap-applications/), [SAP Beyond](https://aws.amazon.com/blogs/awsforsap/tag/sap-beyond/), [SAP transformation](https://aws.amazon.com/blogs/awsforsap/tag/sap-transformation/)

[image1]: /images/3-BlogsTranslated/blog1.hinh1.png
[image2]: /images/3-BlogsTranslated/blog1.hinh2.png
[image3]: /images/3-BlogsTranslated/blog1.hinh3.png
[image4]: /images/3-BlogsTranslated/blog1.hinh4.png
[image5]: /images/3-BlogsTranslated/blog1.hinh5.png
[image6]: /images/3-BlogsTranslated/blog1.hinh6.png
[image7]: /images/3-BlogsTranslated/blog1.hinh7.png
[image8]: /images/3-BlogsTranslated/blog1.hinh8.png
[image9]: /images/3-BlogsTranslated/blog1.hinh9.png
