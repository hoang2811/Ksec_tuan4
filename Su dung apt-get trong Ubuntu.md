##Sử dụng apt-get trong ubuntu

###Giới thiệu về APT

Lúc bắt đầu có .tar.gz. Người dùng phải biên dịch mỗi chương trình họ muốn sử dụng trên hệ thống GNU/Linux. Khi Debian được tạo ra, nó đã cho thấy cần phải có một hệ thống bao gồm một phương thức quản lý các gói được cài đặt trên máy tính. Và hệ thống đó được đặt tên là dpkg. Như vậy, 'package' nổi tiếng đầu tiên xuất hiện trong GNU/Linux, một thời gian trước khi Red Hat quyết định tạo ra hệ thống 'rpm' của chính họ. 
Một tình huống mới nhanh chóng nảy sinh trong suy nghĩ của những người làm ra GNU/Linux. Họ cần một cách nhanh, thực tế, và hữu ích để cài các gói, cái mà sẽ quản lý tự động các phụ thuộc và lưu giữ những tệp cấu hình khi nâng cấp. Một lần nữa, Debian lại đi đầu và cho ra đời APT, viết tắt của Advanced Packageing Tool.

####Các lệnh
Tất cả các lệnh được nói đến đều phải chạy với tài khoản **root** hoặc với quyền siêu người dùng, xem sudo để biết thêm thông tin. Thay tên-gói trong các lệnh bằng tên của gói bạn muốn cài đặt.

####Lệnh cài đặt

* `sudo apt-get install tên-gói`

Lệnh này sẽ cài đặt một gói mới.

* `sudo apt-get build-dep tên-gói`

Lệnh này sẽ tìm kiếm trên kho và cài đặt những gói phụ thuộc cần thiết để có thể cài đặt gói từ mã nguồn. Nếu gói không có trong kho, lệnh sẽ trả về một lỗi.

* apt-get chấp nhận một danh sách các gói làm tham số cài đặt, ví dụ:

`sudo apt-get install tên-gói-1 tên-gói-2 tên-gói-3 ...`

Dùng tùy chọn -s để giả lập một hành động. "sudo apt-get -s install tên-gói" sẽ giả lập việc cài đặt một gói, cho bạn biết nơi gói sẽ được cài đặt và cấu hình của nó. 

####Lệnh tìm gói
Lệnh này sẽ giúp chúng ta tìm 1 gói, hoặc 1 chương trình nào đó trong ubuntu. Ví dụ tôi không nhớ chính xác tên gói cài đặt của chương trình amarok làm sao để cài đặt bằng lệnh, việc này thực hiện rất đơn giản 

`sudo apt-cache search tham số`

Tham số có thể là tên chương trình hay là ghi chú .... nó sẽ trả về tên gói + ghi chú kế bên sau đó bạn chỉ cần sử dụng lệnh apt-get install để cài đặt 

####Lệnh bảo quản

* `sudo apt-get update`

Chạy lệnh này sau khi thay đổi */etc/apt/sources.list* hoặc */etc/apt/preferences*. Để biết thêm về */etc/apt/preferences* xem [PinningHowto](https://help.ubuntu.com/community/PinningHowto) Chạy lệnh này thường xuyên giúp danh sách nguồn của bạn được cập nhật. Nó tương đương với "Reload" trong Synaptic hoặc "Fetch updates" trong Adept.

* `sudo apt-get upgrade`

Lệnh này nâng cấp tất cả các gói đã cài đặt. Nó tương đương với "Mark all upgrades" trong Synaptic. 

* `sudo apt-get dist-upgrade`

Lệnh này nâng cấp toàn hệ thống tới một phiên bản mới hơn. Nó tương tự như ở trên, ngoại trừ thêm đánh dấu thêm "smart upgrade". Nó báo APT sử dụng hệ thống giải quyết xung đột thông minh, và nó sẽ thử nâng cấp những gói quan trọng nhất. Đây không phải là cách được khuyên để nâng cấp bản phân phối, xem Cách nâng cấp bản phân phối để biết thêm thông tin. 

* `sudo apt-get check`

Lệnh này là một công cụ để chuẩn đoán. Nó không cập nhật danh sách nguồn, mà chỉ kiểm tra lỗi phụ thuộc.

* `sudo apt-get -f install`

Lệnh này tương tự như **Edit** -> **Fix Broken Packages** trong Synaptic. Chạy nó nếu bạn nếu bạn gặp phải lỗi phụ thuộc của các gói.

* `sudo apt-get autoclean`

Lệnh này gỡ bỏ các tệp cài đặt .deb đã cũ trong hệ thống của bạn. Phụ thuộc vào thói quen cài đặt của bạn, xóa bỏ các tệp trong /var/cache/apt/archives có thể thu hồi một lượng không gian đĩa đáng kể.

* `sudo apt-get clean`

Lệnh này tương tự như trên nhưng nó sẽ xóa bỏ tất cả các gói trong nơi lưu trữ. Nó không tốt lắm nếu bạn đang sở hữu một đường truyền Internet chậm, vì khi cài đặt sẽ phải tải lại các gói (đáng ra có sẵn tại nơi lưu trữ).

* Nơi lưu trữ các gói đã được cài đặt là /var/cache/apt/archives. Lệnh:

`du -sh /var/cache/apt/archives`

sẽ cho biết dung lượng các gói được lưu trữ. 
