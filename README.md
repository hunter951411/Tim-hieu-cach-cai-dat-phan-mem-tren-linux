# Tim-hieu-cach-cai-dat-phan-mem-tren-linux
Tìm hiểu cách cài đặt phần mềm trên linux

#1. Cài đặt phần mềm trên Ubuntu - Debian

#1.1 Cài phần mềm tải về

- Các gói dành cho Ubuntu thường có đuôi là .deb (Debian). Sau khi tải về file .deb ta sẽ cài bằng lệnh sau:

**#dpkg -i [đường_dẫn_đến_file_.deb]**

- Khi không còn muốn sử dụng và muốn gỡ ta dùng lệnh sau:

**#dpkg -r [tên_của_file]** (chú ý không có .deb)

- Hoặc ta cũng có thể dùng lệnh:

**#apt-get remove [tên_phần_mềm]**

#1.2 Tìm nguồn phần mềm

- Tìm trong apt-cache bằng lệnh:

**#apt-cache search [tên_phần_mềm]**

- Nếu bạn bkhoong biết chính xác tên của phần mềm ta có thể dùng lệnh:

**#dpkg --list | grep [từ_khóa]**

- Sau khi tìm được chính xác tên cần cài đặt

**apt-get install [tên_phần_mềm]**

**Note**: Có thể cài nhiều phần mềm cùng một lúc bằng cách thêm dấu phẩy vào giữa các phần mềm.

#1.3 Cài đặt phần mềm tự động

- Để cập nhập danh sách nguồn phần mềm, ta dùng lệnh:

**#apt-get update**

- Trường hợp phần mềm cần cài chưa có trong danh sách mặc định của Ubuntu, thì cầ phải thêm dòng định nghĩa vào trong tập tin /etc/apt/sources.list. 

- Để cài phần mềm dùng lệnh:

**apt-get install [tên_phần_mềm]**

- Trước khi cài phần mềm, nên cập nhập danh sách nguồn mới nhất. Ubuntu sẽ tự động kiểm tra phiên bản mới nhất, tìm và tải về các phần mềm cần thiết và cài đặt vào server.


#3 Cài đặt phần mềm trên Centos - Redhat

Có 2 dạng nén thông thường là gzip(thường) và bzip2 (mạnh hơn)

##3.1 GZIP
- gõ **#gzip <file>** sẽ nén file và tạo ra file.gz đồng thời xóa file đi 
http://prntscr.com/8r4hba
- Hoặc **#gzip -c file1 file2 > filenen.gz** sẽ nén và gộp file <flie1> <file2> và tạo ra <output> nhưng vấn giữ lại file1 và file2
http://prntscr.com/8r4kkj
- Hoặc **gzip -r <thư mục cần nén>** Nén thư mục

- Để giải nén thì dùng lệnh **#gunzip file.gz** và cũng tạo ra file đồng thời xóa file .gz 

##3.2 Bzip2

- **#bzip2 file** sẽ nén file tạo ra file.bz2 đồng thời xóa file đi

- Để giải nén thì dùng lệnh **bunzip2 file.bz2** cũng tạo ra file đồng thời xóa file .bz2

##3.3 TAR

- Là lệnh gom file theo kiểu storage:
<ul>
<li>**#tar -cf output file1 file2** gom file1 và file2 thành output </li>
<li>**#tar -xf file.tar** bung file ra</li>
</ul>

##3.4 Cài đặt phần mềm với rpm

- Các file RPM có cấu trúc như sau:
<tên gói>-<phiên bản>-<bản phân phối>.<kiến trúc>.rpm
- Với:
<bản phân phối -release>: Số hiệu bản vá vối của phần mềm
<kiến trúc>: nền tảng phần cứng mà gói chạy trên đó.
- Nếu <kiến trúc> là "noarch" nghĩa là nó không phục thuộc vào nền tảng phần cứng. còn "src" nghĩa là đây là mã nguồn cho người sử dụng có thể chỉnh sửa.
- Ví dụ:
**dhcp-4.3.3-3.fc24.src.rpm**
<tên>               dhcp
<phiên bản>         4.3.3
<bản phân phối>     3.fc24
<kiến trúc>         src

- Gõ rpm: lệnh cài đặt gói rpm, một số option hay dùng như sau:
<ul>
<li>-i <gói> cài đặt</li>
<li>-e <tên phần mềm> gỡ bỏ</li>
<li>-U <gói> cập nhập gói(gỡ gói cũ và cài gói mới)</li>
<li>-q <tên phần mềm> in ra tên, phiên bản release, nếu đã được cài</li>
<li>-p <tên gói> in ra thông tin của cả những gói chưa được cài, nhưng phải chỉ rõ đường dẫn <tên gói></li>
<li>-i <tên phần mềm> in ra thoogn tin, nếu đã được cài</li>
<li>-V kiểm tra tính toàn vẹn</li>
<li>--nodeps không kiểm tra các gói phụ thuộc khi cài đặt và cập nhập cũng như gỡ bỏ</li>
<li>--force cài đặt, cập nhập và bỏ cũ</li>
<li>--import nhập GPG Key(/etc/pki/rpm-gpg/RPM_GPG_KEY-CENTOS-<version>)</li>
<li>--replacefiles giải quyết khi có đụng độ trong việc ghi files cho gói cài đặt</li>
</ul>

Ví dụ:
      rpm -ivh <gói>
      rpm -e -nodeps <tên phần mềm>
      
###3.4.2 Cài đặt từ DVD/CD của Centos và rpm

- Mount DVD, CD
- cd vào thư mục đã mount (/media), tìm gói tương ứng muốn cài và gõ rpm -i <tên gói>

- Việc cài đặt một package sẽ xảy ra thất bại khi xảy ra một trong 3 điều sau
