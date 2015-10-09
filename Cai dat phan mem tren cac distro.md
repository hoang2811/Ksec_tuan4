Hầu hết các HDH Linux cũng có công cụ quản lý, cài đặt, gỡ bỏ phần mềm như Add or Remove Programs trong Windows. Ví dụ, trong Ubuntu, nếu server của có nối mạng thì bạn có thể download và cài đặt ứng dụng tự động thông qua công cụ Synaptic Package Manager (giao diện GUI) hoặc sử dụng dòng lệnh apt-get trong Terminal … File cài đặt cho ứng dụng trên Linux thường có phần mở rộng như .deb, .rpm, .bin, .tar, tar.gz, INSTALL, .sh …. Mỗi loại file cài đặt này có 1 cách thức thực thi cài đặt riêng.

##Cài đặt phần mềm trên Ubuntu – Debian
####1.Cài phần mềm tải về
Nếu vì lý do gì đó mà không cài tự động được, hoặc muốn cài phiên bản mới nhất, thường mình phải cài bằng tay thôi, nghĩa là tải bộ binary về rồi cài thôi. Phần biên dịch từ mã nguồn sẽ viết trong bài khác.

Các gói dành cho Ubuntu thường có đuôi là .deb bởi vì Ubuntu từ Debian mà ra. 

Sau khi tải về xong, dùng lệnh này để cài vô:

`#dpkg -i [đường dẫn đến file .deb]`

Còn nếu sau khi cài vào rồi, muốn gỡ ra thì dùng lệnh trên với tham ôố -r và không có đuôi .deb

`#dpkg -r [tên của file không có .deb]`

Tương tự muốn gỡ phần mềm đã cài tự động thì dùng lệnh:

`#apt-get remove [tên phần mềm]`

####2. Tìm nguồn phần mềm

Tìm trong apt-cache bằng lệnh:

`#apt-cache search [tên phần mềm]`

Hoặc nếu không biết chính xác thì có thể tìm một phần của tên phần mềm:

`#dpkg --list | grep [từ khóa]`

Sau khi tìm được chính xác tên cần cài đặt, dùng lệnh apt-get để tải về các phần mềm lệ thuộc và tự động cài vào:

`#apt-get install [tên phần mềm]`

Có thể cài một lúc nhiều phần mềm bằng cách ngăn nhau bởi dấu phẩy



####3. Cài đặt phần mềm tự động

Để cập nhật danh sách nguồn phần mềm, dùng lệnh:

`#apt-get update`

Nếu phần mềm chưa có trong danh sách mặc định của Ubuntu, thì cần phải thêm dòng định nghĩa vào trong tập tin /etc/apt/sources.list. Ví dụ muốn cập nhật phiên bản mới nhất của Oracle XE cho Ubuntu thì thêm dòng này vào:

`deb http://oss.oracle.com/debian unstable main non-free`

Để cài phần mềm, dùng lệnh:

`#sudo apt-get install [tên phần mềm]`

Trước khi cài phần mềm, nên cập nhật danh sách nguồn mới nhất.

Ubuntu sẽ tự động kiểm tra phiên bản mới nhất, tìm và tải về các phần mềm cần thiết và cài đặt vào server.

### * CÀI ĐẶT PHẦN MỀM TỪ TARBALL

Một tarball (thường là các file .tar , .tar.gz , .tgz , .tar.bz2 , .tbz2 ) gồm có mã nguồn cho chương trình mà bạn phải tự biên dịch, trình biên dịch (compile) như GCC… thì thường có sẵn trong Linux . Các bước cài đặt Tarball về cơ bản như sau

####1/ Giải nén tarball

Với những người còn mới với Linux thì tarball là một thuật ngữ được sử dụng chung nhằm ám chỉ một file có chứa các file khác. Nó gần giống như một file nén ZIP hoặc RAR trong Windows, ngoại trừ chương trình tar không nén các file

. Tar làm việc với một chương trình nén như gzip để nén các file, đây là lý do tại sao bạn thấy hai đuôi mở rộng (.tar và .gz). Các đuôi mở rộng này đôi khi còn được viết tắt là .tgz

 Tuy nhiên không cần phải chạy hai chương trình riêng biệt để bung các file mà chúng ta chỉ cần lệnh cho tar chạy các file thông qua gzip để giải nén. Bạn có thể sử dụng tiện ích đồ họa để bung các file này bằng cách kích đúp vào tarball từ bộ quản lý file của mình, hoặc có thể thực hiện điều đó bằng dòng lệnh:

**$ tar zxvf file.tar.gz** hoặc

**$ tar zxf file.tar.gz**

**$ tar zxf file.tgz**

**$ tar jxf file.tar.bz2**

**$ tar jxf file.tbz2**

Các tùy chọn chúng ta cung cấp cho tar được mô tả bên dưới:

 • **-z** để lệnh cho tar chạy file này thông qua gzip để giải nén (sử dụng –j cho các file bzip)

 • **-x để bung các file

 • **-v** cho “verbose”, để chúng ta có thể thấy danh sách các file đang bung

 • **-f** để lệnh cho tar rằng chúng ta đang làm việc với một file

####2/ Configure

Khi các file được bung ra, mở một command terminal và vào thư mục nơi các file được giải nén trong đó. Trước khi biên dịch, chúng ta cần chạy kịch bản cấu hình. Công việc của kịch bản cấu hình là kiểm tra hệ thống của bạn về tất cả những gì phần mềm cần thiết để biên dịch chương trình từ mã nguồn thành chương trình nhị phân có thể sử dụng được. Nó sẽ tìm kiếm những thứ như phiên bản GCC và các công cụ cần thiết khác để xây dựng phần mềm. Khi bạn nằm trong thư mục với tất cả các file đã được bung từ tarball (sử dụng lệnh cd để change directory), hãy đánh vào **./configure**

Nếu tất cả đều diễn ra tốt đẹp, lệnh trên sẽ kiểm tra một loạt các phần khác nhau của hệ thống bạn, sau đó đưa bạn trở lại dòng lệnh như bên dưới:

 Vấn đề gây ra lỗi chung nhất trong bước này là mất dependency. Hãy quan sát bất cứ lỗi nào mà bạn gặp phải để xác định xem gói phần mềm nào bị thiếu.

####3/ Make

Đây là phần cốt lõi của quá trình – nơi chúng ta biên dịch mã nguồn thành một chương trình có khả năng chạy. Đây là bước đơn giản nhất, chỉ yêu cầu một lệnh đơn giản. Nếu bước cấu hình hoàn tất mà không có lỗi, bạn chỉ cần đánh vào  make

Đối với các chương trình lớn, bước này có thể mất đến vài phút. Khi quá trình kết thúc, bạn sẽ được đưa quay trở lại shell nhắc lệnh

Chương trình của bạn lúc này đã hoàn toàn sẵn sàng cho sử dụng. Mặc dù vậy bạn vẫn nên chạy thêm một bước nữa để chương trình có thể được cài đặt hoàn toàn vào đúng location và có thể chạy từ bất cứ đâu.

####4/ Make install

Tất cả những gì cần thiết lúc này là copy chương trình vừa được biên dịch vào các thư mục hệ thống như /usr/bin để có thể chạy từ bất cứ thư mục nào mà không cần chỉ định đường dẫn đến các file. Do nó sẽ copy đến một thư mục bên ngoài thư mục chủ nên bạn có thể cần đến các đặc quyền root. Nếu bước này được hoàn tất mà không có lỗi, bạn hãy chạy **sudo make install** để copy các file. Đến đây, bạn đã hoàn thành xong phần việc của mình. Chương trình mới của bạn có thể được sử dụng giống như bất cứ chương trình nào đang chạy khác.

##Cài đặt phần mềm trên Redhat – Centos

Bản thân các gói RPM không chứa chương trình cài đặt, nó chỉ chứa các thông tin về các file sẽ được cài đặt, thông tin mô tả về phần mềm chứa trong gói và các file nằm trong gói RPM sẽ được cài đặt vào thư mục nào trong hệ thống. Các gói phần mềm dạng RPM được cài đặt vào hệ thống nhờ vào chương trình RPM có trong hệ thống.

Cách đơn giản nhất để cài một gói RPM, chẳng hạn gói foobar-1.0-1.i386.rpm là dùng lệnh:

`rpm -i foobar-1.0-1.i386.rpm`

Để theo dõi quá trình install, bạn có thể thêm tham số:

`rpm –ivh foobar-1.0-1.i386.rpm`

Để uninstall package đã được cài:

`rpm -e foobar`

Nếu có một file RPM mà không biết nó là phần mềm nào, bạn có thể lấy thông tin bằng lệnh:

