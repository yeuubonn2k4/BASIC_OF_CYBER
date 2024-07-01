> Trước khi có những bài viết viết về RSA, AES…. Mình xin phép chia sẻ kiến thức về phân loại các phương pháp mã hóa. Hy vọng bài viết này sẽ có ích cho mọi người.

### Đầu tiên chúng ta cần hiểu Thuật toán mã hóa là gì?

*Là thuật toán nhằm mã hóa thông tin nhằm biến đổi thông tin từ dạng rõ sang dạng mờ -> Ngăn chặn việc đọc trộm nội dung của thông tin hoặc có được thông tin đó cũng không thể hiểu nội dung chứa trong nó là gì.*

### PHÂN LOẠI:

Có rất nhiều phương pháp mã hóa khác nhau đã ra đời và chúng được chia thành 4 loại chính :

**1.	Mã hóa cổ điển** (đơn giản nhất) : (Bên A mã hóa thông tin bằng thuật toán mã hóa cổ điển và bên B giải mã thông tin dựa vào thuật toán của bên A mà không cần dung đến bất kỳ key nào)
Ví dụ : Mã hóa Caesar, Vigenère,…

**2.	Mã hóa một chiều**: là kiểu mã hóa chỉ có thể mã hóa chứ không thể giải mã. 
Ví dụ : Hàm Hash (biến 1 chuỗi thông tin thành 1 chuỗi hash có độ dài nhất định mà không có cách nào khôi phục chuỗi hash về lại chuỗi thông tin ban đầu.)

- 	Trong các giao dịch thương mại điện tử, Hashing thường được sử dụng để bảo vệ mật khẩu và các thông tin nhạy cảm khác.

- Các thuật toán phổ biến để mã hóa băm như MD5,SHA1,SHA256,…

***(mình sẽ viết chi tiết mã Hash trong bài viết sau)***

3.	**Mã hóa đối xứng** : Phương pháp mã hóa mà key mã hóa và key giải mã là như nhau (sử dụng cùng 1 secret key để mã hóa và giải mã) -> Bên gửi và bên nhận cần thống nhất về secret key.

***Đây là phương pháp thông dụng nhất hiện nay dung để mã hóa dử liệu truyền nhận giữa 2 bên***

*Ví dụ* : AES,DES,…

4.	**Mã hóa bất đối xứng** (mã hóa công khai): mà key mã hóa (khóa công khai) và key giiar mã (khóa bí mật) khác nhau. Nghĩa là key sử dụng để mã hóa dữ liệu sẽ khác key dung để giải mã. Tất cả mọi người đều có thể biết được public key (kể cả hacker) và có thể dung public key này để mã hóa thông tin. Nhưng chỉ có người nhận mới nắm giữ private key nên chỉ người nhận mơi có thể giải mã được thông tin.

*Ví dụ* : RSA,DSA,…

*Điểm yếu* : tốc độ mã hóa và giải mã rất chậm so với mã bất đối xứng, chi phí để mã hóa dữ liệu và truyền – nhận giữa hai bên cũng tốn khá nhiều.

+ Các thuật toán sử dụng 1 hoặc nhiều key để mã hóa và giải mã (trừ những thuật toán cổ điển). Như chúng ta thường biết thì Người gửi sẽ dung key mã hóa để mã hóa thông tin sang dạng mờ và người nhận sẽ lấy key đó giải mã thông tin. Do đó chỉ những người nào có key mới đọc được nội dung. Nhưng hacker không có key vẫn có thể đọc được thông tin. Do đó không có bất kì thuật toán mã hóa nào là an toàn mãi mãi cả.

Bài viết này chỉ là khái quát mở đầu về các loại mã hóa.Trong những bài viết sau mình sẽ cố gắng làm rõ hơn những loại mã hóa khác. Hy vọng các bạn sẽ luôn theo dõi, đọc và ủng hộ chúng mình.

#Bài viết có tham khảo từ author Nguyen Minh Duc :3

![image](https://github.com/yeuubonn2k4/BASIC_OF_CYBER/assets/161863346/b2603368-b531-4b3e-975b-2559f896b435)

