---
title: "Báo cáo giữa kỳ"
date: "2025-06-02"
updated: "2025-06-02"
categories:
    - "Hệ thống phân tán"
    - "Distributed Systems"
coverImage: "/images/ảnh đồ án.png"
coverWidth: 16
coverHeight: 9
excerpt: 

---
## Báo cáo nội dung triển khai có trong hệ thống Facebook-clone cócó sử dụng sơ sở dữ liệu Apache HBase

## Hiểu Về Kiến Trúc Hệ Thống Của Trang Web

Trong bài viết này, chúng em sẽ cung cấp một báo cáo phân tích chi tiết về hệ thống web mà chúng em đã thiết kế, tập trung vào từng thành phần chính (tài nguyên media, giao diện tĩnh, hệ thống xây dựng, máy chủ web/CDN, dịch vụ API Python, cơ sở dữ liệu Apache HBase, và trình duyệt người dùng cuối). Đồng thời sẽ giải thích vai trò của từng thành phần, cách chúng tương tác với nhau, bao gồm các giao thức giao tiếp, thuật toán sharding/replication (nếu áp dụng), và cách chúng được triển khai trong thực tế. Ngoài ra, báo cáo sẽ liệt kê các công nghệ và thư viện sử dụng (bao gồm Apache HBase, Docker, Node.js, Python, CDN, HTML/CSS/JS), kèm theo lý do lựa chọn chi tiết và cách tích hợp chúng vào hệ thống. 

Sơ đồ kiến trúc hệ thống
![Sơ đồ kiến trúc hệ thống](images/diagram.png)

### Các Thành Phần Hệ Thống và Vai Trò của Chúng
#### 1. Tài Nguyên Media (Media Assets)

Thành phần này bao gồm các tệp đa phương tiện như hình ảnh (src/img/ chứa các tệp như logo.png, banner.jpg) và video (src/vid/Basketball FRVR - Video Gameplay.mp4). Các tệp này sẽ được lưu trữ dưới dạng tệp tĩnh với định dạng phổ biến như JPEG, PNG cho hình ảnh và MP4 cho video.

Vai trò: Cung cấp nội dung trực quan cho ứng dụng, chẳng hạn như hình ảnh minh họa trên trang chủ hoặc video hướng dẫn người dùng. Đây là tài nguyên quan trọng để tăng tính hấp dẫn và tương tác của giao diện.

Cách hoạt động:
Các tệp media được tải lên máy chủ web/CDN thông qua quá trình triển khai thủ công hoặc tự động (ví dụ: sử dụng script FTP hoặc CI/CD pipeline).
Khi trình duyệt người dùng cuối gửi yêu cầu HTTP GET (ví dụ: GET /img/logo.png), máy chủ web/CDN phản hồi bằng cách gửi tệp media tương ứng, thường với header Content-Type: image/png hoặc Content-Type: video/mp4.
CDN có thể nén hoặc tối ưu hóa các tệp này (ví dụ: sử dụng WebP thay cho JPEG) để tăng tốc độ tải.

Giao thức giao tiếp: Sử dụng giao thức HTTP/HTTPS, thường với phương thức GET để tải tài nguyên.


#### 2. Giao Diện Tĩnh (Static Frontend)

Giao diện bao gồm các tệp tĩnh như trangchu.html (cấu trúc trang), style.css (thiết kế giao diện), và src/js/main.js (tương tác động). Các tệp này thường được viết bằng HTML5, CSS3, và JavaScript ES6, có thể sử dụng các thư viện như Bootstrap hoặc jQuery để tăng tốc phát triển.

Vai trò: Tạo ra giao diện người dùng trực quan, đáp ứng (responsive), và hỗ trợ tương tác cơ bản (như nút bấm, form nhập liệu) mà không cần tải lại trang hoàn toàn.

Cách hoạt động:

trangchu.html định nghĩa cấu trúc trang, liên kết đến style.css và src/js/main.js .
Hệ thống xây dựng (Node.js) biên dịch và tối ưu hóa các tệp này (ví dụ: minify CSS/JS) trước khi triển khai lên máy chủ web/CDN.
Trình duyệt người dùng cuối tải các tệp này qua HTTP GET và render giao diện, sử dụng JavaScript để xử lý các sự kiện (event listeners) như click hoặc submit.

Giao thức giao tiếp: Sử dụng HTTP/HTTPS với phương thức GET để tải các tệp tĩnh.

#### 3. Hệ Thống Xây Dựng (Build System - Node)

Sử dụng Node.js (môi trường chạy JavaScript phía server) và npm (quản lý gói) để quản lý quá trình xây dựng. Các tệp chính bao gồm src/scss/style.scss (mã SCSS nguồn), src/js/main.js (mã JavaScript nguồn), package.json (định nghĩa phụ thuộc và script), và package-lock.json (khóa phiên bản phụ thuộc). Có thể sử dụng các công cụ như Webpack, Gulp, hoặc Sass để biên dịch và đóng gói.

Vai trò: Chuyển đổi mã nguồn thô (SCSS, JS) thành các tệp tĩnh tối ưu hóa (CSS, JS đóng gói) để triển khai lên sản phẩm, đồng thời tự động hóa quy trình build thông qua CI/CD.

Cách hoạt động:
src/scss/style.scss được biên dịch thành src/css/style.css sử dụng trình biên dịch Sass (cài đặt qua npm).
src/js/main.js được đóng gói thành bundled JS bằng Webpack hoặc Rollup, kết hợp các module JavaScript và loại bỏ mã không sử dụng (tree-shaking).
Script trong package.json (ví dụ: "build": "sass src/scss/style.scss src/css/style.css && webpack") được chạy để thực thi quá trình build.
Kết quả được lưu vào thư mục dist/ hoặc triển khai trực tiếp lên máy chủ web/CDN.

Giao thức giao tiếp: Không sử dụng giao thức mạng trực tiếp, nhưng kết quả build được chuyển giao qua hệ thống tập tin (file system) hoặc CI/CD pipeline (như Jenkins, GitHub Actions).

#### 4. Máy Chủ Web 

Máy chủ web có thể là Nginx hoặc Apache, kết hợp với CDN (như Cloudflare, Akamai, hoặc AWS CloudFront) để phân phối nội dung. CDN bao gồm nhiều nút (edge servers) trên toàn cầu, lưu trữ bản sao nội dung tĩnh.

Vai trò: Làm trung gian giữa trình duyệt người dùng và các tài nguyên tĩnh, giảm tải cho máy chủ gốc và tăng tốc độ phân phối nội dung.

Cách hoạt động:
Khi nhận yêu cầu HTTP GET (ví dụ: GET /trangchu.html), máy chủ web/CDN kiểm tra xem nội dung có trong bộ nhớ đệm (cache) của nút gần nhất không. Nếu có, nó trả về nội dung ngay lập tức; nếu không, nó lấy từ máy chủ gốc và lưu vào cache.
CDN sử dụng DNS để định tuyến yêu cầu đến nút gần nhất dựa trên vị trí địa lý của người dùng.

Giao thức giao tiếp: Sử dụng HTTP/HTTPS với phương thức GET cho tài nguyên tĩnh, và có thể sử dụng WebSocket hoặc HTTP/2 để tăng hiệu suất.

Replication trong CDN:
Cơ chế: CDN sử dụng replication để sao chép nội dung tĩnh (HTML, CSS, JS, media) đến các nút edge. Ví dụ, khi trangchu.html được cập nhật, CDN đẩy bản sao đến các nút ở Mỹ, châu Âu, và châu Á.
Logic sao chép: Có hai cách chính:
Pull-based: Nút edge tự động kéo nội dung từ máy chủ gốc khi cache hết hạn (TTL - Time To Live).
Push-based: Máy chủ gốc chủ động đẩy nội dung đến các nút edge khi có cập nhật (sử dụng API CDN).
Thuật toán: CDN thường sử dụng consistent hashing để phân phối nội dung giữa các nút. Ví dụ, hash của URL (/img/logo.png) được ánh xạ đến một nút cụ thể, đảm bảo cân bằng tải và giảm xung đột khi thêm/xóa nút.

