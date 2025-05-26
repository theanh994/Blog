---
title: "Ôn luyện thi cuối kỳ"
date: "2025-04-28"
updated: "2025-04-28"
categories:
    - "Hệ thống phân tán"
    - "Distributed Systems"
coverImage: "/images/he-thong-phan-tan.png"
coverWidth: 16
coverHeight: 9
excerpt: 

---

## Câu 1: Sự khác nhau giữa Hệ thống tập trung, Phi tập trung và Phân tán

Trong lĩnh vực hệ thống máy tính, ba mô hình kiến trúc phổ biến là hệ thống tập trung, hệ thống phi tập trung và hệ thống phân tán. 

### 1. Hệ thống tập trung (Centralized System)

#### Định nghĩa:

Là hệ thống mà mọi xử lý và quản lý dữ liệu đều được thực hiện tại một điểm trung tâm duy nhất — thường là máy chủ.

#### Đặc điểm:

* Một máy chủ trung tâm xử lý toàn bộ.
* Máy khách phụ thuộc hoàn toàn vào máy chủ.
* Nếu máy chủ lỗi, hệ thống ngừng hoạt động.

#### Ví dụ:

* Hệ thống máy chủ nội bộ quản lý nhân sự trong doanh nghiệp nhỏ.
* Máy chủ xác thực đăng nhập duy nhất của một website.


### 2. Hệ thống phi tập trung (Decentralized System)

#### Định nghĩa:

Là hệ thống có nhiều nút xử lý, mỗi nút có thể hoạt động độc lập nhưng vẫn có thể chia sẻ dữ liệu hoặc đồng bộ với nhau.

#### Đặc điểm:

* Không có điểm trung tâm duy nhất.
* Một số nút có thể đảm nhận vai trò tương đương nhau.
* Chịu lỗi tốt hơn hệ thống tập trung.

#### Ví dụ:

* Hệ thống ngân hàng có các chi nhánh độc lập với máy chủ riêng.
* Hệ thống quản lý dữ liệu nội bộ của các bộ phận trong một tập đoàn lớn.


### 3. Hệ thống phân tán (Distributed System)

#### Định nghĩa:

Là hệ thống gồm nhiều máy tính kết nối mạng, phối hợp với nhau để thực hiện một tác vụ chung, dưới góc nhìn người dùng thì như một hệ thống thống nhất.

#### Đặc điểm:

* Các máy tính liên lạc qua mạng để phối hợp hoạt động.
* Không có điểm trung tâm duy nhất.
* Tính chịu lỗi và khả năng mở rộng cao.

#### Ví dụ:

* Google Search.
* Hệ thống blockchain như Bitcoin.
* Dịch vụ đám mây như AWS.

### 4. So sánh tổng quát

| Tiêu chí                   | Tập trung      | Phi tập trung          | Phân tán                |
| -------------------------- | -------------- | ---------------------- | ----------------------- |
| Điểm điều khiển trung tâm  | Có             | Không rõ ràng          | Không                   |
| Sự phụ thuộc vào trung tâm | Cao            | Trung bình             | Thấp                    |
| Tính chịu lỗi              | Thấp           | Tốt hơn                | Rất tốt                 |
| Khả năng mở rộng           | Hạn chế        | Tốt                    | Rất cao                 |
| Ví dụ                      | Máy chủ nội bộ | Ngân hàng đa chi nhánh | Google, Blockchain, AWS |

### 5. Cách xác định sự khác biệt

Để xác định một hệ thống thuộc loại nào, hãy trả lời các câu hỏi sau:

1. **Có một điểm điều khiển trung tâm không?**

   * Nếu có → Tập trung.

2. **Các nút có thể hoạt động độc lập khi một nút khác hỏng không?**

   * Nếu có → Không phải tập trung → Xét tiếp.

3. **Các nút có hợp tác, chia sẻ tài nguyên và hoạt động như một hệ thống thống nhất không?**

   * Nếu có → Phân tán.
   * Nếu không → Phi tập trung.

---

### 6. Tóm tắt

| Loại hệ thống | Từ khóa chính      | Ví dụ dễ hiểu                 |
| ------------- | ------------------ | ----------------------------- |
| Tập trung     | Máy chủ trung tâm  | Hệ thống nhân sự nội bộ       |
| Phi tập trung | Nhiều điểm đồng bộ | Mạng lưới chi nhánh ngân hàng |
| Phân tán      | Phối hợp qua mạng  | Google, Blockchain, AWS       |


## Câu 2: Các đặc tính của hệ phân tán là gì? 

Hệ thống phân tán là tập hợp các máy tính độc lập, được kết nối với nhau qua mạng và phối hợp để thực hiện các nhiệm vụ chung. 

