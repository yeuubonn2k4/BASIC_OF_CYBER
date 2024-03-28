Cre : anh avux
// Có dựa theo 1 vài nguồn tài liệu

# Kiến trúc mạng máy tính : 
## là cách bố trí , sắp xêos các máy tính trong mạng máy tính và việc phân chia công việc cho mỗi máy tính

### Client-SEVER ARCHITECTURE (kiến trúc mô hình khách - chủ)
- Phân chia công viêc giữa bên cung cấp dịch vụ (servers) và bên yêu cầu dịch vụ (clients)

- 1 Máy chủ trung tâm (central server) có thể cung cấp dịch vụ cho nhiều máy khách -> dữ liệu được chia sẻ lên server đều có thể truy cập được trên các máy khách

- - Các máy khách muốn giao tiếp với nhau đều thông qua máy chủ
 
  - Clients và servers giao tiếp với nhau thông qua mô hình request- response

  ### ƯU và Nhược điểm

  +) ƯU điểm:

  - Backup dữ liệu dễ dàng và ít tốn kém do k cần backup dữ liệu riêng lẻ trên mỗi máy tính
 
  - Hiệu suất do máy chủ thường khoẻ hơn rất nhiều so với các máy khách
 
  - Bảo mật hơn do việc truy cập trái phép đều bị server từ chối, tất cả dữ liệu được gửi dều phải thông qua server
 
  - Khả năng thay đổi quy mô dễ do máy chủ có thê kết nối với nhiều máy khách
 
    +) Nhược điểm :

    - Nếu server sập thì tất cả cùng sập
   
    - Phí duy trì, bảo dưỡng server cao
   
    - Tốn kém hơn ở khoản đầu tư cho server để cải thiện tài nguyên
   
    ## VÍ DỤ VỀ KIẾN TRÚC MÔ HÌNH KHÁCH - CHỦ

    - 1  người muốn truy cập dịch vụ online banking thông qua trinh duyệt (client) , so đó trình duyệt sẽ gửi resquest tới web server của ngân hàng
   
    - Tài khảon đăng nhập của người đó được lưu trong database, web server truy cập vào database server
     

    # PEER-TO-PEER (P2P) : Kiến trúc đồng đẳng:
    Không phân biệt máy chủ hay máy khách (peer)  -> Tất cả các máy đều có quyền hạn và công việc ngang hàng nhau

    Các máy tính trong mạng máy tính đều liên kết với nhau

    ## ƯU và Nhược điểm

    +) Ưu điểm

    - Ít tốn kém do không có 1 server trung tâm nào
   
    - Nếu một máy hỏng thì các mảy khác không bị ảnh hưởng
   
    - Dễ cài đặt / xây dựng và duy trì do mỗi máy đều có thể quản lý chính nó
   
    +) Nhược điểm

    - Khả năng thay đổi quy mô (Scalability) rất khó do mỗi máy tính đều kết nối vứi nhau
   
    - Mỗi máy tính đều có dữ liệu backup riêng lẻ và các phương pháp bảo mật cần được cài đặt riêng lẻ trên mỗi máy tính
   
    - Vấn đề bảo mật kém do mỗi máy tự quản lý chính nó

    ### PHân Biệt IPV4 và IPV6

    Địa chỉ IP là địa chỉ duy nhất để định danh cho 1 thiết bị trên Internet ( vị trí ) -> máy đó có thể truy cập được vào mạng

+) IPV4 ( Internet Protocol version 4)

    VD: 192.168.1.1  ( 32 bit, có 2^32 địa chỉ)

    Các thành phần được cách nhau bởi dấu "."

 +) IPV6 (Internet Protocol version 6) có (128 bit,2^128 địa chỉ)

   Các thành phần được ngăn nhau ":"

   ## Domain Name System (DNS) :
"Hệ thống phân giải tên miền) : Chuyển tên miền thành địa chỉ IP tương ứng và ngược lại

