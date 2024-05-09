## Cre : Dev minh di dau the

## MySQL Thực Thi Lệnh SELECT Như Thế Nào?

Khi học SQL, câu lệnh truy vấn đầu tiên mà bạn học chắc hẳn là SELECT. Ví dụ một câu lệnh truy vấn sau:

```
select * from Member where CardNo = 1
```

Nhưng đã bao giờ bạn tự hỏi, điều gì đã diễn ra trong quá trình MySQL thực thi một câu lệnh truy vấn select chưa?
Để lý giải được câu hỏi này, chúng ta cần hiểu rõ về kiến trúc bên trong của MySQL. Vì vậy, mình cùng mọi người phân tích cấu trúc bên trong của MySQL và xem từng thành phần đảm nhận những nhiệm vụ gì nhé.
Let’s go.

### 1. KIẾN TRÚC TỔNG QUAN CỦA MYSQL

Hãy bắt đầu với sơ đồ tổng quan quá trình thực thi câu lệnh của MySQL trước, để chúng ta có cái nhìn toàn cảnh.

![image](https://github.com/yeuubonn2k4/BASIC_OF_CYBER/assets/161863346/0f99da1e-c608-491b-b16e-0d249f42e4f0)

Kiến ​​trúc của MySQL được chia thành hai layer chính là Server Layer và Storage Engine Layer.

- Server Layer: Đảm nhiệm vai trò tạo kết nối, phân tích và thực thi câu lệnh SQL. Hầu hết các module chức năng cốt lõi của MySQL được triển khai ở tầng này. Bao gồm các module như connection manager, query cache, parser, preprocessor, optimizer, executor, ... Ngoài ra, tất cả các built-in functions (date, time, math,… ) và các chức năng khác chẳng hạn như stored procedures, triggers, views, … cũng được triển khai ở Server Layer.

- Storage Engine Layer: Đảm nhiệm vai trò lưu trữ và trích xuất dữ liệu. MySQL hỗ trợ nhiều storage engine khác nhau như InnoDB, MyISAM, Memory, … Mỗi loại storage engine có đặc tính, tính năng khác nhau và performance khác nhau, phù hợp với các trường hợp khác nhau. Nhưng chúng sử dụng chung Server Layer. Storage engine được sử dụng phổ biến nhất hiện nay là InnoDB, nó cũng là storage engine mặc định kể từ MySQL 5.5.
Lưu ý, kiến trúc MySQL còn các thành phần khác, ở đây mình đưa ra những thành phần chính liên quan tới câu lệnh SELECT để giảm độ phức tạp.
Bây giờ, chúng ta đã hiểu cơ bản về Server Layer và Storage Engine Layer. Tiếp theo, chúng ta tìm hiểu chi tiết hơn về quá trình thực thi của một câu lệnh truy vấn SQL và vai trò của từng module.

2. BƯỚC 1: TẠO CONNECTION
Nếu bạn muốn sử dụng MySQL trong hệ điều hành Linux thì bước đầu tiên của bạn phải là kết nối với dịch vụ MySQL.

```
mysql -h $ip -u $user -p
```

Quá trình kết nối trước tiên cần phải trải qua quá trình bắt tay ba bước TCP, vì MySQL dựa trên giao thức TCP để truyền tải. Nếu xác thực người dùng thành công, module Connection Manager sẽ lấy tất cả quyền của user và lưu lại. Mọi hành động tiếp theo của user trong connection này sẽ được kiểm tra theo quyền đã được lưu trước đó tại Connection Manager.
Do đó, nếu user đã thiết lập connection mà quản trị viên lại sửa đổi quyền của user thì sẽ không ảnh hưởng đến quyền của connection hiện tại. Chỉ khi user thực hiện tạo connection mới, thì các thay đổi về quyền mới được áp dụng.

LÀM CÁCH NÀO KIỂM TRA CÓ BAO NHIÊU CLIENT ĐANG KẾT NỐI VỚI MYSQL SERVER?

Bạn có thể chạy lệnh show processlist để kiểm tra.

```
mysql> show processlist;
+----+------+-----------+------+---------+------+-------+------+
| Id | User | Host | db | Command | Time | State | Info |
| 6  | root | localhost | NULL | Sleep | 736 | | NULL |
| 7  | root | localhost | NULL | Query | 0 | init | 0 |
+----+------+-----------+------+---------+------+-------+------+
2 rows in set (0.00 sec)
```

Ví dụ như trong hình trên, có hai user có username là root đang kết nối với dịch vụ MySQL. Trạng thái cột `Command` của user có Id = 6 là `Sleep`, nghĩa là user chưa thực hiện bất kỳ lệnh nào sau khi kết nối với dịch vụ MySQL. Hay nói cách khác, đây là connection không hoạt động và thời lượng không hoạt động là 736 giây (cột `Time`).
CÁC CONNECTION KHÔNG HOẠT ĐỘNG (IDLE CONNECTION) SẼ CHIẾM TÀI NGUYÊN CỦA MYSQL SERVER. LÀM SAO ĐỂ HẠN CHẾ ĐƯỢC VẤN ĐỀ NÀY?
Mặc định, Connection Manager sẽ tự động ngắt các idle connection sau 8 giờ. Chúng ta có thể cấu hình giá trị này qua tham số `wait_timeout`.
```
mysql> show variables like 'wait_timeout';
+---------------+-------+
| Variable_name | Value |
+---------------+-------+
| wait_timeout | 28800 |
+---------------+-------+
1 row in set (0.00 sec)
```
Tất nhiên, chúng ta cũng có thể chủ động ngắt các connection bằng cách sử dụng lệnh `kill connection +<connection_id>`.
```
mysql> kill connection +6;
Query OK, 0 rows affected (0.00 sec)
```
MySQL có giới hạn số connection đồng thời không? Nếu có thì giá trị đó bằng bao nhiêu?
MySQL có giới hạn số lượng connection đồng thời kết nối tới server và giá trị (`max_connections`) mặc định là 151. Nếu vượt quá giá trị này, hệ thống sẽ từ chối yêu cầu kết nối và đưa ra thông báo lỗi "Too many connections".
```
mysql> show variables like 'max_connections';
+-----------------+-------+
| Variable_name | Value |
+-----------------+-------+
| max_connections | 151 |
+-----------------+-------+
1 row in set (0.00 sec)
```

Tóm tắt chức năng của Connection Manager như sau:

- Thực hiện bắt tay ba bước TCP với client để thiết lập connection.

-  Xác thực username và password của user.

- Lấy và lưu lại quyền của user để kiểm tra các thao tác.

- Nếu có sự thay đổi về quyền thì thay đổi đó sẽ không ảnh hưởng đến các connection hiện tại. Quyền mới chỉ có hiệu lực đối với các connection sau thời điểm thay đổi.

### 3. QUERY CACHE
Sau kết nối hoàn tất, nếu SQL là câu lệnh SELECT, MySQL sẽ vào module Query Cache để tìm dữ liệu trước. Query Cache lưu trữ dự liệu dưới dạng key - value. Key là câu lệnh truy vấn SQL và value là kết quả trước của query đó.
Có vẻ Query Cache khá hữu ích? Tuy nhiên, đối với các bảng được cập nhật thường xuyên thì tỷ lệ cache hit rất thấp. Vì bất kể thao tác nào cập nhật lên bảng, các dữ liệu cache thuộc bảng đó sẽ bị xoá đi. Do đó, MySQL 8.0 loại bỏ module Query Cache.
Lưu ý: MySQL 8.0 loại bỏ module Query Cache ở Server Layer, chứ không phải buffer pool trong Storage Engine.

### 4. BƯỚC 2: PHÂN TÍNH CÚ PHÁP SQL
Trước khi câu lệnh truy vấn SQL được thực thi, MySQL sẽ phân tích cú pháp câu lệnh SQL và công việc này được thực hiện bởi các module Parser.

Phần Parser sẽ làm hai việc.

Thứ nhất, Lexical Scanner sẽ xác định từ khóa dựa trên chuỗi bạn nhập vào. Ví dụ câu lệnh SQL `select Name from Member` sẽ nhận được 4 token sau khi phân tích. Trong đó có 2 keyword là `select` và `from` và 2 non-keyword là `Name` và `Member`.

Từ kết quả của Lexical Scanner, sau đó Grammatical Checker sẽ đánh giá xem câu lệnh SQL bạn nhập có thõa mãn cú pháp MySQL hay không. Nếu không có vấn đề gì, Grammatical Checker sẽ xây dựng SQL syntax tree. Parse Tree chứa các thông tin như loại SQL, tên bảng, ... và các module sau sẽ sử dụng những thông tin này. Dưới đây là hình minh hoạ của một Parse Tree:

![image](https://github.com/yeuubonn2k4/BASIC_OF_CYBER/assets/161863346/0d82c046-2ef4-4d69-91b9-a768d8c59485)

Nếu chúng ta nhập câu lệnh SQL sai cú pháp, Parser sẽ báo lỗi. Ví dụ, nếu mình viết sai chính tả từ `from` thành `form` thì Parser sẽ báo lỗi như sau:

```
mysql> select * form Member;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'form Member at line 1
```
Nhưng lưu ý rằng Parser chỉ chịu trách nhiệm kiểm tra cú pháp và xây dựng syntax tree, chứ không tra cứu bảng hoặc sự tồn tại của các trường.
Vậy mobule nào sẽ thực hiện công việc kiểm tra sự tồn tại của các bảng và cột?

### 5. BƯỚC 3: OPTIMIZER

Sau khi đi qua Parser, Optimizer sẽ tiếp nhận Parse Tree (SQL Query) và quá trình được chia thành 2 giai đoạn sau:

- Giai đoạn tiền xử lý (Preprocessor).

- Giai đoạn tối ưu hóa (Optimizer).
  
#### 5.1. GIAI ĐOẠN TIỀN XỬ LÝ (PREPROCESSOR)

giai đoạn tiền xử lý, Preprocessor sẽ thực hiện các công việc sau:

- Kiểm tra xem bảng hoặc trường trong câu lệnh truy vấn SQL có tồn tại hay không.

- Convert từ dấu `*` thành tất cả cột của bảng tương ứng.

Nếu một bảng không tồn tại, Preprocessor sẽ báo lỗi như bên dưới:
```
mysql> select * from test;
ERROR 1146 (42S02): Table 'mysql.test' doesn't exist
```

#### 5.2. GIAI ĐOẠN TỐI ƯU HÓA (OPTIMIZER)

Sau giai đoạn tiền xử lý, Optimizer sẽ xác định chiến lược thực thi (execution plan).
Khi có nhiều index trong một bảng, Optimizer sẽ tính toán ra các chiến lược thực thi tương ứng với mỗi index. Ngoài thông tin về index, Optimizer phải dựa vào nhiều thông tin khác như các thông số dữ liệu (statistics) của bảng, cấu hình hệ thống, … để tính ra một chiến lược thực thi. Cuối cùng, Optimizer sẽ chọn ra một execution plan có chi phi thấp nhất.
Để biết Optimizer chọn index nào để truy vấn, ta có thể sử dụng từ khóa `explain` và xem giá trị của cột key để biết Optimizer chọn index nào:

![image](https://github.com/yeuubonn2k4/BASIC_OF_CYBER/assets/161863346/019a3b58-6370-4056-94c6-dfc9ead3e722)

Nếu giá trị cột key là null, nghĩa là đang không có index nào được sử dụng. Toàn bộ bảng sẽ được scan (type = ALL), truy vấn kiểu này kém hiệu quả nhất.

![image](https://github.com/yeuubonn2k4/BASIC_OF_CYBER/assets/161863346/31f5f914-9abd-49b8-ba37-a8e094436f39)

### 6. BƯỚC 4: QUERY EXECUTOR

Sau giai đoạn tối ưu hóa và xác định được chiến lược thực thi, đã đến lúc Executor thực hiện công việc của mình. Trong quá trình thực thi, Executor tương tác với storage engine.

Query sẽ được thực thi theo 1 trong 3 cách sau:

- Truy vấn duyệt toàn bộ bảng

- Truy vấn sử dụng primary index

- Truy vấn sử dụng composite index

Ở đây mình chỉ lấy một ví dụ truy vấn sử dụng primary index để minh hoạ cho quá trình thực thi query SELECT.

#### 6.1. TRUY VẤN SỬ DỤNG PRIMARY INDEX

Chúng ta xét câu query sau:

```
select * from Member where CardNo = 'M0001'
```
Giả sử, `CardNo` là primary key, nghĩa là chúng ta có unique index trên cột này. Optimizer sẽ sử dụng primary key index trong quá trình thực thi query:

- Executor gọi API của Storage Engine (InnoDB) kèm điều kiện `CardNo = 'M0001'`.

- Storage engine tìm bản ghi đầu tiên có CardNo = 'M0001' thông qua primary key index (B+Tree). Nếu bản ghi tồn tại, bản ghi sẽ được trả về cho Executor.

- Executor kiểm tra xem bản ghi đó có thỏa mãn các điều kiện truy vấn hay không. Nếu thõa mãn, nó sẽ lưu lại bản ghi đó.

- Quá trình truy vấn của Executor là một vòng lặp while. Nhưng index là unique, nghĩa là chỉ có 1 record duy nhất thoải mãn điều kiện trên. Do đó, Executor kết thức vòng lặp, trả kết quả về cho client và truy vấn kết thúc.

- Cuối cùng client hiển thị kết quả truy vấn.

Các cách thức thực thi khác đều có logic lặp và Executor kiểm tra từng record lấy được từ storage engine như trên. Điểm khác biệt là cách mà storage engine lấy ra từng record thoả mãn điều kiện của Executor.

### 7. TỔNG KẾT

- Connection Manager: Thiết lập, quản lý connection và xác thực, kiểm tra quyền của người dùng.

- Query Cache: MySQL 8.0 đã loại bỏ module này.

- Parser: Phân tích cú pháp của câu lệnh SQL và xây dựng parse tree (một trong những đầu vào của optimizer)

- Optimizer:

+ Kiểm tra sự tồn tại của bảng, của trường. Chuyển đổi từ select * thành select tất cả cột tương ứng.

+  Đánh giá chi phí thực thi, chọn phương án thực hiện có chi phí truy vấn thấp nhất.

- Executor: Thực thi truy vấn theo chiến lược thực thi, đọc các bản ghi từ storage engine và trả về cho client.
