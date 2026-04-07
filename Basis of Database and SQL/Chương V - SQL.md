## I. Giới thiệu:
### 1. Ngôn ngữ đại số quan hệ:
- Cách thức truy vấn dữ liệu.
- Khó khăn cho người dùng (vì là ngôn ngữ đại số) trong việc hiểu và truy xuất.

### 2. SQL (Structured Query Language):
- Ngôn ngữ cấp cao.
- Người dùng chỉ cần đưa ra nội dung cần truy vấn.
- Được phát triển bởi IBM (1970s).
- Được gọi là SEQUEL.
- Được ANSI công nhận và phát triển thành chuẩn.
    - SQL86 (SQL87)
    - SQL89
    - SQL92 (SQL2)
    - SQL99 (SQL3)
    - SQL2003
- SQL gồm:
  
    ![image](https://hackmd.io/_uploads/B1NbR_w8Wl.png)
    - Định nghĩa dữ liệu (Data Definition Language - DDL): Khai báo **cấu trúc bảng**, các **mối quan hệ** và các **ràng buộc**.
    - Thao tác dữ liệu (Data Manipulation Language -DML): **Thêm**, **xoá**, **sửa** dữ liệu.
    - Ngôn ngữ truy vấn dữ liệu (Structered Query Language - SQL): Ngôn ngữ **truy vấn** dữ liệu.
    - Ngôn ngữ điều khiển dữ liệu (Data Control Language - DCL): Khai báo **bảo mật** thông tin, cấp và thu hồi **quyền khai thác** database.
    - Định nghĩa khung nhìn.
    - Ràng buộc toàn vẹn.
    - Phân quyền và bảo mật.
    - Điều khiển giao tác.
- SQL sử dụng thuật ngữ:
  
    ![image](https://hackmd.io/_uploads/S1d1U5_Lbx.png)
    - Bảng (Table) ~ Quan hệ
    - Cột (Column) ~ Thuộc tính
    - Dòng (Row) ~ Bộ

## II. Định nghĩa dữ liệu:
- Là ngôn ngữ mô tả:
    - Lược đồ cho mỗi quan hệ.
    - Miền giá trị tương ứng của từng thuộc tính.
    - Ràng buộc toàn vẹn.
    - Chỉ mục trên mỗi quan hệ.
- Gồm:
    - `CREATE TABLE` (Tạo bảng)
    - `DROP TABLE` (Xoá bảng)
    - `ALTER TABLE` (Sửa bảng)
    - `CREATE DOMAIN` (Tạo miền giá trị)
    - `CREATE DATABASE`
    - ...

### 1. Kiểu dữ liệu:
![image](https://hackmd.io/_uploads/SyWXP9OU-e.png)

#### a) Số (numeric):
- INTEGER
- SMALLINT
- NUMERIC, NUMERIC$(p)$, NUMERIC$(p,s)$
- DECIMAL, DECIMAL$(p)$, DECIMAL$(p,s)$
- REAL
- DOUBLE PRECISION
- FLOAT, FLOAT$(p)$

#### b) Chuỗi ký tự (character string):
- CHARACTER, CHARACTER$(n)$
- CHARACTER VARYING$(x)$

#### c) Chuỗi bit (bit string):
- BIT, BIT$(x)$
- BIT VARYING$(x)$

#### d) Ngày giờ (datetime):
- DATE gồm ngày, tháng, năm.
- TIME gồm giờ, phút, giây.
- TIMESTAMP gồm ngày, giờ.

### 2. Các lệnh định nghĩa dữ liệu:
#### a) Lệnh tạo bảng:
- Để định nghĩa một bảng:
    - Tên bảng
    - Các thuộc tính:
        - Tên thuộc tính.
        - Kiểu dữ liệu.
        - Các ràng buộc toàn vẹn (RBTV) trên thuộc tính.
- Từ khoá: `CREATE`
- Cú pháp:
``` sql
CREATE TABLE <Tên_bảng> (
    <Tên_cột> <Kiểu_dữ_liệu> [<RBTV>],
    <Tên_cột> <Kiểu_dữ_liệu> [<RBTV>],
    ...
    [<RBTV>]
)
```
![image](https://hackmd.io/_uploads/rkBOv9OIbe.png)
> ![image](https://hackmd.io/_uploads/ByZvWKDUWl.png)
- Lệnh tạo bảng:
    - `<RBTV>`:
        - `<NOT NULL>`
        - `<NULL>`
        - `UNIQUE`
        - `DEFAULT`
        - `PRIMARY KEY`
        - `FOREIGN KEY`/`REFERENCES`
        - `CHECK`
    - Khai báo ràng buộc toàn vẹn: `CONSTRAINT <Tên_RBTV><RBTV>`
> ![image](https://hackmd.io/_uploads/BkqlGtwLbe.png)
> ![image](https://hackmd.io/_uploads/SyrEMKwI-x.png)
> ![image](https://hackmd.io/_uploads/BJJBfKvL-g.png)
> ![image](https://hackmd.io/_uploads/r1HUzFw8-l.png)

#### b) Lệnh sửa bảng:
- Dùng để:
    - Thay đổi cấu trúc bảng.
    - Thay đổi ràng buộc toàn vẹn.
- Phân loại:
    - Thêm thuộc tính vào bảng.
    - Sửa kiểu dữ liệu của thuộc tính.
    - Xoá thuộc tính.
    - Thêm ràng buộc toàn vẹn.
    - Xoá ràng buộc toàn vẹn.
- Từ khoá: `ALTER`
- Thêm cột (thuộc tính):
``` sql
ALTER TABLE <Tên_bảng> ADD COLUMN <Tên_cột> <Kiểu_dữ_liệu> [<RBTV>]
```
- Sửa kiểu dữ liệu cột (thuộc tính) hay mở rộng cột:
``` sql
ALTER TABLE <Tên_bảng> ALTER COLUMN <Tên_cột> <Kiểu_dữ_liệu_mới>
```
> Không phải sửa thành kiểu dữ liệu nào cũng được.
- Xoá cột (thuộc tính):
``` sql
ALTER TABLE <Tên_bảng> DROP COLUMN <Tên_cột>
```
- Thêm ràng buộc toàn vẹn:
``` sql
ALTER TABLE <Tên_bảng> ADD
    CONSTRAINT <Tên_RBTV> <RBTV>,
    CONSTRAINT <Tên_RBTV> <RBTV>,
    ...
```
![image](https://hackmd.io/_uploads/H1pZYquLbx.png)
- Xoá ràng buộc toàn vẹn: 
``` sql
ALTER TABLE <Tên_bảng> DROP <Tên_RBTV>
```
Khi xoá ràng buộc khoá chính phải xoá hết các ràng buộc khoá ngoại tham chiếu tới nó.
> ![image](https://hackmd.io/_uploads/BJ997twUbx.png)
> ![image](https://hackmd.io/_uploads/B1wjQtwIbe.png)

#### c) Lệnh xoá bảng:
- Dùng để xoá cấu trúc bảng, tất cả dữ liệu của bảng cũng bị xoá.
- Từ khoá: `DROP`
- Cú pháp:
``` sql 
DROP TABLE <Tên_bảng>
```
- Lưu ý: Khi xoá một bảng phải xoá hết các ràng buộc khoá ngoại tham chiếu tới bảng đó.
> ![image](https://hackmd.io/_uploads/HyhkEtPIbe.png)
> ![image](https://hackmd.io/_uploads/HkbyNtDUZl.png)

#### d) Lệnh tạo miền giá trị:
- Tạo ra một kiểu dữ liệu mới kế thừa những kiểu dữ liệu có sẵn.
- Cú pháp:
``` sql
CREATE DOMAIN <Tên_kiểu_dữ_liệu_mới> AS <Kiểu_dữ_liệu>
```
> ![image](https://hackmd.io/_uploads/rJeHVFDL-g.png)

## III. Ngôn ngữ truy vấn dữ liệu:
- Là ngôn ngữ chuẩn, có cấu trúc dùng để truy vấn và thao tác trên database quan hệ, nghĩa là rút trích dữ liệu thoả một số điều kiện nào đó.
- Dựa trên: **Phép toán ĐSQH $+$ Một số bổ sung**
    - Cho phép một bảng có **nhiều dòng trùng nhau**.
- Cú pháp tổng quát:
  
![image](https://hackmd.io/_uploads/SyK5R5O8-l.png)
    - `<Danh_sách_các_thuộc_tính/Hàm>`:
        - Tên các thuộc tính/hàm cần được hiển thị ở kết quả.
        - Các thuộc tính/hàm cách nhau bởi dấu `,`.
    - `<Danh_sách_các_bảng>`:
        - Tên các bảng.
        - Các bảng cách nhau bởi dấu `,`.
    - `<Điều_kiện>`:
        - Sử dụng toán tử so sánh.
        - Là biểu thức Boolean để xác định dòng nào sẽ được chọn.
        - Sử dụng toán tử logic để nối các điều kiện.
- Các toán tử:
    - Các phép toán cơ bản: $+$, $-$, $*$, $\div$
    - Các toán tử so sánh:
        - $=$, $>$, $<$, $\leq$, $\geq$
        - `BETWEEN`
        - `IS NULL`, `IS NOT NULL`
        - `LIKE %` hoặc `_`: `%` đại diện nhiều ký tự, `_` đại diện một ký tự.
        - `IN`, `NOT IN`
        - `EXISTS`, `NOT EXISTS`
        - `SOME`, `ALL`, `ANY`
    - Các toán tử logic: `AND`, `OR`
- Các biểu thức, hàm:
    ![image](https://hackmd.io/_uploads/Hksf-juUbg.png)
    - Các hàm xử lý chuỗi.
    - Các hàm xử lý số.
    - Các hàm xử lý ngày.
    - Các hàm tính toán trên nhóm.
- Các dạng truy vấn:
    - Truy vấn cơ bản, đơn giản.
    - Truy vấn dùng phép toán tập hợp.
    - Truy vấn lồng.
    - Truy vấn dùng các hàm tính toán trên nhóm.
    - Truy vấn dùng các hàm tính toán trên nhóm và có điều kiện.

### 1. Truy vấn cơ bản:
- Gồm ba mệnh đề:
![image](https://hackmd.io/_uploads/H1evWiuUWx.png)
    - `SELECT [DISTINCT] <danh_sách_các_cột>`: Tên các cột cần được hiển thị
    - `FROM <Danh_sách_các_bảng>` được hiển thị trong kết quả truy vấn.
    - `WHERE <Điều_kiện>`:
        - Biểu thức Boolean xác định dòng đươc rút trích.
        - Nối các biểu thức: `AND`, `OR`, `NOT`
        - Phép toán: $<$, $>$, $\leq$, $\geq$,. $=$, $\neq$ `LIKE`, `BETWEEN`.
- Sử dụng `*`: Lấy tất cả các thuộc tính.
> ![image](https://hackmd.io/_uploads/HJUkzo_8Wl.png)
- Sử dụng `AS`: Đặt bí danh.
> ![image](https://hackmd.io/_uploads/ByUeMsuI-e.png)
- Sử dụng hàm, biểu thức tính toán.
> ![image](https://hackmd.io/_uploads/S1mMzjOLbg.png)
> ![image](https://hackmd.io/_uploads/BkdQGjd8Wx.png)
- Sử dụng `DISTINCT`: Loại bỏ các dòng trùng nhau trong kết quả.
> ![image](https://hackmd.io/_uploads/SJrBfs_Ibx.png)
- Sử dụng toán tử so sánh và toán tử logic.
> ![image](https://hackmd.io/_uploads/HJ5qGiOLZl.png)
> ![image](https://hackmd.io/_uploads/S1hiGj_LZg.png)
> ![image](https://hackmd.io/_uploads/rJI2Gs_8Wx.png)
- Sử dụng phép kết bằng để kết hai hai nhiều bảng:
    - Cách 1: Dùng `inner join on <Điều_kiện_kết` ở `FROM`.
    - Cách 2: Đưa `<Điều_kiện_kết>` xuống `WHERE`.
> ![image](https://hackmd.io/_uploads/BJ7f7sdUZg.png)
> ![image](https://hackmd.io/_uploads/rk_7Xod8bx.png)

#### a) Mệnh đề SELECT:
![image](https://hackmd.io/_uploads/rJ0y6KPIWg.png)
![image](https://hackmd.io/_uploads/rydx6YwI-l.png)
![image](https://hackmd.io/_uploads/BymWpKwIbe.png)
![image](https://hackmd.io/_uploads/rkZfaFPUZe.png)
![image](https://hackmd.io/_uploads/rJE7aKDUZl.png)
![image](https://hackmd.io/_uploads/HyaXTYPUWe.png)
> ![image](https://hackmd.io/_uploads/HJ94pFw8-e.png)

#### b) Mệnh đề WHERE:
![image](https://hackmd.io/_uploads/B1wBTtDU-l.png)
![image](https://hackmd.io/_uploads/ryRBpFPUWe.png)
![image](https://hackmd.io/_uploads/rJPITKvIWg.png)
![image](https://hackmd.io/_uploads/rklDptD8-g.png)
![image](https://hackmd.io/_uploads/r1YDpYwIZg.png)
![image](https://hackmd.io/_uploads/ryVO6KDUbl.png)
![image](https://hackmd.io/_uploads/rkp_TFD8bg.png)
![image](https://hackmd.io/_uploads/B19YTtDU-e.png)
![image](https://hackmd.io/_uploads/SJq9aYD8Zg.png)
![image](https://hackmd.io/_uploads/By-sTYw8-g.png)

#### c) Mệnh đề FROM:
![image](https://hackmd.io/_uploads/rk13atDUWg.png)
![image](https://hackmd.io/_uploads/H1cn6YP8Ze.png)
> Tìm họ tên của từng nhân viên và người phụ trách trực tiếp nhân viên đó:
> ``` sql
> SELECT HoNV + ' ' + TENLOT + ' ' + TenNV N1, HoNV + ' ' + TENLOT + ' ' + TenNV N2
> FROM NHANVIEN NV1, NHANVIEN NV2
> WHERE NV1.MaNV = NV2.MA_NQL
> ```

#### d) Mệnh đề ORDER BY:
- Dùng để hiển thị kết quả câu truy vấn theo thứ tụ nào đó.
- Cú pháp:
    - `SELECT <Danh_sách_các_cột>`
    - `FROM <Danh_sách_các_bảng>`
    - `WHERE <Điều_kiện>`
    - `ORDER BY <Danh_sách_các_cột>`
    - `ASC`: Tăng (mặc định)
    - `DESC`: Giảm
> ![image](https://hackmd.io/_uploads/rkFS0Kv8We.png)

### 2. Tập hợp, so sánh tập hợp và truy vấn lồng:
#### a) Phép toán tập hợp trong SQL:
- Sử dụng phép toán tập hợp để kết hợp kết quả của hai câu truy vấn:
``` sql
(Câu truy vấn 1)
<Phép_toán_tập_hợp>
(Câu truy vấn 2)
```
- SQL có cài đặt các phép toán:
    - Hội (`UNION`)
    - Giao (`INTERSECT`)
    - Trừ (`EXCEPT`)
- Kết quả trả về là tập hợp:
    - Loại bỏ các bộ trùng nhau.
    - Để giữ lại các bộ trùng nhau:
        - `UNION ALL`
        - `INTERSECT ALL`
        - `EXCEPT ALL`
- Cú pháp:
``` sql
SELECT <Danh_sách_cột> FROM <Danh_sách_bảng> WHERE <Điều kiện>
UNION [ALL]
SELECT <Danh_sách_cột> FROM <Danh_sách_bảng> WHERE <Điều kiện>
```
``` sql
SELECT <Danh_sách_cột> FROM <Danh_sách_bảng> WHERE <Điều kiện>
INTERSECT [ALL]
SELECT <Danh_sách_cột> FROM <Danh_sách_bảng> WHERE <Điều kiện>
```
``` sql
SELECT <Danh_sách_cột> FROM <Danh_sách_bảng> WHERE <Điều kiện>
EXCEPT [ALL]
SELECT <Danh_sách_cột> FROM <Danh_sách_bảng> WHERE <Điều kiện>
```
> ![image](https://hackmd.io/_uploads/rkYdrUdUbg.png)
> ![image](https://hackmd.io/_uploads/Sy8KrU_8bl.png)
> ![image](https://hackmd.io/_uploads/H1M9rIdI-l.png)

#### b) Truy vấn lồng:
![image](https://hackmd.io/_uploads/ry-6BU_Lbx.png)
![image](https://hackmd.io/_uploads/Hk12QiOLZx.png)
- Gồm hai hay nhiều câu truy vấn lồng vào nhau.
- Các câu lệnh `SELECT` có thể lồng nhau ở nhiều mức.
- Các cây truy vấn con trong cùng một mệnh đề `WHERE` được kết hợp bằng phép nối logic.
- Câu truy vấn con thường trả về một tập các giá trị.
- Mệnh đề `WHERE` của câu truy vấn cha:
    - `<Điều_kiện>`: Truy vấn con trả về hai giá trị tập hợp, so sánh tập hợp thường đi cùng một số toán tử:
        - `<Biểu_thức> [NOT] IN (<Truy_vấn_con>)`
        - `<Biểu_thức> <Phép_toán_so_sánh> ALL (<Truy_vấn_con>)`
        - `ANY` hoặc `SOME`: `<Biểu_thức> <Phép_toán_so_sánh> ANY (<Truy_vấn_con>)`
    - `<Điều_kiện>`: Kiểm tra sự tồn tại trong kết quả của truy vấn con: `[NOT] EXISTS (<Truy_vấn_con>)`
        - Trả về True nếu có ít nhất một bộ trong truy vấn con.
        - Trả về False nếu ngược lại.
- Có hai loại truy vấn lồng:

##### Lồng phân cấp:
- Mệnh đề `WHERE` của truy vấn con không tham chiếu đến thuộc tính của các quan hệ trong mệnh đề `FROM` ở truy vấn cha.
- Khi thực hiện, câu truy vấn con sẽ được thực hiện trước.
> ![image](https://hackmd.io/_uploads/ryQOdLd8-e.png)
> ![image](https://hackmd.io/_uploads/HyTYdU_UWl.png)
> ![image](https://hackmd.io/_uploads/HJccuI_IWe.png)
> ![image](https://hackmd.io/_uploads/HyPjOLOIWx.png)
> ![image](https://hackmd.io/_uploads/BJQhdLOIZx.png)

##### Lồng tương quan:
- Mệnh đề `WHERE` của truy vấn con tham chiếu ít nhất một thuộc tính của các quan hệ trong mệnh đề `FROM` ở truy vấn cha.
- Khi thực hiện, câu truy vấn con sẽ được thực hiện nhiều lần, mỗi lần tương ứng với một bộ của truy vấn cha.
> ![image](https://hackmd.io/_uploads/S1MGYIdIWe.png)
> ![image](https://hackmd.io/_uploads/Sypzt8OI-e.png)
> ![image](https://hackmd.io/_uploads/BkDQYIu8-g.png)
> ![image](https://hackmd.io/_uploads/rJG4YLdIWl.png)
> ![image](https://hackmd.io/_uploads/SyRVY8OLbl.png)

#### c) Nhận xét `IN` và `EXISTS`:
- `IN`:
    - `<Tên_cột> IN <Câu_truy_vấn_con>`
    - Thuộc tính ở mệnh đề `SELECT` của truy vấn con phải có cùng kiểu dữ liệu với thuộc tính ở mệnh đề `WHERE` của truy vấn cha.
- `EXISTS`:
    - Không cần có thuộc tính, hằng số hay biểu thức nào khác đứng trước.
    - Không nhất thiết liệt kê tên thuộc tính ở mệnh đề `SELECT` của truy vấn con.
    - Những câu truy vấn có `= ANY` hay `IN` đều có thể chuyển thành câu truy vấn có `EXISTS`.

#### d) Phép chia trong SQL:
![image](https://hackmd.io/_uploads/H1YcTI_LWe.png)
- $R \div S$ là tập các giá trị $a_i$ trong $R$ sao cho **không có** giá trị $b_i$ nào trong $S$ làm cho bộ $(a_i, b_i)$ **không tồn tại** trong $R$.
- Sử dụng `NOT EXISTS` để biểu diễn:
![image](https://hackmd.io/_uploads/H1CLA8dLWg.png)
> ![image](https://hackmd.io/_uploads/SkyO0I_Ibg.png)
> ![image](https://hackmd.io/_uploads/SyhOCU_Ubl.png)

### 3. Hàm kết hợp và gom nhóm:
Truy vấn sử dụng hàm tính toán trên nhóm:
![image](https://hackmd.io/_uploads/SkKprjuI-l.png)
- Dùng các hàm tính toán, có thể gom nhóm dữ liệu và tính toán trên nhóm.
- Các hàm có đầu vào là một tập giá trị và trả về một giá trị đơn: `Min()`, `Max()`, `Avg()`, `Sum()`, `Count()`

#### a) Hàm kết hợp:
- `COUNT`:
    - `COUNT(*)`: Đếm số dòng
    - `COUNT(<Tên_thuộc_tính>)`: Đếm số giá trị khác `NULL` của thuộc tính.
    - `COUNT(DISTINCT <Tên_thuộc_tính>`: Đếm số giá trị khác nhau và khác `NULL` của thuộc tính.
- `MIN`
- `MAX`
- `SUM`
- `AVG`
- Các hàm kết hợp được đặt ở mệnh đề `SELECT`.
> ![image](https://hackmd.io/_uploads/ByBXJPdUbg.png)
> ![image](https://hackmd.io/_uploads/HyCXyv_8-x.png)
> ![image](https://hackmd.io/_uploads/Sy34JP_L-e.png)

#### b) Gom nhóm:
- Cú pháp:
``` sql
SELECT <Danh_sách_các_cột>
FROM <Danh_sách_các_bảng>
WHERE <Điều_kiện>
GROUP BY <Danh_sách_các_cột_gom_nhóm>
```
- Sau khi gom nhóm, mỗi nhóm các bộ sẽ có cùng giá trị tại các thuộc tính gom nhóm.
> ![image](https://hackmd.io/_uploads/HyaRkw_Lbx.png)
> ![image](https://hackmd.io/_uploads/By5JlwOIZe.png)

##### Điều kiện trên nhóm:
Cú pháp:
``` sql
SELECT <Danh_sách_các_cột>
FROM <Danh_sách_các_bảng>
WHERE <Điều_kiện>
GROUP BY <Danh_sách_các_cột_gom_nhóm>
HAVING <Điều_kiện_trên_nhóm>
```
> ![image](https://hackmd.io/_uploads/SJ9zlvuIZg.png)
> ![image](https://hackmd.io/_uploads/Hk1ExPOUbg.png)

##### Nhận xét:
- Mệnh đề `GROUP BY`: Các thuộc tính trong mệnh đề `SELECT` (trừ những thuộc tính trong các hàm kết hợp) phải xuất hiện trong mệnh đề `GROUP BY`
- Mệnh đề `HAVING`:
    - Sử dụng các hàm kết hợp trong mệnh đề `SELECT` để kiểm tra một số điều kiện nào đó.
    - Chỉ kiểm tra điều kiện trên nhóm, không là điều kiện lọc trên từng bộ.
    - Sau khi gom nhóm, điều kiền trên nhóm mới được thực hiện.
- Thứ tự thực hiện câu truy vấn có mệnh đề `GROUP BY` và `HAVING`:
    - Chọn ra những dòng thoả điều kiện trong mệnh đề `WHERE`.
    - Những dòng này được gom thành nhiều nhóm tương ứng với mệnh đề `GROUP BY`.
    - Áp dụng các hàm kết hợp cho mỗi nhóm.
    - Bỏ qua những nhóm không thoả điều kiện trong mệnh đề `HAVING`.
    - Rút trích các giá trị của các cột và hàm kết hợp trong mệnh đề `SELECT`.
> ![image](https://hackmd.io/_uploads/rkeVZDO8bg.png)
> ![image](https://hackmd.io/_uploads/B134ZDuIWg.png)
> ![image](https://hackmd.io/_uploads/rkUBWDd8bx.png)

### 4. Một số kiểu truy vấn khác:
#### a) Truy vấn con ở mệnh đề `FROM`:
- Kết quả trả về của một câu truy vấn phụ là một **bảng**:
    - Bảng trung gian trong quá trình truy vấn.
    - Không có lưu trữ thật sự.
- Cú pháp:
``` sql
SELECT <Danh_sách_các_cột>
FROM R1, R2 (<Truy_vấn_con>) AS Tên_bảng
WHERE <Điều_kiện>
```

#### b) Điều kiện kết ở mệnh đề `FROM`:
- Kết bằng:
``` sql
SELECT <Danh_sách_các_cột>
FROM R1 [INNER] JOIN R2 ON <Biểu_thức>
WHERE <Điều_kiện>
```
- Kết ngoài:
``` sql
SELECT <Danh_sách_các_cột>
FROM R1 LEFT|RIGHT[OUTER] JOIN R2 ON <Biểu_thức>
WHERE <Điều_kiện>
```
> ![image](https://hackmd.io/_uploads/H1bYzwOU-e.png)
> - Ví dụ 2:
> ![image](https://hackmd.io/_uploads/BJ7hMD_8Wg.png)

#### c) Cấu trúc `CASE`:
- Cho phép kiểm tra điều kiện và xuất thông tin theo từng trường hợp:
- Cú pháp:
``` sql
CASE <Tên_cột>
    WHEN <Giá_trị> THEN <Biểu_thức>
    WHEN <Giá_trị> THEN <Biểu_thức>
    ...
END
```
> ![image](https://hackmd.io/_uploads/S12fXD_IZl.png)
> ![image](https://hackmd.io/_uploads/r1PQmwu8Ze.png)

#### d) Kết luận:
``` sql
SELECT <Danh_sách_các_cột>
FROM <Danh_sách_các_bảng>
[WHERE <Điều_kiện>]
[GROUP BY <Danh_sách_các_cột_gom_nhóm>]
[HAVING <Điều_kiện_trên_nhóm>]
[ORDER BY <Các_thuộc_tính_sắp_thứ_tự>]
```

## IV. Cập nhật dữ liệu:
### 1. Thêm (Insert):
- Dùng để thêm một hay nhiều dòng vào bảng.
- Để thêm dữ liệu cần xác định:
    - Tên quan hệ hay tên bảng cần chèn dữ liệu.
    - Danh sách các thuộc tính cần thêm dữ liệu.
    - Danh sách các giá trị tương ứng.
- Từ khoá: `INSERT`
- Cú pháp thêm một dòng:
``` sql
INSERT INTO <Tên bảng>[(<Danh_sách_các_thuộc_tính>)]
VALUES (<Danh_sách_các_giá_trị>)
```
> ![image](https://hackmd.io/_uploads/BkxQfED_IWe.png)
- Cú pháp thêm nhiều dòng:
``` sql
INSERT INTO <Tên_bảng>[(<Danh_sách_các_thuộc_tính>)]
    <Câu_truy_vấn_con>
```
> ![image](https://hackmd.io/_uploads/ryhjVDuU-e.png)

Cú pháp (SQL Server 2008+):
``` sql
INSERT INTO <Tên_bảng>[(<Danh_sách_các_thuộc_tính>)]
VALUES {(<Danh_sách_các_giá_trị>)}
```
> ![image](https://hackmd.io/_uploads/B1d63c_U-e.png)

Cú pháp:
``` sql
INSERT INTO <Tên_bảng_mới> FROM <Tên_bảng_có_sẵn>
```
> ![image](https://hackmd.io/_uploads/r1ZVT5uI-x.png)

- Nhận xét:
    - Thứ tự các giá trị phải tương ứng với thứ tự các cột.
    - Có thể thêm giá trị `NULL` ở những thuộc tính không là khoá chính và `NOT NULL`.
    - Câu lệnh `INSERT` sẽ gặp lỗi nếu vi phạm ràng buộc toàn vẹn:
        - Khoá chính
        - Tham chiếu/Khoá ngoại.
        - Các thuộc tính có ràng buộc `NOT NULL` bắt buộc phải có giá trị.

### 2. Xoá (Delete):
- Dùng để xoá một hay nhiều dòng của bảng.
- Từ khoá: `DELETE`
- Cú pháp:
``` sql
DELETE FROM <Tên_bảng>
[WHERE <Điều_kiện>]
```
> ![image](https://hackmd.io/_uploads/S1MZBDuUZg.png)
> ![image](https://hackmd.io/_uploads/B1j-rP_I-l.png)
- Nhận xét:
    - Nếu có `WHERE`, số lượng số dòng bị xoá phụ thuộc vào điều kiện ở mệnh đề `WHERE`.
    - Nếu không chỉ định điều kiện ở mệnh đề `WHERE`, tất các các dòng trong bảng sẽ bị xoá.
    - Lệnh `DELETE` có thể gây ra vi phạm ràng buộc tham chiếu:
        - Không cho xoá.
        - Xoá luôn cả những dòng có giá trị đang tham chiếu đến `CASCADE`.
        - Đặt `NULL` cho những giá trị tham chiếu.
> ![image](https://hackmd.io/_uploads/r1XirDuIWe.png)
> ![image](https://hackmd.io/_uploads/r143HPOIbe.png)

### 3. Sửa (Update):
- Dùng để thay đổi giá trị của thuộc tính cho một hay nhiều dòng của bảng.
- Từ khoá: `UPDATE`
- Cú pháp:
``` sql
UPDATE <Tên_bảng>
SET <Tên thuộc tính> = <Giá_trị_mới>,
    <Tên thuộc tính> = <Giá_trị_mới>,
    ...
[WHERE <Điều_kiện>]
```
> ![image](https://hackmd.io/_uploads/HJvzUDu8Wx.png)
> ![image](https://hackmd.io/_uploads/HkZmIw_LZe.png)
- Nhận xét:
    - Nếu có `WHERE`, những dòng thoả điều kiện tại mệnh đề `WHERE` sẽ được cập nhật giá trị mới.
    - Nếu không chỉ định điều kiện ở mệnh đề `WHERE`, tất cả các dòng trong bảng sẽ bị cập nhật.
    - Lệnh `Update` có thể gây ra vi phạm ràng buộc tham chiếu:
        - Không cho sửa dữ liệu.
        - Xoá luôn cả những dòng có giá trị đang tham chiếu đến `CASCADE`.

## V. Khung nhìn (view):
### 1. Định nghĩa:
- Bảng là một quan hệ được **tổ chức lưu trữ** vật lý trong database.
- Khung nhìn cũng là một quan hệL
    - Không được lưu trữ vật lý (bảng ảo).
    - Không chứa dữ liệu.
    - Được định nghĩa từ những bảng khác.
    - Có thể truy vấn hay cập nhật thông qua khung nhìn.
- Tại sao phải sử dụng khung nhìn?
    - Che giấu tính phức tạp của dữ liệu.
    - Đơn giản hoá các câu truy vấn.
    - Hiển thị dữ liệu dưới dạng tiện dụng nhất.
    - An toàn dữ liệu.
- Cú pháp:
``` sql
CREATE VIEW <Tên_khung_nhìn> AS
    <Câu_truy_vấn>
```
``` sql
DROP VIEW <Tên_khung_nhìn>
```
- Bảng ảo này có:
    - Danh sách thuộc tính trùng với các thuộc tính trong mệnh đề `SELECT`.
    - Số dòng phụ thuộc vào điều kiện ở mệnh đề `WHERE`.
    - Dữ liệu được lấy từ các bảng ở mệnh đề `FROM`.
> ![image](https://hackmd.io/_uploads/S1bSGcuIZe.png)

### 2. Truy vấn:
- Tuy không chứa dữ liệu nhưng có thể thực hiện các câu truy vấn trên khung nhìn.
> ![image](https://hackmd.io/_uploads/BkjLXcd8-g.png)
- Có thể viết câu truy vấn dữ liệu từ khung nhìn và bảng.
> ![image](https://hackmd.io/_uploads/H1F_XqOIbg.png)

### 3. Cập nhật:
- Có thể dùng các lệnh `INSERT`, `DELETE` và `UPDATE` cho các **khung nhìn đơn giản** (khung nhìn được xây dựng trên một bảng và có khoá chính của bảng).
- Không thể cập nhật dữ liệu nếu:
    - Khung nhìn có dùng từ khoá `DISTINCT`.
    - Khung nhìn có dùng các hàm kết hợp.
    - Khung nhìn có mệnh đề `SELECT` mở rộng.
    - Khung nhìn được xây dừng từ bảng có ràng buộc trên cột.
    - Khung nhìn được xây dựng từ nhiều bảng.
> ![image](https://hackmd.io/_uploads/B19WVquU-e.png)

## VI. Chỉ mục (index):
- Chỉ mục trên thuộc tính $A$ là một cấu truc dữ liệu làm cho việc tìm kiếm mẫu tin có chứa $A$ hiệu quả hơn.
> ![image](https://hackmd.io/_uploads/Skp44cuUWg.png)
- Cú pháp:
``` sql
CREATE INDEX <Tên_chỉ_mục> ON <Tên_bảng> (<Tên_cột>)
```
``` sql
DROP INDEX <Tên_chỉ_mục>
```
> ![image](https://hackmd.io/_uploads/rkJqN9u8Ze.png)
- Nhận xét:
    - Tìm kiếm nhanh chóng trong trường hợp so sánh với hằng số và phép kết.
    - Làm chậm đi các thao tác thêm, xoá, sửa.
    - Tốn chi phí:
        - Lưu trữ chỉ mục.
        - Truy xuất đĩa nhiều.
- Chọn lựa cài đặt chỉ mục hợp lý.
> ![image](https://hackmd.io/_uploads/Hy-1r9O8-l.png)
> ![image](https://hackmd.io/_uploads/SJ3JS9_UZe.png)
> ![image](https://hackmd.io/_uploads/rJ2lrq_8Wx.png)
