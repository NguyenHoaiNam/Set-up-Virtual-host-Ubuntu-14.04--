Set-up-Virtual-host-Ubuntu-14.04--
==================================
### Người thực hiện : Nguyễn Hoài Nam --ptit--
----
#### Mục lục

1.**Giới thiệu về kĩ thuật Virtual host:**

Virtual host là kĩ thuật để một máy chủ web-server chạy được nhiều trang web với tên miền khác nhau sử dụng chung một địa chỉ IP. Mục đich của kĩ thuật là tối ưu phần cứng của máy chủ web-server, tránh lãng phí, sử dụng hiểu quả tối ưu tài nguyên của máy chủ
**VD:** Khi ta đánh 2 địa chỉ trang web thì máy client sẽ cùng truy cập đến một địa chỉ IP của máy chủ nhưng nó sẽ hiển ra nội dung của 2 trang web khác nhau.

| Tên trang web | Địa chỉ IP ánh xạ đến | Nội dung trang web |
|---------------|-----------------------|--------------------|
|test.com       | 192.168.1.108         | test thành công trang web |
|example| 192.168.1.108 | example thành công trang web |

----

2.**Yều cầu kiến thức cần thiết**

   * Có kiến thức về Linux, hiểu các câu lệnh cơ bản và phân quyên trong Linux
   * Hiểu về kiến trúc php
   * Có kiến thức về sử dụng dns, biết cách cài đặt dns-server

3.**Bắt đầu cài đặt**
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
- Bước 3:






