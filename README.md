Set-up-Virtual-host-Ubuntu-14.04--
==================================
### Người thực hiện : Nguyễn Hoài Nam --ptit--
----
#### Mục lục
#####1.**Giới thiệu về kĩ thuật Virtual host:**

Virtual host là kĩ thuật để một máy chủ web-server chạy được nhiều trang web với tên miền khác nhau sử dụng chung một địa chỉ IP. Mục đich của kĩ thuật là tối ưu phần cứng của máy chủ web-server, tránh lãng phí, sử dụng hiểu quả tối ưu tài nguyên của máy chủ
**VD:** Khi ta đánh 2 địa chỉ trang web thì máy client sẽ cùng truy cập đến một địa chỉ IP của máy chủ nhưng nó sẽ hiển ra nội dung của 2 trang web khác nhau.

| Tên trang web | Địa chỉ IP ánh xạ đến | Nội dung trang web |
|---------------|-----------------------|--------------------|
|test.com       | 192.168.1.108         | test thành công trang web |
|example| 192.168.1.108 | example thành công trang web |

----

#####2.**Yều cầu kiến thức cần thiết**

   * Có kiến thức về Linux, hiểu các câu lệnh cơ bản và phân quyên trong Linux
   * Hiểu về kiến trúc php
   * Có kiến thức về sử dụng dns, biết cách cài đặt dns-server

#####3.**Bắt đầu cài đặt**
- Bước 1 : Cài apache2 trên máy chủ Ubutu
```
apt-get install apache2
```
*Ta sẽ tạo 2 trang web có tên là : test.com và example.com trên một máy chủ cài apache2*
- Bước 2: Dữ liệu trang web thường được lưu ở thư mục `var/www`. Nên ta sẽ tạo 2 thư mục là test.com và example.com và trong mỗi thư mục đó tạo file có tên là public_html.
```
mkdir -p /var/www/test.com/public_html
mkdir -p /var/www/example.com/public_html
```
*tùy chọn -p dùng để tạo luôn 2 thư mục test.com và example.com khi trong thư mục /var/www chưa có*
- Bước 3: Chuyển đổi chủ sở hữu và nhóm sở thư mục example.com và test.com về cho thư mục root
```
chown -R root.root /var/www/test.com
chown -R root.root /var/www/example.com
```
và phân quyền cho thư mục `/var/www` bằng lệnh
```
chmod -R 755 /var/www
```
- Bước 4: Tạo 2 file index.html ở 2 thư mục example.com và test.com để 2 trang web có thể vào lấy nội dung trong file index.html 
```
nano /var/www/example.com/public_html/index.html
nano /var/www/test.com/public_html/index.html
```
- Bước 5: Tạo nội dung mẫu cho file index.html như sau:
```
<html>
  <head>
    <title>Welcome to Example.com!</title>
  </head>
  <body>
    <h1>Success!  The example.com virtual host is working!</h1>
  </body>
</html>
``` 
chỉnh sửa một chút nếu bạn cảm thấy thích =)))
- Bước 6: Copy file cấu hình mẫu vào trong thư mục sau:
```
cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/example.com.conf
```
chỉnh sửa lại thông tin đối với trang web test.com theo mẫu sau
```
<VirtualHost *:80>
    ServerAdmin admin@example.com
    ServerName test.com
    ServerAlias www.test.com
    DocumentRoot /var/www/test.com/public_html
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
*Làm tương tự với trang web exmaple.com*
- Bước 7: Bật cho web-server chạy 2 trang web vừa tao bằng lệnh `a2ensite`.
```
a2ensite example.com.conf
a2ensite test.com.conf
```
và restart lại dịch vụ
```
service apache2 restart
```
 **Quá trình cài đặt 2 trang web trên web-server hoàn tất**

----

#####4. Chỉnh sửa lại DNS-SERVER tên 2 trang web vừa tạo trỏ đến địa chỉ IP của WEB-SERVER
*Note:* Nếu bạn chưa hiểu dns là gì và chưa biết cách tạo ra dns-server trên máy chủ Linux có thể tham khảo tại đây:

[DNS là gì](http://daotaoweb.edu.vn/kien-thuc-web/9-dns-la-gi-tim-hieu-ve-dns)

[Nguyên tắc hoạt động](http://forum.whitehat.vn/threads/4992-Cach-Domain-Name-System-DNS-hoat-dong.html)

[Cài đặt DNS trên máy chủ Linux](https://www.youtube.com/watch?v=swPuK-qvBR8)

#####5. Điều chỉnh máy lên web sử dụng máy chủ dns-server mà tao vào tạo ra.
Lên mạng và kiểm tra




