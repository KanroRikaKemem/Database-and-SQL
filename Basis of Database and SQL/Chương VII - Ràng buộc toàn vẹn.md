## I. Khái niệm:
- Ràng buộc toàn vẹn (Integrety Constraints) xuất phát từ những quy định hay điều kiện:
    - Trong thực tế.
    - Trong mô hình dữ liệu. Các thao tác làm thay đổi dữ liệu không nên được thực hiện một cách tuỳ tiện vì có thể đưa database đến tình trạng xấu.
- Ràng buộc toàn vẹn là một điều kiện được định nghĩa trên một hay nhiều quan hệ khác nhau, nghĩa là **những yêu cầu** mà tất cả thể hiện của quan hệ phải thoả.
- Các ràng buộc toàn vẹn là những điều kiện **bất biến** mà mọi thể hiện của quan hệ đều phải thoả ở bất kì thời điểm.
- Tại sao cần phải có ràng buộc toạn vẹn?
    - Bảo đảm **tính kết dính** của các thành phần cấu tạo nên database.
    - Bảo đảm **tính nhất quán** của dữ liệu.
    - Bảo đảm database luôn biểu diễn **đúng ngữ nghĩa** thực tế.
> ![image](https://hackmd.io/_uploads/ryfYEk5Ibx.png)

## II. Các đặc trưng của ràng buộc toàn vẹn:
### 1. Bối cảnh:
Là những quan hệ có khả năng bị vi phạm ràng buộc toàn vẹn khi thực hiện các phép cập nhật.
> - Ví dụ 1:
> ![image](https://hackmd.io/_uploads/H1Wyr198-e.png)
> - Ví dụ 2:
> ![image](https://hackmd.io/_uploads/rkeQxr1q8Ze.png)

### 2. Nội dung:
Nội dung của một ràng buộc toàn vẹn được phát biểu bằng:
- Ngôn ngữ tự nhiên: Dễ hiểu những thiếu tính chặt chẽ.
- Ngôn ngữ hình thức:
    - Cô đọng, chặt chẽ nhưng đôi lúc khó hiểu.
    - Biểu diễn thông qua:
        - Đại số quan hệ.
        - Phép tính quan hệ.
        - Mã giả (Pseudo code).
> - Ví dụ 1:
> ![image](https://hackmd.io/_uploads/B1CLHJ98We.png)
> - Ví dụ 2:
> ![image](https://hackmd.io/_uploads/ByRvrkcLZx.png)

### 3. Bảng tầm ảnh hưởng:
- Là bảng hai chiều xác định thao tác cập nhật nào cần phải kiểm tra ràng buộc toàn vẹn khi được thực hiện trên quan hệ bối cảnh.
    - Thao tác ảnh hưởng (+) lên các quan hệ nằm trong bối cảnh.
    - Thao tác không ảnh hưởng (-) lên các quan hệ nằm trong bối cảnh.
- Có hai loại:
    - Bảng tầm ảnh hưởng cho một ràng buộc toàn vẹn.
      
    ![image](https://hackmd.io/_uploads/Syyar19UZx.png)
    - Bảng tầm ảnh hưởng tổng hợp.
      
    ![image](https://hackmd.io/_uploads/r1eCHk9LWx.png)
- Kí hiệu:
    - $+$: Có thể gây ra vi phạm ràng buộc toàn vẹn.
    - $-$: Không thể gây ra vi phạm ràng buộc toàn vẹn.
    - $+(A)$: Có thể gây ra vi phạm ràng buộc toàn vẹn trên thuộc tính $A$.
    - $-(*)$: Không thể gây ra vi phạm ràng buộc toàn vẹn do thao tác không thực hiện được.
- Một số quy định:
    - Những thuộc tính khoá (Thuộc tính nằm trong khoá chính của quan hệ) không được phép sửa giá trị.
    - Thao tác thêm và xoá xét trên một bộ giá trị của quan hệ. Thao tác sửa xét từng thuộc tính của quan hệ.
    - Trước khi xét thao tác thực hiện có thể làm vi phạm ràng buộc hay không thì database phải thoả ràng buộc toàn vẹn trước.

## III. Phân loại:
### 1. Một quan hệ:
#### a) Miền giá trị:
- Ràng buộc **quy định các giá trị cho một thuộc tính**:
  
![image](https://hackmd.io/_uploads/S1_IIkqLWe.png)
- Miền giá trị:
    - Liên tục
    - Rời rạc
> - Ví dụ 1:
> ![image](https://hackmd.io/_uploads/BJTvLy5IWl.png)
> - Ví dụ 2:
> ![image](https://hackmd.io/_uploads/rkvKLk58-e.png)

#### b) Liên bộ:
- **Ràng buộc giữa các bộ giá trị khác nhau trong cùng một quan hệ.**
- Sự tồn tại của một hay nhiều bộ phụ thuộc vào sự tồn tại của một hay nhiều bộ khác trong cùng một quan hệ.
  
![image](https://hackmd.io/_uploads/HJpRI198Zl.png)
- Trường hợp đặc biệt:
    - Ràng buộc khoá chính.
    - Ràng buộc duy nhất (unique).
> - Ví dụ 1:
> ![image](https://hackmd.io/_uploads/SJ1fwJ98-l.png)
> - Ví dụ 2:
> ![image](https://hackmd.io/_uploads/Hklmvk5IWx.png)
> - Ví dụ 3:
> ![image](https://hackmd.io/_uploads/ry-4PJ58Ze.png)

#### c) Liên thuộc tính:
Là **ràng buộc giữa các thuộc tính khác nhau trong cùng quan hệ**:

![image](https://hackmd.io/_uploads/B1h9w1c8Wg.png)
> - Ví dụ 1:
> ![image](https://hackmd.io/_uploads/SkniDy9Ubl.png)
> - Ví dụ 2:
> ![image](https://hackmd.io/_uploads/ry9nPy5LZx.png)

### 2. Nhiều quan hệ:
#### a) Tham chiếu:
- Giá trị xuất hiện tại các thuộc tính trong một quan hệ nào đó phải tham chiếu đến giá trị khoá chính của một quan hệ khác cho trước:
  
![image](https://hackmd.io/_uploads/HJ3ldJcLbl.png)
- Trường hợp đặc biệt: Ràng buộc khoá ngoại.
> ![image](https://hackmd.io/_uploads/ByRb_15U-l.png)
- Còn gọi là ràng buộc tồn tại ràng buộc khoá ngoại.
- Thường có bối cảnh là hai quan hệ nhưng có trường hợp suy biến thành một quan hệ.
> ![image](https://hackmd.io/_uploads/HJ9B_k9LWg.png)

#### b) Liên bộ, liên quan hệ:
Là **ràng buộc xảy ra giữa các bộ  trên nhiều quan hệ khác nhau**.

![image](https://hackmd.io/_uploads/HyBPdk9L-g.png)
> ![image](https://hackmd.io/_uploads/Bk9d_JqL-l.png)

#### c) Liên thuộc tính, liên quan hệ:
Là **ràng buộc xảy ra giữa các thuộc tính trên nhiều quan hệ khác nhau**.

![image](https://hackmd.io/_uploads/rkU5dycIZe.png)
> ![image](https://hackmd.io/_uploads/B1UjdyqL-l.png)

#### d) Thuộc tính tổng hợp:
- Là **thuộc tính có giá trị được tính toán từ các thuộc tính khác**.
- Khi database có thuộc tính tổng hợp, ràng buộc toàn vẹn bảo đảm quan hệ giữa thuộc tính tổng hợp và các thuộc tính nguồn.
> ![image](https://hackmd.io/_uploads/H1jkty9L-g.png)

#### e) Chu trình:
- **Ràng buộc do sự có mặt của chu trình**.
- Lược đồ database có thể được biểu diễn bằng đồ thị:
    - Đỉnh:
    ![image](https://hackmd.io/_uploads/BJymYk58Zg.png)
        - Quan hệ
        - Thuộc tính
    - Cạnh: Đường nối một đỉnh quan hệ với một đỉnh thuộc tính trong lược đồ database.
    ![image](https://hackmd.io/_uploads/SyELKJqIWl.png)
- Chu trình: Đồ thị xuất hiện đường đi khép kín ~ Lược đồ database có chu trình.
> - Ví dụ 1:
> ![image](https://hackmd.io/_uploads/rJcuF19Lbe.png)
> ![image](https://hackmd.io/_uploads/r1OtYkq8-e.png)
> - Ví dụ 2:
> ![image](https://hackmd.io/_uploads/S1Epxl9IZg.png)
> ![image](https://hackmd.io/_uploads/r1-Reg9Ube.png)
> ![image](https://hackmd.io/_uploads/SyFyZl9L-g.png)
> ![image](https://hackmd.io/_uploads/S1SeWeqIbl.png)

## IV. Cài đặt:
Các ràng buộc toàn vẹn được cài đặt bởi:
- Primary key
- Foreign key
- Check contraint
- Assertion
- Trigger
- Transaction

### 1. Assertion:
- Là một biểu thức SQL luôn mang giá trị `TRUE` tại mọi thời điểm, user cần cho biết cái gì phải đúng.
- Cú pháp:
``` sql
CREATE ASSERTION <Tên_assertion> CHECK (<Điều_kiện>)
```
``` sql
DROP ASSERTION <Tên_assertion>
```
> - Ví dụ 1:
> ![image](https://hackmd.io/_uploads/rkZI9kqUZg.png)
> - Ví dụ 2:
> ![image](https://hackmd.io/_uploads/SyCU9y5IWg.png)
> ![image](https://hackmd.io/_uploads/HyFPcJcUWe.png)
> - Ví dụ 3:
> ![image](https://hackmd.io/_uploads/r1K_5J9Ubl.png)
> ![image](https://hackmd.io/_uploads/HyBFq15Lbl.png)

### 2. Trigger:
- Là tập hợp các lệnh được thực hiện **tự động** khi xuất hiện một biến cố nào đó.
![image](https://hackmd.io/_uploads/Skfnq1qI-l.png)
- Cú pháp:
``` sql
CREATE TRIGGER <Tên_trigger>
AFTER|BEFORE INSERT|UPDATE|DELETE ON <Tên_bảng> REFERENCING
    NEW ROW|TABLE AS <Tên_1>
    OLD ROW|TABLE AS <Tên_2>
FOR EACH ROW | FOR EACH STATEMENT
WHEN (<Điều_kiện>)
    <Tập_lệnh_SQL>
```
``` sql
DROP TRIGGER <Tên_Trigger>
```
> ![image](https://hackmd.io/_uploads/BJ4vjJqUbx.png)
> ![image](https://hackmd.io/_uploads/HJCwjJ5Lbx.png)
> ![image](https://hackmd.io/_uploads/ryddjk5I-g.png)

### 3. Transaction (Giao tác):
- Là tập lệnh thực hiện một xử lý nào đó trong một ứng dụng database sao cho:
    - Hoặc là tất cả các lệnh đều được thực hiện thành công.
    - Hoặc là không có lệnh nào được thực hiện.
> Ví dụ: Xử lý chuyển tiền trong ngân hàng:
> ![image](https://hackmd.io/_uploads/HJBps15IZx.png)
- Giao tác phải đảm bảo:
    - Tính nguyên tố (atomicity).
    - Tính nhất quán của database (consistency): Các ràng buộc toàn vẹn không bị vi phạm:
        - Trong khi thực hiện giao tác.
        - Trước và sau khi thực hiện giao tác.
> - Ví dụ 1:
> ![image](https://hackmd.io/_uploads/BJ9fh1cIWx.png)
> ![image](https://hackmd.io/_uploads/ryiX319I-g.png)
> - Ví dụ 2:
> ![image](https://hackmd.io/_uploads/S1ErnJ9IZl.png)
> ![image](https://hackmd.io/_uploads/SJWU2y5UZl.png)

### 4. Stored Procedure (Thủ tục lưu trữ nội bộ):
- Các DBMS thương mại cung cấp **cách thức lưu trữ các hàm hay thủ tục**:
    - Được lưu trữ trong lược đồ database.
    - Được dùng trong các câu lệnh SQL.
- Cú pháp:
``` sql
CREATE PROCEDURE <Tên_thủ_tục> <Danh_sách_tham_số>
AS
    Khai_báo_biến_cục_bộ
    Thân_chương_trình
GO
EXEC <Tên_thủ_tục> <Danh_sách_tham_số>
```
> ![image](https://hackmd.io/_uploads/rkByp1c8Wl.png)

### 5. Nhận xét:
- DBMS sẽ kiểm tra ràng buộc toàn vẹn:
    - Sau khi một thao tác cập nhật diễn ra trên database.
    - Cuối mỗi giao tác.
- Nên cài đặt ràng buộc toàn vẹn ở đâu:
    - DBMS
    - Application
    - Trigger quá nhiều $\rightarrow$ Hệ thống chậm.
    - Stored Procedure $\rightarrow$ Hiệu quả cao.
