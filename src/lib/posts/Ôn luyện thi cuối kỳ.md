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

## Câu 17: Các hàm chính trong RPC và chức năng

**RPC (Remote Procedure Call)** là cơ chế cho phép một tiến trình (client) gọi thực thi một thủ tục (procedure) nằm trên một máy khác (server) như thể nó gọi một hàm cục bộ.

---

### Các hàm chính trong RPC:

| Hàm | Vai trò | Mô tả chức năng |
|-----|----------|-----------------|
| **Client Stub** | Interface phía client | Chuẩn bị dữ liệu cho lời gọi từ client, đóng gói (marshal) các tham số vào một thông điệp RPC, gửi đến server stub. |
| **Server Stub** | Interface phía server | Nhận thông điệp từ client stub, giải mã (unmarshal) tham số, gọi thủ tục trên server, đóng gói kết quả gửi lại client. |
| **RPC Runtime** | Giao tiếp | Hỗ trợ truyền nhận thông điệp giữa client và server, quản lý lỗi, kết nối, timeout,... |
| **Procedure on Server** | Logic nghiệp vụ | Hàm hoặc thủ tục thật sự được thực thi trên phía server khi có lời gọi RPC. |
| **Binding Function** | Thiết lập liên kết | Dùng để kết nối client với server (có thể là tĩnh hoặc động) để biết được vị trí và thông tin máy chủ. |
| **Marshalling / Unmarshalling** | Đóng gói / Giải mã dữ liệu | Biến các tham số thành định dạng có thể truyền qua mạng và ngược lại. |
| **Transport Protocol** | Truyền thông | Giao thức như TCP hoặc UDP được sử dụng để truyền dữ liệu giữa client và server. |

---

### Tổng quan quá trình RPC:

1. **Client gọi hàm từ client stub** giống như gọi hàm bình thường.
2. **Client stub** đóng gói tham số và gửi qua mạng.
3. **RPC runtime** dùng giao thức mạng để gửi đến server.
4. **Server stub** giải mã, gọi thủ tục thật sự.
5. Kết quả được trả về theo hướng ngược lại.


## Câu 18: Định nghĩa các khái niệm: Tiến trình, Thread, Multithread Client, Multithread Server

### 1. Tiến trình (Process)

Là một chương trình đang được thực thi. Mỗi tiến trình là một đơn vị độc lập có:
- Không gian địa chỉ riêng
- Ngữ cảnh thực thi riêng
- Tài nguyên hệ thống riêng (file, bộ nhớ, ...)

Mỗi tiến trình hoạt động cách biệt với nhau, không chia sẻ bộ nhớ.


### 2. Luồng (Thread)

Là đơn vị thực thi nhỏ nhất bên trong một tiến trình. Các luồng trong cùng một tiến trình:
- Chia sẻ chung không gian địa chỉ và tài nguyên
- Có ngữ cảnh thực thi độc lập

Nhẹ hơn tiến trình vì không cần tạo không gian nhớ riêng biệt.

### 3. Multithread Client

Là client có khả năng khởi chạy nhiều luồng đồng thời để:
- Gửi nhiều yêu cầu cùng lúc
- Xử lý song song nhiều tác vụ (UI, mạng, xử lý dữ liệu, ...)

Giúp tăng hiệu suất và phản hồi nhanh hơn cho người dùng.

### 4. Multithread Server

Là server có khả năng tạo một luồng mới cho mỗi yêu cầu từ client:
- Mỗi luồng xử lý một kết nối hoặc một tác vụ cụ thể
- Cho phép xử lý nhiều client cùng lúc

Giảm thời gian chờ, tăng khả năng đáp ứng của hệ thống.

## Câu 19: Kiến Thức Cơ Bản về Map, Reduce và Mục Đích Trong Hệ Phân Tán

### 1. Khái niệm Cơ Bản

### **Map (Ánh xạ)**

- **Chức năng chính:** Nhận đầu vào là một cặp **(key, value)** và trả về một tập các cặp **(key, value)** khác.
- **Ý tưởng:** Biến đổi hoặc phân tách dữ liệu đầu vào thành dạng phù hợp để xử lý song song.

