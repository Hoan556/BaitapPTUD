# C. Cấu hình docker compose:
Tạo thư mục: ~/myapp
Chuyển vào trong thư mục ~/myapp
Tạo thư mục: ./myweb
Tạo file ./myweb/index.html (với nội dung là thông tin cá nhân của em)
Tạo file docker-compose.yml để nó sẽ có các dịch vụ sau:
Khai báo sử dụng nodered/node-red, cổng 1880, dữ liệu nằm tại thư mục ./nodered
Khai báo sử dụng nginx, cổng 80, cấu hình trong file ./nginx/nginx.conf
Mount thư mục ./myweb thành thư mục /myweb trong nginx
Mount file ./nginx/nginx.conf vào file /etc/nginx/nginx.conf trong nginx
Edit file ./nginx/nginx.conf để:
Cấu hình web server cổng 80
server_name là sub-domain (sub-domain tuỳ ý của em)
location / trỏ tới root là thư mục /myweb
location /api dùng proxy_pass trỏ tới 1 (hoặc nhiều) node http_in của nodered
Edit file ./nodered/settings.js để nodered bắt buộc đăng nhập
Chạy docker-compose lần đầu để Node-RED tự sinh file cấu hình trong thư mục ./nodered, sau đó mới tiến hành sửa settings.js và restart lại container

# BÀI LÀM
## 1. Tạo thư mục: ~/myapp
<img width="658" height="86" alt="Ảnh chụp màn hình 2026-04-13 171019" src="https://github.com/user-attachments/assets/7ccc96d2-2f53-4c91-affb-930cce435980" />

## 2. Chuyển vào trong thư mục ~/myapp
<img width="626" height="52" alt="Ảnh chụp màn hình 2026-04-13 171110" src="https://github.com/user-attachments/assets/26af7ba2-c6b9-4696-b871-5acc5e2e8ef2" />
## 3.Tạo thư mục: ./myweb
mkdir myweb
<img width="656" height="82" alt="Ảnh chụp màn hình 2026-04-13 171215" src="https://github.com/user-attachments/assets/c80d6299-1551-454c-a139-f6fceafea39f" />
## 4. Tạo file ./myweb/index.html (với nội dung là thông tin cá nhân của em)
nano myweb/index.html
<img width="798" height="427" alt="Ảnh chụp màn hình 2026-04-13 171637" src="https://github.com/user-attachments/assets/0f980ec7-a526-45d1-9ed4-709728d5b2ca" />
5. Tạo file docker-compose.yml để nó sẽ có các dịch vụ sau:
- tạo file docker-compose.yml
- gõ: nano docker-compose.yml để tạo file
<img width="791" height="447" alt="Ảnh chụp màn hình 2026-04-13 171957" src="https://github.com/user-attachments/assets/7dd255c0-055c-4d14-9e4a-afc69040567a" />
  tạo thư mục Nginx và nodered ( vì máy chưa có)
mkdir nginx
mkdir nodered
<img width="768" height="117" alt="Ảnh chụp màn hình 2026-04-13 172220" src="https://github.com/user-attachments/assets/d5506b3a-4ccd-4ebe-a18d-dd0e0f768a99" />
Khai báo sử dụng nodered/node-red, cổng 1880, dữ liệu nằm tại thư mục ./nodered

Khai báo sử dụng nginx, cổng 80, cấu hình trong file ./nginx/nginx.conf

nano nginx/nginx.conf
<img width="792" height="340" alt="Ảnh chụp màn hình 2026-04-13 173413" src="https://github.com/user-attachments/assets/6e800194-7774-4544-bf17-7b0a383b4849" />
<img width="915" height="882" alt="Ảnh chụp màn hình 2026-04-13 174355" src="https://github.com/user-attachments/assets/a809ad36-ed12-45f6-944e-23b8d3934ec2" />
- Mount thư mục ./myweb thành thư mục /myweb trong nginx
  <img width="1920" height="1080" alt="Ảnh chụp màn hình 2026-04-13 174942" src="https://github.com/user-attachments/assets/33a52e6b-0c59-423b-95cc-0f7ba4006e7f" />
-Mount file ./nginx/nginx.conf vào file /etc/nginx/nginx.conf trong nginx
<img width="1257" height="669" alt="image" src="https://github.com/user-attachments/assets/d4e4ac69-8ffe-4069-8315-de87ea4a667a" />
6. Edit file ./nginx/nginx.conf để:
Cấu hình web server cổng 80
Mở file cấu hình nano nginx/nginx.conf
<img width="957" height="447" alt="Ảnh chụp màn hình 2026-04-13 180953" src="https://github.com/user-attachments/assets/db2e8eaf-0f96-4156-9efe-7dd5bea7c8fe" />
location / trỏ tới root là thư mục /myweb
Mở file cấu hình nano nginx/nginx.conf
