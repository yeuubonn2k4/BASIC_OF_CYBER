![image](https://github.com/user-attachments/assets/bc909afa-244c-4ae4-af1f-05bca8ba6b71)## Untrusted Data: Dữ liệu không đáng tin cậy

Nền tảng trong Hacking và Security.

***Làm sao để xác định Untrusted Data?***

Với vị trí là 1 developer thì chúng ta luôn phải quan niệm rằng dữ liệu bên ngoài luôn không đáng tin cậy trừ khi chúng ta có thể kiểm soát được nó. (khi mà chính tay ta gõ, gán giá trị cho biến nào đó).

Nếu mà chúng ta không biết dữ liệu đó có an toàn không thì cứ giả sử trường hợp tệ nhất và coi là dữ liệu đó không an toàn.

-	Tại sao dữ liệu bên ngoài hoặc external (bên ngoài) data lại không đáng tin?

Do hacker và user lẫn vào nhau. Trong hang ngàn cứ request đến server, chỉ cần 1 trong số đó chứa mã khai thác của hacker  thì khiến sập cả hệ thống.

->	Untrust data chính là nơi lỗi bảo mật bắt nguồn.

-	Để phát hiện Untrusted data đòi hỏi phải Tỉ mỉ, khả năng phân tích và có cái nhìn tổng quát về hệ thống mà ta đang bảo vệ.

![image](https://github.com/user-attachments/assets/17975c49-9eff-4d1e-a304-3c4722828ca2)

- Web này sẽ nói Hello + tên bạn khi bạn nhập tên vào đây.

![image](https://github.com/user-attachments/assets/b5c153dc-d315-4cd6-a084-a1b0d0671bae)

- Khi ta nhập tên vào, đầu tiên web sẽ xác định Get name có giá trị không, nếu có sẽ gán giá trị cho $name và echo ra . Ta hoàn toàn có thể kiến soát biến $name bằng input ta nhập vào  $name chính là untrust data mà kẻ tấn công có thể lợi dụng

 ![image](https://github.com/user-attachments/assets/0bb4ce76-c7a2-44b1-9847-dc9b27f38874)

Giao thức mà được Web front-end và Web Server Back-end lợi dụng là HTTP request.

![image](https://github.com/user-attachments/assets/54b23a9a-63f3-4f36-a0ed-23b6b505931b)

![image](https://github.com/user-attachments/assets/803a2f4e-1c61-4a68-b3e7-b892e944835e)

Burp Suite giống như kính lúp giúp chúng ta có thể soi được những lỗi.

![image](https://github.com/user-attachments/assets/b8b6e5a4-d982-40b6-8495-53154ee6b77e)

![image](https://github.com/user-attachments/assets/759cccc3-e693-463e-9843-4da83a1f16d7)

	1 cái hay của Burp Suite là nó tích hợp sẵn trình duyệt giúp ta có thể dễ dàng vừa lướt web vừa quan sát các gói tin HTTP

 ![image](https://github.com/user-attachments/assets/27e296df-0ff4-46e8-8135-75c8c0963afc)

Nhỡ tắt tính năng Intercept đi để giúp ngăn chặn các gói tin đi qua.

![image](https://github.com/user-attachments/assets/cb1c2c7b-1827-4ebc-85b7-dd152a71cf78)

Khi lướt web thì các gói tin sẽ được hiển thị ở đây.

![image](https://github.com/user-attachments/assets/5edc566b-2189-4867-b7e7-65a1a6a0f2a7)

  Đây chính là tất cả các gói tin trong cuộc trò chuyện giữa trình duyệt và máy chủ. Ấn vào cuộc trò chuyện bất kỳ để xem chi tiết nó như thế nào.

  ![image](https://github.com/user-attachments/assets/32c7757b-b985-499c-a330-c6ba517e82c1)

  Bên trái Request là gói tin mà trình duyệt gửi đi. Bên phải Respond là gói tin mà trình duyệt nhận lại được từ máy chủ.

  ![image](https://github.com/user-attachments/assets/5959f886-2d02-4fe0-ba99-ce1c87990503)

Dòng 1 : Cho tôi truy cập trang có đường dẫn là Host (miền muốn truy cập): cyberjutsu.io, Phương thức muốn truy cập là GET (gửi thông tin người dùng đã được mã hóa được phụ them vào yêu cầu trang, truyền thông tin thông qua URL) >< phương thức POST (truyền thông tin thông qua HTTP header)

***Sự khác nhau giữa GET và POST*** https://hoclaptrinh.vn/posts/so-sanh-su-giong-va-khac-nhau-giua-get-va-post

-	Bên phải HTTP Respone

![image](https://github.com/user-attachments/assets/c472dc0f-2849-4ff3-86de-5550f4499ede)

Máy chủ trả về HTTP/1.1 200 OK để nói rằng request đã được thực hiện thành công. Người ta gọi nó là HTTP Status Code.

Dòng 3 cho ta biết máy chủ đang thực hiện Apache/version 2.4.18 (ubuntu) để xử lý các request.

![image](https://github.com/user-attachments/assets/b8a3977e-2834-4584-8291-5dfa56f69f48)

Phân cách với phần body bởi 1 dòng trống.

>Tất cả những trường nào chúng ta nghi ngờ là Untrust data  thì chúng ta hãy nhập test vào trường đó.

![image](https://github.com/user-attachments/assets/02096662-4ebf-4c32-a260-a03cee4dc561)

Khi muốn thay đổi thông tin tab Request có  email thành test thì chuột phải chọn Send to Repeater. Lúc này tab Repeater sẽ nháy nháy. Và ấn vào tab đó bạn hoàn toàn có thể thay đổi được rồi ấn Send.

![image](https://github.com/user-attachments/assets/e4256ea8-6cf0-4af3-8f60-78c54eb64a81)

**Lúc này server đã xử lý được. Kéo xuống và thấy thông báo tìm thấy 1 untrusted data ^^**
