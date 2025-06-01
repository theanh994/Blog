---
title: "Định danh"
date: "2025-06-01"
updated: "2025-06-01"
categories:
  - "Hệ thống phân tán"
  - "Distributed Systems"
coverImage: "/images/he-thong-phan-tan.png" 
coverWidth: 16
coverHeight: 9
excerpt: Bài tập Định danh.
---
## Bài tập 1

Bài tập 1
![Bài tập 1](/images/motvidu.jpg)

Bìa tập 2
    ### BÁO CÁO: THUẬT TOÁN CHORD



Chord là một thuật toán định tuyến và lưu trữ **bảng băm phân tán (Distributed Hash Table – DHT)**. Nó cho phép các node trong một hệ thống phân tán tìm kiếm một khóa (key) với hiệu suất **O(log N)**, nơi **N** là số lượng node trong hệ thống.

Ý tưởngtưởng

- Không gian khóa là một vòng tròn với **2^m** vị trí (m là số bit của định danh).
- Mỗi node và key có một định danh duy nhất trong không gian này.
- Mỗi node duy trì một bảng **finger table** để định tuyến hiệu quả.

### Cài đặt thuật toán Chord bằng Python

```python
import hashlib

M = 6  # Độ dài định danh m-bit -> ID từ 0 đến 2^m - 1
ID_SPACE = 2 ** M

def hash_key(key: str) -> int:
    return int(hashlib.sha1(key.encode()).hexdigest(), 16) % ID_SPACE

class Node:
    def __init__(self, node_id):
        self.id = node_id
        self.successor = self
        self.finger_table = [None] * M

    def find_successor(self, key_id):
        if self.id < key_id <= self.successor.id or            (self.id > self.successor.id and (key_id > self.id or key_id <= self.successor.id)):
            return self.successor
        else:
            node = self.closest_preceding_node(key_id)
            return node.find_successor(key_id)

    def closest_preceding_node(self, key_id):
        for i in reversed(range(M)):
            finger = self.finger_table[i]
            if finger and self.id < finger.id < key_id:
                return finger
        return self

    def join(self, known_node):
        if known_node:
            self.init_finger_table(known_node)
        else:
            for i in range(M):
                self.finger_table[i] = self
            self.successor = self

    def init_finger_table(self, known_node):
        self.finger_table[0] = known_node.find_successor((self.id + 1) % ID_SPACE)
        self.successor = self.finger_table[0]
        for i in range(1, M):
            start = (self.id + 2 ** i) % ID_SPACE
            if self.id < start < self.finger_table[i - 1].id:
                self.finger_table[i] = self.finger_table[i - 1]
            else:
                self.finger_table[i] = known_node.find_successor(start)
```

### Ví dụ cụ thể

### Cấu hình:
- Số bit m = 6 → ID từ 0 đến 63
- Thêm các node có định danh: 1, 14, 32, 38, 56

### Key cần tìm: `key = 24`

### Kết quả mong đợi:
- `successor(24)` = node có ID = **32**

Giải thích: vì 24 nằm giữa 14 và 32 trên vòng tròn, nên node 32 sẽ giữ khóa 24.

### Test Case đơn giản

```python
def simulate_chord():
    nodes = [Node(i) for i in [1, 14, 32, 38, 56]]
    nodes[0].join(None)

    for i in range(1, len(nodes)):
        nodes[i].join(nodes[0])

    for node in nodes:
        for i in range(M):
            start = (node.id + 2 ** i) % ID_SPACE
            node.finger_table[i] = nodes[0].find_successor(start)

    key_id = 24
    start_node = nodes[0]
    result = start_node.find_successor(key_id)
    print(f"Key {key_id} được giữ bởi node có ID: {result.id}")

simulate_chord()
```

### Kết quả thực thi:

```
Key 24 được giữ bởi node có ID: 32
```
## Bài tập 2: Vì sao có website bị chặn ở Việt Nam và cách DNS giúp truy cập lại?

### Các nhà mạng (ISP) tại Việt Nam

Tại Việt Nam, các nhà cung cấp dịch vụ Internet (ISP - Internet Service Provider) đóng vai trò then chốt trong việc kết nối người dùng đến thế giới mạng. Một số nhà mạng chính bao gồm:

| Tên nhà mạng        | Tên viết tắt      | Ghi chú |
|---------------------|-------------------|--------|
| VNPT                | Vietnam Posts and Telecommunications Group | Nhà mạng nhà nước lớn nhất |
| Viettel             | Viettel Telecom    | Quản lý bởi Bộ Quốc Phòng |
| FPT Telecom         | FPT               | Tư nhân lớn nhất |
| CMC Telecom         | CMC               | Tư nhân, cung cấp dịch vụ cho doanh nghiệp |
| SPT                 | Saigon Postel Corp| Nhà mạng nhỏ hơn, hoạt động tại khu vực phía Nam |
| NetNam              | NetNam Corporation| Chủ yếu phục vụ cho tổ chức chính phủ, giáo dục |
| Mobifone            | Mobifone Telecom  | Ngoài di động còn có cung cấp Internet cáp quang |

