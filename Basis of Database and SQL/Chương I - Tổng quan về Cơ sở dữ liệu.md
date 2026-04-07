### I. Giới thiệu:
![image](https://hackmd.io/_uploads/HkvlBqR4bx.png)
- **Dữ liệu:** Một mô tả hình thức về thông tin và hoạt động.
> - Tên, địa chỉ, SĐT khách hàng
> - Báo cáo doanh thu
> - Đăng ký học phần
#### Cơ sở dữ liệu (Database):
- Một tập hợp **có cấu trúc** của những dữ liệu có liên quan với nhau được lưu trữ trong máy tính.
> - Danh sách sinh viên
> - Niên giám điện thoại
> - Danh mục các đề án
- Một database biểu diễn một phần của thế giới thực (thế giới thu nhỏ).
- Database được thiết kế, xây dựng và lưu trữ với mục đích xác định, phục vụ cho một số ứng dụng và user.
- Tập ngẫu nhiên của các dữ liệu không thể xem là một database.
> ![image](https://hackmd.io/_uploads/H1vpLc0NWl.png)
> Quản lý đề án của một công ty:
> - Định nghĩa cơ sở dữ liệu: Cấu trúc bảng gồm các thành phần dữ liệu và kiểu dữ liệu tương ứng.
> - Xây dựng database: Đưa dữ liệu vào các bảng.
> - Xử lý database:
>    - Thực hiện các truy vấn: "Cho biết những nhân viên thuộc phòng 5"
>    - Thưc hiện các phép cập nhật: "Chuyển nhân viên Nguyễn Thanh Tùng sang phòng số 1"
- Ưu điểm so với các hệ thống thông tin khác:
    - **Giảm trùng lặp** thông tin xuống mức thấp nhất, đảm bảo tính nhất quán và toàn vẹn dữ liệu.
    - Đảm bảo dữ liệu **được truy xuất** theo nhiều cách khác nhau.
    - Khả năng **chia sẻ thông tin** cho nhiều người, nhiều ứng dụng khác nhau.
#### Hệ quản trị cơ sở dữ liệu (Database Management System):
- Tập hợp các chương trình cho phép user tạo ra, phân tích, thiết kế, khai thác và duy trì database.
- Một phần mềm hệ thống cho phép định nghĩa, xây dựng và xử lý dữ liệu.
    - **Định nghĩa:** Khai báo bộ khung dữ liệu cùng với các mô tả chi tiết về dữ liệu.
    - **Xây dựng:** Lưu trữ dữ liệu trên bộ nhớ phụ.
    - **Xử lý:** Truy vấn, cập nhật và phát sinh báo cáo.
- Một hệ quản trị database phải có:
    - Ngôn ngữ giao tiếp giữa user và database.
    - Từ điển dữ liệu.
    - Biện pháp bảo mật khi có yêu cầu.
    - Cơ chế giải quyết tranh chấp dữ liệu.
    - Cơ chế sao lưu và phục hồi.
    - Đảm bảo tính độc lập giữa dữ liệu và chương trình.
#### Hệ cơ sở dữ liệu (Database System):
![image](https://hackmd.io/_uploads/ryei8cC4-e.png)

### II. Quá trình phát triển:
- **Tập tin (File):**

![image](https://hackmd.io/_uploads/ryecPcAVbe.png)
- **Hạn chế:**
    - Dữ liệu bị trùng lặp và dư thừa.
    - Thiếu tính nhất quán giữa các dữ liệu.
    - Khó khăn trong việc truy xuất.
    - Việc chia sẻ dữ liệu bị hạn chế.
    - Khó khôi phục.
- **Database:**

![image](https://hackmd.io/_uploads/ByN1ucCEZl.png)

### III. Một số đặc tính của cơ sở dữ liệu:
#### Tính tự mô tả:
- Hệ database không chỉ chứa bản thân database mà còn chứa **định nghĩa đầy đủ** (mô tả) của database.
- Các định nghĩa được lưu trữ trong **catalog**: Chứa các thông tin về cấu trúc tập tin, kiểu và dạng thức lưu trữ của mỗi thành phần dữ liệu và những ràng buộc dữ liệu.
- Dữ liệu trong catalog gọi là metadata (data of data).
- Các chương trình ứng dụng có thể truy xuất đến nhiều database nhờ thông tin cấu trúc được lưu trữ trong catalog.
#### Tính độc lập giữa chương trình và dữ liệu:
![image](https://hackmd.io/_uploads/H1WVcqANZx.png)
Vì định nghĩa về cấu trúc database được lưu trữ trong catalog nên khi có **thay đổi nhỏ về cấu trúc** ta phải sửa lại chương trình.

#### Tính trừu tượng dữ liệu:
- Hệ database cho phép trình bày dữ liệu ở một mức trừu tượng cho phép, nhằm che bớt những chi tiết lưu trữ thật của dữ liệu.
- Trừu tượng hoá dữ liệu: Mô hình dữ liệu:
    - Đối tượng
    - Thuộc tính của đối tượng
    - Mối liên hệ

#### Tính nhất quán:
- Lưu trữ dữ liệu thống nhất giúp tránh được tình trạng trùng lặp thông tin.
- Có cơ chế điều khiển truy xuất dữ liệu hợp lý:
    - Tránh được việc tranh chấp dữ liệu.
    - Bảo đảm dữ liệu luôn đúng tại mọi thời điểm.

#### Các cách nhìn dữ liệu:
- Hệ database cho phép nhiều user thao tác lên cùng một database.
- Mỗi user đòi hỏi một cái nhìn (view) khác nhau về database.
- Một view là một phần của database hoặc dữ liệu tổng hợp từ database.

### IV. Người sử dụng cơ sở dữ liệu:
#### Quản trị viên (Database Administrator - DBA):
Có trách nhiệm quản lý hệ database:
- Cấp quyền truy cập database.
- Điều phối và giám sát việc sử dụng database.

#### Thiết kế viên (Database Designer):
- Chịu trách nhiệm về:
    - Lựa chọn cấu trúc phù hợp để lưu trữ dữ liệu.
    - Quyết định những dữ liệu nào cần được lưu trữ.
- Liên hệ với user để nắm bắt được những yêu cầu và đưa ra một thiết kế database thoả yêu cầu.
- Có thể là một nhóm các DBA quản lý các database sau khi việc thiết kế hoàn tất.

#### Người dùng cuối (End User):
- Người ít sử dụng:
    - Ít khi truy cập database nhưng cần những thông tin khác nhau trong mỗi lần truy cập và dùng những câu truy vấn phức tạp.
- Người sử dụng thường xuyên:
    - Thường xuyên truy vấn và cập nhật database nhờ vào một số các chức năng đã được xây dựng sẵn.
    - Nhân viên.
- Người sử dụng đặc biệt:
    - Thông thạo về hệ quản trị database, tự xây dựng những truy vấn phức tạp cho công việc.
    - Kỹ sư, nhà khoa học, người phân tích,...

### V. Kiến trúc của hệ quản trị cơ sở dữ liệu:
![image](https://hackmd.io/_uploads/H1PbMi0Ebl.png)
#### Kiến trúc ba lược đồ:
![image](https://hackmd.io/_uploads/HkbkljCNZx.png)
- **Mức trong (lược đồ trong):** Mô tả cấu trúc lưu trữ vật lý database.
- **Mức quan niệm (lược đồ quan niệm):**
    - Mô tả cấu trúc toàn thể database cho một cộng đồng user, gồm thực thể, kiểu dữ liệu, mối liên hệ và ràng buộc.
    - Che bớt các chi tiết của cấu trúc lưu trữ vật lý.
- **Mức ngoài (lược đồ ngoài):**
    - Còn gọi là mức khung nhìn (view).
    - Mô tả một phần database mà một nhóm user quan tâm đến và che giấu phần còn lại của database đối với nhóm user đó.

#### Độc lập dữ liệu:
- **Độc lập logic:** Khả năng thay đổi lược đồ quan niệm mà không thay đổi lược đồ ngoài hoặc các chương trình ứng dụng.
- **Độc lập vật lý:** Khả năng thay đổi lược đồ trong mà không làm thay đổi lược đồ quan niệm cũng như lược đồ ngoài.

### VI. Các tính năng của hệ quản trị cơ sở dữ liệu:
- **Kiểm soát được tính dư thừa của dữ liệu:** Tích hợp các nhu cầu dữ liệu của user để xây dựng một database thống nhất.
- **Chia sẻ dữ liệu:** Trong môi trường đa user, các hệ quản trị phải cho phép truy xuất dữ liệu đồng thời.
- **Hạn chế những truy cập trái phép:** Từng user và nhóm user có một tài tài khoản và mật mã để truy xuất dữ liệu.
- **Cung cấp nhiều giao diện:** Hệ quản trị cung cấp ngôn ngữ giữa database và user.
- **Đảm bảo các ràng buộc toàn vẹn (Integrity Constraints):**
    - Ràng buộc toàn vẹn là những quy định cần được thoả mãn để đảm bảo dữ liệu luôn phản ánh đúng ngữ nghĩa của thế giới thực.
    - Một số ràng buộc có thể được khai báo với hệ quản trị và hệ quản trị sẽ tự động kiểm tra. Một số ràng buộv khác được kiểm tra nhờ chương trình ứng dụng.
- **Khả năng tự động sao lưu dự phòng khi gặp sự cố:** Có khả năng khôi phục dữ liệu khi có sự hư hỏng về phần cứng hoặc phần mềm.
- Các tính năng khác:
    - **Chuẩn hoá:** Cho phép DBA định nghĩa và bắt buộc áp dụng một chuẩn thống nhất cho mọi user.
    - **Uyển chuyển:** Khi nhu cầu công việc thay đổi, cấu trúc database rất có thể thay đổi, hệ quản trị cho phép thêm hoặc mở rộng cấu trúc mà không làm ảnh hưởng chương trình ứng dụng.
    - **Giảm thời gian phát triển ứng dụng.**
    - **Tính khả dụng:** Khi có một thay đổi lên database, tất cả user đều thấy được.

### VII. Các khái niệm:
#### Mô hình dữ liệu (Data Model):
- Bao gồm:
    - Các khái niệm biểu diễn dữ liệu.
    - Các phép toán xử lý dữ liệu.
- Phân loại:
    - **Mô hình mức cao:**
        - Cung cấp các khái niệm gần gũi với user.
        - Mô hình phải tự nhiên và giàu ngữ nghĩa.
    - **Mô hình cài đặt:** Đưa ra các khái niệm user có thể hiểu được nhưng không quá xa với cách dữ liệu được tổ chức thật sự trên máy tính.
    - **Mô hình mức thấp (mô hình vật lý):** Đưa ra các khái niệm mô tả chi tiết về cách thức dữ liệu được lưu trữ trong máy tính.
> Ví dụ:
> - Mô hình mức cao: Mô hình thực thể kết hợp (ER), mô hình đối tượng,...
> ![image](https://hackmd.io/_uploads/H1bGBjCNZe.png)
> ![image](https://hackmd.io/_uploads/HJXHSsANZl.png)
> - Mô hình cài đặt: Mô hình quan hệ, mô hình mạng, mô hình phân cấp:
> ![image](https://hackmd.io/_uploads/r1QvBoAEZg.png)
> ![image](https://hackmd.io/_uploads/By4OSsRVbx.png)
> ![image](https://hackmd.io/_uploads/rJxtSiA4-g.png)

#### Lược đồ cơ sở dữ liệu (Database Schema):
Là các mô tả về cấu trúc và ràng buộc trên database.
> ![image](https://hackmd.io/_uploads/ryOoSiANWg.png)

#### Thể hiện cơ sở dữ liệu (Database Instance):
- Là dữ liệu hiện thời được lưu trữ trong database ở một thời điểm nào đó.
- Còn gọi là tình trạng của database:
> ![image](https://hackmd.io/_uploads/SJqRriAE-x.png)

### VIII. Ngôn ngữ cơ sở dữ liệu:
- **Ngôn ngữ định nghĩa dữ liệu (DDL - Data Definition Language):** Xác định ra lược đồ quan niệm
- **Ngôn ngữ lưu trữ dữ liệu (SDL - Storage Definition Language):** Ngôn ngữ định nghĩa lược đồ trong
- **Ngôn ngữ định nghĩa khung nhìn (VDL - View Definition Language):** Ngôn ngữ định nhgiã lược đồ ngoài
- **Ngôn ngữ thao tác dữ liệu (DML - Data Manipulation Language):**
    - Cho phép truy xuất, thêm, xoá, sửa dữ liệu.
    - Mức cao (phi thủ tục).
    - Mức thấp (thủ tục).
