>Trong các cuộc thi CTF , 1 trong những dạng mã luôn có trong đó là RSA. Vậy nên hôm nay chúng ta hãy cùng nhau tìm hiểu về RSA nhé^^

### Khái niệm:

*RSA (viết tắt của tên tác giả Rivest-Shamir-Adleman) là một hệ thống mật mã bất đối xứng(Mật mã công khai) (Các loại mật mã này mình cũng đã từng có bài viết). Trong mật mã bất đối xứng gốm có **khóa công khai** được sử dung để *mã hóa dữ liệu* và chỉ có thể sử dụng**khóa riêng tư** để *giảm mã dữ liệu*.*

**Các định nghĩa dung trong giải mã RSA**

-	Khóa công khai được tạo thành từ (n,e)
  
-	Khóa riêng được tạo thành từ (n,d)
  
-	Thông điệp được biểu diễn dưới dạng m và được chuyển đổi thành 1 số
  
-	Tin nhắn được mã hóa hoặc văn bản mã hóa được biểu diễn bằng c

-	p và q là các số nguyên tố tạo nên n
  
-	e là số mũ công khai
  
-	n là mô-đun và độ dài của nó tính bằng bit (RSA 1024 bit)
  
-	d là số mũ riêng

-	Số toàn phần λ( n ) được dung để tính d
   
**RSA được sử dụng phổ biến vì rất khó để tìm d ngay cả với m,n và e vì việc phân tích các số lớn là một quá trình gian nan.**

### Chúng ta hãy cùng đến 1 ví dụ để biết RSA giải mã như thế nào nha:

>1 số công thức hay dung: n=p*q;
λ( pq)=  lcm(p-1,q-1);
d x e mod λ( n ) = 1;

***Ví dụ cho 2 số nguyên tố p= 61 và q=53***

-	*Tìm n*: n=pq=3233

-	*Tính λ( pq)=  lcm(p-1,q-1)*
  
λ(3233)= lcm(60,52)=780

-	Chọn 1 số mũ công khai sao cho 1<e< λ(n) và là số nguyên tố cùng nhau (không phải là ước của) λ(n). Thường tiêu chuẩn hầu hết các trường hợp là 65537.

Ở đây chúng ta sẽ dung e=17 (thỏa mã 1<e<780 và 17 và 780 là số nguyên tố cùng nhau(số không có ước chung lớn hơn 1)

Tính d thỏa mãn :  d x e mod λ( n ) = 1;

Với e=17 -> d x 17 mod 780 =1 

->	d=413

Vậy chúng ta có khóa công khai là (3233,17) và khóa riêng là (3233,413)

*Nếu Mã hóa* chúng ta sẽ dùng e=17 để m có thể mã hóa 1 cách dễ dàng:

>*c= m^e^mod n*

        c = m ^17^ mod 3233

*Nếu Giải mã* chúng ta  có công thức 

>*m = c^ d mod n*

m = c^ 413 ^ mod 3233

*Cũng chính bởi việc mã hóa và giải mã RSA khá phức tạp nên RSA được ứng dụng rất nhiều trong bảo mật dữ liệu:*

- **Chứng thực dữ liệu** : được áp dụng khi yêu cầu xác minh bằng cách đưa ra các con số gửi về email hay số điện thoại trước khi đăng nhập. Đó chính là ứng dụng thuật toán RSA để tránh những tính trạng mạo danh, hack tài khoản người dùng...

- **Truyền tải dữ liệu an toàn** : Nhằm tránh tình trạng nghe lén, theo dõi hoạt động cũng như lấy cắp dữ liệu cá nhân trên các trang mạng xã hội và các trang web lưu lại các hoạt động, hành vi truy cập để phục vụ các mục đích Marketing. RSA giúp bảo vệ dữ liệu khỏi các cuộc tấn công của kẻ xấu**.

- **Chữ ký số/ Chữ ký điện tử** : Thẻ ATM luôn có phần chữ ký điện tử được mã hóa từ chữ ký của khách hàng khi đăng ký tài khoản tại ngân hàng. RSA được ứng dụng để bảo mật dữ liệu khi người dùng thực hiện những giao dịch ngân hàng, giúp khách hàng an tâm hơn.

- **Trong công nghệ thông tin** : Trong ngôn ngữ lập trình Java, lập trình viên thường sử dụng những đoạn code chứa RSA để tăng tính bảo mật cho trang web và ứng dụng cũng như đảm bảo an toàn cho người dùng. Các đoạn code RSA có thể hoạt động dù bất kỳ sự thay đổi nào của môi trường.

- *Ngoài ra các lạp trình viên cũng sử dụng những ngôn ngữ lập trình khác để có thể tìm hiểu và ứng dụng những tính năng của RSA trong hoạt động làm việc và bảo mật thông tin.*

- Bài viết là những thông tin mình sưu tầm được. Hy vọng sẽ có ích với mọi người

- #Cre nhiều nguồn trên Internet

- ![image](https://github.com/user-attachments/assets/55e55616-0cf9-4221-b6cf-5be267d17fc5)