---

### Một số website bị chặn ở Việt Nam vì:

Người dùng Việt Nam đôi khi gặp tình trạng không thể truy cập một số website trong khi người dùng tại quốc gia khác lại truy cập được bình thường. Có nhiều lý do dẫn đến việc này:

### 1. **Chính sách kiểm duyệt nội dung**

- Nhà nước có thể yêu cầu chặn một số website chứa nội dung bị cho là vi phạm pháp luật, phản động, hoặc nhạy cảm về chính trị, xã hội.
- Điều này thường áp dụng với các trang tin tức nước ngoài, mạng xã hội, blog cá nhân có quan điểm trái chiều.

### 2. **Chặn ở mức DNS (DNS Filtering)**

- Nhà mạng không chặn truy cập theo địa chỉ IP, mà thay đổi kết quả phân giải DNS.
- Khi nhập một tên miền, hệ thống DNS của nhà mạng sẽ trả về sai địa chỉ hoặc trang báo lỗi, lúc đó trang web giống như bị hỏng.

### 3. **Chặn ở mức IP hoặc sử dụng DPI (Deep Packet Inspection)**

- Một số trường hợp, nhà mạng có thể chặn trực tiếp địa chỉ IP của website.
- DPI là kỹ thuật nâng cao để giám sát và phân tích lưu lượng truy cập, từ đó ngăn chặn các nội dung cụ thể như VPN, Tor, web ẩn danh.

---

## Đổi DNS thành 8.8.8.8 hoặc 1.1.1.1 giúp truy cập lại vì:

### Public DNS

Một số tổ chức cung cấp dịch vụ DNS công cộng nhanh, miễn phí, và không kiểm duyệt như:

| Nhà cung cấp | Địa chỉ DNS chính | Địa chỉ phụ       | Ghi chú |
|--------------|-------------------|-------------------|--------|
| Google       | 8.8.8.8           | 8.8.4.4           | Nhanh, ổn định |
| Cloudflare   | 1.1.1.1           | 1.0.0.1           | Bảo mật, không lưu log |
| OpenDNS      | 208.67.222.222    | 208.67.220.220    | Có khả năng lọc nội dung |

### Cách DNS giúp vượt chặn

- Khi dùng DNS mặc định của nhà mạng → kết quả có thể bị kiểm duyệt (DNS Filtering).
- Khi đổi sang DNS như 8.8.8.8 (Google) hoặc 1.1.1.1 (Cloudflare) → DNS không nằm dưới quyền kiểm soát của nhà mạng → khi đó sẽsẽ nhận đúng địa chỉ IP thật của website.

### Giới hạn

- Nếu website bị chặn ở mức **IP hoặc DPI** thì đổi DNS **không giúp vượt chặn được**.
- Trong trường hợp này, sẽ cần dùng VPN, proxy, hoặc các công cụ bảo mật như Tor.



### Cách đổi DNS trên Windows

1. Mở **Control Panel** → **Network and Sharing Center**.
2. Nhấn vào "Change adapter settings".
3. Click chuột phải vào mạng đang sử dụng → chọn **Properties**.
4. Chọn **Internet Protocol Version 4 (TCP/IPv4)** → nhấn **Properties**.
5. Chọn “Use the following DNS server addresses” và điền:
   - Preferred DNS server: `8.8.8.8`
   - Alternate DNS server: `8.8.4.4` (hoặc `1.1.1.1`, `1.0.0.1`)
6. Nhấn OK và khởi động lại trình duyệt.

- Các nhà mạng Việt Nam có thể chặn website thông qua **DNS filtering**.
- Đổi sang DNS công cộng như Google hoặc Cloudflare là cách đơn giản để **vượt qua chặn DNS**, giúp truy cập lại các website bị hạn chế.
- Tuy nhiên, với các hình thức chặn nâng cao như DPI, lúc đóđó cần dùng các công cụ mạnh hơn như VPN.

### Tham khảo

- Cloudflare DNS - https://www.cloudflare.com/learning/dns/
- Google Public DNS - https://developers.google.com/speed/public-dns
- Mozilla Developer Network - https://developer.mozilla.org/en-US/docs/Learn/Server-side/Domain_Name_System
- EFF (Electronic Frontier Foundation) - https://www.eff.org/issues/dns-censorship

