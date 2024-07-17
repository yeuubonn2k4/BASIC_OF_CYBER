>Cre: Dev oi minh di dau the
>
## DEADLOCK LÀ GÌ?

Deadlock xảy ra khi hai hoặc nhiều tiến trình đang chờ đợi lẫn nhau giải phóng tài nguyên mà chúng cần để tiếp tục. Điều này dẫn đến tình huống không tiến trình nào có thể tiếp tục, và chúng kết thúc trong trạng thái chờ đợi vô hạn.

🔹 ĐIỀU KIỆN COFFMAN

Các điều kiện Coffman, được đặt theo tên của Edward G. Coffman, Jr., người đầu tiên mô tả chúng vào năm 1971, phác thảo bốn điều kiện cần thiết phải cùng xuất hiện để deadlock xảy ra:

- Loại trừ lẫn nhau: Tài nguyên không thể được chia sẻ đồng thời

- Giữ và chờ đợi: Các tiến trình giữ tài nguyên trong khi chờ đợi tài nguyên khác

- Không có thu hồi: Tài nguyên không thể bị lấy đi một cách cưỡng bức

- Chờ đợi vòng tròn: Một chuỗi tiến trình hình tròn, mỗi tiến trình chờ đợi tài nguyên do tiến trình tiếp theo nắm giữ

🔹 PHÒNG NGỪA DEADLOCK

- Sắp xếp tài nguyên: Yêu cầu các tiến trình yêu cầu tài nguyên theo một thứ tự cụ thể

- Thời gian chờ: Đặt giới hạn thời gian sử dụng tài nguyên để ngăn chặn việc giữ vô thời hạn

- Thuật toán Banker: Một phương pháp kiểm tra xem việc cấp yêu cầu tài nguyên có dẫn đến trạng thái an toàn hay không

🔹 KHÔI PHỤC SAU DEADLOCK

- Chọn nạn nhân: Chọn một hoặc nhiều tiến trình để kết thúc hoặc quay lại

- Quay lại: Hoàn tác các hành động của (các) tiến trình được chọn để giải phóng tài nguyên

![image](https://github.com/user-attachments/assets/d9f3e2ac-0d81-4093-a159-a68904203fa4)
