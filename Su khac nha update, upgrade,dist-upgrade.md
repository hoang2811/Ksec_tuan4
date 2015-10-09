##So sánh sự khác nhau giữa update, upgrade và dist-upgrade

|Task |Red Hat/Fedora| Ubuntu|
|-----------|-------------------------------|----------------------------|
|Làm mới list và repository| Tự động khi chạy lệnh Yum |apt-get update |
|Cập nhật phiên bản| yum update rpm -Uvh [args]| apt-get upgrade|
|Cập nhật nhân| yum upgrade |apt-get dist-upgrade|

####Cụ thể
######1.Update
- Lệnh update cho chúng ta cập nhập các package . Câu lệnh trên sẽ cập nhập tất cả các package từ các repository

######2.Upgrade vs Dist-Upgrade
- Thông thường các phần mềm mã nguồn mở thường được nâng cấp nhiều lần và thường xuyên có các bản cái tiến . Upgrade sẽ cho chúng ta biết các package nào cần được cập nhập và tao có thể xác nhận lại những câp nhập đó .
- Upgrade sẽ thay thế hoàn toàn phiên bản cũ bằng phiên bản mới
- Tuy nhiên có 1 vài trường hợp , 1 số phần mềm lại yêu cầu gói cài đăt trước đó vì vậy ta s dung dist-upgrade
- Lệnh này thực sự hữu ích nếu bạn không chắc rằng việc cập nhật này có ảnh hưởng đến các thành phần khác trong hệ thống hay không
