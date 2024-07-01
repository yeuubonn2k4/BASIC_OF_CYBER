### Khái niệm :

**Hashing** là quá trình biến đổi đầu vào có kích thước, độ dài bất kỳ rồi sử dụng những thuật toán, công thức toán học để biến thành đầu ra tiêu chuẩn có độ dài nhất định. Quá trình đó sử dụng những Hàm băm (Hash function).

*Ví dụ* : Server sẽ mã hóa mật khẩu của người dùng, biến chúng thành 1 tổ hợp các ký tự, chữ cái và con số dài

**Hàm băm** (hashing function) là mật mã 1 chiều (bài viết trước mình có viết rồi).

*Ví dụ* : Tải 1 bức ảnh trên mạng về, cho chạy qua hàm MD5 bạn sẽ nhận được 1 chuỗi dài 32 ký tự, cho chạy "apple" qua hàm hash MD5 kết quả sẽ là "1f3870be274f6c49b3e31a0c6728957f" (32bit)

-> ***Bạn cho bất kỳ gì vào hàm, đầu ra sẽ luôn là 1 chuỗi có độ dài nhất định***

### Đặc điểm của hàm băm

- Hàm băm mang

 ***tính tránh va chạm*** : 2 giá trị khác nhau nhưng khi chạy qua hàm băm lại trả về 2 kết quả giống nhau

 ***tính hiệu quả*** : thời gian tính toán những giá trị băm phải nhanh
 
 ***tính nhạy cảm*** : chỉ cần thay đổi nhỏ trong giá trị ban đầu có thể thay đổi hoàn toàn giá trị băm
 

### Chi tiết từng mã

*Đầu tiên chúng ta sẽ tìm hiểu chi tiết về hàm MD5* :

Mã MD5 là mã để kiểm tra tính an toàn, chính xác của file khi chúng ta down về, mỗi file sẽ cho chúng ta 1 mã MD5. Khi có 1 chỉnh sửa nhỏ trong file là MD5 thay đổi ngay.

Với những file có dung lượng lớn, thời gian tải dài nên khả năng đứt mạng, lỗi trong quá trình tải thường xảy ra. Do đó để kiểm tra xem file tải đã đúng như file gốc hay chưa, chúng ta cần kiểm tra mã MD5 và so sánh với mã gốc mà người chia sẻ file cung cấp

*Từ những năm 2000 thì hàm băm MD5 trở lên không an toàn trước sự phát triển của công nghệ thám mã gần đây do chúng ta đã có thể tính toán các va chạm trong MD5 với độ phức tạp 2^21 chỉ trong vài giây (mật khẩu sử dụng toàn chữ cái thường bị phá trong vòng 6s, nếu thêm chữ in hoa thì thời gian tối đa là 24 phút. Điều đó khiến thuật toán không còn phù hợp với hầu hết các trường hợp sử dụng trong thực tế.Hầu như bây giờ người ta sử dụng SHA512 và những thuật toán nâng cấp hơn*