### 1. Chia sẻ tài nguyên (Resource Sharing)

- Các máy trong hệ phân tán chia sẻ phần cứng và phần mềm (máy in, file, cơ sở dữ liệu...).
- Ưu điểm:
  - Giảm chi phí đầu tư
  - Tăng khả năng sẵn sàng
  - Hỗ trợ làm việc nhóm hiệu quả
- Thách thức:
  - Gia tăng rủi ro về bảo mật và an toàn thông tin

### 2. Tính trong suốt (Transparency)

- Người dùng không cần quan tâm đến sự phân tán vật lý của hệ thống.
- Các loại "trong suốt":
  - Truy cập: Che giấu cách biểu diễn và truy cập tài nguyên
  - Địa điểm: Ẩn vị trí thật của tài nguyên
  - Di trú: Tài nguyên có thể chuyển nơi mà không ảnh hưởng người dùng
  - Sao lưu: Dữ liệu có thể đến từ nhiều bản sao
  - Tương tranh: Nhiều người cùng truy cập mà không bị xung đột
  - Thứ lỗi: Che giấu lỗi và phục hồi
  - Bền vững: Giấu thông tin lưu trữ trên RAM hay đĩa

---

### 3. Tính mở (Openness)

- Cho phép tích hợp các thành phần từ nhiều nhà sản xuất khác nhau.
- Được mô tả bằng giao diện (IDL) thống nhất.
- Hệ phân tán mở thường có:
  - Tính khả chuyển (Portability)
  - Khả năng phối hợp (Interoperability)
  - Tính mở rộng và mềm dẻo

---

### 4. Tính co giãn (Scalability)

- Hệ thống có thể mở rộng về:
  - Số lượng người dùng/tài nguyên
  - Không gian địa lý
  - Quy mô tổ chức
- So sánh:
  - Mô hình tập trung dễ nghẽn cổ chai
  - Mô hình phân tán phức tạp hơn nhưng mở rộng tốt hơn

---

### 5. Các nguyên lý nền tảng kỹ thuật

Một số nguyên lý quan trọng hỗ trợ hệ phân tán:
- Kiến trúc hệ thống
- Liên lạc (Communication)
- Sao lặp & tính nhất quán
- Đồng bộ hóa
- Định danh (Naming)
- Chịu lỗi
- Bảo mật

## Câu 3: Mục Đích Của Nút Chủ Trong Hệ Phân Tán Và Hậu Quả Khi Nút Chủ Gặp Sự Cố

1. Trong một hệ thống phân tán, nút chủ (master node) là một nút có vai trò quản lý, điều phối và giám sát hoạt động của các nút khác (gọi là nút con hoặc nút công nhân - worker nodes). Nút chủ thường đảm nhận các chức năng quan trọng như:

Quản lý tài nguyên hệ thống (CPU, bộ nhớ, mạng,...).

Phân phối công việc hoặc dữ liệu tới các nút con.

Theo dõi trạng thái, hiệu suất và tình trạng lỗi của các nút trong hệ thống.

Ghi nhận nhật ký (logs) và duy trì thông tin trạng thái toàn cục.

Trong một số hệ thống (ví dụ Hadoop, Kubernetes), nút chủ còn quyết định lịch trình (scheduling) và phục hồi lỗi.

2. Mục đích Của nút Chủ
Nút chủ đóng vai trò trung tâm trong việc điều phối hoạt động của toàn hệ thống, bao gồm:

Điều phối công việc: Xác định công việc cần làm, phân chia và gán công việc cho các nút con thực hiện.

Quản lý dữ liệu hoặc luồng thông tin: Duy trì metadata (thông tin mô tả) hoặc bảng định tuyến.

Theo dõi tình trạng hệ thống: Ghi nhận lỗi, hiệu năng, và cảnh báo khi có sự cố.

Ra quyết định: Ví dụ chọn node lưu trữ dữ liệu, node thực thi, hoặc quyết định phục hồi.

3. Khi nút chủ gặp sự cố (ví dụ: hỏng phần cứng, mất kết nối, treo hệ thống), toàn bộ hệ thống phân tán có thể chịu nhiều ảnh hưởng nghiêm trọng:

a. Hệ thống bị đình trệ
Nút con không nhận được chỉ thị mới.

Công việc bị trì hoãn, không thể lập lịch thực thi tiếp.

b. Mất khả năng điều phối
Không có ai kiểm soát, theo dõi tình trạng các nút.

Việc phân phối hoặc cân bằng tải không được thực hiện.

c. Dữ liệu có thể không nhất quán
Nếu metadata hoặc bảng điều phối bị mất, dữ liệu có thể không được truy xuất đúng.

