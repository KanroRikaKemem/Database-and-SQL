## I. Giới thiệu:
- Là ngôn ngữ truy vấn hình thức.
- Do Codd đề nghị vào năm 1972, "Data Base Systems", Prentice Hall, p33 - 98.
- Đặc điểm:
    - Phi thủ tục.
    - Dựa vào lý thuyết logic.
    - Rút trích cái gì (What) $\neq$ Rút trích như thế nào (How).
    - Khả năng diễn đạt tương đương với đại số quan hệ.
- Có hai loại:
    - Phép tính quan hệ trên bộ (Tuple Rational Calculus): SQL
    - Phép tính quan hệ trên miền (Domain Rational Calculus): QBE (Query By Example)

## II. Phép tính quan hệ trên bộ:
Biểu thức phép tính quan hệ trên bộ có dạng: $\{t.A | P(t)\}$
- $t$ là biến bộ:
    - Biến nhận giá trị là một bộ của quan hệ trong database.
    - $t.A$ là giá trị của bộ $t$ tại thuộc tính $A$.
- $P$ là công thức có liên quan đến $t$. $P(t)$ có giá trị `TRUE` hoặc `FALSE` phụ thuộc vào $t$.
- Kết quả trả về là tập các bộ $t$ sao cho $P(t)$ đúng.
> - Ví dụ 1:
> ![image](https://hackmd.io/_uploads/B1uITqFIbl.png)
> - Ví dụ 2:
> ![image](https://hackmd.io/_uploads/SJcPp9F8-x.png)
> - Ví dụ 3:
> ![image](https://hackmd.io/_uploads/Bk5OT5KLWx.png)
> ![image](https://hackmd.io/_uploads/r1Tt65KLbe.png)
> - Ví dụ 4:
> ![image](https://hackmd.io/_uploads/r1lia9tIZl.png)
> - Ví dụ 5:
> ![image](https://hackmd.io/_uploads/BkH3TcFLbl.png)
> - Ví dụ 6:
> ![image](https://hackmd.io/_uploads/SJnap9YIZe.png)
> - Ví dụ 7:
> ![image](https://hackmd.io/_uploads/Sk3AacY8Zg.png)
> - Ví dụ 8:
> ![image](https://hackmd.io/_uploads/HJ2yRcY8bx.png)
> ![image](https://hackmd.io/_uploads/Bk7fCcKLWg.png)
> - Ví dụ 9:
> ![image](https://hackmd.io/_uploads/rylQ05tLZg.png)
> ![image](https://hackmd.io/_uploads/rkjQ0qYUZg.png)

### 1. Định nghĩa hình thức:
Một công thức truy vấn tổng quát có dạng: $$\{t_1.A_i, t_2.A_j,...,t_n.A_k | P(t_1, t_2,..., t_n)\}$$ Với:
- $t_1$, $t_2$,..., $t_n$ là các biến bộ.
- $A_i$, $A_j$,..., $A_k$ là các thuộc tính trong các bộ $t$ tương ứng.
- $P$ là công thức, được hình thành từ những công thức nguyên tố.

### 2. Biến bộ:
- Biến tự do (Free variable): $$\{t | t \in NHANVIEN \land t.LUONG > 30000\}$$ Với $t$ là biến tự do.
- Biến kết buộc (Bound variable): $$\{t | t \in NHANVIEN \land \exists s \in PHONGBAN (s.MAPHG = t.PHG)\}$$ Với:
    - $t$ là biến tự do.
    - $s$ là biến kết buộc.

### 3. Công thức nguyên tố:
- (1) $t \in R$:
    - $t$ là biến bộ.
    - $R$ là quan hệ.
> $t\ in NHANVIEN$
- (2) $r.A \theta s.B$:
    - $A$ là thuộc tính của biến bộ $t$.
    - $B$ là thuộc tính của biến bộ $s$.
    - $\theta$ là các phép so sánh: $<$, $>$, $\leq$, $\geq$, $\neq$, $=$.
> $t.MANV = s.MANV$
- (3) $t.A \theta c$:
    - $c$ là hằng số.
    - $A$ là thuộc tính của biến bộ $t$.
    - $\theta$ là các phép so sánh: $<$, $>$, $\leq$, $\geq$, $\neq$, $=$.
> s.LUONG > 30000$
- Mỗi công thức nguyên tố đều mang giá trị `TRUE` hoặc `FALSE` gọi là chân trị của công thức nguyên tố.
- Công thức (1):
    - Chân trị `TRUE` nếu $t$ là một bộ thuộc $R$.
    - Chân trị `FALSE` nếu $t$ không thuộc $R$.
> ![image](https://hackmd.io/_uploads/HJnI-jF8Zl.png)
- Công thức (2) và (3): Chân trị tuỳ thuộc vào việc thay thế giá trị thật sự của bộ vào vị trí biến bộ.
> ![image](https://hackmd.io/_uploads/r1gi-iKL-x.png)

### 4. Quy tắc:
- Mọi công thức nguyên tố đều là công thức.
- Nếu $P$ là công thức thì:
    - $\neg{P}$ là công thức.
    - $(P)$ là công thức.
- Nếu $P_1$ và $P_2$ là các công thức thì:
    - $P_1 \lor P_2$ là công thức.
    - $P_1 \land P_2$ là công thức.
    - $P_1 \rightarrow P_2$ là công thức.
- Nếu $P(t)$ là công thức thì:
    - $\forall t \in R (P(t))$ là công thức:
        - Chân trị `TRUE` khi $P(t)$ `TRUE` với mọi bộ $t$ trong $R$.
        - Chân trị `FALSE` khi có ít nhất một bộ làm cho $P(t)$ `FALSE`.
    - $\exists E \in R (P(t))$ là công thức:
        - Chân trị `TRUE` khi có ít nhất một bộ làm cho $P(t)$ `TRUE`.
        - Chân trị `FALSE` khi $P(t)$ với mọi bộ $t$ trong $R$.
- Nếu $P$ là công thức nguyên tố thì các biến bộ $t$ trong $P$ là biến tự do.
- Công thức $P = P_1 \land P_2$, $P = P_1 \lor P_2$, $P = P_1 \rightarrow P_2$: Sự xuất hiện của biến $t$ trong $P$ là tự do hay kết buộc phụ thuộc vào việc nó là tự do hay kết buộc trong $P_1$, $P_2$.

### 5. Một số biến đổi:
- $P_1 \land P_2 = \neg{(\neg{P_1} \lor \neg{P_2})}$
- $\forall t \in R, (P(t)) = \neg{\exists t \in R (\neg{P(t)})}$
- $\exists t \in R (P(t)) = \neg{\forall t \in R (\neg{P(t)})}$
- $P \rightarrow Q = \neg{P} \lor Q$

### 6. Công thức an toàn:
- Xét công thức: $\{t | \neg{(t \in NHANVIEN)}\}$
    - Có rất nhiều bộ $t$ không thuộc quan hệ `NHANVIEN`, thậm chí không có trong database.
    - Kết quả trả về không xác định.
- Một công thức $P$ gọi là an toàn nếu các giá trị trong kết quả đều lấy từ **miền giá trị của $P$**:
    - $DOM(P)$
    - Tập các giá trị được đề cập trong $P$.
> ![image](https://hackmd.io/_uploads/ry_YIjKIZe.png)

## III. Phép tính quan hệ trên miền:
Biểu thức phép tính quan hệ trên miền có dạng: $$\{x_1, x_2,..., x_n | P(x_1, x_2,..., x_n)\}$$ Với:
- $x_1$, $x_2$,..., $x_n$ là các biến miền - biến nhận giá trị là một miền giá trị của một thuộc tính.
- $P$ là công thức theo $x_1$, $x_2$,..., $x_n$, $P$ được hình thành từ những công thức nguyên tố.
- Kết quả trả về là tập các giá trị $x_1$, $x_2$, $x_n$ sao cho khi các giá trị được thay thế cho các $x_i$ thì $P$ `TRUE`.
> ![image](https://hackmd.io/_uploads/BkQqwsY8-e.png)
> ![image](https://hackmd.io/_uploads/S1p5Pjt8Wx.png)
> ![image](https://hackmd.io/_uploads/rJIsPjKLWx.png)

### 1. Công thức nguyên tố:
- (1) $<x_1, x_2,..., x_n> \in R$:
    - $x_i$ là biến miền.
    - $R$ là quan hệ có $n$ thuộc tính.
- (2) $x \theta y$:
    - $x$, $y$ là các biến miền.
    - Miền giá trị của $x$ và $y$ phải giống nhau.
    - $\theta$ là các phép so sánh: $<$, $>$, $\leq$, $\geq$, $\neq$, $=$.
- (3) $x \theta c$:
    - $c$ là hằng số.
    - $x$ là biến miền.
    - $\theta$ là các phép so sánh: $<$, $>$, $\leq$, $\geq$, $\neq$, $=$.

### 2. Nhận xét:
- Một công thức nguyên tố mang giá trị `TRUE` hoặc `FALSE` với một tập giá trị cụ thể tương ứng với các biến miền gọi là chân trị của công thức nguyên tố.
- Một số quy tắc và biến đổi tương tự với phép tính quan hệ trên bộ.

### 3. Công thức an toàn:
- Xét công thức: $\{p, r, s | \neg{(<p, q, r, s, t, u, v, x, y, z> \in NHANVIEN)}\}$:
    - Các giá trị trong kết quả trả về không thuộc miền giá trị của biểu thức.
    - Công thức không an toàn.
- Xét công thức: $\{x | \exists y (<x, y> \in R) \land \exists z (\neg{<x, z} \in R \land P(x,z))\}$
    - Với:
        - Công thức 1: $\exists y (<x, y> \in R)$
        - Công thức 2: $\exists z (\neg{<x, z} \in R \land P(x,z))$
    - $R$ là quan hệ có tập các giá trị hữu hạn.
    - Cũng có một tập hữu hạn các giá trị không thuộc $R$.
    - Công thức 1: Chỉ xem xét các giá trị trong $R$.
    - Công thức 2: Không thể kiểm tra khi không biết tập giá trị hữu hạn của $z$.
- Biểu thức $\{x_1, x_2,..., x_n | P(x_1, x_2,..., x_n)\}$ được gọi là an toàn nếu:
    - Các giá trị xuất hiện trong các bộ của biểu thức phải thuộc về miền giá trị của $P$.
    - Vị từ $\exists$: Biểu thức $\exists x (Q(x))$ `TRUE` khi và chỉ khi xác định được giá trị của $x$ thuộc $DOM(Q)$ làm cho $Q(x)$ `TRUE`.
    - Vị từ $\forall$: Biểu thức $\forall x (Q(x))$ `TRUE` khi và chỉ khi $Q(x)$ `TRUE` với mọi giá trị của $x$ thuộc $DOM(Q)$.