**Ví dụ đơn giản:**  
Tính số lần xuất hiện của mỗi từ trong văn bản.  
```
Đầu vào (1 dòng văn bản): "hello world"  
Map sẽ tạo: [("hello", 1), ("world", 1)]
```

### **Reduce (Rút gọn)**

- **Chức năng chính:** Nhận một **key** và danh sách các **value** tương ứng, sau đó tổng hợp chúng để cho ra kết quả cuối cùng.
- **Ý tưởng:** Tổng hợp dữ liệu đã nhóm theo key từ bước Map.

**Ví dụ tiếp theo:**
```
Đầu vào Reduce: ("hello", [1, 1, 1])  
Reduce tạo: ("hello", 3)
```

### 2. Mục Đích Trong Hệ Thống Phân Tán

Trong một hệ thống phân tán (distributed system), Map và Reduce là **mô hình lập trình song song** giúp xử lý **dữ liệu lớn (Big Data)** một cách hiệu quả. Cụ thể:

### **Tối ưu xử lý song song**
- Mỗi tác vụ `Map` có thể chạy độc lập trên các nút khác nhau.
- Dữ liệu được chia nhỏ và phân tán tự động.
- Tăng tốc độ xử lý đáng kể với khối lượng dữ liệu lớn.

### **Khả năng mở rộng tốt**
- Khi cần xử lý nhiều dữ liệu hơn, chỉ cần thêm nhiều máy hơn.
- Phù hợp với môi trường cloud hoặc cụm máy tính.

### **Tăng độ chịu lỗi**
- Nếu một nút xử lý `Map` hoặc `Reduce` bị lỗi, có thể tái thực hiện ở nút khác mà không ảnh hưởng toàn cục.
- Được hỗ trợ tốt bởi các framework như Hadoop, Spark.

### **Đơn giản hóa logic xử lý**
- Lập trình viên chỉ cần viết logic cho `Map` và `Reduce`.
- Việc phân tán, gom nhóm, đồng bộ, xử lý lỗi được hệ thống đảm nhiệm.

## Câu 20: Ảo Hóa (Virtualization) và Vai Trò Trong Hệ Phân Tán

### Ảo hóa là:

**Ảo hóa** là kỹ thuật tạo ra phiên bản ảo của một tài nguyên **phần cứng hoặc phần mềm**, như:
- Máy chủ (Server)
- Bộ nhớ (RAM)
- Thiết bị lưu trữ (Storage)
- Hệ điều hành (OS)
- Mạng (Network)

Thông qua **Hypervisor**, nhiều hệ thống ảo có thể cùng chia sẻ một máy vật lý.

#### Hypervisor gồm:
- **Type 1 (Bare Metal):** Chạy trực tiếp trên phần cứng (VD: VMware ESXi, Xen)
- **Type 2 (Hosted):** Chạy trên hệ điều hành (VD: VirtualBox)

---

### Mục đích của Ảo Hóa

- **Tối ưu tài nguyên phần cứng**
- **Dễ dàng quản lý và triển khai**
- **Tiết kiệm chi phí**
- **Tăng tính di động**
- **Cách ly an toàn giữa các hệ thống**


### Mục đích trong Hệ Thống Phân Tán

| Mục đích | Ý nghĩa trong hệ phân tán |
|---------|----------------------------|
| **Tách biệt môi trường thực thi** | Mỗi node có thể chạy nhiều máy ảo, mỗi máy phục vụ một dịch vụ riêng |
| **Khả năng mở rộng linh hoạt** | Khi cần thêm tài nguyên, chỉ cần tạo thêm máy ảo |
| **Quản lý tài nguyên hiệu quả** | Dễ phân phối tài nguyên theo nhu cầu từng ứng dụng |
| **Khôi phục và chịu lỗi tốt hơn** | VM có thể di chuyển sang node khác nếu node bị lỗi |
| **Tạo môi trường thử nghiệm/phát triển** | Mô phỏng nhiều node mà không cần nhiều máy vật lý |

## Câu 21: Kiến Trúc Server Đa Luồng


### Server đa luồng là:

Server đa luồng (**Multithreaded Server**) là mô hình trong đó mỗi yêu cầu của client được xử lý bởi một luồng riêng biệt. Mô hình này giúp server có thể xử lý **nhiều kết nối đồng thời**, cải thiện khả năng phản hồi và hiệu suất hệ thống.