`rpm -qpi koules-1.4-1.i386.rpm`

Nếu đã lỡ xóa một vài file nào đó và không chắc chắn rằng file đó đang còn cần thiết cho chương trình nào đó, bạn có thể xem thử hệ thống đang thiếu file cần thiết nào:

`rpm –Va`

Thường khi cài một gói RPM nào đó, đòi hỏi phải cài thêm các gói phụ thuộc, bạn phải đi tìm và cài đặt các gói phụ thuộc trước khi cài được gói phần mềm trên. Hoặc cũng có thể gộp chung lại trên một dòng lệnh với lệnh RPM một danh sách các file RPM, được cách nhau bởi dấu khoảng trắng.

Trong Redhat hoặc Mandrake ở các phiên bản mới, Software Package Installation cũng tương tự như trình Add/Removed Software trong Windows vậy. Các tiện ích đi kèm trong bộ cài đặt được liệt kê đầy đủ theo từng nhóm để tiện theo dõi. Khi cài đặt một phần mềm, chương trình sẽ tự động kiểm tra các gói phụ thuộc và sẽ yêu cầu bạn đưa các CD cần thiết vào trong quá trình cài đặt.

Một kiểu cài đặt phần mềm phổ biến khác là bạn cài đặt từ các gói mã nguồn, thường được viết bằng ngôn ngữ C. Các gói này có dạng file nén *.TAR.GZ, *.BZ hoặc *.SRC.RPM. Trong trường hợp này, máy tính của bạn phải có sẵn các bộ công cụ biên dịch và các thư viện lập trình.

Sở dĩ phải có dạng TAR vì các file phải được gói lại thành một file trước khi nén thành GZ hoặc BZ, chứ không thể nén trực tiếp từ nhiều file thành một file nén được. Bản thân file *.TAR không phải là một file nén mà chỉ là một file chứa một tập các file khác gom lại mà thôi.

Với các gói nén bằng TAR.GZ, bạn bung nén như sau:

`#tar xvzf file.tar.gz`

Sau khi giải nén, một thư mục chứa các file trong file nén được tạo ra. Bạn vào thư mục này và thực hiện quá trình biên dịch theo như file INSTALL hướng dẫn. Các bước thông thường (chứ không phải tất cả) là như sau:

`#./configure`

`# make`

`#make install`

Bước chạy lệnh configure là để chương trình script xác lập cấu hình hệ thống cho việc biên dịch chương trình. Tùy vào cấu hình máy mà có chế độ biên dịch phù hợp và tối ưu cho chính hệ thống đó.

Lệnh make dùng để biên dịch mã nguồn thành file thực thi. Sau đó lệnh install để cài đặt file đã biên dịch lên hệ thống.

Bạn cũng có thể dùng lệnh yum để cài đặt phần mềm, vd bạn muốn cái webserver gõ lệnh sau

`# yum install httpd`

Sau đó nhấn -y để xác nhận, hoặc có thể tìm một gói cài đặt bằng cách dùng lệnh yum search, sẽ liệt kê các gói cần cài đặt

`# yum search httpd`





##So sánh các giải pháp cài đặt phần mềm

####1.RPM
- Do Redhat phát triển.
- Cài đặt các gói binary ( nhị phân ) đã được biên dịch rồi
- Cài đặt không sử dụng internet
- Thủ công
- Mất nhiều thời gian 
- Không có khả năng tùy chọn
- Sử dụng:
      + **rpm -Uvh package_name.rpm**            : Cài đặt
      + **rpm -e package_name**                  : Xóa phần mềm
      
####2.YUM
- Do Redhat phát triển
- Cài đặt các gói binary ( nhị phân ) đã được biên dịch rồi
- cài đặt sử dụng internet
- Nhanh và dễ dàng
- Không tối ưu
- Sử dụng:
      + **yum install package_name -y**   : Cài đặt
      + **yum remove package_name**       : Xóa

####Compile
- Hỗ trợ tất cả các distro
- Không cần sử dụng internet khi cài (cần internet để tải phần mềm về)
- thủ công và phức tạp
- Tối ưu tài nguyên và bảo mật
- Sử dụng:
      + Định dạng file source <br>
        `- tar -xvzf package_name.tar.gz` <br>
        `- tar -jvxf package_name.tar.bz2`
      + **./configure -prefix=/path**
      + make
      + make install
        