d. Giảm độ tin cậy hệ thống
Một điểm lỗi duy nhất (single point of failure) khiến hệ thống mất tính sẵn sàng.

4. Để giảm thiểu rủi ro khi nút chủ gặp sự cố, hệ thống phân tán thường áp dụng các giải pháp:

Sao lưu nút chủ (Backup Master): Có một bản sao dự phòng sẵn sàng chuyển đổi khi cần.

Tái cấu trúc hệ thống: Sử dụng kiến trúc leader election (ví dụ: sử dụng thuật toán Raft hoặc Paxos) để chọn nút chủ mới tự động.

Thiết kế phi tập trung: Không có nút chủ rõ ràng, mọi nút đều có thể điều phối (ví dụ: hệ thống ngang hàng - P2P).

## Câu 4: Trong một mạng không gian, tại sao các máy thường giao tiếp với nhau qua gossip protocol mà không gửi thông tin đến tất cả các máy khác hoặc gửi về một nút trung tâm

1. Vấn đề của việc gửi thông tin đến tất cả các máy hoặc về một nút trung ttâm
Trong một hệ thống phân tán lớn, nếu một nút cố gắng:

Gửi thông tin đến tất cả các máy khác (broadcast), hoặc

Gửi thông tin về một nút trung tâm duy nhất (central node)

thì sẽ gặp phải một số vấn đề nghiêm trọng:

a. Chi phí truyền thông cao (Scalability Issue)
Gửi thông tin cho tất cả các nút sẽ cần O(n) thông điệp, khiến mạng bị quá tải khi số lượng máy tăng lên.

Nút trung tâm nếu nhận thông tin từ tất cả các nút, cũng sẽ bị quá tải, làm cổ chai mạng.

b. Độ trễ và nghẽn mạng
Quá nhiều thông tin được gửi đồng thời gây tắc nghẽn hoặc tăng độ trễ toàn hệ thống.

c. Điểm lỗi trung tâm (Single Point of Failure)
Nếu một nút trung tâm bị lỗi, toàn bộ hệ thống sẽ mất khả năng liên lạc hoặc điều phối.

2. Giải Pháp: Giao Thức Gossip
Giao thức Gossip (hay còn gọi là rumor-mongering) là một cơ chế truyền thông phân tán, trong đó mỗi nút định kỳ chọn ngẫu nhiên một nút khác để truyền thông tin hoặc cập nhật trạng thái.
Cách thức này tương tự như cách tin đồn lan truyền trong xã hội.

Ưu điểm của giao thức Gossip:
a. Khả năng mở rộng cao (Scalability)
Thay vì gửi đến tất cả các máy, mỗi nút chỉ giao tiếp với một số ít nút khác trong mỗi vòng lặp.

Số lượng thông điệp tăng chậm hơn nhiều so với broadcast toàn mạng.

b. Phân tán hoàn toàn (Fully decentralized)
Không cần nút trung tâm, giảm rủi ro điểm lỗi duy nhất.

Dễ triển khai trên các hệ thống lớn, động (các nút có thể tham gia/rời khỏi mạng linh hoạt).

c. Dung sai lỗi cao (Fault-tolerance)
Nếu một số nút bị lỗi, thông tin vẫn có thể lan rộng qua các nút còn lại.

Giao thức vẫn hoạt động hiệu quả ngay cả khi có mất gói tin hoặc lỗi mạng cục bộ.

d. Lan truyền theo thời gian logarit
Dưới các điều kiện nhất định, toàn bộ mạng có thể cập nhật thông tin trong thời gian O(log n).

## Câu 5: Các yếu tố cốt lõi của một hệ phân tán là gì

1. Tính minh bạch (Transparency)
Tính minh bạch trong hệ phân tán giúp người dùng hoặc lập trình viên không cần biết chi tiết nội bộ hệ thống mà vẫn có thể tương tác hiệu quả. Có nhiều loại minh bạch, bao gồm:

Minh bạch vị trí (Location transparency): Người dùng không cần biết tài nguyên đang ở đâu.

Minh bạch truy cập (Access transparency): Cách truy cập tài nguyên từ xa giống như tài nguyên cục bộ.

Minh bạch di trú (Migration transparency): Tài nguyên có thể di chuyển mà không ảnh hưởng đến truy cập.

Minh bạch sao chép (Replication transparency): Nhiều bản sao nhưng người dùng chỉ thấy một.

Minh bạch lỗi (Failure transparency): Hệ thống có thể xử lý lỗi mà không làm gián đoạn dịch vụ.

2. Tính mở (Openness)
Hệ thống phân tán được xây dựng trên các giao thức và tiêu chuẩn mở.

Dễ dàng tích hợp, mở rộng hoặc thay thế các thành phần trong hệ thống.

