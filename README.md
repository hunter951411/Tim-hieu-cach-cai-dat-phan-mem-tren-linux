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

Lúc bắt đầu có .tar.gz. Người dùng phải biên dịch mỗi chương trình họ muốn sử dụng trên hệ thống GNU/Linux. Khi Debian được tạo ra, nó đã cho thấy cần phải có một hệ thống bao gồm một phương thức quản lý các gói được cài đặt trên máy tính. Và hệ thống đó được đặt tên là dpkg. Như vậy, 'package' nổi tiếng đầu tiên xuất hiện trong GNU/Linux, một thời gian trước khi Red Hat quyết định tạo ra hệ thống 'rpm' của chính họ. Một tình huống mới nhanh chóng nảy sinh trong suy nghĩ của những người làm ra GNU/Linux. Họ cần một cách nhanh, thực tế, và hữu ích để cài các gói, cái mà sẽ quản lý tự động các phụ thuộc và lưu giữ những tệp cấu hình khi nâng cấp. Một lần nữa, Debian lại đi đầu và cho ra đời APT, viết tắt của Advanced Packageing Tool.

###Các lệnh

Tất cả các lệnh được nói đến đều phải chạy với tài khoản root hoặc với quyền siêu người dùng, xem sudo để biết thêm thông tin. Thay tên-gói trong các lệnh bằng tên của gói bạn muốn cài đặt.

###1.3.1 Lệnh cài đặt

- Ta dùng lệnh:

      **#sudo apt-get install tên_gói** 

- Để cài đặt một gói mới.

      **#sudo apt-get build-dep tên_gói** 

- Tìm kiếm trên kho và cài đặt những gói phụ thuộc cần thiết để có thể cài đặt gói từ mã nguồn. Nếu gói không có trong kho, lệnh sẽ trả về một lỗi.

      **#sudo apt-get -s install tên-gói** 

- Sẽ giả lập việc cài đặt một gói, cho bạn biết nơi gói sẽ được cài đặt và cấu hình của nó. 

###1.3.2 Lệnh tìm gói

- Lệnh này sẽ giúp chúng ta tìm 1 gói, hoặc 1 chương trình nào đó trong ubuntu. Ví dụ tôi không nhớ chính xác tên gói cài đặt của chương trình amarok làm sao để cài đặt bằng lệnh, việc này thực hiện rất đơn giản 

      **#sudo apt-cache search tham số**

- Tham số có thể là tên chương trình hay là ghi chú .... nó sẽ trả về tên gói + ghi chú kế bên sau đó bạn chỉ cần sử dụng lệnh 

      **#apt-get install để cài đặt** 

###1.3.3 Lệnh bảo quản

-       
      **#sudo apt-get update**

- Chạy lệnh này sau khi thay đổi /etc/apt/sources.list hoặc /etc/apt/preferences. Sử dụng lệnh này thường xuyên giúp danh sách nguồn của bạn được cập nhật. 

      **#sudo apt-get upgrade**

- Lệnh này nâng cấp tất cả các gói đã cài đặt. 

      **#sudo apt-get dist-upgrade**

- Lệnh này nâng cấp toàn hệ thống tới một phiên bản mới hơn. Nó tương tự như ở trên, ngoại trừ thêm đánh dấu thêm "smart upgrade". Nó báo APT sử dụng hệ thống giải quyết xung đột thông minh, và nó sẽ thử nâng cấp những gói quan trọng nhất. Đây không phải là cách được khuyên để nâng cấp bản phân phối, xem Cách nâng cấp bản phân phối để biết thêm thông tin. 

      **#sudo apt-get check**

- Lệnh này là một công cụ để chuẩn đoán. Nó không cập nhật danh sách nguồn, mà chỉ kiểm tra lỗi phụ thuộc.

      **#sudo apt-get -f install**