#### 5. Dịch Vụ API Python

Dịch vụ API được viết trong tệp api.py, sử dụng framework như Flask (đồng bộ) hoặc FastAPI (bất đồng bộ) để xử lý yêu cầu. API có thể kết nối với HBase thông qua thư viện Python như happybase hoặc thrift.

Vai trò: Xử lý yêu cầu động (như lấy dữ liệu người dùng, lịch sử truy cập) và phản hồi dữ liệu dạng JSON hoặc XML.

Cách hoạt động:
Khi nhận yêu cầu HTTP POST/GET từ máy chủ web/CDN (ví dụ: POST /api/userdata), API phân tích yêu cầu (thông qua header và body).
API truy vấn HBase để lấy dữ liệu (ví dụ: row key là user123, trả về lịch sử xem video).
Phản hồi được gửi lại dưới dạng JSON (ví dụ: {"user_id": "user123", "history": ["video1.mp4"]}) với mã trạng thái HTTP 200.

Giao thức giao tiếp: Sử dụng HTTP/HTTPS với RESTful API (phương thức GET, POST, PUT, DELETE) để giao tiếp với máy chủ web/CDN, và giao thức HBase Thrift hoặc REST để kết nối với HBase.

#### 6. Apache HBase (Cơ Sở Dữ Liệu Phân Tán)

HBase là cơ sở dữ liệu NoSQL phân tán, chạy trên Hadoop HDFS, hỗ trợ lưu trữ dữ liệu lớn với mô hình key-value (row key, column family, column qualifier, value). Ví dụ, một hàng có thể là user123:views:video1=2025-06-02.

Vai trò: Lưu trữ dữ liệu động như lịch sử truy cập media, thông tin phiên người dùng, hoặc dữ liệu phân tích (lượt xem, thời gian xem).

Cách hoạt động:
Dữ liệu được lưu trong các region, mỗi region chứa một tập hợp row key liên tiếp (ví dụ: user001 đến user500).
API Python gửi yêu cầu truy vấn (qua happybase.Connection) với row key (ví dụ: user123), HBase trả về dữ liệu tương ứng.
HBase sử dụng HDFS để lưu trữ dữ liệu và ZooKeeper để quản lý metadata (ví dụ: vị trí của region).

Sharding trong HBase:
Cơ chế: HBase tự động phân mảnh dữ liệu thành các region dựa trên row key. Khi một region đạt ngưỡng kích thước (mặc định 10GB), HBase chia nó thành hai region nhỏ hơn.
Logic phân mảnh: Sử dụng range partitioning, chia dữ liệu theo phạm vi row key (ví dụ: user001-user500 thành user001-user250 và user251-user500).
Thuật toán: HBase sử dụng thuật toán split policy (mặc định là IncreasingToUpperBoundRegionSplitPolicy) để xác định khi nào cần chia region, dựa trên kích thước và số lượng row.

Replication trong HBase:
Cơ chế: HBase dựa vào replication của HDFS, sao chép mỗi khối dữ liệu (HFile) đến nhiều nút. Mặc định replication factor là 3.
Logic sao chép: Sử dụng master-slave replication, với HDFS đảm bảo mỗi bản sao được lưu trên các rack khác nhau (ví dụ: rack 1, rack 2, rack 3) để tăng độ tin cậy. Dữ liệu được đồng bộ hóa theo thời gian thực thông qua HLog (Write-Ahead Log).
Thuật toán: HDFS sử dụng thuật toán rack awareness để chọn nút lưu bản sao, giảm nguy cơ mất dữ liệu khi một rack gặp sự cố.

