# B. Cài đặt Ubuntu + Docker
1. Cài đặt hệ điều hành Ubuntu 24.04.4 LTS
  + Sử dụng một trong các công cụ để giả lập: HyperV (có sẵn của windows), VirutualBox (Miễn phí), VM_Ware (bản quyền)
  + Download file iso để cài đặt.
  + Cấu hình mạng trong Ubuntu (và công cụ giả lập) để cho phép truy cập SSH vào Ubuntu từ cmd của windows
- Ví dụ:
  + để ssh tới ubuntu ở ip 192.168.100.123, user là admin thì mở CMD trên windows,
  + gõ lệnh: ssh admin@192.168.100.123
  + hệ thống sẽ yêu cầu nhập password (chú ý : password sẽ không hiện ra)
  + sau khi login thành công sẽ thấy màn hình chào hỏi của ubuntu
2. Tìm hiểu các lệnh cơ bản của ubuntu

- Các lệnh cần tìm hiểu:
  + Liệt kê các file trong thư mục: ls
  + Tạo thư mục: mkdir nameFolder
  + Chuyển thư mục làm việc: cd path
  + Copy file: cp file_nguồn path/file_đích
  + Thay đổi quyền thao tác file: sudo chmod xxx filename
  + Edit file: sudo nano tenfile
    + CTRL+o : lưu nội dung sau khi edit
    + CTRL+x : thoát edit file
  + Xem ip của máy ubuntu: ip -4 addr
3. Cài đặt docker cho Ubuntu
4. Kiểm tra phiên bản docker vừa cài đặt, kiểm tra phiên bản của docker compose
5. Cấu hình để docker chạy mà không cần tiền tố sudo
6. Tìm hiểu tập lệnh của docker và docker compose
7. Đảm bảo tường lửa trên Ubuntu đã cho phép các cổng 80, 1880, 9630 (Lệnh: sudo ufw allow ...)
## Bài làm
1. Cài đặt hệ điều hành Ubuntu 24.04.4 LTS
 - Cài đặt hệ điều hành Ubuntu 24.04.4 LTS
  + Sử dụng một trong các công cụ để giả lập: VM_Ware
<img width="1920" height="1080" alt="Ảnh chụp màn hình 2026-04-13 162122" src="https://github.com/user-attachments/assets/797f4507-c5e7-45ac-a720-b15b41ab8651" />
- Cài SSH trong Ubuntu
<img width="1293" height="582" alt="Ảnh chụp màn hình 2026-04-13 093245" src="https://github.com/user-attachments/assets/f416f5a0-bc8e-421e-b460-0ce15fce96ac" />
- khởi động dịch vụ SSH và cấu hình để SSH tự động chạy khi khởi động hệ thống. Sau đó, kiểm tra trạng thái dịch vụ và đảm bảo SSH hoạt động bình thường
<img width="1920" height="1080" alt="Ảnh chụp màn hình 2026-04-13 163006" src="https://github.com/user-attachments/assets/aef793a8-c0ef-42e0-83f4-cf67f98c6c56" />
<img width="1920" height="1080" alt="Ảnh chụp màn hình 2026-04-13 163446" src="https://github.com/user-attachments/assets/b34793b3-5b64-4284-b4d2-f604c4deb7ec" />
- truy cập SSH vào Ubuntu từ cmd của windows
- BƯỚC 1: Lấy IP của Ubuntu Trong Ubuntu, gõ: ip -4 addr để xem ip của máy ubuntu
<img width="1920" height="1080" alt="Ảnh chụp màn hình 2026-04-13 163446" src="https://github.com/user-attachments/assets/2245df8b-d0c3-48a1-bbae-1ac0a69ad681" />

- BƯỚC 2: Mở CMD trên Windows
  + gõ lệnh : ssh nguyenvanhoan@192.168.16.
- sau đó máy sẽ hỏi : Are you sure you want to continue connecting (yes/no/[fingerprint])?. chọn yes và sau đó nhập mật khẩu của ubuntu.

- cấu hình SSH trên Ubuntu và sử dụng lệnh ssh từ máy Windows để kết nối đến máy Ubuntu thông qua địa chỉ IP. Sau khi nhập đúng thông tin đăng nhập, hệ thống hiển thị màn hình chào của Ubuntu, chứng tỏ kết nối SSH thành công
<img width="1115" height="773" alt="Ảnh chụp màn hình 2026-04-13 163457" src="https://github.com/user-attachments/assets/aa46aa79-8145-473b-91a8-7651d733afde" />
2. Tìm hiểu các lệnh cơ bản của ubuntu
  
  - Liệt kê các file trong thư mục: ls
  - Tạo thư mục: mkdir nameFolder
  - Chuyển thư mục làm việc: cd path
  - Copy file: cp file_nguồn path/file_đích
     + CTRL+o : lưu nội dung sau khi edit
     + CTRL+x : thoát edit file