Hỗ trợ khả năng tương tác giữa các hệ thống khác nhau (interoperability).

3. Khả năng mở rộng (Scalability)
Hệ thống phân tán phải có khả năng mở rộng theo:

Số lượng nút (size scalability): Có thể thêm nhiều máy vào hệ thống.

Khoảng cách địa lý (geographical scalability): Các nút có thể phân bố ở nhiều nơi khác nhau trên thế giới.

Khối lượng công việc (load scalability): Xử lý được lượng người dùng hoặc dữ liệu tăng lên.

4. Khả năng chịu lỗi (Fault Tolerance)
Hệ thống phải tiếp tục hoạt động ngay cả khi một số thành phần bị lỗi.

Cơ chế sao lưu, phục hồi, tái khởi động, và phân phối lại công việc được tích hợp.

Đây là một yêu cầu bắt buộc vì lỗi trong hệ phân tán xảy ra thường xuyên hơn so với hệ thống tập trung.

5. Đồng bộ và thời gian (Time and Synchronization)
Không có đồng hồ chung, vì vậy các hệ phân tán phải xử lý vấn đề đồng bộ hóa thời gian logic hoặc đồng bộ gần đúng.

Ví dụ: sử dụng thuật toán Lamport Clock, Vector Clock, hoặc NTP để đảm bảo thứ tự sự kiện.

6. Bảo mật (Security)
Vì hệ thống phân tán thường hoạt động qua mạng, nên bảo mật là vấn đề quan trọng.

Bao gồm: xác thực, phân quyền, mã hóa, phát hiện tấn công và an toàn dữ liệu.

7. Truyền thông (Communication)
Các nút trong hệ phân tán giao tiếp thông qua mạng bằng nhiều cơ chế: message passing, RPC (Remote Procedure Call), REST API, message queues, v.v.

Giao tiếp phải được thiết kế tối ưu, đáng tin cậy và có thể xử lý mất gói, trễ hoặc lỗi mạng.

## Câu 6: Nêu những lí do sử dụng hệ phân tán

Hệ phân tán (Distributed System) là mô hình hệ thống gồm nhiều máy tính độc lập phối hợp hoạt động để cung cấp một dịch vụ thống nhất cho người dùng. Việc sử dụng hệ phân tán mang lại nhiều lợi ích thiết thực, cả về hiệu suất, chi phí, độ tin cậy và khả năng mở rộng.

1. Chia sẻ tài nguyên
Các tài nguyên phần cứng (CPU, bộ nhớ, ổ cứng) và phần mềm (file, cơ sở dữ liệu, dịch vụ) có thể được chia sẻ giữa nhiều người dùng trong mạng.

Ví dụ: máy in dùng chung, hệ quản trị cơ sở dữ liệu phân tán, hệ thống lưu trữ cloud.

2. Tăng tính sẵn sàng và độ tin cậy
Khi một thành phần bị lỗi, hệ thống vẫn có thể tiếp tục hoạt động nhờ các nút sao lưu hoặc cơ chế phục hồi lỗi.

Hệ phân tán giúp tránh "single point of failure" – điểm lỗi duy nhất dễ gây sập toàn bộ hệ thống.

3. Hiệu năng cao hơn nhờ xử lý song song
Công việc có thể được chia nhỏ và thực hiện đồng thời trên nhiều nút, giúp tăng tốc độ xử lý.

Ví dụ: tính toán khoa học, xử lý dữ liệu lớn (big data), hệ thống MapReduce như Hadoop.

4. Khả năng mở rộng (Scalability)
Dễ dàng mở rộng hệ thống bằng cách thêm nút mới mà không cần thay đổi kiến trúc tổng thể.

Có thể mở rộng theo chiều ngang (thêm máy) thay vì chiều dọc (nâng cấp phần cứng).

5. Tính linh hoạt và phân bố địa lý
Các nút trong hệ phân tán có thể được đặt ở nhiều vị trí địa lý khác nhau, giúp:

Phân phối tải.

Phục vụ người dùng toàn cầu với độ trễ thấp hơn.

Tuân thủ các quy định địa phương về dữ liệu.

6. Tối ưu chi phí
Có thể sử dụng các máy rẻ tiền (commodity hardware) thay vì đầu tư một siêu máy tính đắt đỏ.

Giảm chi phí bảo trì hệ thống nhờ khả năng thay thế hoặc mở rộng linh hoạt.

7. Tính chịu lỗi và phục hồi
Hệ thống có thể tự phát hiện lỗi, cô lập nút bị lỗi và phục hồi bằng cách sử dụng các bản sao dự phòng (replicas) hoặc tái phân phối công việc.