### Các Kiến Trúc Server Đa Luồng Phổ Biến

### 1. **Thread per Connection (Một luồng mỗi kết nối)**

- Mỗi kết nối client được gán một luồng xử lý riêng.
- Đơn giản, dễ triển khai.

**Ưu điểm:**
- Dễ phát triển và debug.
- Tăng khả năng đáp ứng với nhiều client.

**Nhược điểm:**
- Tốn nhiều tài nguyên (mỗi kết nối là một thread).
- Không hiệu quả với hàng ngàn kết nối (vì context switching và chi phí tạo thread cao).


### 2. **Thread Pool (Bể luồng)**

- Một nhóm cố định các luồng được tạo sẵn.
- Mỗi yêu cầu được gán cho một luồng rảnh trong pool.

**Ưu điểm:**
- Giảm chi phí tạo/destroy thread.
- Kiểm soát tài nguyên tốt hơn.

**Nhược điểm:**
- Nếu tất cả thread đều bận, client phải chờ.
- Cần thiết kế hàng đợi yêu cầu hợp lý.


### 3. **Asynchronous + Threaded Hybrid**

- Sử dụng mô hình **event-driven** để xử lý kết nối I/O không đồng bộ.
- Dùng thread cho các tác vụ xử lý nặng (CPU-bound).

**Ưu điểm:**
- Tối ưu I/O và CPU cùng lúc.
- Hiệu quả cao cho hệ thống lớn.

**Nhược điểm:**
- Cấu trúc phức tạp, khó debug.
- Cần quản lý thread và event loop đồng thời.


### 4. **Reactor Pattern (Một luồng chính điều phối + đa luồng xử lý)**

- Một luồng chính lắng nghe sự kiện I/O (socket ready/read/write).
- Khi có sự kiện, giao cho thread xử lý tương ứng.

**Ưu điểm:**
- Phù hợp với ứng dụng thời gian thực (game server, chat server).
- Tăng hiệu suất bằng cách tách I/O và xử lý.

**Nhược điểm:**
- Cần quản lý đồng bộ giữa thread chính và các thread worker.


### So Sánh Tóm Tắt

| Mô hình | Ưu điểm | Nhược điểm |
|--------|----------|-------------|
| Thread per connection | Dễ cài đặt, phản hồi tốt | Tốn tài nguyên, không mở rộng tốt |
| Thread pool | Kiểm soát tốt tài nguyên | Có thể nghẽn nếu hết thread |
| Async + Threaded | Tối ưu cả I/O và CPU | Phức tạp khi triển khai |
| Reactor pattern | Hiệu quả, mở rộng tốt | Cần điều phối và đồng bộ phức tạp |

## Câu 22: Các Hướng Tiếp Cận Cài Đặt Luồng (Threading Approaches)

### 1. Kernel-Level Threads (Luồng cấp nhân)

### Đặc điểm:
- Được quản lý hoàn toàn bởi hệ điều hành (kernel).
- Mỗi luồng ánh xạ với một luồng thực thi (kernel thread).
- Hệ điều hành chịu trách nhiệm lập lịch và quản lý tài nguyên.

### Ưu điểm:
- Có thể chạy song song trên nhiều CPU.
- Hệ điều hành xử lý trực tiếp các sự kiện như blocking I/O.

###  Nhược điểm:
- Chi phí chuyển đổi ngữ cảnh cao hơn (context switching).
- Tạo/destroy thread tốn nhiều tài nguyên hơn.


### 2. User-Level Threads (Luồng cấp người dùng)

### Đặc điểm:
- Luồng được quản lý bởi **thư viện người dùng**, không cần kernel can thiệp.
- Hệ điều hành chỉ thấy 1 luồng (1 process).

### Ưu điểm:
- Tạo và quản lý thread nhanh chóng.
- Không cần gọi system call ⇒ tiết kiệm chi phí.

### Nhược điểm:
- Một luồng bị block thì **toàn bộ process** cũng bị block.
- Không tận dụng được đa lõi CPU hiệu quả.


### 3. Hybrid Threads (Mô hình kết hợp)

### Đặc điểm:
- Kết hợp luồng cấp người dùng và luồng cấp nhân.
- Mỗi kernel thread có thể xử lý nhiều user thread.

### Ưu điểm:
- Tận dụng được ưu điểm của cả hai mô hình trên.
- Cho phép lập lịch linh hoạt hơn.

### Nhược điểm:
- Thiết kế và quản lý phức tạp.
- Phải đồng bộ trạng thái giữa user và kernel thread.


### Tổng kết So Sánh

| Mô hình | Quản lý bởi | Ưu điểm | Nhược điểm |
|--------|-------------|----------|-------------|
| **Kernel-Level** | Hệ điều hành | Tận dụng đa lõi, quản lý tốt blocking | Tốn tài nguyên, chậm |
| **User-Level**   | Thư viện người dùng | Nhanh, nhẹ | Không tận dụng đa lõi, blocking ảnh hưởng toàn bộ |
| **Hybrid**       | Cả 2 | Linh hoạt, hiệu quả hơn | Phức tạp khi triển khai |

## Câu 23: Review Bảng Băm Phân Tán, Consistent Hashing và Finger Table


### 1. Tại sao sử dụng bảng băm phân tán?

- Trong hệ phân tán lớn, cần lưu trữ và truy xuất dữ liệu hiệu quả mà không phụ thuộc vào nút trung tâm.
- Bảng băm phân tán giúp:
  - Phân phối dữ liệu đều trên các nút.
  - Tra cứu nhanh dựa trên key.
  - Mở rộng linh hoạt khi thêm hoặc bớt nút.
  - Chịu lỗi tốt khi một số nút chết.

### 2. Mục đích của bảng băm phân tán

- Phân phối và lưu trữ dữ liệu phân tán mà không cần điều phối trung tâm.
- Cung cấp cơ chế tra cứu phân tán hiệu quả (thường O(log N)).
- Đảm bảo cân bằng tải và tính sẵn sàng cao.
- Quản lý mạng động khi nút thay đổi.


### 3. Consistent Hashing là gì?

- Kỹ thuật băm giúp giảm thiểu ảnh hưởng khi thêm/bớt nút.
- Key và nút được ánh xạ trên vòng băm (hash ring).
- Mỗi key gán cho nút gần nhất theo chiều kim đồng hồ.
- Khi nút thay đổi, chỉ một phần nhỏ key bị ảnh hưởng.

### 4. Tại sao cần Consistent Hashing?

- Tránh băm lại toàn bộ dữ liệu khi nút thay đổi.
- Hỗ trợ mở rộng linh hoạt và chịu lỗi tốt.


### 5. Finger Table là gì?

- Bảng nhỏ chứa các chỉ số (finger) trỏ tới các nút khác trên vòng băm.
- Khoảng cách các chỉ số theo lũy thừa 2.
- Giúp giảm số bước tra cứu key từ O(N) xuống O(log N).

### 6. Finger Table để làm gì?

- Giúp nút chuyển truy vấn đến nút gần key hơn nhanh chóng.
- Tăng tốc định tuyến trong DHT.

### 7. Tại sao sử dụng Finger Table?

- Tra cứu nhanh hơn so với duyệt tuần tự.
- Giúp mạng mở rộng và giữ thời gian tra cứu thấp.

## Câu 24: Review: Không gian phẳng, Định danh và đặc điểm của không gian phẳng


### 1. Không gian phẳng (Metric Space) là gì?

- Là một tập hợp \( M \) kèm theo một hàm khoảng cách (metric) \( d : M \times M \to \mathbb{R} \) thỏa mãn các tính chất:
  - \( d(x, y) \geq 0 \) (khoảng cách không âm)
  - \( d(x, y) = 0 \) khi và chỉ khi \( x = y \)
  - \( d(x, y) = d(y, x) \) (tính đối xứng)
  - \( d(x, z) \leq d(x, y) + d(y, z) \) (bất đẳng thức tam giác)

- Mô tả sự "cách biệt" giữa các điểm trong tập \( M \).

### 2. Định danh (Identifier) là gì?

- Là một giá trị hoặc chuỗi dùng để nhận dạng duy nhất một thực thể, đối tượng hoặc nút trong hệ thống.
- Định danh giúp phân biệt các phần tử khác nhau, dùng trong hệ phân tán, mạng, database,...
- Ví dụ: địa chỉ IP, UUID, tên người dùng,...


