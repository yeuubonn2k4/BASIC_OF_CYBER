## UTF-8

### Khi mà chúng ta thực hiện thao tác View source code chúng ta hay thấy có một dòng sẽ có ghi “UTF-8”. Chúng ta sẽ thắc mắc nó là gì? Vì vậy hôm nay mình xin giới thiệu tới mọi người UTF-8, bước khởi đầu để bạn khám phá ngành Công nghệ thông tin.

👍 UTF-8 là gì?

(Unicode Transformation Format – 8 bit) là một chuẩn mã hóa ký tự Unicode. Nó sử dụng biểu diễn biến đổi dựa trên độ dài của byte để mã hóa các kí tự Unicode.

Ví dụ: Dòng chữ “Hello” khi được biến đổi thành UTF-8
01001000 01100101 01101100 01101111 01101111

👍Tóm tắt qua thì Unicode là một hệ thống mã hóa ký tự quốc tế bao gồm hơn 143,000 ký tự từ hầu hết các ngôn ngữ trên thế giới bằng cách sử dụng các dãy byte, khác hẳn với bảng mã ASCII khi chỉ mã hóa được 256 kí tự .

👍Cách UTF-8 biểu diễn ký tự:

Với ký tự ASCII (1 byte): Đầu tiên nó kiểm tra xem lý tự cần biểu diễn có thuộc bảng mã ASCII không. Nếu thuộc, UTF-8 sẽ được biểu diễn bằng 1 byte duy nhất, có giá trị từ 0 đến 127, sau đó chuyển số đó về U + số thuộc hệ 16. Cuối cùng ta chuyển số thuộc hệ 16 về hệ nhị phân 8 bit

• Ví dụ:
Kí tự “H” có mã ASCII là 72 (Hệ 10) chuyển sang UTF-8 ta được U + số 72 (hệ Hex) là 48. Sau đó chuyển 48 về hệ nhị phân ta được 01001000
Vậy Kí tự “H” khi chuyển sang UTF-8 là 01001000

👉Bạn cũng có thể tra ký tự H ở Hex qua link sau: (hxxps://jrgraphix.net/r/Unicode/0020-007F)

Với các ký tự không phải ASCII (2-4 byte). Nó sẽ sử dụng nhiều byte hơn. Đầu tiên, UTF-8 xác định số lượng byte cần thiết để biểu diễn các ký tự bằng cách kiểm tra các giá trị của ký tự trong bảng mã Unicode (hxxps://jrgraphix.net/r/Unicode/0020-007F)

Cụ thể:
• Kí tự Unicode từ U + 0080 -> U +07FF được biểu diễn bằng 2 byte
• Kí tự Unicode từ U + 0800 -> U +FFFF được biểu diễn bằng 3 byte
• Kí tự Unicode từ U + 10000 -> U +10FFFF được biểu diễn bằng 4 byte

Mỗi byte bên ngoài ký tự ASCII (2-4 byte) sẽ bắt đầu bằng một tiền tố byte để chỉ ra số byte được sử dụng cho ký tự này. Tiền tố byte có các bit đặc biệt để xác định số lượng byte và định dạng biểu diễn. Ví dụ:
• Một ký tự 2-byte bắt đầu bằng tiền tố “110xxxxx 10xxxxxx”.
• Một ký tự 3-byte bắt đầu bằng tiền tố “1110xxxx 10xxxxxx 10xxxxxx”.
• Một ký tự 4-byte bắt đầu bằng tiền tố “11110xxx 10xxxxxx 10xxxxxx 10xxxxxx”.

🤘Mình xin ví dụ về ký tự không nằm trong ASCII:

Ký tự ”世" (U+4E16) một ký tự không nằm trong bảng mã ASCII:

Bước 1: Xác định mã Unicode của ký tự "世" là U+4E16

Bước 2: Chuyển đổi mã Unicode thành dạng nhị phân 01001110 00010110

Bước 3 : Xác định số byte cần thiết để biểu diễn UTF-8

Theo bảng mã UTF-8:

• 1 byte cho ký tự trong khoảng từ U+0000 đến U+007F (7 bit đầu tiên)

• 2 byte cho ký tự trong khoảng từ U+0080 đến U+07FF (11 bit đầu tiên)

• 3 byte cho ký tự trong khoảng từ U+0800 đến U+FFFF (16 bit đầu tiên)

• 4 byte cho ký tự trong khoảng từ U+10000 đến U+10FFFF (21 bit đầu tiên)

Vì ký tự "世" có mã Unicode U+4E16 nằm trong khoảng từ U+0800 đến U+FFFF, nên nó sẽ được biểu diễn bằng 3 byte trong UTF-8.

Bước 4: Xác định các bit cho mỗi byte: Đối với các ký tự UTF-8 có độ dài lớn hơn 1 byte, chúng ta sử dụng các byte tiếp theo để lưu trữ phần còn lại của mã Unicode.

Đối với 3 byte:

• Byte đầu tiên bắt đầu với 1110xxxx.

• Byte thứ hai và ba bắt đầu với 10xxxxxx.

Bước 5: Gắn các bit từ mã Unicode vào vị trí tương ứng trong các byte UTF-8:

Byte đầu tiên: 1110xxxx

• Ta gắn 3 bit đầu từ mã Unicode vào các vị trí "x": 11100100

Byte thứ hai: 10xxxxxx

• Ta gắn 4 bit kế tiếp từ mã Unicode vào các vị trí "x": 10011000

Byte thứ ba: 10xxxxxx

• Ta gắn 4 bit cuối từ mã Unicode vào các vị trí "x": 10101100

🫶 Vậy kết quả cuối cùng chúng ta thu được mã UTF-8 cho ký tự "世": 11100100 10011000 10101100.

![image](https://github.com/yeuubonn2k4/BASIC_OF_CYBER/assets/161863346/beca4732-2e33-4dbb-9f86-c941c7ec4dd3)
