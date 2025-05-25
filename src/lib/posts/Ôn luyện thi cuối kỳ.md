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