<img width="1920" height="1080" alt="Ảnh chụp màn hình 2026-04-13 164111" src="https://github.com/user-attachments/assets/7ffa1a00-e5fd-423f-bd46-7d2beda68dff" />
Thay đổi quyền thao tác file: sudo chmod xxx filename
<img width="1920" height="1080" alt="Ảnh chụp màn hình 2026-04-13 164209" src="https://github.com/user-attachments/assets/30ebbd94-1f23-4a24-ac21-23b6eb340d4d" />
Lệnh chmod 777 được sử dụng để cấp toàn quyền (đọc, ghi, thực thi) cho tất cả người dùng đối với file.
## 3. Cài đặt docker cho Ubuntu
## A. Cài Doker
- BƯỚC 1: Cập nhật hệ thống : sudo apt update
 - BƯỚC 2: Cài Docker : sudo apt install docker.io -y
<img width="1920" height="1080" alt="Ảnh chụp màn hình 2026-04-13 164647" src="https://github.com/user-attachments/assets/d7f8beb8-6f16-40f0-a8e0-a7bbaba88df8" />
BƯỚC 3:
Bật Docker : sudo systemctl start docker
Cho Docker tự chạy khi bật máy: sudo systemctl enable docker
<img width="1118" height="645" alt="Ảnh chụp màn hình 2026-04-13 165012" src="https://github.com/user-attachments/assets/0c186246-a18f-45c8-b1ea-35aae45a8422" />
BƯỚC 4 : Test Docker : sudo docker run hello-world
<img width="1093" height="643" alt="Ảnh chụp màn hình 2026-04-13 165410" src="https://github.com/user-attachments/assets/ebd1a005-678f-4b9a-a018-bedfa1755284" />
=> đã cài đặt Docker trên Ubuntu bằng lệnh apt install docker.io, sau đó khởi động dịch vụ Docker và cấu hình để Docker tự động chạy khi khởi động hệ thống. Cuối cùng, kiểm tra bằng lệnh docker run hello-world và nhận được kết quả thành công.
## B. Cài Docker Compose
Cài Docker Compose : sudo apt update sudo apt install docker-compose-v2 -y
<img width="1093" height="643" alt="Ảnh chụp màn hình 2026-04-13 165410" src="https://github.com/user-attachments/assets/128155ae-424d-478e-a562-9d19bf263d7b" />
4. Kiểm tra phiên bản docker vừa cài đặt, kiểm tra phiên bản của docker compose
<img width="1110" height="125" alt="Ảnh chụp màn hình 2026-04-13 165523" src="https://github.com/user-attachments/assets/626b6616-8e8c-4156-a4d6-864ea843278d" />
5. Cấu hình để docker chạy mà không cần tiền tố sudo
- BƯỚC 1: Thêm user vào nhóm docker
  + sudo usermod -aG docker $USER
- BƯỚC 2: Áp dụng thay đổi
  + newgrp docker
- BƯỚC 3: TEST
  + docker run hello-world
  <img width="780" height="525" alt="Ảnh chụp màn hình 2026-04-13 165803" src="https://github.com/user-attachments/assets/6eaced98-3f01-402d-bb6c-674e96f3085f" />
6. Tìm hiểu tập lệnh của docker và docker compose
- Lệnh docker
  + docker --version: Kiểm tra phiên bản Docker
  + docker run hello-world: Chạy container để kiểm tra Docker hoạt động
  + docker ps: Xem các container đang chạy
  + docker ps -a: Xem tất cả container (kể cả đã dừng)
  + docker images: Xem danh sách các image
  + docker logs <container_name>: Xem log của container
  + docker stop <container_name>: Dừng container
  + docker rm <container_name>: Xóa container
- Lệnh docker compose
  + docker compose up -d: Chạy toàn bộ service trong docker-compose.yml
  + docker compose down: Dừng toàn bộ service
  + docker compose ps: Xem trạng thái các container
  + docker compose logs: Xem log các service
  + docker compose restart: Restart lại service
  + docker compose up -d --build: Build và chạy lại container
7. Đảm bảo tường lửa trên Ubuntu đã cho phép các cổng 80, 1880, 9630 (Lệnh: sudo ufw allow ...)
<img width="773" height="510" alt="Ảnh chụp màn hình 2026-04-13 170209" src="https://github.com/user-attachments/assets/18d1aadd-4d3d-461e-b55b-858b7fd84125" />