8. Hỗ trợ phát triển các ứng dụng phân tán hiện đại
Rất nhiều hệ thống và dịch vụ hiện đại dựa trên kiến trúc phân tán:

Dịch vụ web và microservices

Cloud computing (AWS, Azure, GCP)

Blockchain, mạng P2P, hệ thống AI phân tán

## Câu 7: Nêu định nghĩa hệ phân tán

Hệ phân tán là một tập hợp các máy tính độc lập mà, đối với người dùng, nó
như thể một hệ thống đơn gắn kết.

## Câu 8: Chụp và để lên blog các hình của thuật toán Cristian, Berkeley, RBS, Lamport, Bully, Ring

Thuật toán Cristian
![Thuật toán Cristian](/images/Cristian.png)

Thuật toán Berkeley
![Thuật toán Berkeley](/images/Berkeley.png)

Thuật toán RBS
![Thuật toán RBS](/images/RBS.png)

Thuật toán Lamport
![Thuật toán Lamport](/images/Lamport.png)

Thuật toán Bully
![Thuật toán Bully](/images/Bully.png)

Thuật toán Ring
![Thuật toán Ring](/images/Ring.png)

## Câu 9:  Kỹ thuật phân tán nào hỗ trợ lập trình thủ tục, lập trình web, hướng đối tượng, liệt kê

| **Mô hình lập trình**               | **Kỹ thuật phân tán hỗ trợ**                                                                  |
|------------------------------------|-----------------------------------------------------------------------------------------------|
| **Lập trình thủ tục (Procedural)** | **RPC (Remote Procedure Call)** – gọi hàm từ xa như gọi hàm cục bộ qua mạng.                 |
| **Lập trình hướng đối tượng (OOP)**| **RMI (Remote Method Invocation)** – gọi phương thức trên đối tượng từ xa, phổ biến trong Java.|
| **Lập trình web**                  | **HTTP + REST API / SOAP / gRPC** – dùng các giao thức web để trao đổi dữ liệu giữa các hệ thống.|
| **Lập trình sự kiện / Message-driven** | **Message Queue (MQ), Publish/Subscribe** – ví dụ: Kafka, RabbitMQ, MQTT.              |

### RPC – Remote Procedure Call

- Cho phép một chương trình gọi hàm được thực thi trên một máy tính khác.
- Gần với lập trình thủ tục truyền thống.
- Giao diện đơn giản, dễ hiểu, ẩn đi chi tiết truyền thông mạng.

### RMI – Remote Method Invocation

- Hỗ trợ lập trình hướng đối tượng, cho phép gọi phương thức trên đối tượng từ xa.
- Dữ liệu và hành vi đều được phân phối.
- Phổ biến trong Java (Java RMI).

### Web-based Communication (REST, SOAP, gRPC)

- Hỗ trợ **lập trình web**, nơi các hệ thống trao đổi dữ liệu thông qua HTTP, JSON/XML hoặc Protobuf.
- REST đơn giản, phổ biến trong phát triển API hiện đại.
- SOAP có tính formal và hỗ trợ tốt giao thức phức tạp.
- gRPC tối ưu hiệu suất với binary format.

### Message Queue / Event-Driven (Kafka, RabbitMQ)

- Hỗ trợ mô hình lập trình sự kiện hoặc xử lý bất đồng bộ (asynchronous).
- Các thành phần trong hệ thống tương tác qua việc gửi/nhận thông điệp.

## Câu 10: Tiến trình nhẹ, tiến trình, luồng có những ưu điểm và nhược điểm gì, liệt kê. Khi một lời gọi hệ thống dừng thì đối với 3 loại như thế nào. Tiến trình nhẹ, tiến trình và luồng có mối quan hệ như thế nào với nhau và với chính nó?

### 1. Khái niệm

| Khái niệm | Mô tả |
|----------|------|
| **Tiến trình (Process)** | Là đơn vị thực thi độc lập có không gian địa chỉ riêng và tài nguyên riêng biệt. |
| **Luồng (Thread)** | Là đơn vị thực thi nhỏ hơn tiến trình, chia sẻ cùng không gian địa chỉ của tiến trình cha. |
| **Tiến trình nhẹ (Lightweight Process – LWP)** | Là một trừu tượng trung gian giữa process và thread, thường dùng trong hệ điều hành hỗ trợ đa luồng người dùng. |

### 2. Ưu điểm và Nhược điểm