- Sử dụng lệnh này nếu bạn nếu bạn gặp phải lỗi phụ thuộc của các gói.

      **#sudo apt-get autoclean**

- Lệnh này gỡ bỏ các tệp cài đặt .deb đã cũ trong hệ thống của bạn. Phụ thuộc vào thói quen cài đặt của bạn, xóa bỏ các tệp trong /var/cache/apt/archives có thể thu hồi một lượng không gian đĩa đáng kể.

      **#sudo apt-get clean**

- Lệnh này tương tự như trên nhưng nó sẽ xóa bỏ tất cả các gói trong nơi lưu trữ. Nó không tốt lắm nếu bạn đang sở hữu một đường truyền Internet chậm, vì khi cài đặt sẽ phải tải lại các gói (đáng ra có sẵn tại nơi lưu trữ).

- Nơi lưu trữ các gói đã được cài đặt là /var/cache/apt/archives. Lệnh:

      **#du -sh /var/cache/apt/archives**

- Cho biết dung lượng các gói được lưu trữ. 

#2. Cài đặt với YUM

- YUM (Yellowdog Updater Modified) là phương pháp cài đặt phần mềm có xu hướng tự động hóa và tập trung hóa. Người dùng chỉ việc đánh lệnh, và yum sẽ kết nối với server cập nhập, cài đặt hay gỡ bỏ phần mềm dựa trên những thông tin về các gói cài đặt sẵn có trên Interner

- Trên Centos mặc định là có sẵn lệnh **yum**. Để kiểm tra phiên bản lệnh yum ta dùng lệnh:

      **#yum --version**

##2.1 Cài đặt các gói thông tin lưu trữ (Repository) cho YUM

- Về cơ bản là YUM có rất nhiều thông tin các gói phần mềm thông dụng cho server. Tuy nhiên, đôi lúc sẽ có những phần mềm khác mà YUM không có sẵn trong gói cơ bản. Để cài được hầu hết các phần mềm phổ biến bằng YUM, bạn cần phải bổ sung thêm các gói thông tin lưu trữ cho YUM bằng những lệnh sau :

- Lệnh cài đặt EPEL Repository bằng YUM :

- Cách đơn giản nhất để cài đặt EPEL Repository là thông qua YUM, YUM sẽ tự động cài EPEL Repository cho server phù hợp với hệ điều hành và phiên bản của hệ điều hành :

      sudo yum install epel-release

###Lệnh cài đặt EPEL Repository cho hệ điều hành 64bit :

**CentOS 6 64bit :**

      sudo rpm -Uvh http://download.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm

###Lệnh cài đặt EPEL Repository cho hệ điều hành 32bit :

**CentOS 6 32bit :**

      sudo rpm -Uvh http://download.fedoraproject.org/pub/epel/6/i386/epel-release-6-8.noarch.rpm

###Lệnh cài đặt REMI Repository (dùng chung cho hệ điều hành 32bit và 64bit) :

**CentOS 7 (32bit + 64bit) :**

      sudo rpm -Uvh http://rpms.famillecollet.com/enterprise/remi-release-7.rpm

**CentOS 6 (32bit + 64bit) :**

      sudo rpm -Uvh http://rpms.famillecollet.com/enterprise/remi-release-6.rpm

**CentOS 5 (32bit + 64bit) :**

      sudo rpm -Uvh http://rpms.famillecollet.com/enterprise/remi-release-5.rpm

- REMI và EPEL là 2 Repository được sử dụng phổ biến nhất giúp bạn cài đặt hầu như tất cả các phần mềm thông dụng cho server bằng lệnh YUM

###Lệnh cài đặt RepoForge (RPMforge) Repository cho hệ điều hành 64bit :

**CentOS 6 64bit :**

      sudo rpm -Uvh http://pkgs.repoforge.org/rpmforge-release/rpmforge-release-0.5.3-1.el6.rf.x86_64.rpm

