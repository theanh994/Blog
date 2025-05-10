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

## Các bài toán CNTT áp dụng đa luồng, đa tiến trình

Dưới đây là bảng liệt kê các **bài toán phổ biến trong ngành Công nghệ Thông tin**, và cách chúng ứng dụng **đa luồng (multithreading)** hoặc **đa tiến trình (multiprocessing)**:

| STT | Bài toán                               | Ứng dụng đa tiến trình/đa luồng như thế nào?                  |
|-----|----------------------------------------|---------------------------------------------------------------|
| 1   | Web server                             | Mỗi request sinh ra một thread để xử lý                       |
| 2   | Trình biên dịch (compiler)            | Biên dịch các file mã nguồn song song bằng tiến trình        |
| 3   | Game engine                            | Mỗi thành phần (đồ họa, âm thanh, vật lý) xử lý bằng các luồng riêng |
| 4   | Xử lý ảnh/video                        | Chia nhỏ frame để các tiến trình/luồng xử lý song song       |
| 5   | Trí tuệ nhân tạo (AI/ML Training)     | Dữ liệu huấn luyện chia theo batch, xử lý bằng nhiều tiến trình |
| 6   | Web crawler                            | Mỗi tiến trình xử lý một domain khác nhau                    |
| 7   | Chat server                            | Mỗi client là một luồng kết nối riêng                        |
| 8   | Cơ sở dữ liệu (database)              | Mỗi truy vấn có thể xử lý bằng một thread độc lập            |
| 9   | Blockchain                             | Mỗi node hoặc block là một tiến trình riêng biệt             |
| 10  | Công cụ tìm kiếm                       | Mỗi phần dữ liệu (shard) xử lý riêng qua tiến trình/luồng    |
| 11  | Phân tích log                          | Mỗi file log hoặc dòng log xử lý song song                   |
| 12  | Video streaming platform              | Mỗi client stream video thông qua luồng riêng                |


## Khi nào nên dùng Thread, Process, hoặc cả hai?

Việc lựa chọn giữa **Thread**, **Process**, hoặc kết hợp cả hai trong hệ thống phân tán phụ thuộc vào:  
- Mức độ chia sẻ tài nguyên  
- Tính chất xử lý (I/O-bound hay CPU-bound)  
- Độ cách ly và độ ổn định mong muốn  
- Mức độ đồng thời, hiệu suất, và chi phí tài nguyên  

Dưới đây là **bảng phân tích chi tiết**, bao gồm mô tả kỹ thuật, trường hợp nên dùng, ưu nhược điểm và ví dụ minh họa thực tế:

| Tiêu chí                     | Dùng **Thread**                                                                                      | Dùng **Process**                                                                                 | Dùng **Cả hai**                                                                                          |
|-----------------------------|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| **Cách thức hoạt động**     | Các luồng trong cùng một tiến trình, chia sẻ không gian bộ nhớ, tốc độ tạo nhanh.                  | Mỗi tiến trình chạy độc lập, không chia sẻ không gian bộ nhớ.                                      | Dùng process để cách ly nhóm nhiệm vụ, mỗi process có thể tạo nhiều thread để xử lý song song.           |
| **Tính chia sẻ tài nguyên** | Chia sẻ biến, vùng nhớ giữa các thread rất dễ dàng.                                                 | Cô lập bộ nhớ, chỉ có thể chia sẻ qua IPC (Inter-Process Communication).                          | Thread chia sẻ trong process, nhưng giữa các process vẫn cô lập với nhau.                               |
| **Hiệu suất**               | Tạo thread nhanh hơn process, context switching nhẹ hơn.                                            | Tạo process tốn tài nguyên hơn, context switching nặng.                                           | Tối ưu xử lý song song mà vẫn đảm bảo tính cách ly và an toàn.                                          |
| **Ổn định**                 | Lỗi ở một thread có thể gây crash cả tiến trình.                                                    | Lỗi ở một process không ảnh hưởng đến các process khác.                                           | Giảm thiểu tác động lan truyền lỗi nếu phân tách hợp lý.                                                 |
| **Xử lý I/O blocking**      | Dễ bị block nếu dùng User Space Thread (không được kernel quản lý trực tiếp).                      | Có thể xử lý blocking I/O tốt, vì mỗi process quản lý riêng.                                      | Dùng LWP (lightweight process) để cân bằng lợi ích của cả hai.                                           |
| **Trường hợp sử dụng**     | - Ứng dụng giao diện, game<br>- Web server nhỏ<br>- Đa tác vụ nhẹ                                   | - ML Training<br>- Video rendering<br>- Phân tích dữ liệu lớn, crawling                           | - Microservices, hệ thống backend lớn<br>- ChatGPT, AI model server<br>- Webserver đa tầng              |
| **Ví dụ thực tế**           | - Một app calculator có 1 thread UI và 1 thread tính toán<br>- Mô hình `thread-per-request`         | - Training GPT model: chia data, mỗi phần xử lý trên 1 GPU/process<br>- `multiprocessing` Python | - Một server xử lý request bằng process, mỗi request tiếp tục phân thành nhiều thread xử lý logic con. |
| **Áp dụng kiến trúc**       | - Thread-per-request<br>- Thread-per-connection                                                     | - Multiprocess + message queue (ZeroMQ, Kafka...)                                                 | - Dispatcher thread + worker thread trong mỗi process                                                      |

### Giải thích thêm một số khái niệm:

- **Light Weight Process (LWP):** là sự kết hợp giữa kernel thread (được hệ điều hành quản lý) và user thread (dễ lập trình, nhẹ), giúp xử lý I/O không làm treo cả tiến trình.
- **Dispatcher Thread:** trong server lớn, một thread chuyên nhận request và phân phối đến các thread khác, tăng hiệu suất điều phối.
- **Thread-per-request:** tối đa hóa băng thông, nhưng tiêu tốn tài nguyên nếu số lượng request lớn.
- **Thread-per-connection / Thread-per-object:** phù hợp cho hệ thống có trạng thái lâu dài (VD: chat app, payment service).

## Cách ChatGPT được huấn luyện bằng hệ thống phân tán (Distributed System)

## Hệ thống phân tán trong quá trình huấn luyện ChatGPT

Việc huấn luyện ChatGPT (đặc biệt là GPT-3, GPT-4) đòi hỏi xử lý khối lượng dữ liệu và tham số khổng lồ, dẫn đến yêu cầu cao về hiệu suất phân tán.

### 1. Mục tiêu của huấn luyện phân tán

- **Mô hình lớn:** GPT-3 có 175B tham số, GPT-4 thậm chí còn lớn hơn.
- **Dữ liệu huấn luyện cực lớn:** hàng trăm terabyte văn bản.
- **Thời gian huấn luyện:** hàng tuần, hàng ngàn GPU đồng thời.

---

### 2. Data Parallelism

#### Mô tả
- Mỗi node (GPU/máy) giữ một bản sao đầy đủ của mô hình.
- Dữ liệu được chia thành các phần nhỏ (mini-batch).
- Các node thực hiện tính toán trên batch riêng của mình.

#### Ưu điểm
- Dễ triển khai.
- Phù hợp khi mô hình vừa với VRAM GPU.

#### Nhược điểm
- Tăng giao tiếp khi số GPU tăng.
- Gradient đồng bộ cần tối ưu bằng **NCCL** hoặc **AllReduce**.

---

### 3. Model Parallelism

#### Mô tả
- Mô hình quá lớn → chia mô hình theo chiều dọc (layers) hoặc chiều rộng (tensors).

#### Tensor Parallelism:
- Chia ma trận nhân, ví dụ A x B = C → chia A và B theo hàng/cột.
- Dùng Megatron-LM hoặc DeepSpeed.

#### Ưu điểm
- Cho phép xử lý mô hình cực lớn.

#### Nhược điểm
- Cần lập kế hoạch pipeline phức tạp.
- Giao tiếp nhiều giữa GPU.

---

### 4. Hybrid Parallelism – ZeRO

#### Khái niệm
- Kết hợp Data + Model + Optimizer State partitioning.

#### Ưu điểm
- Tiết kiệm VRAM 10–15 lần.
- Tăng khả năng huấn luyện mô hình 10B+ trên 1–4 GPU.

#### Công cụ
- DeepSpeed (Microsoft)
- Megatron-DeepSpeed
- FairScale (Meta)

---

### 5. RLHF (Reinforcement Learning from Human Feedback)

#### Quy trình 3 giai đoạn:
1. **Supervised Fine-tuning**
2. **Training Reward Model** (từ so sánh giữa nhiều câu trả lời)
3. **Huấn luyện với PPO** – cập nhật policy model dựa trên feedback.

#### Kỹ thuật phân tán đi kèm
- Reward model & policy chạy trên các cụm GPU riêng.
- Tối ưu với Ray, DeepSpeed Actor/Critic.

#### Khó khăn:
- Đồng bộ trạng thái.
- So sánh feedback theo thời gian thực.

---

## 6. Hạ tầng và Công cụ

### Ray

- Framework phân tán task.
- Quản lý GPU, lại nhiệm task khi thất bại.

### DeepSpeed

- Thư viện tối ưu hoá huấn luyện mô hình lớn.
- Hỗ trợ ZeRO, pipeline, gradient checkpointing.

---

## 7. Hạ tầng vật lý

- Các supercomputer do Microsoft xây dựng.
- GPU NVIDIA A100 (tối đa 40/80GB VRAM).
- Kết nối bằng NVLink, InfiniBand.
- Hệ thống làm mát dùng nước quy mô lớn.

---

## 8. Tài liệu tham khảo

| Nội dung             | Liên kết                                                                                                                                                                                                                                     |
| -------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Kiến trúc GPT        | [https://www.geeksforgeeks.org/chatgpts-architecture](https://www.geeksforgeeks.org/chatgpts-architecture)                                                                                                                                   |
| Ray + ChatGPT        | [https://www.analyticsinsight.net/artificial-intelligence/how-does-ray-a-distributed-ai-system-powers-openais-chatgpt](https://www.analyticsinsight.net/artificial-intelligence/how-does-ray-a-distributed-ai-system-powers-openais-chatgpt) |
| RLHF chi tiết        | [https://arxiv.org/abs/2312.11819](https://arxiv.org/abs/2312.11819)                                                                                                                                                                         |
| DeepSpeed Chat       | [https://arxiv.org/abs/2308.01320](https://arxiv.org/abs/2308.01320)                                                                                                                                                                         |
| Guide huấn luyện GPT | [https://github.com/MahdiSheikhi/ChatGPT-Training-Guide](https://github.com/MahdiSheikhi/ChatGPT-Training-Guide)                                                                                                                             |

---
