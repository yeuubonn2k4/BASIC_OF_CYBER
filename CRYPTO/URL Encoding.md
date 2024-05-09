## URL Encoding ( Mã hóa dạng %)

Hôm nay mình xin tiếp tục chia sẻ tới mọi người dạng mã hoá tiếp theo
👉“URL encoding” (Percent encoding)👈

Đầu tiên chúng ta sẽ tìm hiểu về URL nhé:

URL (Uniform Resource Locator) với ý nghĩa là vị trí của một trang web trên Internet.

Mỗi URL được tạo thành từ nhiều thành phần khác nhau:

<scheme>://<user>:<password>@<host>: <port>/<path>?<query>#<fragment>
(Xem hình 1)

URL được hình thành từ 2 vùng là Reverse Character và Unreverse Character.

Các Reverse Character trong URL thường được sử dụng để mã hoá các ký tự đặc biệt (các kí tự có thể gây nhầm lẫn hoặc bị mã hoá để tránh sự xâm phạm bảo mật hoặc vấn đề khác). Phổ biến nhất các kí tự này được mã hoá bằng cách sử dụng phương pháp gọi là “URL encoding” hoặc “percent encoding”.

Phương pháp này thay thế các kí tự không an toàn bằng một dãy hai ký tự thập lục phân có dạng ‘%xx’ (trong đó ‘xx’ là mã thập lục phân của ký tự đó trong bảng ASCII.)

Ví dụ về cách mã hoá: Dấu cách (space) sẽ được mã hoá thành ‘%20’.

Để hình dung rõ loại mã hoá URL coding này chúng ta sẽ cùng đến một ví dụ:

URL gốc: //www.example.com/search?q=hello world
URL với reverse characters: //www.example.com/search?q=hello%20world

Trong ví dụ này, dấu cách giữa “hello” và “world” đã được mã hoá thành ‘%20’ để tránh sự nhầm lẫn và đảm bảo rằng URL có thể được xử lý chính xác trên mạng.

Đặc điểm nhận dạng loại mã này: Sử dụng các dấu % và 1 số văn bản gốc (mặc dù có mã hoá URL base64 và base32)

Công cụ mã hoá và giải mã URL
https://meyerweb.com/eric/tools/dencoding/

Khi encoding hoặc decoding bạn có thể sử dụng các bảng trong https://datacadamia.com/web/resource/encoding

Hãy thử giải decoding ví dụ này để hiểu hơn về URL encoding nha:
%20This%20is%20an%20example%20of%20URL%20or%20Percent%20Encoding.%0A

Cảm ơn mọi người đã đọc bài chia sẻ của mình. Nếu có bất cứ thắc mắc hay góp ý gì đừng ngần ngại comment để chúng ta có thể học hỏi lẫn nhau nha :3