#### 7. Trình Duyệt Người Dùng Cuối (End User Browser)

Trình duyệt như Google Chrome, Mozilla Firefox, hoặc Microsoft Edge, hỗ trợ các tính năng hiện đại như HTML5, CSS Grid, và JavaScript async/await.

Vai trò: Hiển thị giao diện người dùng và xử lý tương tác (như click, nhập liệu), đồng thời gửi yêu cầu đến máy chủ.

Cách hoạt động:
Trình duyệt phân tích HTML (trangchu.html), áp dụng CSS (style.css), và thực thi JavaScript (bundled JS) để render giao diện.
Gửi yêu cầu HTTP/HTTPS (ví dụ: GET /api/userdata) thông qua XMLHttpRequest hoặc Fetch API, nhận phản hồi JSON, và cập nhật giao diện động.

Giao thức giao tiếp: Sử dụng HTTP/HTTPS với phương thức GET/POST, có thể sử dụng WebSocket cho giao tiếp thời gian thực.

### Cách Các Thành Phần Hoạt Động Cùng Nhau

#### Quy Trình Cơ Bản

Trình duyệt người dùng cuối gửi yêu cầu HTTP (ví dụ: HTTP GET cho trangchu.html, CSS/JS, hoặc media) đến máy chủ web/CDN.
Máy chủ web/CDN phục vụ các tài nguyên tĩnh từ giao diện tĩnh và tài nguyên media.
Đối với dữ liệu động, máy chủ web/CDN chuyển tiếp yêu cầu API đến dịch vụ API Python (qua /api).
Dịch vụ API Python xử lý yêu cầu và gửi phản hồi HTTP qua máy chủ web/CDN đến trình duyệt người dùng cuối.
Hệ thống xây dựng (Node) đảm bảo mã nguồn (SCSS, JS) được biên dịch và đóng gói trước khi triển khai lên máy chủ web/CDN.

#### Quy Trình Xây Dựng

Các công cụ CI/CD & Dev Tools trong package.json và package-lock.json định nghĩa phụ thuộc và chạy các script npm.
Hệ thống xây dựng biên dịch src/scss/style.scss thành src/css/style.css và đóng gói src/js/main.js thành tệp bundled JS.

#### Xem Xét Về Sharding và Replication

Sharding 

Sơ đồ kiến trúc không cho thấy rõ việc sử dụng sharding (phân mảnh dữ liệu giữa các nút) vì trong quá trình code dự án, chúng em đang gặp vấn đề về việc đưa lên môi trường cho web. Thế nên nếu có thể tiếp tục chỉnh sửa và áp dụng, dữ liệu như media hoặc nội dung tĩnh có thể được phân phối dựa trên hash của URL hoặc key (ví dụ: thuật toán consistent hashing) để cân bằng tải giữa các nút CDN. Điều này không chưa được áp dụng nên chưa được mô tả chi tiết trong sơ đồ.

Replication

CDN thường sử dụng replication để sao chép nội dung tĩnh (HTML, CSS, JS, media) đến nhiều nút trên toàn cầu. Logic sao chép có thể bao gồm:

Kéo (Pull-based): Các nút CDN kéo dữ liệu từ máy chủ gốc khi cần.
Đẩy (Push-based): Máy chủ gốc đẩy dữ liệu đến CDN. Mặc dù thuật toán cụ thể (ví dụ: master-slave, multi-master) không được nêu rõ nhưng đây là cách phổ biến trong các CDN như Cloudflare hoặc Akamai để tối ưu hiệu suất để có thể nâng cấp cho hệ thống của chúng em.

### Công Nghệ và Thư Viện Sử Dụng Trong Hệ Thống Web

Hệ thống này bao gồm các thành phần như tài nguyên media, giao diện tĩnh, hệ thống xây dựng, máy chủ web/CDN, dịch vụ API Python, và trình duyệt người dùng cuối. Đặc biệt, chúng em được yêu cầu sử dụng Apache HBase như một phần của hệ thống.

