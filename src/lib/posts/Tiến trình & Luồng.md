---
title: "Phân tích hiệu năng máy tính cá nhân dựa trên bài học Hệ thống phân tán"
date: "2025-05-05"
updated: "2025-05-05"
categories:
  - "Hệ thống phân tán"
  - "Distributed Systems"
coverImage: "/images/Aser.png"
coverWidth: 16
coverHeight: 9
excerpt: Bài viết này phân tích cấu hình máy tính cá nhân sử dụng CPU Intel i5-11400H, GPU RTX 1650 và RAM 16GB, liên hệ đến hiệu năng khi học và thực hành hệ thống phân tán.
---

## Cấu hình phần cứng máy tính

Máy tính sử dụng trong bài viết này là **Acer Nitro AN515-45**, với cấu hình như sau:

- **CPU:** Intel Core i5-11400H (6 nhân, 12 luồng, 2.7GHz – 4.5GHz)
- **GPU:** NVIDIA GeForce RTX 1650 4GB GDDR6
- **RAM:** 16GB DDR4

Người dùng có thể kiểm tra thông tin chi tiết bằng các công cụ như:
- `Task Manager` (tab Performance)
- `dxdiag`
- `msinfo32`

## Phân tích hiệu năng theo kiến thức Hệ thống phân tán

Dựa trên kiến thức từ bài học về hệ thống phân tán, ta có thể phân tích các yếu tố sau:

### CPU – Khả năng xử lý song song

- Bộ xử lý **Intel Core i5-11400H** với 6 nhân 12 luồng hỗ trợ **đa luồng (multithreading)** tốt.
- Phù hợp với các mô hình server-client, hệ thống đa tiến trình, hoặc ứng dụng cần xử lý đồng thời nhiều yêu cầu.

### GPU – Tăng tốc xử lý tính toán

- **RTX 1650** tuy không phải dòng cao cấp, nhưng vẫn có thể hỗ trợ các bài toán tính toán song song (nếu học CUDA hoặc các thư viện liên quan).
- Hữu ích khi mô phỏng hệ thống phân tán có giao diện đồ họa, xử lý dữ liệu lớn hoặc thị giác máy tính.

### RAM – Đáp ứng cho môi trường thực hành

- **16GB RAM** đủ dùng cho việc chạy đồng thời nhiều tiến trình, máy ảo, container (Docker), hoặc các công cụ mô phỏng môi trường phân tán.
- Giảm nguy cơ nghẽn bộ nhớ khi làm việc với hệ thống nhiều node.

## Kết luận

Với cấu hình như trên, máy tính hoàn toàn đáp ứng tốt cho việc:

- Học và thực hành các mô hình hệ thống phân tán
- Viết và chạy chương trình đa tiến trình, socket, hoặc client-server
- Mô phỏng và triển khai microservices hoặc mô hình phân tán nhỏ

Đây là một lựa chọn phù hợp cho sinh viên ngành Công nghệ thông tin hoặc người mới bắt đầu học về hệ thống phân tán.
