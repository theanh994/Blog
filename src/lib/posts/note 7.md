---
title: "Các kiến trúc trong HPT"
date: "2025-06-01"
updated: "2025-06-01"
categories:
  - "Hệ thống phân tán"
  - "Distributed Systems"
coverImage: "/images/he-thong-phan-tan.png" 
coverWidth: 16
coverHeight: 9
excerpt: Bài tập Note 7.
---

## Bìa tập 1: So sánh và liên hệ giữa các giao thức HTTP, TCP/IP, UDP, REST, GraphQL, SOAP, AJAX, RPC, gRPC

### Phân loại theo tầng giao thức

| Giao thức | Tầng hoạt động | Mục đích |
|-----------|----------------|----------|
| TCP, UDP  | Transport Layer | Truyền dữ liệu giữa máy |
| IP        | Network Layer   | Định tuyến gói tin |
| HTTP      | Application Layer | Giao tiếp web |
| RPC, gRPC | Application Layer | Gọi hàm từ xa |
| REST, SOAP, GraphQL, AJAX | Dựa trên HTTP | API hoặc giao tiếp client-server |


### Tóm tắt từng giao thức

### 1. TCP (Transmission Control Protocol)
- Tầng: Giao vận (Transport)
- Mục đích: Giao tiếp đáng tin cậy, có kiểm soát lỗi, theo thứ tự.
- Ứng dụng: Web, email, SSH, FTP.
- Quan hệ: HTTP hoạt động trên TCP.

### 2. UDP (User Datagram Protocol)
- Tầng: Giao vận
- Mục đích: Giao tiếp không cần xác nhận, nhanh, không tin cậy.
- Ứng dụng: Streaming video, game online, DNS.

### 3. IP (Internet Protocol)
- Tầng: Mạng
- Mục đích: Định tuyến gói tin đến đích.
- Quan hệ: TCP và UDP hoạt động trên IP.

### 4. HTTP (HyperText Transfer Protocol)
- Tầng: Ứng dụng
- Mục đích: Truyền dữ liệu web (HTML, JSON,...).
- Quan hệ: HTTP thường dùng TCP để truyền tải.

### 5. AJAX (Asynchronous JavaScript and XML)
- Tầng: Ứng dụng (client-side kỹ thuật)
- Mục đích: Gửi HTTP request không đồng bộ từ trình duyệt.
- Quan hệ: AJAX sử dụng HTTP, thường với REST hoặc GraphQL.

### 6. REST (Representational State Transfer)
- Tầng: Giao tiếp API (trên HTTP)
- Mục đích: Thiết kế API đơn giản, dạng tài nguyên URL, CRUD (GET, POST, PUT, DELETE).
- Quan hệ: Một kiểu kiến trúc sử dụng HTTP.

### 7. SOAP (Simple Object Access Protocol)
- Tầng: Giao tiếp API (trên HTTP, SMTP)
- Mục đích: Trao đổi dữ liệu XML có cấu trúc, hỗ trợ bảo mật, giao dịch.
- Quan hệ: API phức tạp hơn REST, nhưng mạnh mẽ hơn.

### 8. GraphQL
- Tầng: Giao tiếp API (thường trên HTTP)
- Mục đích: Truy vấn dữ liệu theo cấu trúc cần thiết, tránh dư thừa.
- Quan hệ: Thay thế REST trong một số hệ thống hiện đại.

### 9. RPC (Remote Procedure Call)
- Tầng: Ứng dụng
- Mục đích: Gọi hàm từ xa như gọi hàm cục bộ.
- Quan hệ: Là cơ sở của gRPC, RMI, CORBA, DCOM.

### 10. gRPC (Google RPC)
- Tầng: Ứng dụng
- Mục đích: Gọi hàm từ xa với hiệu suất cao (dùng HTTP/2 và Protobuf).
- Quan hệ: Kế thừa từ RPC, hiệu quả hơn REST trong microservices.

---

### Mối liên hệ giữa các giao thức

```
IP
 └── TCP/UDP
      ├── TCP → HTTP
      │       ├── REST / SOAP / GraphQL
      │       └── AJAX (client-side HTTP)
      └── UDP → Truyền không tin cậy (Video, Game, DNS)
          └── ít dùng cho API

RPC
 ├── Truyền dữ liệu nhị phân (tùy implement)
 └── gRPC (HTTP/2 + Protobuf)

HTTP
 ├── REST
 ├── SOAP
 ├── GraphQL
 └── AJAX (client)
```

---

### Tóm tắt theo mục đích sử dụng

