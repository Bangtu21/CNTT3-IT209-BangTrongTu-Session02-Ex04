1. Mục tiêu
Cấu hình UFW trên Ubuntu VPS để:

Từ chối các kết nối vào mặc định.
Cho phép kết nối SSH qua port 22.
Cho phép truy cập HTTP qua port 80.
Chặn các port không được cho phép.
2. Cấu hình UFW

Các lệnh đã thực hiện:

sudo ufw default deny incoming

sudo ufw default allow outgoing

sudo ufw allow 22/tcp

sudo ufw allow 80/tcp

sudo ufw enable

3. Kiểm tra trạng thái UFW

Lệnh kiểm tra:
sudo ufw status verbose

Kết quả:

Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW IN    Anywhere
80/tcp                     ALLOW IN    Anywhere
22/tcp (v6)                ALLOW IN    Anywhere (v6)
80/tcp (v6)                ALLOW IN    Anywhere (v6)

UFW hoạt động với chính sách mặc định deny đối với kết nối vào. Chỉ port 22 và 80 được phép truy cập.

4. Kiểm tra SSH

Từ máy cá nhân thực hiện kết nối SSH:

ssh root@160.250.246.219

Kết quả: Kết nối SSH thành công qua port 22.

5. Kiểm tra HTTP

Truy cập trên trình duyệt:

http://160.250.246.219

Kết quả: Trang web giới thiệu cá nhân hiển thị thành công qua port 80.

6. Kiểm tra port bị chặn

Từ máy cá nhân thực hiện:

curl -I --connect-timeout 5 http://160.250.246.219:8080

Kết quả:

curl: (28) Connection timed out after 5005 milliseconds

Port 8080 không được phép truy cập và kết nối bị timeout.