#### Các Công Nghệ và Thư Viện Sử Dụng

##### 1. Apache HBase (Cơ Sở Dữ Liệu Phân Tán)

Mô tả: Apache HBase là một cơ sở dữ liệu NoSQL phân tán, mã nguồn mở, được xây dựng dựa trên Hadoop HDFS, hỗ trợ truy cập ngẫu nhiên và theo thời gian thực vào dữ liệu lớn.
Lý do lựa chọn:
Khả năng mở rộng: HBase được thiết kế để xử lý dữ liệu lớn (hàng petabyte) trên hàng nghìn máy chủ, phù hợp với hệ thống có khối lượng dữ liệu tăng trưởng nhanh, chẳng hạn như dữ liệu người dùng hoặc lịch sử truy cập trong ứng dụng web.
Hiệu suất cao: HBase cho phép truy vấn nhanh dựa trên row key, lý tưởng cho các truy vấn thời gian thực như tra cứu thông tin người dùng hoặc lịch sử hoạt động.
Tích hợp với Hadoop: HBase tích hợp tốt với hệ sinh thái Hadoop, cho phép sử dụng các công cụ như MapReduce để xử lý dữ liệu lớn, phù hợp với các tác vụ phân tích trong hệ thống.
Tính linh hoạt: Là một cơ sở dữ liệu NoSQL, HBase không yêu cầu schema cố định, giúp dễ dàng thêm hoặc sửa đổi dữ liệu (ví dụ: thông tin người dùng, lịch sử giao dịch) mà không cần thay đổi cấu trúc bảng.
Ứng dụng cụ thể trong hệ thống: HBase sẽ giúp lưu trữ dữ liệu động như lịch sử truy cập của người dùng vào các tệp media (hình ảnh, video) hoặc dữ liệu phiên (session) từ trình duyệt người dùng cuối, thay vì chỉ dựa vào API Python.

##### 2. Docker (Công Cụ Đóng Gói và Triển Khai)

Docker sử dụng container để đóng gói ứng dụng cùng phụ thuộc, cho phép chạy ứng dụng một cách nhất quán trên nhiều nền tảng.

Lý do lựa chọn:
Tính nhất quán môi trường: Đảm bảo các thành phần như API Python, HBase, và hệ thống xây dựng hoạt động giống nhau trên các môi trường (phát triển, kiểm thử, sản xuất).
Triển khai nhanh chóng: Container chứa toàn bộ runtime (Python, Node.js, Java) và thư viện, giảm thời gian thiết lập (từ giờ xuống còn phút).
Quản lý tài nguyên: Sử dụng cgroups và namespaces để cô lập tài nguyên, tối ưu hóa CPU/RAM trên máy chủ.
Hỗ trợ CI/CD: Tích hợp với Jenkins/GitHub Actions để build và deploy container tự động.
Ứng dụng cụ thể: Docker được sử dụng để triển khai các dịch vụ trong hệ thống, bao gồm:
Chạy API Python trong container với Gunicorn, đảm bảo môi trường Python và các thư viện (như Flask/FastAPI) được cài đặt sẵn.
Chạy HBase trong container riêng, tích hợp với Hadoop và ZooKeeper để quản lý dữ liệu lớn.
Chạy hệ thống xây dựng Node.js trong container để biên dịch SCSS và đóng gói JS, hỗ trợ quy trình build tự động.

##### 3. Node.js và npm (Hệ Thống Xây Dựng)

Mô tả: Node.js là một môi trường chạy JavaScript phía máy chủ, và npm là trình quản lý gói đi kèm, được sử dụng để quản lý các công cụ xây dựng như biên dịch SCSS và đóng gói JavaScript.
Lý do lựa chọn:
Hiệu quả trong xây dựng giao diện tĩnh: Node.js và npm cho phép biên dịch src/scss/style.scss thành src/css/style.css và đóng gói src/js/main.js thành bundled JS, đảm bảo mã nguồn được tối ưu trước khi triển khai.
Hỗ trợ CI/CD: Các công cụ trong package.json và package-lock.json giúp tự động hóa quy trình xây dựng và triển khai, giảm thiểu lỗi thủ công.
Ứng dụng cụ thể trong hệ thống: Hệ thống xây dựng này được sử dụng để chuẩn bị các tệp tĩnh (trangchu.html, style.css, main.js) trước khi triển khai lên máy chủ web/CDN.

