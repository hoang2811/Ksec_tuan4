

####Phần 1 : Cài đặt Apache2

* Bước 1 : Chuyển sang quyền **root**  ( nếu bỏ qua bước này thì trước các câu lệnh dưới thêm **sudo** vào đầu dòng lệnh)

`sudo su`

![](http://imgur.com/JjuOoxD.png)

Nhập mật khẩu -> Enter

* Bước 2 : Cập nhật các **Repository**:

`apt-get update`

![](http://imgur.com/VhczcFe.png)

Bước 3 : Cài đặt apache2 bằng lệnh

`apt-get install apache2`

![](http://imgur.com/RBfukAC.png)

Gõ "**Y**" rồi Enter

Quá trình cài đặt sẽ diễn ra trong ít phút

![](http://imgur.com/hXxIghS.png)

Sau đó start dịch vụ apache2:

`service  apache2  restart`

![](http://imgur.com/iKWMRjQ.png)

Sau khi mọi thứ hoàn thành, bạn đã có một web server sẵn sàng. Để kiểm tra nó, trước tiên phải dò địa chỉ IP của server, gõ lệnh:

`ifconfig | grep inet`

![](http://imgur.com/TCk9B3D.png)

IP là cái IP đầu tiên trả về. Như bạn thấy, ở đây, IP là 192.168.254.132. Mở trình duyệt và truy cập vào địa chỉ IP. Nếu bạn thấy dòng chữ "It works!" (Nó đang chạy), thì web server đã chạy.

![](http://imgur.com/yeXp9iO.png)

####Phần 2: Cấu hình Apache2

Lưu ý bạn một số file  và thư mục cần lưu tâm:

**/var/www** : Thư mục mặc định chứa website

**/etc/apache2/apache2.conf** : File cấu hình Apache2

**/etc/apache2/mods-enabled** : Thư mục chứa các module của Apache module (các module đang hoạt động

**/etc/apache2/sites-enabled** : Thư mục chứa các cài đặt định danh cho các website (Virtual Host)

**/etc/apache2/conf.d** : Các cấu hình mở rộng cho Apache.

Sau khi cài đặt Apache, ứng dụng sẽ được thêm vào danh sách init.d của hệ thống, do đó có thể tự khởi động cùng với hệ điều hành. Sử dụng những lệnh sau để khởi động, kích hoạt và ngừng hoạt động của Apache:

`sudo /etc/init.d/apache2 start` #chạy apache

`sudo /etc/init.d/apache2 stop` #dừng apache

`sudo /etc/init.d/apache2 restart` #khởi động lại apache

Nếu không muốn Apache tự khởi động cùng hệ thống, gõ lệnh sau:

`sudo update-rc.d -f apache2 remove`

Còn nếu muốn làm ngược lại quá trình trên (khởi động cùng hệ thống) thì sử dụng lệnh:

`sudo update-rc.d apache2 defaults`


