---
title: "Bài tập 1 – Tìm hiểu RabbitMQ"
date: "2025-05-11"
updated: "2025-05-11"
categories:
  - "Hệ thống phân tán"
  - "Distributed Systems"
coverImage: "/images/rabbitmq-cover.png"
coverWidth: 16
coverHeight: 9
---

# BÀI TẬP 1 – TÌM HIỂU DỊCH VỤ TRUYỀN THÔNG ĐIỆP: RABBITMQ

---

## Mô tả bài tập
> Tìm hiểu cơ chế, chức năng và cài đặt một trong các dịch vụ truyền thông điệp như RabbitMQ, Kafka, ActiveMQ, Redis Pub/Sub, Google Pub/Sub,... (Viết thành báo cáo)

---

## Dịch vụ được chọn: **RabbitMQ**

RabbitMQ là một message broker mã nguồn mở, sử dụng giao thức AMQP, hỗ trợ giao tiếp bất đồng bộ giữa các tiến trình trong hệ thống phân tán.

---

## Kiến trúc tổng quan

RabbitMQ bao gồm các thành phần:

- **Producer**: tiến trình gửi thông điệp.
- **Exchange**: định tuyến thông điệp đến các hàng đợi.
- **Queue**: lưu trữ thông điệp.
- **Consumer**: tiến trình nhận và xử lý thông điệp.
- **Broker**: thực thể trung tâm điều phối (RabbitMQ server).

```plaintext
Producer --> Exchange --> Queue --> Consumer
```

---

## Cơ chế hoạt động

### Các loại Exchange:
- `Direct`: định tuyến theo khóa chính xác.
- `Fanout`: gửi tới tất cả các hàng đợi liên kết.
- `Topic`: định tuyến theo mẫu (pattern).
- `Headers`: dùng thông tin header để định tuyến.

Quy trình:
1. Producer gửi message tới Exchange.
2. Exchange định tuyến message tới Queue.
3. Consumer lắng nghe và xử lý message.

---

## Chức năng chính

- Giao tiếp bất đồng bộ
- Quản lý hàng đợi tin cậy (durable)
- Giao diện Web UI dễ sử dụng
- Cơ chế xác nhận và lưu trữ thông điệp
- Hỗ trợ clustering và HA (High Availability)

---

## Cài đặt RabbitMQ trêntrên Docker

### Bước 1: Tải image

```bash
docker pull rabbitmq:3-management
```

### Bước 2: Chạy container (viết 1 dòng nếu dùng PowerShell)

```bash
docker run -d --hostname rabbitmq-host --name rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:3-management
```

### Bước 3: Truy cập giao diện

- Truy cập: [http://localhost:15672](http://localhost:15672)
- Tài khoản:
  - Username: `guest`
  - Password: `guest`

---

## Kiểm tra hoạt động

- Truy cập Web UI
- Tạo queue mới
- Gửi và nhận message thử qua lệnh hoặc đoạn code đơn giản

---

## Kết luận

RabbitMQ là một message broker mạnh mẽ và phổ biến, phù hợp với các hệ thống cần giao tiếp bất đồng bộ, hiệu quả và có độ tin cậy cao. Việc triển khai bằng Docker giúp tiết kiệm thời gian cấu hình và dễ dàng thử nghiệm.

---

## Tài liệu tham khảo

- [https://www.rabbitmq.com](https://www.rabbitmq.com)
- [https://hub.docker.com/_/rabbitmq](https://hub.docker.com/_/rabbitmq)
- [https://www.rabbitmq.com/tutorials/tutorial-one-python.html](https://www.rabbitmq.com/tutorials/tutorial-one-python.html)

# BÀI TẬP 2 – CÀI ĐẶT HỆ THỐNG SỬ DỤNG RABBITMQ

---

## Mục tiêu
Xây dựng một hệ thống đơn giản mô phỏng mô hình **Producer–Consumer** sử dụng RabbitMQ:
- **Producer** gửi thông điệp từ người dùng.
- **Consumer** nhận và hiển thị thông điệp.

---

## Công cụ và công nghệ

| Thành phần     | Công nghệ sử dụng         |
|----------------|---------------------------|
| Message broker | RabbitMQ (Docker)         |
| Ngôn ngữ        | Python 3                  |
| Thư viện        | `pika` (RabbitMQ client) |

---

## Bước 1: Cài đặt thư viện Python

```bash
pip install pika
```

---

## Bước 2: Code producer (Gửi thông điệp)

Tạo file `producer.py`:

```python
import pika

connection = pika.BlockingConnection(pika.ConnectionParameters('localhost'))
channel = connection.channel()
channel.queue_declare(queue='hello')

message = input("Nhập thông điệp để gửi: ")
channel.basic_publish(exchange='', routing_key='hello', body=message.encode())

print(f"✔ Đã gửi: {message}")
connection.close()
```

---

## Bước 3: Code consumer (Nhận thông điệp)

Tạo file `consumer.py`:

```python
import pika

connection = pika.BlockingConnection(pika.ConnectionParameters('localhost'))
channel = connection.channel()
channel.queue_declare(queue='hello')

def callback(ch, method, properties, body):
    print(f"📨 Nhận được: {body.decode()}")

channel.basic_consume(queue='hello', on_message_callback=callback, auto_ack=True)

print('⏳ Chờ nhận thông điệp... Nhấn Ctrl+C để thoát.')
channel.start_consuming()
```

---

## Bước 4: Chạy thử chương trình

1. Mở terminal và chạy `consumer.py`:
```bash
python consumer.py
```

2. Mở terminal khác và chạy `producer.py`:
```bash
python producer.py
```

Nhập một thông điệp bất kỳ và xem kết quả ở cửa sổ consumer.

---

## Kết quả mong đợi

- Gửi được thông điệp từ producer → queue RabbitMQ.
- Consumer nhận và hiển thị thông điệp ngay lập tức.
![Mô phỏng kết quả](./images/ketqua-rabbitmq.png)

---