| Đặc điểm | **Tiến trình (Process)** | **Tiến trình nhẹ (LWP)** | **Luồng (Thread)** |
|----------|----------------------------|----------------------------|----------------------|
| **Ưu điểm** | - Cách ly tốt, ổn định<br>- Dễ kiểm soát lỗi | - Tận dụng hiệu quả nhiều CPU<br>- Chia sẻ được tài nguyên | - Tạo và hủy nhanh<br>- Giao tiếp nhanh giữa các luồng |
| **Nhược điểm** | - Tốn tài nguyên<br>- Giao tiếp chậm (IPC) | - Phức tạp trong quản lý<br>- Cần hệ điều hành hỗ trợ | - Khó kiểm soát lỗi<br>- Một lỗi có thể ảnh hưởng toàn bộ tiến trình |

### 3. Khi một lời gọi hệ thống (system call) dừng thì:

| Tình huống | Ảnh hưởng |
|-----------|-----------|
| **Tiến trình** | Cả tiến trình bị chặn, không tiến hành xử lý thêm. |
| **Luồng** | Toàn bộ tiến trình (và các luồng khác) có thể bị ảnh hưởng nếu là luồng chính. |
| **Tiến trình nhẹ (LWP)** | LWP bị chặn, nhưng hệ thống có thể tiếp tục xử lý các LWP khác nếu được hỗ trợ. |

### 4. Mối quan hệ giữa Process – Thread – LWP

### Tiến trình và luồng:
- Một tiến trình có thể có **nhiều luồng**.
- Các luồng trong cùng một tiến trình **chia sẻ tài nguyên** (bộ nhớ, file descriptor,...).
- Nếu một luồng bị lỗi nghiêm trọng → **toàn bộ tiến trình có thể bị ảnh hưởng.**

### Tiến trình nhẹ (LWP):
- Là một **cầu nối giữa luồng người dùng và luồng kernel**.
- Trong một số hệ điều hành (như Solaris), **luồng người dùng được ánh xạ vào LWP**, sau đó LWP thực thi trên CPU như một đơn vị độc lập.
- Nhiều luồng người dùng có thể dùng chung một LWP, hoặc một-một, tùy vào mô hình ánh xạ (1-1, M-1, M-N).

## Câu 11: Mô hình client server là gì, vai trò của máy chủ và máy khách là gì.

Mô hình **Client-Server** (Khách – Chủ) là một mô hình kiến trúc trong hệ thống phân tán, trong đó:

- **Client (Máy khách)** là các thiết bị hoặc ứng dụng gửi yêu cầu (request) đến máy chủ để nhận dịch vụ hoặc tài nguyên.
- **Server (Máy chủ)** là hệ thống cung cấp dịch vụ, xử lý yêu cầu từ các client và trả về kết quả hoặc dữ liệu tương ứng.

Mô hình này phân tách rõ ràng giữa phần yêu cầu dịch vụ và phần cung cấp dịch vụ, giúp hệ thống có thể mở rộng, bảo trì dễ dàng và quản lý hiệu quả.

### Vai trò của máy chủ và máy khách

| Thành phần | Vai trò chính |
|------------|--------------|
| **Máy khách (Client)** | - Khởi tạo và gửi yêu cầu đến máy chủ.<br>- Nhận và xử lý dữ liệu hoặc kết quả trả về từ máy chủ.<br>- Thường là giao diện người dùng hoặc ứng dụng cuối. |
| **Máy chủ (Server)** | - Lắng nghe và nhận các yêu cầu từ máy khách.<br>- Xử lý các yêu cầu, thực hiện các tác vụ hoặc truy xuất tài nguyên.<br>- Trả kết quả hoặc dữ liệu về cho máy khách.<br>- Quản lý và điều phối tài nguyên hệ thống để phục vụ nhiều client cùng lúc. |

## Câu 12: Quá trình gọi thủ tục từ xa là gì

**Gọi thủ tục từ xa (RPC)** là một kỹ thuật trong hệ phân tán cho phép một chương trình (client) gọi và thực thi một thủ tục (procedure) hoặc hàm trên một máy khác (server) như thể nó đang gọi thủ tục cục bộ.

### Cách hoạt động cơ bản của RPC:

1. **Client gọi thủ tục**: Client gọi một thủ tục từ xa, truyền các tham số cần thiết.
2. **Gói đóng gói yêu cầu (Marshalling)**: Các tham số được đóng gói thành một thông điệp chuẩn để truyền qua mạng.
3. **Gửi yêu cầu qua mạng**: Thông điệp được gửi từ client đến server.
4. **Server nhận và giải đóng gói (Unmarshalling)**: Server nhận thông điệp và giải mã để lấy các tham số.
5. **Thực thi thủ tục trên server**: Server chạy thủ tục với các tham số nhận được.
6. **Đóng gói kết quả**: Kết quả được đóng gói thành thông điệp trả về.
7. **Gửi kết quả về client**: Server gửi thông điệp chứa kết quả về client.
8. **Client nhận và giải mã kết quả**: Client nhận và sử dụng kết quả như thể là kết quả trả về của một hàm cục bộ.

### Ưu điểm của RPC:

- Giúp lập trình viên thao tác với các thủ tục từ xa dễ dàng, giống như gọi thủ tục nội bộ.
- Ẩn đi chi tiết về mạng và truyền thông giữa các hệ thống.
- Hỗ trợ xây dựng các ứng dụng phân tán phức tạp một cách đơn giản hơn.

### Thách thức khi sử dụng RPC:

- Xử lý lỗi mạng (mất gói, trễ,...)
- Đồng bộ hoặc bất đồng bộ trong giao tiếp
- Đảm bảo tính nhất quán và an toàn trong môi trường phân tán

## Câu 13: Nêu mục đích và lợi ích của mô hình phân tầng giao thức, hướng thông điệp bền vững

### Mục đích và lợi ích của mô hình phân tầng giao thức

### Mục đích:

Mô hình phân tầng giao thức (protocol layering model) được xây dựng nhằm:

* **Tổ chức rõ ràng** các chức năng trong truyền thông mạng.
* **Phân tách trách nhiệm** giữa các tầng (layer), giúp dễ dàng thiết kế, bảo trì và phát triển hệ thống.
* **Chuẩn hóa giao tiếp** giữa các thiết bị và hệ thống khác nhau.
* **Tạo khả năng mở rộng**: thay đổi ở tầng này không ảnh hưởng đến tầng khác nếu tuân thủ đúng giao diện.

Ví dụ:

Hai mô hình phổ biến là **OSI** (7 tầng) và **TCP/IP** (4 tầng).

Lợi ích:

| Lợi ích                         | Mô tả                                                       |
| ------------------------------- | ----------------------------------------------------------- |
| **Tính mô-đun (Modularity)**    | Mỗi tầng có chức năng riêng biệt, dễ quản lý và thay thế.   |
| **Tính độc lập (Independence)** | Tầng cao không cần biết cách tầng dưới hoạt động chi tiết.  |
| **Dễ dàng chuẩn hóa**           | Giao thức có thể được định nghĩa rõ ràng và thống nhất.     |
| **Dễ phát triển và bảo trì**    | Lỗi dễ truy vết hơn vì từng tầng độc lập.                   |
| **Tái sử dụng**                 | Các tầng có thể tái sử dụng trong nhiều hệ thống khác nhau. |

Hướng thông điệp bền vững trong mô hình phân tầng

**Thông điệp bền vững (reliable message delivery)** là một trong các tiêu chí quan trọng trong thiết kế hệ thống phân tán.

### Cách mô hình phân tầng hỗ trợ truyền thông bền vững:

* **Tầng vận chuyển (Transport Layer)** trong mô hình TCP/IP (hoặc OSI) thường đảm nhận vai trò **đảm bảo độ tin cậy**:

  * **TCP**: đảm bảo truyền tin có kiểm soát lỗi, kiểm soát luồng, phân mảnh và sắp xếp lại gói tin.
  * **UDP**: không đảm bảo độ tin cậy, dùng cho các ứng dụng cần tốc độ cao hơn độ chính xác (như streaming).

### Lợi ích của hướng truyền thông bền vững:

* Đảm bảo dữ liệu không bị mất, bị trùng lặp hoặc sai lệch.
* Giúp các hệ thống phân tán giao tiếp chính xác và hiệu quả.
* Quan trọng trong các ứng dụng tài chính, y tế, hệ thống điều khiển phân tán,...

## Câu 14: Sharding là gì

Sharding là một kỹ thuật trong cơ sở dữ liệu và hệ thống phân tán dùng để chia nhỏ dữ liệu thành các phần (shard), mỗi phần được lưu trữ trên một máy chủ hoặc nút riêng biệt nhằm cải thiện hiệu năng, khả năng mở rộng và khả năng chịu lỗi.
### Cách hoạt động:

- Thay vì lưu toàn bộ dữ liệu trên một máy chủ, hệ thống chia nhỏ dữ liệu dựa trên một tiêu chí nhất định, như:
  - Giá trị khóa chính (user ID, region ID,...)
  - Băm (hash) của dữ liệu
  - Phân vùng theo thời gian

Mỗi shard chứa một phần của dữ liệu và hoạt động độc lập.

### Lợi ích của Sharding:

| Lợi ích | Mô tả |
|--------|-------|
| **Khả năng mở rộng cao** | Có thể thêm nhiều shard để chứa dữ liệu mới khi cần. |
| **Tăng hiệu suất** | Các truy vấn được phân tán, tránh quá tải một máy chủ. |
| **Chịu lỗi tốt hơn** | Nếu một shard gặp sự cố, các shard khác vẫn hoạt động. |
| **Quản lý dữ liệu lớn hiệu quả** | Hệ thống dễ quản lý hơn khi dữ liệu được phân chia. |