### 3. Đặc điểm của không gian phẳng (Metric Space)

- **Khoảng cách không âm:** Khoảng cách giữa hai điểm luôn ≥ 0.
- **Tính phân biệt:** Khoảng cách bằng 0 chỉ khi hai điểm trùng nhau.
- **Tính đối xứng:** Khoảng cách từ điểm A đến B bằng khoảng cách từ B đến A.
- **Bất đẳng thức tam giác:** Khoảng cách trực tiếp không lớn hơn tổng khoảng cách qua điểm trung gian.
- **Phù hợp cho đo lường và phân tích:** Dùng trong việc định nghĩa các khái niệm như lân cận, liên thông, cụm,...

## Câu 25: Đồng bộ hóa đồng hồ trong hệ phân tán


### 1. Tại sao cần đồng bộ hóa đồng hồ logic?

- Trong hệ phân tán, không có đồng hồ vật lý chung, các nút hoạt động độc lập.
- Cần thứ tự sự kiện nhất quán để:
  - Xác định thứ tự các sự kiện.
  - Phối hợp xử lý và giao tiếp chính xác giữa các tiến trình.
- Đồng hồ logic giúp thiết lập thứ tự tương đối giữa các sự kiện mà không cần đồng bộ thời gian tuyệt đối.


### 2. Tại sao đồng hồ vật lý không đảm bảo?

- Đồng hồ vật lý của mỗi nút:
  - Có thể lệch nhau do sai số bộ dao động.
  - Bị trôi (drift) theo thời gian.
  - Độ trễ mạng gây chênh lệch khi đồng bộ.
- Do đó, không thể hoàn toàn tin tưởng vào thời gian vật lý để định thứ tự sự kiện trong hệ phân tán.


### 3. Mục đích của đồng bộ hóa

- Đảm bảo thứ tự các sự kiện trong hệ phân tán được xác định rõ ràng.
- Giúp phối hợp hoạt động, tránh xung đột và đồng nhất dữ liệu.
- Hỗ trợ phát hiện lỗi và đồng nhất trạng thái hệ thống.


### 4. Các thuật toán đồng bộ hóa đồng hồ phổ biến

### 4.1. Thuật toán Lamport (Lamport Logical Clock)

- Mỗi nút giữ một bộ đếm logic.
- Tăng bộ đếm trước khi phát sinh sự kiện.
- Gửi timestamp kèm thông điệp.
- Khi nhận thông điệp, cập nhật bộ đếm lớn hơn giữa bộ đếm hiện tại và timestamp nhận được.
- Thiết lập thứ tự "ít nhất" giữa các sự kiện.

### 4.2. Vector Clock

- Mỗi nút giữ một vector đếm, kích thước bằng số nút trong hệ.
- Cập nhật vector khi sự kiện xảy ra hoặc nhận thông điệp.
- Cho phép xác định chính xác mối quan hệ thứ tự giữa các sự kiện: trước, sau hoặc song song.

### 4.3. Thuật toán đồng bộ hóa đồng hồ vật lý

- Ví dụ như NTP (Network Time Protocol).
- Cố gắng đồng bộ hóa đồng hồ vật lý giữa các nút.
- Giảm sai số nhưng không thể hoàn toàn loại bỏ chênh lệch.

## Câu 26: Đồng hồ Lamport


### 1. Đồng hồ Lamport giải quyết vấn đề gì?

- Trong hệ phân tán, không có đồng hồ vật lý đồng bộ tuyệt đối, nên khó xác định thứ tự tuyệt đối các sự kiện.
- Vấn đề chính: **xác định thứ tự tương đối các sự kiện** (trước, sau hay song song) để đảm bảo tính nhất quán trong hệ phân tán.
- Đồng hồ Lamport cung cấp cách đánh dấu thời gian logic giúp:
  - Thiết lập thứ tự tổng quát (partial order) giữa các sự kiện.
  - Giúp đồng bộ hóa, phối hợp các tiến trình và giải quyết các vấn đề liên quan đến thứ tự sự kiện.

### 2. Các quy tắc (Rules) của đồng hồ Lamport

Giả sử mỗi tiến trình \( P_i \) có một bộ đếm đồng hồ logic \( C_i \), ban đầu \( C_i = 0 \).

