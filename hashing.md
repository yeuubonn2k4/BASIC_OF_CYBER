### Khái niệm :

**Hashing** *là quá trình biến đổi đầu vào có kích thước, độ dài bất kỳ rồi sử dụng những thuật toán, công thức toán học để biến thành đầu ra tiêu chuẩn có độ dài nhất định. Quá trình đó sử dụng những Hàm băm (Hash function)*

*Ví dụ* : Server sẽ mã hóa mật khẩu của người dùng, biến chúng thành 1 tổ hợp các ký tự, chữ cái và con số dài

**Hàm băm (hashing function)** *là mật mã 1 chiều (bài viết trước mình có viết rồi).*

*Ví dụ* : Tải 1 bức ảnh trên mạng về, cho chạy qua hàm MD5 bạn sẽ nhận được 1 chuỗi dài 32 ký tự, cho chạy "apple" qua hàm hash MD5 kết quả sẽ là "1f3870be274f6c49b3e31a0c6728957f" (32bit)

-> ***Bạn cho bất kỳ gì vào hàm, đầu ra sẽ luôn là 1 chuỗi có độ dài nhất định***

### Đặc điểm của hàm băm

- **Tính tránh va chạm** : nhiều đầu vào khác nhau dẫn đến cùng một hàm băm. Trong một hàm băm hoàn hảo, điều này không khả thi.
  Có 1 số loại va chạm với khả năng khai thác khác nhau:

1.	**Tiền tố giống hệt nhau**: Tiền tố của 2 tệp giống nhau và sau đó có 1 vài khối va chạm với dữ liệu khác 

*Ví dụ* : Ta dùng hàm băm MD5 giá trị băm “0x1a2b3c4d5e67” và “0x1a2b3c4f5” có tiền tố giống nhau.

2.	**Tiền tố đã chọn** : Tiền tố của 2 tệp có thể là bất kỳ thứ gì bạn muốn và có thể khác nhau. Sau đó có 1 vài khối va chạm và cuối cùng kết thúc bằng 1 hậu tố giống hệt nhau

- **Tính hiệu quả** : thời gian tính toán những giá trị băm phải nhanh
tính nhạy cảm : chỉ cần thay đổi nhỏ trong giá trị ban đầu có thể thay đổi hoàn toàn giá trị băm

Để có thể coi đó là một hàm băm mật mã thì nó cần phải có các dấu hiệu : Với mỗi input chỉ tạo ra 1 output duy nhất, tính toán nhanh, không thể đảo ngược (có output nhưng chúng ta sẽ không thể biết input là gì giống như 8=3+5=2+6=1+7....), tránh va chạm (mỗi hàm băm sẽ có những đặc điểm nhất định để không bị giống các hàm băm khác), một khi input thay đổi một chút thì output sẽ thay đổi rất nhiều, input có thể là mọi kiểu dữ liệu. 

- Có rất nhiều thuật toán băm có sẵn, mỗi thuật toán đều có điểm mạnh và điểm yếu riêng. Trong blockchain người ta thường dùng:

1.	SHA-256 (Thuật toán băm an toàn 256-bit, được sử dụng phổ biến nhất khi tạo ra 1 hàm băm 256 bit có độ dài cố định và có tính bảo mật và tốc độ cao)

2.	Scrypt: Thuật toán được sử dụng trong 1 số loại tiền điện tử như Litecoin và Dofecoin với ưu điểm nhiều bộ nhớ hơn SHA-256 nên nó ít bị tấn công dựa trên ASIC hơn.

3.	SHA-3 (Thuật toán băm an toàn 3): sự kế thừa của SHA-2 và cung cấp khả năng bảo mật tốt hơn trước các cuộc tấn công, tạo ra 1 hàm băm có độ dài cố định lên tới 521 bit
......

### Chúng ta sẽ tìm hiểu về hàm MD5 (mã băm phổ biến nhất)

**Mã MD5** là mã để kiểm tra tính an toàn, chính xác của file khi chúng ta down về, mỗi file sẽ cho chúng ta 1 mã MD5. Khi có 1 chỉnh sửa nhỏ trong file là MD5 thay đổi ngay.

Với những file có dung lượng lớn, thời gian tải dài nên khả năng đứt mạng, lỗi trong quá trình tải thường xảy ra. Do đó để kiểm tra xem file tải đã đúng như file gốc hay chưa, chúng ta cần kiểm tra mã MD5 và so sánh với mã gốc mà người chia sẻ file cung cấp.

>Từ những năm 2000 thì hàm băm MD5 trở lên không an toàn trước sự phát triển của công nghệ thám mã gần đây do chúng ta đã có thể tính toán các va chạm trong MD5 với độ phức tạp 2^21 chỉ trong vài giây (mật khẩu sử dụng toàn chữ cái thường bị phá trong vòng 6s, nếu thêm chữ in hoa thì thời gian tối đa là 24 phút. Điều đó khiến thuật toán không còn phù hợp với hầu hết các trường hợp sử dụng trong thực tế.Hầu như bây giờ người ta sử dụng SHA512 và những thuật toán nâng cấp hơn

- **Tư tưởng của MD5** sẽ là dùng các phép toán XOR rất phức tạp và trải qua nhiều bước để tạo ra output. (mình đã để kèm ảnh sơ đồ để mn thấy nó qua được nó mã hóa như thế nào)

- Code chạy mã hóa MD5 áp dụng vào các ngôn ngữ lập trình :
hxxps://hanam88.com/kho-tai-lieu/63/102/su-dung-giai-thuat-md5-trong-cac-ngon-ngu-lap-trinh-va-cac-he-quan-tri-co-so-du-lieu-khac-nhau-.html

- **1 số tool mã hóa MD5 online:**

hxxps://bietmaytinh.com/md5/

hxxps://vsudo.net/tools/vi/md5-online

![image](https://github.com/yeuubonn2k4/BASIC_OF_CYBER/assets/161863346/2218bff6-60a6-4cd0-8e7e-82839a58ff54)