---

### Thách thức:

- **Phức tạp trong thiết kế**: cần xác định cách chia shard hợp lý.
- **Khó bảo trì và backup**: nhiều shard cần được quản lý đồng bộ.
- **Vấn đề khi join dữ liệu giữa các shard**: có thể chậm hoặc phức tạp.

## Câu 15: Các gói luồng có thế làm những nhiệm vụ gì?

Các **gói luồng** (thread packages hoặc thread libraries) là các thư viện/phần mềm hỗ trợ việc **tạo, quản lý và đồng bộ hóa luồng (thread)** trong một chương trình. Chúng cung cấp một giao diện lập trình cho việc sử dụng luồng trên các hệ điều hành khác nhau.


### Các nhiệm vụ chính mà các gói luồng có thể thực hiện:

| Nhiệm vụ | Mô tả |
|----------|-------|
| **Tạo luồng (Thread creation)** | Cho phép tạo và khởi động luồng mới để thực thi một đoạn mã đồng thời. |
| **Kết thúc luồng (Thread termination)** | Cho phép luồng kết thúc sau khi hoàn thành công việc hoặc bị hủy bởi chương trình. |
| **Chờ luồng kết thúc (Thread join)** | Cho phép một luồng đợi đến khi luồng khác hoàn thành để tiếp tục. |
| **Đồng bộ hóa (Synchronization)** | Cung cấp cơ chế như mutex, semaphore, barrier để tránh tranh chấp tài nguyên dùng chung giữa các luồng. |
| **Quản lý trạng thái luồng** | Hỗ trợ chuyển luồng giữa các trạng thái: chạy, chờ, bị khóa,... |
| **Ưu tiên và lập lịch (Scheduling)** | Một số gói hỗ trợ đặt mức ưu tiên cho luồng và kiểm soát lịch trình thực thi. |
| **Giao tiếp giữa các luồng** | Hỗ trợ trao đổi dữ liệu giữa luồng thông qua biến dùng chung hoặc hàng đợi (queue). |
| **Hủy luồng (Thread cancellation)** | Hỗ trợ dừng một luồng trong trường hợp cần thiết, có thể là tức thời hoặc an toàn. |

---

### Một số gói luồng phổ biến:

| Gói luồng | Nền tảng | Đặc điểm |
|-----------|----------|----------|
| **POSIX Threads (pthreads)** | Unix/Linux | Chuẩn POSIX, mạnh mẽ, dùng phổ biến trong C/C++. |
| **Java Threads** | Java | Tích hợp trong JVM, dễ dùng, hỗ trợ đa luồng. |
| **C++ std::thread** | C++11+ | Chuẩn hóa quản lý luồng trong C++. |
| **OpenMP** | C/C++/Fortran | Tập trung vào lập trình song song chia sẻ bộ nhớ. |
| **.NET Threads / Tasks** | .NET | Hỗ trợ lập trình đa luồng trong C#, F#, VB.NET. |
| **Python threading** | Python | Dễ dùng, nhưng bị giới hạn bởi GIL (Global Interpreter Lock). |

## Câu 16: Phân loại sự khác nhau giữa luồng kiểu người dùng và luồng kiểu nhân

Trong hệ điều hành, **luồng (thread)** có thể được triển khai theo hai cách phổ biến:

- **Luồng kiểu người dùng (User-level Thread - ULT)**
- **Luồng kiểu nhân (Kernel-level Thread - KLT)**

### So sánh:

| Tiêu chí | Luồng kiểu người dùng (ULT) | Luồng kiểu nhân (KLT) |
|----------|------------------------------|-------------------------|
| **Quản lý bởi** | Thư viện ở không gian người dùng | Hệ điều hành (kernel) |
| **Tốc độ chuyển đổi** | Nhanh (vì không cần gọi hệ thống) | Chậm hơn do phải chuyển sang kernel mode |
| **Khả năng tùy biến** | Dễ tùy chỉnh lịch trình bởi lập trình viên | Do hệ điều hành quyết định |
| **Tương tác với HĐH** | HĐH không biết về các ULT | HĐH quản lý toàn bộ KLT |
| **Chạy song song trên nhiều CPU** | Không (trừ khi ánh xạ qua KLT) | Có thể thực hiện song song thật sự |
| **Gọi hệ thống** | Nếu một ULT gọi hệ thống -> cả tiến trình bị chặn | Một luồng bị chặn không ảnh hưởng luồng khác |
| **Ví dụ** | POSIX user threads, Green threads (Java cũ) | Windows threads, Linux pthreads (thực hiện dưới dạng KLT) |

