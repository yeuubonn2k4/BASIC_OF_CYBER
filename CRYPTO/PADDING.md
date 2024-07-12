### Khai niem

>1 ky tu bo sung duoc phan bo co the duoc su dung de buoc dau ra duoc ma hoa thanh boi so nguyen cua 4 ky tu (hoac tuong duong khi van ban nhi phan chua ma hoa khong phai boi so cua 3 byte); cac ky tu dem nay sau do phai bi loai bo khi giai ma nhung van cho phep tinh toan do dai hieu dung cua van ban chua ma hoa khi do dai nhi phan dau vao cua no khong phai la boi so cua 3 byte (ky tu khong phai dem cuoi cung thuong duoc ma hoa sao cho khoi 6 bit cuoi cung ma no bieu dien se duoc dem bang 0 tren cac bit it quan trong nhat cua no, nhieu nhat la 2 ky tu dem co the cuat hien o cuoi luong duoc ma hoa"

> Kết luận của bạn rằng việc đệm là không cần thiết là đúng. Luôn có thể xác định độ dài của đầu vào một cách rõ ràng từ độ dài của chuỗi được mã hóa.

Tuy nhiên, việc đệm sẽ hữu ích trong những trường hợp mà các chuỗi được mã hóa base64 được nối lại theo cách mà độ dài của từng chuỗi riêng lẻ bị mất, ví dụ như có thể xảy ra trong một giao thức mạng rất đơn giản.

Nếu các chuỗi không đệm được nối lại, không thể khôi phục dữ liệu gốc vì thông tin về số byte lẻ ở cuối mỗi chuỗi riêng lẻ bị mất. Tuy nhiên, nếu sử dụng chuỗi đệm, không có sự mơ hồ và toàn bộ chuỗi có thể được giải mã chính xác.

## Vi du padding:

I ma hoa thanh SQ( padding xong no se thanh SQ==)

Giả sử chúng ta có một chương trình mã hóa base64 các từ, nối chúng lại và gửi chúng qua mạng. Nó mã hóa "I", "AM" và "TJM", kẹp các kết quả lại với nhau mà không cần đệm và truyền chúng.

Imã hóa thành SQ( SQ==có đệm)

AMmã hóa thành QU0( QU0=có đệm)

TJMmã hóa thành VEpN( VEpNcó đệm)

>Vì vậy, dữ liệu được truyền là SQQU0VEpN. Người nhận giải mã base64 thành I\x04\x14\xd1Q)thay vì IAMTJM. Kết quả là vô nghĩa vì người gửi đã phá hủy thông tin về vị trí kết thúc của mỗi từ trong chuỗi được mã hóa. Nếu người gửi đã gửi SQ==QU0=VEpNthay vào đó, người nhận có thể giải mã thành ba chuỗi base64 riêng biệt sẽ nối lại để tạo ra IAMTJM.

### Vay ki tu dem la gi?

Ký tự đệm là gì?

Các ký tự đệm giúp đáp ứng yêu cầu về độ dài và không mang ý nghĩa nào khác.

Ví dụ về số thập phân đệm: Với yêu cầu tùy ý là tất cả các chuỗi phải có độ dài 8 ký tự, số 640 có thể đáp ứng yêu cầu này bằng cách sử dụng các số 0 trước làm ký tự đệm vì chúng không mang ý nghĩa gì, "00000640".

Mã hóa nhị phân
Mô hình Byte: Đối với mã hóa, byte là đơn vị đo lường chuẩn thực tế và bất kỳ lược đồ nào cũng phải liên quan đến byte.

Base256 phù hợp chính xác với mô hình byte. Một byte bằng một ký tự trong base256.

Base16 , hệ thập lục phân hoặc hex, sử dụng 4 bit cho mỗi ký tự. Một byte có thể biểu diễn hai ký tự base16.

Base64 không phù hợp với mô hình byte (base32 cũng vậy), không giống như base256 và base16. Tất cả các ký tự base64 có thể được biểu diễn bằng 6 bit, thiếu 2 bit so với một byte đầy đủ.

Chúng ta có thể biểu diễn mã hóa base64 so với mô hình byte dưới dạng phân số: 6 bit cho mỗi ký tự trên 8 bit cho mỗi byte . Phân số này được rút gọn thành 3 byte trên 4 ký tự.

Tỷ lệ này, 3 byte cho mỗi 4 ký tự base64, là quy tắc mà chúng ta muốn tuân theo khi mã hóa base64. Mã hóa Base64 chỉ có thể đảm bảo đo lường đồng đều với các bó 3 byte, không giống như base16 và base256 khi mỗi byte có thể đứng riêng.

