## I. Quá trình thiết kế cơ sở dữ liệu:
![image](https://hackmd.io/_uploads/SkzvI_NSWl.png)
![image](https://hackmd.io/_uploads/r1RYLdVHbe.png)

## II. Mô hình thực thể - kết hợp (E/R):
- Được dùng để thiết kế database ở mức quan niệm.
- Biểu diễn **trừu tượng** cấu trúc của database.
- Lược đồ thực thể kết hợp (Entity - Relationship Diagram):

### 1. Thực thể (Entity Sets):
- Một thực thể là một đối tượng của thế giới thực.
- Tập hợp các thực thể giống nhau tạo thành một tập thực thể.
- Chú ý: Tương tác trên từng đối tượng một, không thao tác trên dữ liệu.
  
    ![image](https://hackmd.io/_uploads/SkdoLWvrZx.png)
    - Thực thể (Entity).
    - Đối tượng (Object).
    - Tập thực thể (Entity set).
    - Lớp đối tượng (Class of objects).
> Quản lý đề án công ty:
> - Một nhân viên là một thực thể.
> - Tập hợp các nhân viên là tập thực thể.
> - Một đề án là một thực thể.
> - Tập hợp các đề án là tập thực thể.
> - Một phòng ban là một thực thể.
> - Tập hợp các phòng ban là tập thực thể.

### 2. Thuộc tính (Atributes):
- Là những **đặc tính riêng biệt** của tập thực thể.
> Tập thực thể `NHANVIEN` có các thuộc tính:
> - Họ tên
> - Ngày sinh
> - Địa chỉ
> - ...
- Là những giá trị nguyên tố:
    - Kiểu chuỗi
    - Kiểu số nguyên
    - Kiểu số thực

### 3. Mối quan hệ (Relationship):
Là sự liên kết giữa hai hay nhiều tập thực thể.
> Giữa tập thực thể `NHANVIEN` và `PHONGBAN` có các liên kết:
> - Một nhân viên thuộc một phòng ban nào đó.
> - Một phòng ban có một nhân viên làm trưởng phòng.

### 4. Lược đồ thực thể - kết hợp (E/R):
#### a) Lược đồ E/R:
Là đồ thị biểu diễn các tập thực thể, thuộc tính và mối quan hệ:
- Đỉnh:

![image](https://hackmd.io/_uploads/HJYZYO4HWx.png)
- Cạnh là đường nối giữa:
    - Tập thực thể và thuộc tính.
    - Mối quan hệ và tập thực thể.
> ![image](https://hackmd.io/_uploads/HJHwFO4HZx.png)

#### b) Thể hiện của lược đồ E/R:
- Một database được mô tả bởi lược đồ E/R sẽ chứa đựng **những dữ liệu cụ thể** gọi là thể hiện database.
    - Mỗi tập thực thể sẽ có tập hợp hữu hạn các thực thể (Giả sử tập `NHANVIEN` có các thực thể như `NV1`, `NV2`,..., `NVn`).
    - Mỗi thực thể sẽ có một giá trị cụ thể tại mỗi thuộc tính.
- Chú ý:
    - Không lưu trữ lược đồ E/R trong database (Khái niệm trừu tượng).
    - Lược đồ E/R chỉ giúp thiết kế database trước khi chuyển quan hệ và dữ liệu xuống mức vật lý.

##### Mối quan hệ - Thể hiện:
Thể hiện database còn chứa các mối quan hệ cụ thể:
- Cho mối quan hệ $R$ kết nối $n$ tập thực thể $E_1$, $E_2$,..., $E_n$.
- Thể hiện của $R$ là tập hữu hạn các danh sách ($e_1$, $e_2$,..., $e_n$), trong đó $e_i$ là các giá trị được chọn từ các tập thực thể $E_i$.
> ![image](https://hackmd.io/_uploads/rk8biOVBWg.png)

##### Mối quan hệ - Multiplicity:
- Xét mối quan hệ nhị phân $R$ (Binary Relationship) giữa hai tập thực thể $E$ và $F$, tính mutiplicity gồm:
    - Một - Nhiều:
      
    ![image](https://hackmd.io/_uploads/HkO9sOEBZg.png)
        - Một $E$ có quan hệ với nhiều $F$.
        - Một $F$ có quan hệ với một $E$.
    - Một - Một:
      
    ![image](https://hackmd.io/_uploads/r160i_4BWx.png)
        - Một $E$ có quan hệ với một $F$.
        - Một $F$ có quan hệ với một $E$.
    - Nhiều - Nhiều:
      
    ![image](https://hackmd.io/_uploads/Byqf3OVrWe.png)
        - Một $E$ có quan hệ với nhiều $F$.
        - Một $F$ có quan hệ với nhiều $E$.
- $(min, max)$ chỉ định mỗi thực thể $e \in E$ tham gia ít nhất và nhiều nhất vào thể hiện của $R$:
  
![image](https://hackmd.io/_uploads/S1JSp_NSWx.png)
    - $(0, 1)$: Không hoặc một.
    - $(1, 1)$: Duy nhất một.
    - $(0, n)$: Không hoặc nhiều.
    - $(1, n)$: Một hoặc nhiều.
> Ví dụ:
> - Một phòng ban có nhiều nhân viên:
> ![image](https://hackmd.io/_uploads/ByVupuNrWe.png)
> - Một nhân viên chỉ thuộc một phòng ban:
> ![image](https://hackmd.io/_uploads/B1yqauESZl.png)
> - Một nhân viên có thể được phân công vào nhiều đề án hoặc không được phân công vào đề án nào:
> ![image](https://hackmd.io/_uploads/rJXhauNSZe.png)
> - Một nhân viên có thể là trưởng phòng của một phòng ban nào đó:
> ![image](https://hackmd.io/_uploads/S13Rp_EBWx.png)

##### Mối quan hệ - Vai trò:
Một loại thực thể có thể tham gia nhiều lần vào một quan hệ với nhiều vai trò khác nhau:
> ![image](https://hackmd.io/_uploads/H1eNRd4HWg.png)

##### Thuộc tính trên mối quan hệ:
- Thuộc tính trên mối quan hệ mô tả tính chất cho mối quan hệ đó.
- Thuộc tính này không thể gắn liền với những thực thể tham gia vào mối quan hệ.
> ![image](https://hackmd.io/_uploads/S1rOA_VBWg.png)

##### Thuộc tính khoá:
- Các thực thể trong tập thực thể cần phải được phân biệt.
- Khoá $K$ của tập thực thể $E$ là một hay nhiều thuộc tính sao cho lấy ra hai thực thể bất kỳ $e_1$ và $e_2$ trong $E$ thì $e_1$ và $e_2$ không thể có các giá trị giống nhau tại các thuộc tính trong $K$.
- Chú ý:
    - Mỗi tập thực thể phải có một khoá.
    - Một khoá có thể có một hay nhiều thuộc tính.
    - Có thể có nhiều khoá trong một tập thực thể, chọn ra một khoá làm khoá chính cho tập thực thể đó.
> ![image](https://hackmd.io/_uploads/rkLo1tNBZg.png)

### 5. Tập thực thể yếu (Weak Entity Set):
- Là tập thực thể mà khoá có được từ những thuộc tính của tập thực thế khác.
- Thực thể yếu (Weak Entity Set) phải tham gia vào mối quan hệ mà trong đó có một tập thực thể chính (nghĩa là không có điều kiện để làm một thực thể bình thường).
- Ký hiệu: Hình chữ nhật đôi
> ![image](https://hackmd.io/_uploads/SJRegKNrbx.png)
> ![image](https://hackmd.io/_uploads/r1pWxYNBWe.png)

## III. Thiết kế:
### 1. Các bước thiết kế:
- Xác định tập thực thể.
- Xác định mối quan hệ.
- Xác định thuộc tính và gắn thuộc tính cho tập thực thể và mối quan hệ.
- Quyết định miền giá trị cho thuộc tính.
- Quyết định thuộc tính khoá.
- Quyết định $(min, max)$ cho mối quan hệ.

### 2. Quy tắc thiết kế:
- Chính xác
- Tránh trùng lặp
- Dễ hiểu
- Chọn đúng mối quan hệ
- Chọn đúng kiểu thuộc tính

## IV. Ví dụ:
