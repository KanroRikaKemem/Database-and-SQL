## I. Giới thiệu:
> ![image](https://hackmd.io/_uploads/BJcwTY2LZx.png)
- Sự trùng lặp thông tin dẫn đến:
    - Tăng chi phí lưu trữ.
    - Tăng chi phí kiểm tra ràng buộc toàn vẹn.
    - Thiếu nhất quán.
    - Vi phạm tính toàn vẹn của dữ liệu.
> ![image](https://hackmd.io/_uploads/SJT5TFn8Ze.png)
- Dạng chuẩn đuọc dùng để **chuẩn hoá quan hệ**, đáp ứng các mục tiêu thiết kế:
    - Giảm tối đa trùng lặp thông tin.
    - Kiểm tra ràng buộc toàn vẹn dễ dàng.
- Đánh giá chất lượng thiết kế của lược đồ cơ sở dữ liệu:
    - E.F.Codd đưa ra ba dạng chuẩn (Normal Form).
    - R.F.Boyce và E.F.Codd cải tiến dạng chuẩn 3 gọi là **dạng chuẩn Boyce - Codd** (BC).
- Các dạng chuẩn được định nghĩa dựa trên khái niệm phụ thuộc hàm.
- Mục đích của quá trình chuẩn hoá:
    - Biểu diễn được mọi quan hệ trong database.
    - Tránh sai sót khi thêm, xoá, sửa dữ liệu.
    - Tránh phải xây dựng lại cấu trúc của các quan hệ khi cần đến các kiểu dữ liệu mới.
- Các cấp chuẩn hoá quan hệ:
  
![image](https://hackmd.io/_uploads/ry4bn9hUZx.png)

## II. Dạng chuẩn 1 (1NF):
- Định nghĩa:
    - Một lược đồ quan hệ $Q$ được gọi là đạt chuẩn 1 nếu **mọi thuộc tính của $Q$ đều là thuộc tính đơn**, nghĩa là **tất cả thuộc tính đều mang giá trị nguyên tố**.
    - Giá trị nguyên tố là giá trị không phân nhỏ được nữa.
    - Các thuộc tính đa trị (multi-valued), thuộc tính đa hợp (composite) không là nguyên tố.
    - Một lược đồ database được gọi là đạt dạng chuẩn 1 nếu mọi lược đồ quan hệ con $Q_i$ của nó đều đạt dạng chuẩn 1.
- Thuộc tính đơn:
    - Giả sử có lược đồ quan hệ $Q$.
    - Một thuộc tính $A$ của $Q$ gọi là thuộc tính đơn nếu nó không phải là sự tích hợp của nhiều thuộc tính khác.
> ![image](https://hackmd.io/_uploads/B1K4y52L-l.png)
> ![image](https://hackmd.io/_uploads/SyNHkchUbl.png)

## III. Dạng chuẩn 2 (2NF):
- Định nghĩa: Một lược đồ quan hệ $Q$ gọi là đạt dạng chuẩn 2 nếu:
    - $Q$ đạt dạng chuẩn 1.
    - Mọi thuộc tính không khoá của $Q$ đều **phụ thuộc đầy đủ** vào các khoá của $Q$.
- Một lược đồ database được gọi là đạt dạng chuẩn 2 nếu mọi lược đồ quan hệ con $Q_i$ của nó đều ở dạng chuẩn 2.
- Phụ thuộc đầy đủ:
    - Giả sử có một lược đồ quan hệ $Q$ và tập phụ thuộc hàm $F$.
    - Thuộc tính $A$ được gọi là **phụ thuộc đầy đủ** vào một tập thuộc tính $X$ nếu:
        - $A \in X^+_F$
        - $X \rightarrow A$ phụ thuộc hàm nguyên tố (không tồn tại $X' \subseteq X$, mà $X' \rightarrow A$).
> ![image](https://hackmd.io/_uploads/BJPGe93Ibe.png)
- Kiểm tra Dạng chuẩn 2:
    - Tìm tất cả khoá của $R$.
    - Với mỗi khoá $K$, tìm $S_i^+$ với $S_i$ là tất cả các tập con thực sự của $K$.
    - Nếu tồn tại $S_i^+$ chứa thuộc tính không khoá thì $R$ không đạt dạng chuẩn 2, ngược lại $Q$ đạt dạng chuẩn 2.
- Nhận xét:
    - Nếu lược đồ quan hệ $Q$ chỉ có một khoá $K$ và $K$ chỉ có một thuộc tính thì $Q$ đạt dạng chuẩn 2.
    - Một lược đồ quan hệ $Q$ ở dạng chuẩn 2 vẫn có thể chứa đựng sự trùng lặp thông tin.

## IV. Dạng chuẩn 3 (3NF):
- Định nghĩa 1: Một lược đồ quan hệ $Q$ đạt dạng chuẩn 3 nếu:
    - $Q$ ở dạng chuẩn 2.
    - Mọi thuộc tính không khoá của $Q$ đều không **phụ thuộc bắc cầu** vào một khoá nào của $Q$.
- Phụ thuộc bắc cầu: Thuộc tính $A \in R^+$ được gọi là phụ thuộc bắc cầu vào tập thuộc tính $X$ nếu $\exists Y \in R^+$:
    - $X \rightarrow Y \in F^+$ và $Y \rightarrow A \in F^+$
    - $Y \rightarrow X \notin F^+$
    - $A \notin (X \cup Y)$
- Định nghĩa 2: Lược đồ $R$ đạt dạng chuẩn 3 nếu tất cả các phụ thuộc hàm $X \rightarrow Y \in F$, với $Y \notin X$ đều có:
    - $X$ là siêu khoá, hoặc
    - $Y$ là thuộc tính khoá
- Một lược đồ database được gọi là đạt dạng chuẩn 3 nếu mọi lược đồ quan hệ con $Q_i$ của nó đều đạt dạng chuẩn 3.
- Kiểm tra dạng chuẩn 3:
    - Tìm tất cả khoá của $R$.
    - Phân rã vế phải của các phụ thuộc hàm trong $F$ thành các phụ thuộc hàm có vế phải một thuộc tính.
    - Nếu mọi phụ thuộc hàm $X \rightarrow Y \in F$ và $Y \notin X$ đều thoả:
        - $X$ là siêu khoá (vế trái chứa một khoá), hoặc
        - $Y$ là thuộc tính khoá (vế phải là tập con của khoá).
        $\rightarrow$ $R$ đạt dạng chuẩn 3, ngược lại $R$ không đạt dạng chuẩn 3.
- Nhận xét:
    - Lược đồ đạt dạng chuẩn 3 thì cũng đạt dạng chuẩn 2.
    - Phụ thuộc bắc cầu gây nên trùng lặp dữ liệu.
    - Khi thiết kế database, yêu cầu tối thiểu đạt dạng chuẩn 3.

## V. Dạng chuẩn Boyce - Codd:
- Định nghĩa:
    - Một lược đồ quan hệ $Q$ được gọi là đạt dạng chuẩn Boyce - Codd (BC) nếu **mọi phụ thuộc hàm không hiển nhiên của $F$ đều có vế trái chứa khoá**, nghĩa là tất cả phụ thuộc hàm $X \rightarrow Y \in F$ với $Y \notin X$ đều có $X$ là siêu khoá.
    - Một lược đồ database được gọi là ở dạng chuẩn BC nếu mọi lược đồ quan hệ con $Q_i$ của nó đều đạt dạng chuẩn BC.
- Nhận xét:
    - Nếu một lược đồ quan hệ $Q$ đạt dạng chuẩn BC thì cũng đạt dạng chuẩn 3.
    - Trong một lược đồ quan hệ $Q$ đạt dạng chuẩn BC, việc kiểm tra phụ thuộc hàm chủ yếu là **kiểm tra khoá nội**.
- Kiểm tra dạng chuẩn BC:
    - Tìm tất cả khoá của $R$.
    - Phân rã vế phải của các phụ thuộc hàm trong $F$ thành các phụ thuộc hàm có vế phải một thuộc tính.
    - Nếu mọi phụ thuộc hàm $X \rightarrow Y \in F$ và $Y \notin X$ đều thoả $X$ là siêu khoá (vế trái chứa một khoá).
    $\rightarrow$ $R$ đạt dạng chuẩn BC, ngược lại $R$ không đạt dạng chuẩn BC.

## VI. Dạng chuẩn của Lược đồ quan hệ, Lược đồ cơ sở dữ liệu:
- Dạng chuẩn của lược đồ quan hệ là dạng chuẩn **cao nhất** của lược đồ quan hệ đó.
- Dạng chuẩn của lược đồ cơ sở dữ liệu là dạng chuẩn thấp nhất của các lược đồ quan hệ con.
- Kiểm tra dạng chuẩn của lược đồ quan hệ $R$:
    - Tìm mọi khoá của $R$.
    - Kiểm tra dạng chuẩn BC, nếu đúng thì kết luận $R$ đạt dạng chuẩn BC, ngược lại qua bước tiếp theo.
    - Kiểm tra dạng chuẩn 3, nếu đúng thì kết luận $R$ đạt dạng chuẩn 3, ngược lại qua bước tiếp theo.
    - Kiểm tra dạng chuẩn 2, nếu đúng thì kết luận $R$ đạt dạng chuẩn 2, ngược lại kết luận $R$ đạt dạng chuẩn 1.

## VII. Chuẩn hoá Lược đồ Cơ sở dữ liệu - Phương pháp phân rã:
- Quá trình chuẩn hoá 1 lược đồ database:
    - Nhắm mục đích nâng cao chất lượng thiết kế.
    - Đưa các lược đồ quan hệ con **từ dạng chuẩn thấp lên dạng chuẩn cao hơn** mà tối thiểu phải là dạng chuẩn 3.
- **Phương pháp phân rã** là một phương pháp dùng để chuẩn hoá một lược đồ cơ sở dữ liệu.
- Sự bảo toàn thông tin:
    - Việc chuẩn hoá một lược đồ quan hệ hay một lược đồ database phải bảo đảm yêu cầu: Bảo toàn thông tin.
    - Phép phân rã $Q$ thành $Q_1$, $Q_2$,... được gọi là bảo toàn thông tin nếu: $$\forall T_Q: T_Q = T_Q[Q_1] |><| [Q_2] ... |><| ...$$
- Định lý Delobel:
    - Cho lược đồ quan hệ $Q(XYZ)$ và tập phụ thuộc hàm $F$.
    - Nếu $X \rightarrow Y \in F^+$ thì phép phân rã $Q$ thành hai lược đồ quan hệ con: $Q_1(XY)$ và $Q_2(XZ)$ là bảo toàn thông tin.
    - Phương pháp phân rã:
      
    ![image](https://hackmd.io/_uploads/S1NGqq2Ibe.png)
> ![image](https://hackmd.io/_uploads/Hylm55nIWe.png)
> ![image](https://hackmd.io/_uploads/ry9X95n8-l.png)
- Nhận xét:
    - Thuật toán phân rã như trên là bảo toàn thông tin (định lý Delobel).
    - Các lược đồ quan hệ con cuối cùng (nút lá trong cây phân rã) đều đạt ít nhất là **dạng chuẩn 3**.
    - Thuật toán phân rã có thể tạo ra các lược đồ quan hệ con không có nhiều ngữ nghĩa trong thực tế.
    - Chất lượng của database kết quả có phụ thuộc vào việc chọn phương thức $f_0$ ở từng bước phân rã.
    - Thông thường phương thức được chọn là phương thức gây ra chất lượng xấu của lược đồ quan hệ (không đầy đủ, bắc cầu).

## VIII. Ví dụ:
- Ví dụ 1:
![image](https://hackmd.io/_uploads/By7XsqnLbe.png)
![image](https://hackmd.io/_uploads/SylVsqn8-x.png)
![image](https://hackmd.io/_uploads/B1sEo5hI-x.png)
![image](https://hackmd.io/_uploads/Hk2Hi93UWx.png)
![image](https://hackmd.io/_uploads/S1L8oc38be.png)
![image](https://hackmd.io/_uploads/HJTOs53UZe.png)
![image](https://hackmd.io/_uploads/ryoYo928Wx.png)
![image](https://hackmd.io/_uploads/rkEijchLbe.png)
![image](https://hackmd.io/_uploads/rkzni5nI-g.png)
![image](https://hackmd.io/_uploads/H1JaiqhIWe.png)

- Ví dụ 2:
![image](https://hackmd.io/_uploads/r1Cfh93UWx.png)
![image](https://hackmd.io/_uploads/SJCmnq38Wl.png)
![image](https://hackmd.io/_uploads/rylXI3qhUZl.png)
