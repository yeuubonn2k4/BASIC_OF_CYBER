> Do tình cờ nhìn thấy một cái ảnh về phân biệt giữa những khái niệm Encoding – Encryption - Hashing nên mình đã nảy ra ý tưởng viết bài viết này để giúp cho mọi người có thêm cái nhìn phần nào để phân biệt cụ thể được 3 khái niệm trên hơn.

### 1. ENCODING 

Encoding là việc biến đổi data thành một format khác dựa trên một quy chuẩn nào đó để đáp ứng nhu cầu cần khi xử lý thông tin.

- Ví dụ:

Biến đổi từ kí tự ASCII “A” thành dãy số nhị phân 01000001. Và quy chuẩn ở đây là ASCII.

- Một số dạng Encoding:

ASCII,Unicode,URL Encoding, Base64,…(mình đã có viết bài về những chủ đề này ở trước đó, các bạn có thể tìm đọc để hiểu thêm về các dạng Encoding này).

- Mục đích của Encoding?

Chuyển đổi dữ liệu thành một dạng dữ liệu để đảm bảo dữ liệu có thể được sử dụng hoàn toàn (properly and safety).

- Nhược điểm:

Vì Encoding chuyển đổi dữ liệu sang một format khác sử dụng các biểu đồ có sẵn được public trên mạng do đó nó có thể hoàn toàn dịch ngược được mà không cần sử dụng bất kì key nào để dịch decode mà chỉ cần thuật toán encode nó.

2. ENCRYPTION 

Encryption là phương pháp để biến thông tin (phim ảnh, văn bản, hình ảnh….) từ định dạng bình thường sang dạng thông tin không thể hiểu được nếu không có phương tiện giải mã

- Sự khác biệt do với encoding ?

Encoding chúng ta chỉ cần có đúng công cụ encode để decode ngược lại là xong.

Encrytion quá trình sẽ kèm theo 1 secret-key hay là 1 mã bảo mật mà chỉ cần người tạo biết được.

- 1 số dạng Encrytion:

Asymmetric encrytions: Mã hóa bất đối xứng.

Symmetric encrytions: Mã hóa đối xứng.

TripleDES,Blowfish,AES,Twofish,IDEA,,RSA(RC4,RC5,RC6,..) (nếu có dịp mình sẽ cố gắng viết về những dạng này)

- Để có thể giải mã, chúng ta cần có đủ 3 thông tin:Đoạn dữ liệu đã bị mã hóa,Thuật toán dùng để mã hóa,key mật do người tạo đã sử dụng cho thuật toán này.

- Lợi ích của việc encryption này là có thể gửi thông tin đến một người nhận cụ thể và chỉ họ mới có thể đọc được hay truyền một số thông tin nhảy cảm trên Internet…

### 3. HASHING

Hashing là một quy trình biến đổi một chuỗi data đầu vào (input), xử lý bằng một thuật toán đặc biệt (hash function) và cho ra kết quả là dạng data khác.

- Ví dụ : MD5, SHA 1,HMAC,...

- Đặc điểm của hashing:

+ Với 1 đầu vào thì luôn chỉ cho ra 1 đầu ra duy nhất (tuy nhiên trong thực tế vẫn có hash function cho ra cùng 1 output với 2 input khác nhau được gọi là collision (đụng độ giá trị băm)

-> Hashing được đại diện cho sự toàn vẹn dữ liệu. Nếu có bất kì 1 thay đổi nhỏ nào của input thì sẽ có 1 output hoàn toàn khác.

+ Là quá trình 1 chiều, biến đổi từ input -> output chứ không làm ngược lại được.

-> Hashing được dùng trong các tính năng của hệ thống mà không cần phải tương tác với dữ liệu dạng sơ khai để nhằm bảo mật.

- Khác biệt với Encryption?

Encryption là quy trình mã hóa 2 chiều. Với Encrytion sau khi mã hóa ta hoàn toàn có thể dung secret-key để giải mã và lấy ra plain-text ban đầu.

Hashing không có không có key như vậy nên nó là quy trình chỉ có 1 chiều mã hóa chữ không giải mã được.

Vì đây là một bài viết chỉ nhằm phân biệt giữa ba khái niệm nên mình xin phép không đi quá sâu vào từng khái niệm nhằm giúp các bạn có thể hình dung được sự khác biệt chứ không quá lan man. Mình sẽ có những bài viết đi sâu hơn nữa để làm rõ những khái niệm trên. Bài viết của mình xin kết thúc tại đây, cảm ơn các bạn đã đọc bài viết của mình. Nếu các bạn có điều gì muốn share với nhau và có bất kỳ góp ý nào đừng ngần ngại comment để cùng nhau trao đổi học hỏi lẫn nhau nha. Mình rất mong có thể nhận được góp ý của mọi người để hoàn thiện bài viết ngày càng tốt hơn :3

Cre ảnh: Gotatech 

![image](https://github.com/yeuubonn2k4/BASIC_OF_CYBER/assets/161863346/54d6e0e5-19a6-4993-b797-6a50463c83ed)