- DNS server thực hiện các truy vấn DNS và DNS client thực hiện gửi truy vấn DNS

  ### Cách thức DNS hoạt động:

  - 4 server làm việc với nhau để lấy IP:

    1) Recursive resolver Nhận truy vấn từ DNS client sau đó truy vấn 3 server còn lại . sau khi nhận IP từ authoritative server, chuyển trực tiếp về slient,Recursive resolver lưu địa chỉ IP đó vào cache để khi có bất kì truy vấn nào khác vào tên miền đó , nó sẽ trả ngay mà không cần truy vấn tới các servers.
   
    2) Root server: resolver truy vấn server này đầu tiên ( root sẽ trả về resolver địa chỉ IP của TLD server tương ứng)
   
    3) TLD server (Top- level domain) lưu trữ thông tin của tên miền. sau khi nhận request từ resolver thì gửi IP của authoritative server
   
    4) Authorative nameserve: gửi IP thật của server gốc ban đầu
   
******

`
Ví dụ về cách thức hoạt động:
`

-Nhập google.com vào thanh tìm kiếm trên trình duyệt. Truy vấn được tạo ra bởi DNS client có sẵn trong trình duyệt và gửi cho recursive resolver đầu tiên

- Sau khi recursive resolver tiếp nhận truy vấn, nó gọi đến lần lượt 3 DNS servers còn lại

- Đầu tiên nó gọi đến root server. Nó phân tích truy vấn, thấy TLD là ".com" nên nó trả về resolver địa chỉ IP của TLD server, cụ thể là .com TLD server

- Tiếp theo resolver giao tiếp với TLD server. TLD server kiểm tra xem tên miền "google.com" có tồn tại không, nếu có thì nó sẽ gửi trả về kết quả địa chỉ IP của authorative nameserver cho resolver

- Cuối cùng, resolver gọi đến authorative nameserver. Authorative server sẽ trả về IP tương ứng với tên miền google.com cho resolver

- Nhận được IP từ authorative server, resolver thực hiện trả về IP cho trình duyệt


## API 

### Khái niệm 

![github](https://raw.githubusercontent.com/a-vux/30daysOfHappiness/main/001-ComputerNetwork/src/api-eg.png)

API (Application Programming Interface : Giao dịch lập trình ứng dụng ) : 1 phần mềm trung gian giúp 2 ứng dụng giao tiếp với nhau.

!
Nếu UI là giao diện tương tác của người dùng và ứng dụng

API giao diện tương tác giữa ứng dụng A và ứng dụng B. Giống người dùng chỉ việc thao tác sử dụng ứng dụng theo chỉ dẫn mà không cần biết cách thức hoạt động ra sao, ứng dụng A cũng chỉ cần làm theo ứng dụng để có thể Tương tác được mà không cần biết gì thêm.

#### Lợi ích API

- Lợi nhuận ( ưng dụng A thu nhiều lợi nhuận phải kết hợp với nhiều ứng dụng khác. Mà xây dựng thủ công thì không khả thi -> API giải quyết . Các ứng dụng khác sẽ bultd các API của họ, nếu ứng dụng A muốn sử dụng tới ứng dụng hoặc chức năng nào đó mà API cụ thể nào đấy cung cấp thì A sẽ gửi API request, sau đó nhận được phản hồi từ ứng dụng kia

- - Các lợi ích :
 
    + Tính đơn giản : API cung cấp dữ liệu mong muốn đến bên sử dụng mà không cần biết quá nhiều về ứng dụng kia làm như thế nào
   
      + Tính hiệu quả : Không cần code quá nhiều, bê dữ liệu hoặc chức năng của API bên thứ ba về là được
     
        + Customization : lấy dữ liệu về rồi thì sử dụng như thé nào cũng nữa
       

  ## Phân loại:

  1) Internal API : API sử dụng bên trong phần mềm hoặc ứng dụn ( cùng 1 hệ thống)  VD: API kết nối Front-end và Back-end
 
     Private API : dùng cho nội bộ

     API provided by Third Parties : được cung cấp bởi bên thứ 3

     Public/ Externally API : được đưa ra thị trường 1 cách công khai
    