| Giao thức | Mục đích chính | Ưu điểm | Nhược điểm |
|-----------|----------------|---------|------------|
| TCP       | Truyền tin cậy | Đảm bảo thứ tự, kiểm tra lỗi | Chậm hơn UDP |
| UDP       | Truyền nhanh   | Tốc độ cao | Không đảm bảo tin cậy |
| HTTP      | Giao tiếp web | Phổ biến, dễ dùng | Truyền qua text, không tối ưu |
| REST      | API đơn giản   | Linh hoạt, dễ hiểu | Không chuẩn hóa sâu |
| SOAP      | API phức tạp   | Bảo mật, giao dịch | Nặng, dùng XML |
| GraphQL   | API hiệu quả   | Truy vấn linh hoạt | Học khó hơn REST |
| AJAX      | Giao tiếp nền (frontend) | Mượt, không tải lại trang | Phụ thuộc JS |
| RPC       | Gọi hàm từ xa | Gần gũi OOP | Khó mở rộng qua internet |
| gRPC      | RPC hiện đại   | Nhanh, hỗ trợ đa ngôn ngữ | Yêu cầu HTTP/2 |

---


## Bài tập 2: Nghiên cứu về thư viện OPENMPI

### Nghiên cứu OpenMPI và giải bài toán tính 10 triệu số nguyên tố đầu tiên

### Giới thiệu về OpenMPI

**OpenMPI** (Open Message Passing Interface) là một thư viện giao tiếp song song cho lập trình phân tán. Nó cho phép các tiến trình chạy trên nhiều máy hoặc nhiều lõi xử lý có thể giao tiếp với nhau thông qua các hàm truyền thông tuân theo chuẩn **MPI (Message Passing Interface)**.

### Tính năng chính của OpenMPI

| Tính năng | Mô tả |
|----------|-------|
| Giao tiếp phân tán | Gửi/nhận dữ liệu giữa các tiến trình ở các máy khác nhau |
| Chia công việc | Phân mảnh bài toán để thực hiện đồng thời |
| Đồng bộ hóa | Chờ đồng bộ, hàng rào (barrier), broadcast, reduce |
| Hỗ trợ cluster và multicore | Chạy song song trên cả nhiều máy và nhiều nhân |
| Khả năng mở rộng | Từ vài đến hàng nghìn tiến trình |

### Một số hàm MPI phổ biến

| Hàm | Mục đích |
|-----|----------|
| `MPI_Init()` | Khởi tạo môi trường MPI |
| `MPI_Comm_rank()` | Lấy ID của tiến trình hiện tại |
| `MPI_Comm_size()` | Lấy tổng số tiến trình |
| `MPI_Send()` / `MPI_Recv()` | Gửi/nhận dữ liệu giữa các tiến trình |
| `MPI_Bcast()` | Phát dữ liệu từ một tiến trình đến tất cả |
| `MPI_Reduce()` | Tổng hợp dữ liệu từ nhiều tiến trình |
| `MPI_Finalize()` | Kết thúc môi trường MPI |

---

### Bài toán: Tính 10,000,000 số nguyên tố đầu tiên

### Mục tiêu:
- Tính đúng 10 triệu số nguyên tố đầu tiên
- Sử dụng tối đa 32 nhân xử lý
- Cho kết quả giống nhau, dù sử dụng 8, 10, 12 hay 32 tiến trình

---

### Thuật toán lựa chọn: Sieve of Eratosthenes

- Tạo mảng từ 2 đến N
- Loại bỏ các bội số của từng số nguyên tố nhỏ
- Áp dụng thuật toán theo từng đoạn để xử lý song song

---

### Giải pháp dùng MPI để xử lý phân tán

### 1. Phân công dữ liệu
- Mỗi tiến trình xử lý một đoạn `[start, end]` riêng
- Các tiến trình con gửi kết quả về cho tiến trình `master`

### 2. Đồng bộ hóa dữ liệu đầu vào
- Tiến trình `rank 0` tính các số nguyên tố 
- Gửi broadcast cho các tiến trình con

### 3. Tổng hợp kết quả
- Tiến trình con gửi mảng kết quả về master
- Master tổng hợp → Đếm đủ 10 triệu số nguyên tố

---

### Giải pháp mở rộng cho số nhân linh hoạt

```c
int rank, size;
MPI_Comm_rank(MPI_COMM_WORLD, &rank);
MPI_Comm_size(MPI_COMM_WORLD, &size);

int range = (N - 2 + 1) / size;
int start = 2 + rank * range;
int end = (rank == size - 1) ? N : start + range - 1;
```

Cách này đảm bảo bài toán chạy đúng dù dùng 8, 10, 12 hoặc 32 tiến trình.

### Tham khảo

1. [Sieve of Eratosthenes – Wikipedia](https://en.wikipedia.org/wiki/Sieve_of_Eratosthenes)
2. [OpenMPI Official Documentation](https://www.open-mpi.org/doc/)
3. Slide môn Distributed Systems – "Distributed System notes 7.pdf"
