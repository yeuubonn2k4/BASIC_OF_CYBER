## Khái niệm :

- Banconian là môt phương pháp steganography (một phương pháp che giấu một thông điệp bí mật chứ không phải chỉ là mật mã). Một thông điệp được ẩn giấu trong quá cách trình bày văn bản thay vì nội dung của nó

## Đặc điểm

- Mật mã Baconian là mật mã thay thế trong đó mỗi chữ cái được thay thế bằng một chuỗi gồm 5 ký tự. Trong mật mã ban đầu gồm các chuỗi 'A' và 'B' nhưng dần dần mỗi chữ cái được gán cho một chuỗi gồm 5 chữ số nhị phân có thể là các chữ cái 'A' và 'B', số 0 và 1 hoặc bất cứ thứ gì bạn mong muốn.*

*Ví dụ : chữ 'D' được thay thế bằng 'aaabb', chữ 'O' được thay thế bằng 'abbab'....

## Phân loại:

- Có 2 loại mật mã Baconian:

+ ***Mật mã 24 chữ cái*** : Trong đó chữ I,J có cùng bảng mã, U,V cũng có cùng bảng mã

Ảnh

![image](https://github.com/yeuubonn2k4/BASIC_OF_CYBER/assets/161863346/fbca83bf-f273-4c89-930b-7fce06225f4e)

+ ***Mật mã 26 chữ cái*** : Trong đó tất cả các chữ cái đều có bảng mã duy nhất.

Ảnh

![image](https://github.com/yeuubonn2k4/BASIC_OF_CYBER/assets/161863346/590c29ff-112e-4abd-ba4d-4e522ffa5202)

## Giải mã thủ công chúng như thế nào?

- Giả sử mình sẽ viết 1 thông điệp bị mã hóa. Ở đây mình sẽ dùng mã 24 kí tự
BA BAAAA BBBAAA AABAA BA AAB AABA ABBAAB AABAA AA

- Viết lại theo mỗi chuỗi gồm 5 kí tự 

BABAA AABBB AAAAA BAABA AABAA BAABB AABAA BAAAA

*Bước 1* : Chúng ta sẽ xem B như 1 và A như 0 và ta có dãy số mới

BABAA <-> 10100 = 16+4=20

AABBB <-> 00111 = 4+2+1=7

AAAAA <-> 00000 = 0

BAABA <-> 10010 = 16+2=18

AABAA <-> 00100 =4

BAABB <-> 10011 = 16+2+1=19

AABAA <-> 00100 = 4

BAAAA <-> 10000 = 16

*Bước 2* : Chúng ta sẽ đánh số bảng chữ cái Tiếng Anh bắt đầu từ 0 đến 23 tương ứng với từ A đến Z
(với bảng mật mã 24 chữ cái vì I,J có cùng 1 bảng mã và U,V cũng có cùng bảng mã)

Dựa theo các con số đã tính trên : 20 là W, 7 là H, 0 là A , 18 là T, 4 là E, 19 là U/V , 4 cũng là E, 16 là R

Vậy ta có được thông điệp là WHATEUVER

- Để có thể giải mã nhanh chúng ta có thể so sánh luôn với ảnh 2 bảng mình đính kèm bài viết.

- 1 số tool hay dùng để giải mã

hxxps://www.dcode.fr/bacon-cipher

hxxps://cryptii.com/pipes/bacon-cipher

- Bạn cũng có thể áp dụng để giải mã dòng mã hóa này nha 

ba aabbaa b aaabaaa abba aaaaaa bb aaa bbabaabba ba aaaaaaaa ab b baaab bb babb ab baa abbaabb 'b' bb 'b'.

(*lưu ý ở dòng mã này sẽ có vài kí tự không tạo thành 1 phần của thông điệp*) :v

- Đây chỉ là bài viết dựa trên sự tự tìm hiểu của mình. Nếu như bài viết có bất cứ gì sai sót các bạn có thể comment và để lại ý kiến nha. Cảm ơn mọi người đã dành thời gian đọc <3