##### 4. Python và Flask/FastAPI (Dịch Vụ API)

Mô tả: Python là ngôn ngữ lập trình được sử dụng để xây dựng dịch vụ API (api.py), và có thể sử dụng các framework như Flask hoặc FastAPI để triển khai API.
Lý do lựa chọn:
Dễ phát triển và bảo trì: Python có cú pháp đơn giản, dễ đọc, giúp phát triển API nhanh chóng, đặc biệt phù hợp cho các dịch vụ nhỏ như xử lý yêu cầu dữ liệu động.
Hiệu suất cao với FastAPI: Nếu sử dụng FastAPI, API sẽ có hiệu suất cao nhờ thiết kế bất đồng bộ, phù hợp với các yêu cầu thời gian thực từ trình duyệt.
Ứng dụng cụ thể trong hệ thống: Dịch vụ API Python xử lý các yêu cầu động (chuyển tiếp qua /api) từ máy chủ web/CDN, chẳng hạn như lấy dữ liệu người dùng hoặc thông tin phiên từ HBase.

##### 5. CDN (Mạng Phân Phối Nội Dung)

Mô tả: CDN là một hệ thống các máy chủ phân tán được sử dụng để phân phối nội dung tĩnh như HTML, CSS, JS và media đến người dùng cuối.
Lý do lựa chọn:
Tăng tốc độ tải: CDN lưu trữ nội dung tĩnh gần người dùng hơn, giảm độ trễ khi tải trangchu.html, style.css, hoặc các tệp media.
Khả năng mở rộng: CDN tự động sao chép nội dung đến nhiều nút trên toàn cầu, đảm bảo hệ thống hoạt động ổn định ngay cả khi lượng truy cập tăng đột biến.
Ứng dụng cụ thể trong hệ thống: CDN được sử dụng để phân phối các tệp tĩnh và media từ src/img/ và src/vid/ đến trình duyệt người dùng cuối.

##### 6. HTML, CSS, JavaScript (Giao Diện Tĩnh)

Mô tả: HTML (trangchu.html), CSS (style.css), và JavaScript (src/js/main.js) được sử dụng để xây dựng giao diện người dùng tĩnh.
Lý do lựa chọn:
Tiêu chuẩn web: Đây là bộ ba công nghệ cốt lõi để xây dựng giao diện web, đảm bảo tính tương thích với mọi trình duyệt.
Hiệu suất: Các tệp tĩnh nhẹ và dễ tối ưu, giảm tải cho máy chủ.
Ứng dụng cụ thể trong hệ thống: Các tệp này được biên dịch và đóng gói để phục vụ giao diện người dùng, chẳng hạn như hiển thị trang chủ và các tính năng tương tác.


K vesty Tích Hợp Apache HBase Vào Hệ Thống
Cách Tích Hợp Apache HBase

Tích hợp với API Python: Dịch vụ API Python (api.py) có thể truy vấn dữ liệu từ HBase (ví dụ: thông tin người dùng, lịch sử truy cập) và trả về kết quả cho trình duyệt người dùng cuối thông qua máy chủ web/CDN.
Lưu trữ dữ liệu động: HBase sẽ lưu trữ các dữ liệu không cần schema cố định, chẳng hạn như lịch sử truy cập media hoặc thông tin phiên người dùng.
Tích hợp với Hadoop: Nếu cần phân tích dữ liệu lớn (ví dụ: thống kê lượt xem video), HBase có thể hoạt động cùng MapReduce để xử lý dữ liệu hiệu quả.

