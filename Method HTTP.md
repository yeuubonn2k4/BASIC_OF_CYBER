## Cre : Dev minh di dau the

### 1. GET (Truy xuất):
Chức năng: Lấy thông tin từ một tài nguyên trên máy chủ.

Đặc điểm (Idempotent): Việc thực hiện nhiều yêu cầu GET giống nhau sẽ trả về cùng một kết quả.

Ví dụ: Truy cập trang web, tải xuống hình ảnh, lấy danh sách sản phẩm.

### 2. POST (Gửi):
Chức năng: Gửi dữ liệu đến máy chủ để tạo hoặc cập nhật một tài nguyên.

Đặc điểm: (Non-idempotent): Việc thực hiện nhiều yêu cầu POST giống nhau có thể dẫn đến việc tạo hoặc cập nhật tài nguyên nhiều lần.

Ví dụ: Đăng ký tài khoản, tạo bài viết, gửi đơn đặt hàng.

### 3. PUT (Cập nhật):

Chức năng: Cập nhật nội dung của một tài nguyên hiện có trên máy chủ.

Đặc điểm:Idempotent : Việc thực hiện nhiều yêu cầu PUT giống nhau sẽ cập nhật tài nguyên với cùng một nội dung.

Ví dụ: Cập nhật thông tin cá nhân, chỉnh sửa bài viết, thay đổi số lượng sản phẩm trong giỏ hàng.

### 4. DELETE (Xóa):

Chức năng: Xóa một tài nguyên khỏi máy chủ.

Đặc điểm(Idempotent): Việc thực hiện nhiều yêu cầu DELETE giống nhau sẽ xóa tài nguyên chỉ một lần.

Ví dụ: Xóa bài viết, hủy đơn hàng, xóa tài khoản.

### 5. PATCH (Cập nhật một phần):

Chức năng: Cập nhật một phần nội dung của một tài nguyên trên máy chủ.

Đặc điểm(Non-idempotent): Việc thực hiện nhiều yêu cầu PATCH giống nhau có thể dẫn đến việc cập nhật tài nguyên nhiều lần.

Ví dụ: Cập nhật địa chỉ email, thay đổi mật khẩu, cập nhật trạng thái đơn hàng.

### 6. HEAD (Lấy tiêu đề):

Chức năng: Lấy thông tin tiêu đề của một tài nguyên trên máy chủ, bao gồm loại tài nguyên, kích thước, thời gian sửa đổi, v.v.

Đặc điểm:Không trả về nội dung phản hồi (response body): Khác với GET, HEAD chỉ trả về thông tin tiêu đề, giúp tiết kiệm băng thông và thời gian tải.

Ví dụ: Kiểm tra xem tài nguyên có tồn tại hay không, lấy thông tinlastModified để xác định xem tài nguyên có được cập nhật hay không.

### 7. CONNECT (Kết nối):

Chức năng: Thiết lập một đường hầm TCP được mã hóa giữa máy khách và máy chủ.

Đặc điểm:Được sử dụng cho các giao thức không hỗ trợ HTTPS: Ví dụ như SSH, FTP.

Cung cấp bảo mật cho việc truyền dữ liệu nhạy cảm: Giúp bảo vệ dữ liệu khỏi bị đánh cắp hoặc thay đổi trong quá trình truyền tải.

### 8. OPTIONS (Lấy tùy chọn):

Chức năng: Lấy thông tin về các phương thức HTTP được hỗ trợ bởi một tài nguyên trên máy chủ.

Đặc điểm:Giúp xác định các hành động có thể thực hiện trên tài nguyên: Ví dụ như GET, POST, PUT, DELETE, v.v.

Có ích cho các ứng dụng muốn tương tác với các API web: Giúp ứng dụng biết cách tương tác với API một cách chính xác.

### 9. TRACE (Theo dõi):

Chức năng: Theo dõi hành trình của một yêu cầu HTTP từ máy khách đến máy chủ và ngược lại.

Đặc điểm: Giúp gỡ lỗi các vấn đề về kết nối mạng và máy chủ: Bằng cách theo dõi từng bước của yêu cầu, có thể xác định được điểm gặp sự cố.

Ít được sử dụng trong thực tế: Do tính phức tạp và ít ứng dụng thực tế


![image](https://github.com/yeuubonn2k4/BASIC_OF_CYBER/assets/161863346/6063ded3-3cf7-467c-b1a1-7af9f091ebd9)
