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
<ul>
<li>Package xxx is already installed: Package cần cài đã được cài đặt rồi. Giải quyết bằng cách: không cài nữa hoặc cài đè lên thì thêm tham số --replacepkgs hoặc -force.</li>
<li>Conflicting file: Package đang cần ghi một file vào một nơi đã có file khác trùng tên rồi. Giải quyết bằng cách không cài nữa hoặc ghi đè lên file đã có sẵn bằng cách thêm tham số --replacefiles.</li>
<li>Failed dependecncy: Package cần cài phụ thuộc vào package khác chưa được cài trước đó. Cách giải quyết là cài package phụ thuộc vòng: gói A phục thuộc B, B phụ thuộ C, C phụ thuộc A. Để cài được gó A chỉ viêc cài đồng thời cả 3 gói A, B, C tức là rpm -ivh A B C. Có thể dùng kí tự đại diện *, ? để cài đồng thời nhiều gói cùng 1 lúc.</li>
</ul>

- Cài gói rpm ở dạng source code .src.rpm

- Có nhiều khi gói phần mềm rpm được cung cấp ở dạng source code, tên những gói này có phần đuôi là .src.rpm. Trước hết cần build nó thành một gói binary rpm bằng lệnh:

**rpm -rebuild filename.src.rpm**

Sau lệnh rebuild, gói binary vừa tạo ra được đặt trong /usr/src/redhat/RPM/; chỉ cần vào thư mục này và cài gói vừa tạo ra như bình thường.

- Kiểm tra tính toàn vẹn: Khi một gói phần mềm được cài đặt vào trong máy, cơ sở dữ liệu RPM lưu thông tin về từng file của gói phần mềm đó. Có 8 trường thông tin cho mỗi file: file size, file permission, mã md5 được tính ra từ nội dung file, major/minor number (nếu file đó là device file), đối tương được trỏ đến bởi file (nếu file là symbolic linkk), chủ sở hữu file, nhóm chủ sở hữu file, quyền truy cập file. RPM cũng lưu thông tin về kiểu file (kiểu file ở đây không phải là kiểu file của Linux mà là kiểu file trong gói phần mềm): file cấu hình, file tài liệu hướng dẫn, file ảo (xuất hiện sau khi đã cài package, không nằm trong package nguyên thủy), file chứa thông tin bản quyền, file readme. Khi verify file, 8 trường thông tin của file sẽ được so sánh với thông tin lưu trong RPM database. Nếu khớp sẽ hiển thị dấu chấm, không khớp sẽ hiển thị kí hiệu của trường thông tin trước đó, nếu không kiểm tra được sẽ hiển thị dấu ?.

##3.5 Cài đặt với YUM

- YUM (Yellowdog Updater Modified) là phương pháp cài đặt phần mềm có xu hướng tự động hóa và tập trung hóa. Người dùng chỉ việc đánh lệnh, và yum sẽ kết nối với server cập nhập, cài đặt hay gỡ bỏ phần mềm dựa trên những thông tin về các gói cài đặt sẵn có trên Interner

- Trên Centos mặc định là có sẵn lệnh **yum**. Để kiểm tra phiên bản lệnh yum ta dùng lệnh:

      **#yum --version**

- Cài đặt các gói thông tin lưu trữ (Repository ) cho yum: Để cài được hầu hết các phần mềm phổ biến bằng lệnh YUM, cần phải bổ sung thêm các gói thông tin lưu trữ YUM bằng lệnh sau:
<ul>
<li>Lệnh cài đặt EPEL Repository bằng YUM: **#yum install epel-release**</li>
<li>Lệnh cài đặt EPEL Repository cho HĐH CENTOS 64 bit: **#rpm -Uvh http://pkgs.repoforge.org/rpmforge-release/rpmforge-release-0.5.3-1.el4.rf.x86_64.rpm**</li>
</ul>

##1. Lệnh **yum check-update** và **yum list updates**

- Là lệnh có chức năng tương tự như nhau là dùng để cập nhật thông tin và danh sách các gói phần mềm được hỗ trợ cài đặt bằng lệnh YUM. Lưu ý là dòng lệnh này không cài đặt phần mềm mà chỉ là cập nhật danh sách các phần mềm được hỗ trợ của YUM. Cú pháp:

      **#yum check-update**

      **#yum list updates**

##2. Lệnh **yum list all và **yum list**

- Là lệnh dùng để liệt kê tất cả các gói phần mềm có thể được cài đặt bằng lệnh YUM và những phần mềm đã được cài đặt. Cú pháp:

      **#yum list all**

      **#yum list**

##3. Lệnh **yum list installed**

- Là lệnh liệt kê tất cả các phần mềm đã được cài đặt. Nếu bạn muốn kiểm tra phần mềm nào đó đã cài đặt hay chưa thì có thể dùng lệnh sau :

      **#yum list installed tên_phần_mềm**

##4. Lệnh **yum list available**

- Là lệnh liệt kê tất cả các phần mềm có thể cài đặt bằng lệnh YUM. Cú pháp:

      **#yum list available**

##5. Lệnh **yum info**

- Là lệnh dùng để xem thông tin của gói phần mềm. Ví dụ lệnh trên là để xem thông tin của phần mềm nginx. Cú pháp:

      **#yum info nginx**


##6. Lệnh **yum search**

- Là lệnh dùng để tìm kiếm gói phần mềm được hỗ trợ cài đặt bằng yum. Ví dụ lệnh trên là để tìm phần mềm nginx, tất cả những phần mềm có tên file hoặc thông tin có chứa ký tự nginx sẽ được liệt kê bên dưới. Cú pháp:

      **#yum search tên_phần_mềm**

##7. Lệnh **yum install**

- Là lệnh dùng để cài đặt gói phần mềm do bạn chỉ định. Cú pháp:

      **#yum install tên_phần_mềm**


##8. Lệnh **yum update**

- Là lệnh dùng để kiểm tra và cập nhật phiên bản mới nhất của gói phần mềm. Nó sẽ cập nhật phiên bản mới nhất cho tất cả các gói phần mềm đã được cài đặt trên server. 
 
      **#yum update**

- Nếu bạn muốn chỉ kiểm tra và cập nhật phiên bản mới nhất cho 1 phần mềm bạn chỉ định thì sử dụng lệnh: 

      **#yum update tên_phần_mềm**


##9. Lệnh **yum remove**

- Là lệnh dùng để gỡ bỏ và xoá gói phần mềm do bạn chỉ định.

      **#yum remove tên_phần_mềm**
      
##10.Lệnh **yum clean all**

- Thông thường YUM sẽ tạo và sử dụng cache cho các lần truy vấn, để xoá hết cache của yum thì bạn chạy lệnh sau :

      **#yum clean all**