**CentOS 5 64bit :**

      sudo rpm -Uvh http://pkgs.repoforge.org/rpmforge-release/rpmforge-release-0.5.3-1.el5.rf.x86_64.rpm

**CentOS 4 64bit :**

      sudo rpm -Uvh http://pkgs.repoforge.org/rpmforge-release/rpmforge-release-0.5.3-1.el4.rf.x86_64.rpm

**CentOS 3 64bit :**

      sudo rpm -Uvh http://pkgs.repoforge.org/rpmforge-release/rpmforge-release-0.5.3-1.el3.rf.x86_64.rpm

###Lệnh cài đặt RepoForge (RPMforge) Repository cho hệ điều hành 32bit :

**CentOS 6 32bit :**

      sudo rpm -Uvh http://pkgs.repoforge.org/rpmforge-release/rpmforge-release-0.5.3-1.el6.rf.i686.rpm

**CentOS 5 32bit :**

      sudo rpm -Uvh http://pkgs.repoforge.org/rpmforge-release/rpmforge-release-0.5.3-1.el5.rf.i386.rpm

**CentOS 4 32bit :**

      sudo rpm -Uvh http://pkgs.repoforge.org/rpmforge-release/rpmforge-release-0.5.3-1.el4.rf.i386.rpm

**CentOS 3 32bit :**

      sudo rpm -Uvh http://pkgs.repoforge.org/rpmforge-release/rpmforge-release-0.5.3-1.el3.rf.i386.rpm

###Lệnh cài đặt Atomic Repository cho CentOS 6 64 bit

      sudo rpm -Uvh http://www6.atomicorp.com/channels/atomic/centos/6/x86_64/RPMS/atomic-release-1.0-19.el6.art.noarch.rpm

###Những lệnh cơ bản của YUM

##2.2. Lệnh yum check-update và yum list updates

- Là lệnh có chức năng tương tự như nhau là dùng để cập nhật thông tin và danh sách các gói phần mềm được hỗ trợ cài đặt bằng lệnh YUM. Lưu ý là dòng lệnh này không cài đặt phần mềm mà chỉ là cập nhật danh sách các phần mềm được hỗ trợ của YUM. Cú pháp:

      **#yum check-update**

      **#yum list updates**

##2.3. Lệnh yum list all và yum list

- Là lệnh dùng để liệt kê tất cả các gói phần mềm có thể được cài đặt bằng lệnh YUM và những phần mềm đã được cài đặt. Cú pháp:

      **#yum list all**
      
      và
      
      **#yum list**

##2.4. Lệnh yum list installed

- Là lệnh liệt kê tất cả các phần mềm đã được cài đặt. Nếu bạn muốn kiểm tra phần mềm nào đó đã cài đặt hay chưa thì có thể dùng lệnh sau :

      **#yum list installed tên_phần_mềm**

##2.5. Lệnh yum list available

- Là lệnh liệt kê tất cả các phần mềm có thể cài đặt bằng lệnh YUM. Cú pháp:

      **#yum list available**

##2.6. Lệnh yum info

- Là lệnh dùng để xem thông tin của phần mềm. Cú pháp:

      **#yum info tên_phần_mềm**

##2.7. Lệnh yum search

- Là lệnh dùng để tìm kiếm gói phần mềm được hỗ trợ cài đặt bằng yum. Cú pháp:

      **#yum search tên_phần_mềm**

##2.8. Lệnh yum install

- Là lệnh dùng để cài đặt gói phần mềm do bạn chỉ định. Cú pháp:

      **#yum install tên_phần_mềm**


##2.9. Lệnh yum update

- Là lệnh dùng để kiểm tra và cập nhật phiên bản mới nhất của gói phần mềm. Nó sẽ cập nhật phiên bản mới nhất cho tất cả các gói phần mềm đã được cài đặt trên server. 
 
      **#yum update**

