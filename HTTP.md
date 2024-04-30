# Khái niệm cơ bản

- Sever : máy chủ cung cấp dịch vụ cho những máy khác

- Clients : máy khách : các máy sử dụng dịch vụ do server cung cấp

-> Đó chính là mô hình Clients - Server

Những người viết mã trên Clients được gọi là Front End Developer

Những người viết mã trên Server được gọi là Back End Developer

- Chúng ta sử dụng Các giao thức HTTP.. để đảm bảo giao tiếp giữa Clients và Server

 ## 2. TELNET ( Terminal Network )

- Là giao thức mạng cho phép giao tiếp với các thiết bị mạng

- ![image](https://github.com/yeuubonn2k4/BASIC_OF_CYBER/assets/161863346/d6000e32-2dda-4ed7-902c-f3e422d01fd0)

apache.org là trang web hiếm hoi mà ta có thể thử với HTTP/0.9 này

Phiên bản HTTP lúc này từ 0.9 sang HTTP/1.0 (1996) (không được coi là 1 tiêu chuẩn)

- 1997 phiên bản chính thức đầu tiên : HTTP/1.1 (RFC 2068)

- 1999 phiên bản nâng cấp RFC 2616

- Gần đây là RFC 7231, RFC 7232 , ... , RFC 7235

- Vậy RFC là gì?  (Request for Comments) là một chuỗi bản ghi nhớ chứa đựng những nghiên cứu mới, những đổi mới và phương pháp luận ứng dụng cho công nghệ Internet.

- Hiện nay vẫn sử dụng HTTP/1.1

- 2015 giới thiệu HTTP/2.0 chính thức trở thành tiêu chuẩn mạng Innternet với RFC :7540

  ## Tim hieu ve HTTP/1.1

  ### Tim hieu HTTP Resources và URIURLURN

  - Các máy chủ cung cấp các dịch vụ như tìm kiếm,email,... các tài nguyên này được gọi là Resources

  - Định danh tài nguyên (Uniform Resource Identifier) (RFC 3986)
 
  - Ví dụ về URI định danh cho 1 ftp  ftp://ftp.is.co.za/rfc/rfc1808.txt
 
  -> URI định danh khá chung chung cho các Resources

  ### Các định danh con của URI
 
  - URL (Uniform Resource Loctor) : cho biết nơi cất giữ tại 1 server nào đó và cách thức truy cập
 
  - URN (Uniform Resource Name) : Định danh cho phần nội dung ( độc lập với nơi nó đang được lưu trữ)
(khi dịch chuyển file tới 1 nơi khác thì URL sẽ thay đổi, cần định danh lại những URN thì không cần , nó không thay đổi)

![image](https://github.com/yeuubonn2k4/BASIC_OF_CYBER/assets/161863346/e10e367c-b2b2-4d0b-8c6b-fdccd4aa8cc4)

Tuy nhiên trên thực tế vẫn chưa thực hiện được ý tưởng đó 
Dịch vụ của Amazon :Khi mà từ Azure sang dịch vụ clould Amazon thì sẽ xuất hiện ARNs ( định danh các dịch vụ và resouces trên Amazon)

-> Đó là lý do URN chưa được sử dụng rộng rãi như URL

-> Như vậy với mỗi định danh 1 resource ta có thể gọi nó là URI, khi ta muốn nói cách thức truy cập giao thức đó ta dùng URL, còn URN trên thực tế không được sử dụng phổ biến

### CẤU TRÚC URL (chỉ bàn về HTTP)

![image](https://github.com/yeuubonn2k4/BASIC_OF_CYBER/assets/161863346/abaf4cde-f267-4fd2-bce0-9cba5d7c5f19)

- Scheme : các giao thức

  + Với http : http
 
  + Với https : https
 
  + Với Web Socket là ws
 
- "://" các kí tự bắt buộc phải có

- <user>:<password>@<host>:<port> : phần authority :

  Ví dụ trong ![image](https://github.com/yeuubonn2k4/BASIC_OF_CYBER/assets/161863346/be282e99-f9c9-4dce-a90a-f3875edf3fbe)
sẽ là www.cione.vn

![image](https://github.com/yeuubonn2k4/BASIC_OF_CYBER/assets/161863346/725524d9-614e-4802-8903-cbff012b0bf8)

-> Không có user và password bởi vì chỉ cần có hostname còn mấy phần còn lại trong authority có cũng được :> 

Tại sao lại thường không có user-info ( trong đó có user-password) ? vì nếu ghi ra user-password như vậy sẽ dễ lộ thông tin, rất nguy hiểm.

![image](https://github.com/yeuubonn2k4/BASIC_OF_CYBER/assets/161863346/17b24f0d-7e60-49fb-b15e-07d225832200)

- port là gì?

Trên 1 máy sẽ có rất nhiều dịch vụ , để có thể kết nối chính xác với dịch vụ đó chúng ta cần truy cập đúng các port ( các cổng )

Cổng 80 : làm việc với web

Cổng 25 : làm việc với email

- Bảng 1 số port của 1 số dịch vụ

  ![image](https://github.com/yeuubonn2k4/BASIC_OF_CYBER/assets/161863346/99850d85-e328-424a-8cc9-daea3b2294a9)

-/<path> đường dẫn đến resources ( bắt đầu từ / chúng ta có thể đọc là slash)

Ví dụ : class và login gọi là slash 

![image](https://github.com/yeuubonn2k4/BASIC_OF_CYBER/assets/161863346/fec01057-e553-4301-929e-411d1250c7ce)

? Chú ý : Đôi khi mấy cái slash này sẽ không hiện trên server đâu mà backend mới nhìn thấy

- 1 cặp name
  
![image](https://github.com/yeuubonn2k4/BASIC_OF_CYBER/assets/161863346/a13bcc57-6e39-4fe0-8e7a-8879a72e3a52)

- 2 cặp name

![image](https://github.com/yeuubonn2k4/BASIC_OF_CYBER/assets/161863346/38314106-868a-451c-84dc-b13c128ee327)

- fragment được gọi là hash : để trỏ đến đúng địa điểm

![image](https://github.com/yeuubonn2k4/BASIC_OF_CYBER/assets/161863346/889e0d8b-1ad1-4a5c-bd31-adc6aeb8b9d9)

headling có thể dùng /,?

![image](https://github.com/yeuubonn2k4/BASIC_OF_CYBER/assets/161863346/db642d89-0df4-423a-b63e-70d45a669bd2)

Đó chính là 1 ví dụ về headling

https://www.youtube.com/watch?v=5pryvIsW_HM&list=PL75xdq9Y-GaTZaU5l4z2J9-IFyFBQg6lP&index=5