### Rule 1: Tăng đồng hồ cho sự kiện nội bộ

- Trước khi tiến trình \( P_i \) thực hiện bất kỳ sự kiện nào (gửi, nhận hay nội bộ), tăng đồng hồ:
  \[
  C_i = C_i + 1
  \]

### Rule 2: Gửi thông điệp

- Khi tiến trình \( P_i \) gửi thông điệp, gán timestamp bằng đồng hồ logic hiện tại của nó (sau khi tăng theo Rule 1).
- Thông điệp sẽ mang timestamp này.

### Rule 3: Nhận thông điệp

- Khi tiến trình \( P_j \) nhận thông điệp với timestamp \( T \):
  \[
  C_j = \max(C_j, T) + 1
  \]
- Đồng hồ logic được cập nhật thành lớn hơn cả giá trị hiện tại và timestamp nhận được, đảm bảo thứ tự logic.


### 3. Ý nghĩa

- Thứ tự logic giữa các sự kiện được duy trì.
- Giúp xác định mối quan hệ "trước" và "sau" (happened-before).
- Không đảm bảo thứ tự tuyệt đối trên toàn hệ thống, nhưng đảm bảo tính nhất quán cho các sự kiện có liên hệ.

## Câu 27:
## Câu 28: Giao thức đồng bộ thời gian NTP và PTP


### 1. NTP (Network Time Protocol) là gì?

- NTP là giao thức dùng để **đồng bộ hóa đồng hồ hệ thống** trên các máy tính qua mạng IP.
- Mục đích: Đảm bảo các nút trong mạng có cùng chuẩn thời gian chính xác.
- NTP sử dụng mô hình phân cấp server-client (stratum) để truyền thời gian chuẩn từ server cấp cao đến các client.

### Cách tính toán thời gian trong NTP

- NTP sử dụng 4 mốc thời gian (timestamps) trong quá trình đồng bộ:

| Mốc thời gian          | Ý nghĩa                         |
|-----------------------|---------------------------------|
| \( T_1 \)             | Thời gian client gửi yêu cầu    |
| \( T_2 \)             | Thời gian server nhận yêu cầu   |
| \( T_3 \)             | Thời gian server gửi phản hồi   |
| \( T_4 \)             | Thời gian client nhận phản hồi  |

- Tính **độ trễ (delay)**:
  \[
  \text{delay} = (T_4 - T_1) - (T_3 - T_2)
  \]

- Tính **độ lệch (offset)** giữa đồng hồ client và server:
  \[
  \text{offset} = \frac{(T_2 - T_1) + (T_3 - T_4)}{2}
  \]

- Client điều chỉnh đồng hồ của mình dựa trên offset, giảm sai số thời gian.


### 2. PTP (Precision Time Protocol) là gì?

- PTP là giao thức đồng bộ thời gian chính xác cao được chuẩn hóa trong IEEE 1588.
- Dùng nhiều trong các hệ thống yêu cầu độ chính xác cực kỳ cao (ví dụ: mạng công nghiệp, viễn thông, tài chính).
- PTP hoạt động qua việc gửi các thông điệp đồng bộ và điều chỉnh thời gian trên các thiết bị trong mạng.

### Cách tính toán trong PTP

- PTP cũng sử dụng 4 mốc thời gian tương tự NTP (\( T_1, T_2, T_3, T_4 \)) để tính toán delay và offset.
- Thời gian delay và offset được tính toán giống NTP:
  \[
  \text{delay} = (T_4 - T_1) - (T_3 - T_2)
  \]
  \[
  \text{offset} = \frac{(T_2 - T_1) + (T_3 - T_4)}{2}
  \]
- Điểm khác biệt là PTP thường chạy trên mạng LAN, hỗ trợ phần cứng timestamping để tăng độ chính xác.


### 3. So sánh NTP và PTP

| Tiêu chí          | NTP                         | PTP                            |
|-------------------|-----------------------------|--------------------------------|
| Độ chính xác       | Khoảng vài ms               | Từ nanosecond đến microsecond  |
| Môi trường sử dụng | Mạng Internet, WAN          | Mạng LAN, môi trường công nghiệp|
| Cách timestamp    | Phần mềm                    | Hỗ trợ phần cứng               |

