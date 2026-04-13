# CÂU HỎI VỀ BÀI LÀM
## 1. Tại sao phải dùng Nginx làm Reverse Proxy mà không trỏ thẳng Tunnel vào Node-RED?

Việc sử dụng Nginx làm Reverse Proxy mang lại nhiều lợi ích:

Tăng bảo mật: Nginx đứng trung gian giúp che giấu service Node-RED phía sau, tránh bị truy cập trực tiếp.
Quản lý nhiều dịch vụ: Có thể phân luồng request:
 → web tĩnh (HTML)
api → Node-RED
Hỗ trợ xử lý nâng cao: SSL, cache, giới hạn request, logging,...
Dễ mở rộng hệ thống: Có thể thêm nhiều backend khác mà không cần thay đổi cấu trúc chính.

Ngược lại, nếu trỏ trực tiếp Tunnel vào Node-RED:

Khó tách frontend/backend
Bảo mật kém hơn
Khó mở rộng trong tương lai
## 2. Sự khác biệt giữa Mount file và Mount thư mục trong Docker
Mount file:
Chỉ ánh xạ một file cụ thể từ máy host vào container
Thường dùng cho file cấu hình (ví dụ: nginx.conf)
Mount thư mục:
Ánh xạ toàn bộ thư mục
Thường dùng cho source code hoặc web tĩnh

Kết luận:

Mount file → dùng cho cấu hình
Mount thư mục → dùng cho dữ liệu hoặc code
3. Nếu thay đổi file index.html ở Ubuntu, nội dung trên web có thay đổi ngay không? Tại sao?

Có, nội dung sẽ thay đổi ngay trong hầu hết trường hợp.

Lý do:

File index.html được mount từ máy host vào container
Khi chỉnh sửa file trên Ubuntu, container sẽ đọc nội dung mới ngay lập tức

Ngoại lệ:

Trình duyệt cache (cần Ctrl + F5)
Không dùng mount mà copy file vào container
## 4. restart: always và restart: unless-stopped dùng để làm gì?

Trong file docker-compose.yml:

restart: always
Container luôn tự khởi động lại khi bị dừng hoặc khi Docker restart
restart: unless-stopped
Tương tự always, nhưng nếu người dùng dừng container thủ công thì sẽ không tự chạy lại

Kết luận:

Dùng unless-stopped phổ biến hơn trong thực tế
## 5. Cách khai báo để tất cả services dùng chung 1 network và lợi ích
Khai báo:
version: '3.8'

services:
  nginx:
    image: nginx
    networks:
      - mynetwork

  nodered:
    image: nodered/node-red
    networks:
      - mynetwork

  cloudflared:
    image: cloudflare/cloudflared
    networks:
      - mynetwork

networks:
  mynetwork:
    driver: bridge
Lợi ích:
Các container có thể gọi nhau bằng tên service (ví dụ: http://nodered:1880)
Không cần mở port nội bộ
Tăng bảo mật
Dễ quản lý và mở rộng hệ thống
6. Đưa Cloudflare Token vào .env và thêm vào .gitignore – Tại sao quan trọng?
Cách thực hiện:

File .env:

CLOUDFLARE_TOKEN=your_token_here

Trong docker-compose.yml:

environment:
  - TUNNEL_TOKEN=${CLOUDFLARE_TOKEN}

File .gitignore:

.env
Ý nghĩa bảo mật:
Token là thông tin nhạy cảm (secret)
Nếu đưa lên GitHub, người khác có thể chiếm quyền hệ thống
.env giúp tách cấu hình ra khỏi mã nguồn

Kết luận: Đây là nguyên tắc quan trọng trong bảo mật: không hardcode thông tin nhạy cảm

## 7. Tại sao nên thêm hậu tố :ro khi mount file cấu hình Nginx?

Ví dụ:

- ./nginx.conf:/etc/nginx/nginx.conf:ro
:ro (read-only) giúp container chỉ đọc file, không thể chỉnh sửa
Tránh bị ghi đè hoặc thay đổi cấu hình ngoài ý muốn
Tăng độ ổn định và bảo mật
## 8. Khi dùng Cloudflare Tunnel có cần mở cổng không?

Không cần mở cổng ra Internet

Lý do:

Tunnel tạo kết nối từ server ra Cloudflare (outbound)
Người dùng truy cập qua Cloudflare, không truy cập trực tiếp server

Luồng hoạt động:

User → Cloudflare → Tunnel → Nginx → Node-RED
Lợi ích:
Không cần NAT hoặc Port Forward
Tăng bảo mật (không lộ server)
Dùng được cả khi không có IP public