- Nếu bạn muốn chỉ kiểm tra và cập nhật phiên bản mới nhất cho 1 phần mềm bạn chỉ định thì sử dụng lệnh: 

      **#yum update tên_phần_mềm**


##2.10. Lệnh yum remove

- Là lệnh dùng để gỡ bỏ và xoá gói phần mềm do bạn chỉ định.

      **#yum remove tên_phần_mềm**
      
##2.11. Lệnh yum clean all

- Thông thường YUM sẽ tạo và sử dụng cache cho các lần truy vấn, để xoá hết cache của yum thì bạn chạy lệnh sau :

      **#yum clean all**


#3 Cài đặt phần mềm trên Centos - Redhat

Có 2 dạng nén thông thường là gzip(thường) và bzip2 (mạnh hơn)

##3.1 GZIP

- gõ **#gzip <file>** sẽ nén file và tạo ra file.gz đồng thời xóa file đi 

<img src="http://prntscr.com/8r4hba">

- Hoặc **#gzip -c file1 file2 > filenen.gz** sẽ nén và gộp file <flie1> <file2> và tạo ra <output> nhưng vấn giữ lại file1 và file2

<img src="http://prntscr.com/8r4kkj">

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

###3.4.1 Cài đặt một package

- Để tải một tập tin trên mạng ta dùng lệnh wget

**#wget https:link_download**

**#rpm -ivh tên_gói.rpm**

- Giải thích ý nghĩa các tùy chọn đã dùng:
<ul>
<li>**–i:**  (install) cài đặt một package</li>
<li>**–v:** (verbose) hiện thị tóm tắt kết quả sau khi cài đặt package</li>
<li>**–h:** (hash) hiện thị dấu “#” thông báo quá trình cài đặt đang tiếp diễn</li>
</ul>

###3.4.2 Cập nhật một package (upgrade):

**#rpm -Uvh tên_gói.rpm**

- Ta có thể dụng lệnh rpm với các tùy chọn:
<ul>
<li>**—nodeps:** lệnh rpm sẽ bỏ qua các gói phụ thuộc</li>
<li>**—force:** lệnh rpm sẽ bỏ qua lỗi xung đột</li>
</ul>

###3.4.3 Truy vấn các package đã được cài đặt trên hệ thống (Query):

- Liệt kê các package có tên gói

     **#rpm -qa tên_gói**

- Liệt kê các package có chứa tên gói

     **#rpm -qa |grep “tên_gói”**

- Liệt kê các files tài liệu liên quan đến gói

     **#rpm -qd tên_gói**

- Liệt kê các thông tin mô tả gói:

     **#rpm -qi tên_gói**

- Liệt kê tất các tập tin cấu hình của gói

     **#rpm -qc tên_gói**

- Giải thích các tùy chọn:
<ul>
<li>**–q:** (packagefile) hiện thị package</li>
<li>**–a:** (all) truy vấn tất cả các package đã được cài đặt</li>
<li>**–d:** (documentation) liệt kê các files tài liệu liên quan đến package</li>
<li>**–i:**  (information) liệt kệ các thông tin như package name, description, release number, và các thông tin khác</li>
<li>**–c:** (configuration) liệt kê các tập tin cấu hình của package</li>
</ul>

###3.4.5 Gỡ bỏ một package (Erase):

-    Để gỡ bỏ một gói

     **# rpm -e tên_gói**

- Dùng lệnh để kiểm tra kết quả:

     **# rpm -qa |grep “tên_gói”**

- Nếu gỡ bỏ một package mà package đó còn phụ thuộc vào các package khác thì khi gỡ bỏ ta dùng thêm tùy chọn –nodeps.
      
#4. Biên dịch phần mềm

