## I. Giới thiệu:
- Do tiến sĩ E. F. Codd đưa ra: *" A Relation Model for Large Shared Data Banks"* (Communications of ACM, 06/1970), dựa trên nền tảng hình thức về lý thuyết tập hợp, khái niệm lý thuyết tập hợp trên các quan hệ tức là tập của các bộ giá trị (value tuples).
- Cung cấp một cấu trúc dữ liệu đơn giản và đồng bộ.
- Có nên tảng lý thuyết vững chắc.
- Là cơ sở của các hệ quản trị database thương mại.
> Oracle, DB2, SQL Server,...

## II. Các khái niệm của mô hình quan hệ:
### 1. Quan hệ (Relation):
- Các thông tin lưu trữ trong database được tổ chức thành **bảng hai chiều** gọi là quan hệ, nghĩa là một **tập hữu hạn các thuộc tính**.
> ![image](https://hackmd.io/_uploads/H1ws0GIrWl.png)
- Gồm:
    - Tên
    - Tập hợp các cột:
        - Cố định
        - Được đặt tên
        - Có kiểu dữ liệu
    - Tập hợp các dòng: Thay đổi theo thời gian
- Một dòng ~ Một thực thể
- Quan hệ ~ Tập thực thể

### 2. Thuộc tính (Atribute):
- Tên các cột của quan hệ.
- Mô tả ý nghĩa cho các giá trị tại cột đó, nghĩa là **đặc trưng, tính chất riêng biệt của đối tượng** cần được lưu trữ trong database để phục vụ việc khai thác dữ liệu về đối tượng.
- Tất cả các dữ liệu trong cùng một cột đều có dùng kiểu dữ liệu.
- Tại một thời điểm, một thuộc tính không có giá trị hoặc chưa xác định được giá trị thì mang giá trị null.
> ![image](https://hackmd.io/_uploads/B11SkQLHbl.png)

### 3. Lược đồ (Schema):
#### a) Lược đồ quan hệ:
- Lược đồ quan hệ mô tả cấu trúc của một quan hệ và các mối liên hệ giữa các thuộc tính trong quan hệ đó.
- Cấu trúc của một quan hệ là tập thuộc tính của quan hệ đó.
- Gồm:
    - Tên của quan hệ
    - Tên của tập thuộc tính
> ![image](https://hackmd.io/_uploads/BkuvkmUS-e.png)
- Lược đồ database: Gồm nhiều lược đồ quan hệ.
> ![image](https://hackmd.io/_uploads/BysqJ7IS-g.png)
- Đặc trưng bởi:
    - Một tên phân biệt.
    - Một tập hợp hữu hạn các thuộc tính $(A_1, A_2,..., A_n)$ và mô tả để xác định ý nghĩa, mối liên hệ giữa các thuộc tính.
- Ký hiệu: $R(A_1:D_1, A_2:D_2,..., A_n:D_n)$ - Lược đồ quan hệ $R$ gồm $n$ thuộc tính $(A_1, A_2,..., A_n)$ và các miền giá trị $D_1$, $D_2$,..., $D_n$ tương ứng.

#### b) Lược đồ cơ sở dữ liệu:
![image](https://hackmd.io/_uploads/SJ-ILEUrZg.png)
Là tập hợp gồm các lược đồ quan hệ và mối liên hệ giữa chúng trong cùng một hệ thống quản lý.
> Lược đồ database quản lý điểm thi của sinh viên:
> 
> ![image](https://hackmd.io/_uploads/Hy5dIELr-x.png)

### 4. Bộ (Tuple):
- Là các dòng của quan hệ (trừ dòng tiêu đề - tên của các thuộc tính).
- Thể hiện dữ liệu cụ thể của các thuộc tính trong quan hệ, nghĩa là các **thông tin của một đối tượng**.
> ![image](https://hackmd.io/_uploads/S1mAJX8BWg.png)

### 5. Miền giá trị (Domain):
Là tập các **giá trị nguyên tố** (duy nhất) gắn liền với một thuộc tính:
- Kiểu dữ liệu cơ sở:
    - Chuỗi ký tự (string)
    - Số (interger)
- Các kiểu dữ liệu phức tạp (không được chấp nhận):
    - Tập hợp (set)
    - Danh sách (list)
    - Mảng (array)
    - Bản ghi (record)
> Ví dụ kiểu dữ liệu record:
> ```
> struct SV {
>    maSV char[5];
>    HoTen char[30];
>    diem float;
> };
> ```

### 6. Tân từ:
- Là một quy tắc dùng để mô tả một quan hệ.
- Làm rõ ngữ nghĩa, sự liên hệ giữa các thuộc tính trong quan hệ.
- Ký hiệu: $||R||$
> `SINHVIEN(MaSV, HoTen, GioiTinh, NoiSinh, MaLop)`
> Tân từ `||SINHVIEN||`: Mỗi sinh viên có mã sinh viên duy nhất (MaSV) để phân biệt với các sinh viên khác, có họ tên (HoTen), giới tính (GioiTinh), nơi sinh (NoiSinh) và thuộc về một lớp (MaLop).

### 7. Phép chiếu:
#### a) Chiếu một quan hệ lên tập thuộc tính:
- Dùng để **trích giá trị của một số thuộc tính** trong danh sách các thuộc tính của quan hệ.
- Ký hiệu: $R[X]$ hay $R.X$ - Phép chiếu của quan hệ $R$ lên tập thuộc tính $X$.
> ![image](https://hackmd.io/_uploads/HyCWGVLHZe.png)

#### b) Chiếu của một bộ lên tập thuộc tính:
- **Trích chọn các giá trị cụ thể của một bộ** theo các thuộc tính được chỉ ra trong danh sách thuộc tính của một quan hệ.
- Ký hiệu: $t_R[X]$ hoặc $t[X]$ - Chiếu của một bộ giá trị $t$ lên tập thuộc tính $X$ của quan hệ $R$. Nếu $X$ có một thuộc tính: $t_R.X$.
> ![image](https://hackmd.io/_uploads/Hk2UmEUS-e.png)

### 8. Định nghĩa hình thức:
#### a) Lược đồ quan hệ:
- Cho $A_1$, $A_2$,..., $A_n$ là các thuộc tính.
- Có các miền giá trị $D_1$, $D_2$,..., $D_n$ tương ứng.
- Ký hiệu $R(A_1:D_1, A_2:D_2,..., A_n:D_n)$ là một lược đồ quan hệ.
- Bậc của lược đồ quan hệ là số lượng thuộc tính trong lược đồ.
> ![image](https://hackmd.io/_uploads/HJtWbmLH-e.png)

#### b) Quan hệ (hay thể hiện quan hệ):
- Thể hiện quan hệ là **tập hợp các bộ giá trị của quan hệ** tại một thời điểm.
- Một quan hệ $r$ của lược đồ quan hệ $R(A_1, A_2,..., A_n)$, ký hiệu $r(R)$, là một tập các bộ $r = \{t_1, t_2,..., t_k\}$.
- Trong đó mỗi $t_i$ là một danh sách **có thứ tự** của $n$ giá trị $t_i = <v_1, v_2,..., v_n>$ (mỗi $v_i$ là một phần tử của miền giá trị $DOM(A_j)$ hoặc giá trị rỗng).
> ![image](https://hackmd.io/_uploads/HkzODBg8We.png)

#### c) Tóm tắt các ký hiệu:
![image](https://hackmd.io/_uploads/SktLKEIr-g.png)
- Lược đồ quan hệ $R$ bậc $n$: $R(A_1, A_2,..., A_n)$.
- Tập thuộc tính của $R$: $R^+$.
- Quan hệ (thể hiện quan hệ): $R$, $S$, $P$, $Q$
- Bộ: $t$, $u$, $v$
- Miền giá trị của thuộc tính $A$: $DOM(A)$ hay $MGT(A)$
- Giá trị tại thuộc tính $A$ của bộ thứ $t$: $t.A$ hay $t[A]$

### 9. Các đặc trưng của quan hệ:
- Mỗi quan hệ có một tên duy nhất.
- Mỗi thuộc tính của một quan hệ đều có tên khác nhau.
- Mỗi bộ là duy nhất, không trùng nhau.
- Mỗi giá trị trong một bộ là một giá trị nguyên tố hoặc rỗng (null).

## III. Ràng buộc toàn vẹn (Integrity Constraint):
- Là những quy tắc, điều kiện, ràng buộc cần được thoả mãn cho mọi thể hiện của database quan hệ.
- Được mô tả khi định nghĩa lược đồ quan hệ.
- Được kiểm tra khi các quan hệ có thay đổi.

### 1. Super Key:
- Các bộ trong quan hệ phải khác nhau từng đôi một.
- Siêu khoá (Super Key):
    - Gọi $SK$ là một tập con khác rỗng các thuộc tính của $R$, $SK$ là siêu khoá khi: $$\forall r, \forall {t_1, t_2} \in r, t_1 \ne t_2 \rightarrow t_1[SK] \ne t_2[SK]$$
    - Siêu khoá là tập các thuộc tính dùng để xác định **tính duy nhất** của mỗi bộ trong quan hệ, nghĩa là **tập con** các thuộc tính của $R^+$ mà giá trị của chúng có thể **phân biệt hai bộ khác nhau** trong cùng một thể hiện $T_R$ bất kỳ.
    - Mọi lược đồ quan hệ có tối thiểu một siêu khoá.
> ![image](https://hackmd.io/_uploads/S18ZE4UB-x.png)

### 2. Key:
- Định nghĩa:
    - Gọi $K$ là một tập con khác rỗng các thuộc tính của $R$.
    - $K$ là khoá nếu thoả đồng thời hai điều kiện:
        - $K$ là một siêu khoá của $R$.
        - $\forall K' \subset K, K' \ne K$, $K'$ không phải siêu khoá của $R$.
- Nhận xét:
    - Thuộc tính tham gia vào một khoá gọi là thuộc tính khoá, ngược lại là thuộc tính không khoá.
    - Giá trị của khoá dùng để nhận biết một bộ trong quan hệ.
    - Khoá là một đặc trung của lược đồ quan hệ, không phụ thuộc vào thể hiện quan hệ.
    - Khoá được xây dựng dựa vào ý nghĩa của một số thuộc tính trong quan hệ.
    - Lược đồ quan hệ có thể có nhiều khoá.
>![image](https://hackmd.io/_uploads/SJzr4E8BWg.png)

### 3. Primary Key:
Xét quan hệ: `NHANVIEN(MANV, TENNV, HONV, NGSINH, DCHI, PHAI, LUONG, PHONG)`
- Có hai khoá:
    - `MANV`
    - `HONV, TENNV, NGSINH`
- Khi cài đặt quan hệ thành bảng (thiết kế database), nếu quan hệ có nhiều hơn một khoá:
    - Chọn một khoá làm cơ sở để nhận biết các bộ, khoá có ít thuộc tính hơn.
    - Khoá được chọn gọi là **khoá chính** (Primary Key - $PK$):
        - Các thuộc tính khoá chính phải có giá trị khác null.
        - Các thuộc tính khoá chính thường được gạch dưới.
    - Các khoá còn lại gọi là khoá tương đương.
> ![image](https://hackmd.io/_uploads/r1VOuQ8H-l.png)

### 4. Tham chiếu:
Một bộ trong quan hệ $R$, tại thuộc tính $A$ nếu nhận một giá trị từ một thuộc tính $B$ của quan hệ $S$, ta gọi $R$ tham chiếu $S$. Bộ được tham chiếu phải tồn tại trước.
> ![image](https://hackmd.io/_uploads/SyHRdX8HZx.png)

### 5. Foreign Key:
- Xét hai lược đồ $R$ và $S$, gọi $FK$ là tập thuộc tính khác rỗng của $R$. $FK$ là khoá ngoại (Foreign Key) của $R$ khi:
    - Các thuộc tính trong $FK$ phải có cùng miền giá trị với các thuộc tính khoá chính của $S$.
    - Giá trị tại $FK$ của một bộ $t_1 \in R$:
        - Hoặc bằng giá trị tại khoá chính của một bộ $t_2 \in S$.
        - Hoặc bằng giá trị rỗng.
> ![image](https://hackmd.io/_uploads/r1ruKQLBbe.png)
- Nhận xét:
    - Trong một lược đồ quan hệ, một thuộc tính vừa có thể tham gia vào khoá chính vừa tham gia vào khoá ngoại.
    - Khoá ngoại có thể tham chiếu đến khoá chính trên cùng một lược đồ quan hệ.
    - Có thể có nhiều khoá ngoại tham chiếu đến cùng một khoá chính.
    - Ràng buộc tham chiếu = Ràng buộc khoá ngoại.
> ![image](https://hackmd.io/_uploads/HJHCKQIB-x.png)

## IV. Các đặc trưng của quan hệ:
- Thứ tự các bộ trong quan hệ là không quan trọng.
> ![image](https://hackmd.io/_uploads/HkxlTQLSZe.png)
- Thứ tự giữa các giá trị trong một bộ là quan trọng.
> ![image](https://hackmd.io/_uploads/B1ybTXIBWl.png)
- Mỗi giá trị trong một bộ:
    - Hoặc là một giá trị nguyên tố.
    - Hoặc là một giá trị rỗng (null).
- Không có bộ nào trùng nhau.

## V. Chuyển lược đồ E/R sang thiết kế quan hệ:
### 1. Các bước chuyển đổi:
#### a) Ánh xạ các loại thực thể chuyên biệt hoá, tổng quát hoá (nếu có) về dạng thường:
##### Trường hợp 1: Mức chuyên biệt hoá không có thuộc tính riêng:
$\rightarrow$ Gom lên mức tổng quát hoá và bổ sung thêm thuộc tính và các ràng buộc toàn vẹn.
> ![image](https://hackmd.io/_uploads/SyE5DE8H-x.png)
##### Trường hợp 2: Mức chuyên biệt hoá có ít thuộc tính riêng:
$\rightarrow$ Gom lên mức tổng quát, bổ sung thêm thuộc tính và các ràng buộc toàn vẹn.
> ![image](https://hackmd.io/_uploads/SkJ0D4LSWe.png)
##### Trường hợp 3: Mức chuyên biệt hoá có nhiều thuộc tính riêng:
$\rightarrow$ Tách thành nhiều thực thể riêng.
> ![image](https://hackmd.io/_uploads/r1AMOELBZl.png)

#### b) Ánh xạ tất cả loại thực thể thành quan hệ:
Tất cả các loại thực thể thành quan hệ.
> ![image](https://hackmd.io/_uploads/rkHBOVLHZg.png)

#### c) Ánh xạ các mối kết hợp:
##### Trường hợp 1: Mối kết hợp 1 - n:
$\rightarrow$ Lấy khoá chính của bên $n$ về là thuộc tính khoá ngoại của bên $1$.
> ![image](https://hackmd.io/_uploads/rkM1KV8rZg.png)

##### Trường hợp 2: Mối kết hợp n - n:
$\rightarrow$ Tạo quan hệ mới (Tên quan hệ?, Thuộc tính?, Khoá chính?)
> ![image](https://hackmd.io/_uploads/HyOzKE8SWe.png)

#### d) Chuẩn hoá các quan hệ:
> ![image](https://hackmd.io/_uploads/SyamK4USZg.png)
> ![image](https://hackmd.io/_uploads/BkiEKEIBZe.png)

### 2. Các quy tắc chuyển đổi:
- Tập thực thể: Các tập thực thể (Trừ tập thể yếu) chuyển thành các quan hệ có cùng tên và tập thuộc tính.
> ![image](https://hackmd.io/_uploads/H1Aqa7LrZl.png)
- Mối quan hệ:
    - Nhiều - Nhiều: Tạo một quan hệ mới có:
        - Tên quan hệ là tên của mối quan hệ.
        - Thuộc tính là những thuộc tính khoá của các tập thực thể liên quan.
    ![image](https://hackmd.io/_uploads/SJE1C7US-l.png)
    - Một - Nhiều: Thêm vào 'quan hệ một' thuộc tính khoá của 'quan hệ nhiều'.
    ![image](https://hackmd.io/_uploads/BJIV07IBZg.png)
    - Một - Một:
        - Hoặc thêm vào quan hệ này thuộc tính khoá của quan hệ kia.
        - Hoặc thêm thuộc tính khoá vào cả hai quan hệ.
    ![image](https://hackmd.io/_uploads/ryJtC78HZe.png)
- Thực thể yếu: Chuyển thành một quan hệ:
    - Có cùng tên với thực thể yếu.
    - Thêm vào thuộc tính khoá của quan hệ liên quan.
> ![image](https://hackmd.io/_uploads/BkM3CQ8rbl.png)
