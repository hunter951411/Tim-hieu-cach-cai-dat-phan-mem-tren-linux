# Tim-hieu-cach-cai-dat-phan-mem-tren-linux
Tìm hiểu cách cài đặt phần mềm trên linux

- Có nhiều cách để cài đặt phần mềm, ứng dụng trên Linux. Nếu có kết nối mạng bạn có thể cài đặt ứng dụng tự động qua công cụ Synaptic Package Manager(giao diện GUI) hoặc sử dụng dòng lệnh **apt-get**  trong Terminal.... File cài đặt ứng dụng trên Linux thường có đuôi là .deb, .rpm, .tar, .tar.gz, INSTALL, .sh...... Mỗi loại file lại có một cách cài đặt khác nhau.

#1. Cài đặt phần mềm từ source trên Linux

- Trước tiên, để cài đặt bạn cần phải có source file của gói đó. Lên mạng search bất kfi gói nào bạn thích như thư viện Gtk+ hoặc Gnome..... Sau khi tải về, thường có dạng là .gz hoặc .bz2, đây đều là 2 chuẩn nén khác nhau, sau khi giải nén bằng gunzing hoặc bunzip2 hoặc cho bz2 thì các gói sẽ có dạng mới là tar, cũng là một chuẩn nén khác, bạn có thể giải nén bằng lệnh tar -xvf..... Thế nhưng để dễ dàng và tiết kiệm dung lượng ổ đĩa thì chúng ta có thể goppj các lệnh đó thành 1 câu lệnh như sau:

- Đối với gói **.gz**: #tar -zxvf tengoi.gz
- Đối với gói **.bz2*: #tar -jxvf tengoi.bz2

- Sau khi giải nén xong và tìm tập tin ISTALL để đọc cụ thể cho phần hướng dẫn cài đặt. thế nhưng hầu hết các gói đều tuân theo thao tác tuần tự sau:

- **#./config**

(Là một shell script sẽ kiểm tra những yêu cầu của hệ thống của bạn có đáp ứng đủ để cài đặt lên gói hay không, ví dụ một số gói đòi ỏi bạn phải có sẵn thư viện đồ họa Gtk 2.4 trở lên hoặc thư viện để giải nén nhạc Mp3...)

- **#make**

(Sau khi thực hiện lệnh make toàn bộ mã nguồn của gói đã được biên dịch sang dạng thực thi nhưng các file thực thi vẫn còn nằm trên thư mục hiện hành. Do đó bạn cần phải thực hiện lệnh make install để chép các file thực thi đó sang đúng vị trí của nó trên hệ thống. Nếu không có thông báo lỗi gì xảy ra thì bạn đã hoàn tất việc cài đặt gói lên hệ thống của mình)

- **make install**


##1.2 Tổ chức các file trên hệ thống