- Phương pháp này thì khác hơn so với RPM và Yum nó không phụ thuộc bạn dùng distro nào miễn là dùng Linux là điều có thể dùng phương pháp này. Bước đầu tiên khi muốn thực hiện phương pháp cài đặt này là bạn phải có file source của nó(có định dạng thường là file nén tag.gz. tar.bz2,..). Sau khi down file source về bạn tiến hành giải nén nó ra, sau đó bay vào trong thư mục giải nén thực hiện quá trình đầu tiên là check thư viện và các config file. Lỗi 98% thường xuất hiện tại bước này, vì cũng giống như RPM biên dịch phần mềm cũng cần phải đầy đủ thư viện thì mới có thể biên dịch được. Và bước này cũng chiếm nhiều thời gian nhất trong 3 bước cài đặt, qua được bước này 2 bước kia coi như là hoàn tất.

- Nhìn chung biên dịch phần mềm có phần giống với tiện ích RPM là không thể tự động tìm các gói phụ thuốc để cài đặt trước như tiện ích Yum, và 1 đặc điểm chung nữa là cả Yum và RPM điều cài đặt những gói nhị phân. Nói một cách dễ hiểu, cài đặt gói nhị phân như RPM hay Yum thì nhượt điểm đó là bạn không thể tự mình điều khiển được những gì muốn cài vào hệ thống mà gần như mặc định là cài tất cả. Nhưng 1 trong 3 nguyên tắc trong bảo mật hệ thống “những gì không dùng nên xóa hoặc tắt bỏ”, mục đích của nguyên tắc này là giảm thiểu rủi ro một cách tối ưu nhất có thể cho hệ thống phát sinh từ những thành phần hay module trong phần mềm. Với yêu cầu này thì phương pháp biên dịch phần mềm có thể giúp bạn giải quyết được, bạn có thể tùy chỉnh cài đặt những thành phần nào vào hệ thống ở bước đầu tiên.

- Bên cạnh đó, việc sử dụng phương pháp biên dịch bạn có thể tối ưu hóa tài nguyên hệ thống, Mặt khác, đối với kiến thức trong tương lai, biên dịch có thể cho bạn những kiến thức cơ bản đầu tiên về biên dịch kernel trên Linux và đích cuối cùng chính là tự mình biên dịch một distro linux cho riêng mình.

##Biên dịch phần mềm httpd:

**Bước 1:** Tải httpd-2.4.10.tar.bz2

**Bước 2:** Giải nén tập tin

**#unzip                   để giải nén                       name_package.zip**
**#tar -xvzf             đẻ giải nén                       name_package.tar.gz**
**#tar -jvxf              để giải nén                       name_package.tar.bz2**
**#tar -x                   để giải nén                       name_package.tgz**

**Bước 3:** Tạo thư mục để cài phần mềm

- Tạo thư mục httpd trong thư mục /usr/local/

- Sử dụng lệnh #ll để kiểm tra thư mục vừa tạo

**Bước 4:** Vào thư mục vừa giải nén để chuẩn bị biên dịch

**#cd httpd-2.4.10**

- Các bạn đọc file README hoặc INSTALL để xem hướng dẫn cài đặt.

**#vi README**
**#vi INSTALL**

**Bước 5:** Cấu hình cho gói phần mềm (Bước này xảy ra lỗi nhiều nhất)

**# ./configure –prefix=/usr/local/httpd/ –with-included-apr**

**–prefix** là nơi sẽ cài phần mềm vào giống như chọn đường dẫn để cài phần mềm trong windows.

**–with-included-apr:** trong tập tin INSTALL có hướng dẫn là tải apr và apr-util rồi copy vào /httpd-2.4.10/srclib/

**Bước 6:** Biên dịch cho gói phần mềm:

- make

**# make**

**Bước 7:** Cài đặt gói phần mềm httpd vừa biên dịch:

- make install

**#make install**

- Khởi động dịch vụ httpd:

**#/usr/local/httpd/bin/apachectl start**

- Xong các bước trên các bạn cài phần mềm w3m để lướt web trên giao diện dòng lệnh:

**#yum install w3m**

**#w3m localhost**
