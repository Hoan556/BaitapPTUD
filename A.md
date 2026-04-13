# BaitapPTUD
 ## A. Đăng ký tên miền xịn cho cá nhân:
Đăng ký domain xịn (có thể dùng của mắt bão, tên miền *.id.vn đang miễn phí cho mọi công dân việt nam <= 23 tuổi, *.io.vn : giá 30k vnđ/năm)
Đăng ký tài khoản cloudflare
Thêm domain đã đăng ký vào trong cloudflare : Nhận 2 dòng namespace
Nhập 2 dòng namespace của cloudflare vào trong trang quản lý DNS record của tên miền đăng ký (vd trên mắt bão)
# BÀI LÀM
## 1 Đăng ký domain
Truy cập đường link : https://www.matbao.net/ten-mien/ten-mien-mien-phi.html để vào Mắt Bão
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c82b9068-c283-4523-b625-754e2c81f50f" />
Sau khi vào Mắt bão ta sẽ thực hiện hiện đăng kí domain bằng cách nhập tên miền, sau đó thực hiện các thao tác trang web yêu cầu để đăng kí tên miền
kết quả sau khi đăng kí thành công
<img width="1290" height="2796" alt="image" src="https://github.com/user-attachments/assets/b1547ccb-b2ab-4292-8768-07f4a24c18ba" />
## 2 Đăng ký tài khoản [cloudflare]
Vào trang chủ của Cloudflare , nhấn sign in để tạo tài khoản và thực hiện nhập các thông tin theo yêu cầu.
<img width="1920" height="1080" alt="Ảnh chụp màn hình 2026-04-13 090431" src="https://github.com/user-attachments/assets/bc8dc3a4-e478-4ac9-8645-615b4fca5285" />
## 3. Thêm domain đã đăng kí vào Cloudflare : nhận 2 dòng namespace
thêm domain vào Cloudflare bằng chức năng "Add a Site" và chọn gói miễn phí. Hệ thống đã cung cấp hai bản ghi Nameserver, em đã lưu lại để sử dụng trong bước cấu hình DNS tiếp theo.
[ luciana.ns.cloudflare.com ]
[ patrick.ns.cloudflare.com ]
<img width="1920" height="1080" alt="Ảnh chụp màn hình 2026-04-13 090658" src="https://github.com/user-attachments/assets/17b7a068-139e-4250-b799-76aa46ac0ba1" />
4. Nhập 2 dòng namespace của cloudflare vào trong trang quản lý DNS record của tên miền đăng ký (vd trên mắt bão)
<img width="1920" height="1080" alt="Ảnh chụp màn hình 2026-04-13 091108" src="https://github.com/user-attachments/assets/d5dc4cab-ba85-4c88-bdf4-3b552e6cdab7" />
Vào quản lý tên miền Tìm mục: Tên miền (Domains) → Chọn domain (tenban.id.vn)
- Sửa Nameserver Xoá cái cũ: ns1.matbao.com ns2.matbao.com - Nhập cái mới của Cloudflare: - [ luciana.ns.cloudflare.com ] - [ patrick.ns.cloudflare.com ] - Bấm: Save / Update / Apply
- <img width="1920" height="1080" alt="Ảnh chụp màn hình 2026-04-13 091256" src="https://github.com/user-attachments/assets/fd3ff9f4-ddb9-4219-8565-494ba602296d" />
- Sau khi thực hiện các bước đăng ký tên miền và cấu hình Nameserver trên Cloudflare, hệ thống đã hiển thị trạng thái “Active”. Điều này chứng tỏ domain đã được kết nối thành công với Cloudflare và có thể sử dụng để triển khai các dịch vụ web. -
- <img width="1920" height="1080" alt="Ảnh chụp màn hình 2026-04-13 092607" src="https://github.com/user-attachments/assets/8041cdb6-4632-4a57-a912-9d8e7eecbc3b" />



