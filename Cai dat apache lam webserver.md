# 
Cài đặt Apache2 trên Ubuntu rất đơn giản và Nhanh chóng. Trong bài viết này mình sẽ hướng dẫn cài đặt và cấu hình Apache2 trên Ubuntu Server 12.04.
Phần 1 : Cài đặt Apache2

Bước 1 : Chuyển sang quyền root

sudo su

Cài đặt Apache2 trên Ubuntu Server

Nhập mật khẩu -> Enter

Bước 2 : Cập nhật các Repository:

apt-get update

Bước 3 : Cài đặt apache2 bằng lệnh

sudo apt-get install apache2

Cài đặt Apache2 trên Ubuntu Server

Gõ "Y" rồi Enter

Quá trình cài đặt sẽ diễn ra trong ít phút

Cài đặt Apache2 trên Ubuntu Server

sau khi hoàn tất, bạn hãy mở bất kỳ trình duyệt nào và gõ vào địa chỉ IP server bạn. Ví dụ http://192.168.168.130

Nếu màn hình hiện ra "It works" có nghĩa bạn đã cài đặt thành công apache2 trên Ubuntu Server

Cài đặt Apache2 trên Ubuntu Server

Phần 2: Cấu hình Apache2

Trước khi bắt đầu, thủ thuật việt nam lưu ý bạn một số file  và thư mục cần lưu tâm

/var/www : Thư mục mặc định chứa website

/etc/apache2/apache2.conf : File cấu hình Apache2

/etc/apache2/mods-enabled : Thư mục chứa các module của Apache module (các module đang hoạt động

/etc/apache2/sites-enabled : Thư mục chứa các cài đặt định danh cho các website (Virtual Host)

/etc/apache2/conf.d : Các cấu hình mở rộng cho Apache.

Sau khi cài đặt Apache, ứng dụng sẽ được thêm vào danh sách init.d của hệ thống, do đó có thể tự khởi động cùng với hệ điều hành. Sử dụng những lệnh sau để khởi động, kích hoạt và ngừng hoạt động của Apache:

sudo /etc/init.d/apache2 start #chạy apache
sudo /etc/init.d/apache2 stop #dừng apache
sudo /etc/init.d/apache2 restart #khởi động lại apache
Nếu không muốn Apache tự khởi động cùng hệ thống, gõ lệnh sau:

sudo update-rc.d -f apache2 remove

Còn nếu muốn làm ngược lại quá trình trên (khởi động cùng hệ thống) thì sử dụng lệnh:

sudo update-rc.d apache2 defaults

- See more at: http://thuthuatvietnam.com/cai-dat-va-cau-hinh-apache2-tren-ubuntu-server-1204.html#sthash.uViZglVA.dpuf
