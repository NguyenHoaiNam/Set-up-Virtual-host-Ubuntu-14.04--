Set-up-Virtual-host-Ubuntu-14.04--
==================================
### Người thực hiện : Nguyễn Hoài Nam --ptit--
----
#### Mục lục
1. Giới thiệu về kĩ thuật Virtual host :

Virtual host là kĩ thuật để một máy chủ web-server chạy được nhiều trang web với tên miền khác nhau sử dụng chung một địa chỉ IP. Mục đich của kĩ thuật là tối ưu phần cứng của máy chủ web-server, tránh lãng phí, sử dụng hiểu quả tối ưu tài nguyên của máy chủ
**VD:** Khi ta đánh 2 địa chỉ trang web thì máy client sẽ cùng truy cập đến một địa chỉ IP của máy chủ nhưng nó sẽ hiển ra nội dung của 2 trang web khác nhau.

| Tên trang web | Địa chỉ IP ánh xạ đến | Nội dung trang web |
|---------------|-----------------------|--------------------|
|test.com       | 192.168.1.108         | test thành công trang web |
|example| 192.168.1.108 | example thành công trang web |

---
1. 
