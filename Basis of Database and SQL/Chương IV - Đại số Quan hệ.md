## I. Giới thiệu:
> Xét một số xử lý trên quan hệ `NHANVIEN`:
> 
> ![image](https://hackmd.io/_uploads/r1iKuuoBbe.png)
> - Thêm mới một nhân viên.
> - Chuyển nhân viên có tên là "Tùng" sang phòng số 1.
> - Cho biết họ tên và ngày sinh các nhân viên có lương trên 20000.
- Có hai loại xử lý:
    - Cập nhật (làm thay đổi) dữ liệu: Thêm mới, xoá, sửa
    - Không làm thay đổi dữ liệu (rút trích): Truy vấn (query).
- Thực hiện các xử lý:
    - Đại số quan hệ (Relational Algebra): Biểu diễn câu truy vấn dưới dạng biểu thức.
    - Phép tính quan hệ (Relational Calculus): Biểu diễn kết quả.
    - SQL (Structured Query Language)

## II. Đại số quan hệ:
### 1. Nhắc lại:
- Đại số:
    - Toán tử (operator)
    - Toán hạng (operand)
- Trong số học:
    - Toán tử: $+$, $-$, $*$, $/$
    - Toán hạng - biến (variables): $x$, $y$, $z$
    - Hằng (constant)
    - Biểu thức

### 2. Đại số quan hệ:
- Biến là các **quan hệ** (tập hợp - set).
- Toán tử là các phép toán (operations):
    - Trên tập hợp:
        - Hội (union): $\cup$
        - Giao (intersec): $\cap$
        - Trừ (difference): $-$
    - Rút trích một phần của quan hệ:
        - Chọn (selection): $\sigma$
        - Chiếu (projection): $\pi$
    - Kết hợp các quan hệ:
        - Tích Cartesian (Cartesian product): x
        - Kết (join): $\bowtie$
    - Đổi tên: $\rho$
- Hằng số là thể hiện của một quan hệ.
- Biểu thức:
    - Gọi là câu truy vấn.
    - Là chuỗi các phép toán đại số quan hệ.
    - Kết quả trả về là một thể hiện của quan hệ.

## III. Phép toán tập hợp:
- Quan hệ là tập hợp các bộ:
    - Hội (union): $R \cup S$
    - Giao (intersec): $R \cap S$
    - Trừ (difference): $R - S$
- Tính khả hợp (Union Compatibility): Hai lược đồ quan hệ $R(A_1, A_2,..., A_n)$ và $S(B_1, B_2,..., B_n)$ là **khả hợp** nếu:
    - Cùng bậc $n$
    - Miền giá trị thuộc tính phải tương thích: $DOM(A_i) = DOM(B_i)$, $1 \leq i \leq n$
- Kết quả của $\cup$, $\cap$, $-$ là một **quan hệ** có cùng tên thuộc tính với quan hệ đầu tiên ($R$).
> ![image](https://hackmd.io/_uploads/SJ9bAujr-g.png)

### 1. Phép hội:
![image](https://hackmd.io/_uploads/S1s830hHbl.png)
Cho hai quan hệ $R$ và $S$ khả hợp, phép hội của $R$ và $S$:
- Ký hiệu: $R \cup S$
- Là một quan hệ gồm các bộ thuộc $R$ hoặc thuộc $S$, hoặc cả hai (các bộ trùng lặp sẽ bị bỏ): $$R \cup S = \{t | t \in R \lor t \in S\}$$
> ![image](https://hackmd.io/_uploads/ByNe1tsBZl.png)

### 2. Phép giao:
![image](https://hackmd.io/_uploads/SkhP3A3BZg.png)
Cho hai quan hệ $R$ và $S$ khả hợp, phép giao của $R$ và $S$:
- Ký hiệu: $R \cap S$
- Là một quan hệ gồm các bộ thuộc $R$ đồng thời thuộc $S$: $$R \cap S = \{t | t \in R \land t \in S\}$$
> ![image](https://hackmd.io/_uploads/rydIJYiS-e.png)

### 3. Phép trừ:
![image](https://hackmd.io/_uploads/HJuO3Rnr-e.png)
Cho hai quan hệ $R$ và $S$ khả hợp, phép trừ của $R$ và $S$:
- Ký hiệu: $R - S$
- Là một quan hệ gồm các bộ thuộc $R$ và không thuộc $S$: $$R - S = \{t | t \in R \lor t \notin S\}$$
> ![image](https://hackmd.io/_uploads/HJyh1KsBWx.png)

### 4. Các tính chất:
- Giao hoán:
    - $R \cup S = S \cup R$
    - $R \cap S = S \cap R$
- Kết hợp:
    - $R \cup (S \cup T) = (R \cup S) \cup T$
    - $R \cap (S \cap T) = (R \cap S) \cap T$

## IV. Phép chọn:
- Dùng để lấy ra các dòng (bộ) của quan hệ $R$ thoả điều kiện: $\sigma_P(R) = \{t | t \in R \land P(t)\}$
- Các bộ được chọn phải thoả **điều kiện chọn $P$**.
- Ký hiệu: $\sigma_p(R)$
- $P$ - điều kiện chọn là biểu thức gồm các mệnh đề có dạng:
    - `<tên thuộc tính><phép so sánh/phép logic><hằng số>`
    - `<tên thuộc tính><phép so sánh/phép logic><tên thuộc tính>`
        - `<phép so sánh>` gồm $<$, $>$, $\leq$, $\geq$
        - Các mệnh đề được nối lại nhờ các phép $\land$, $\lor$, $\neg$ là `<phép thuộc tính>`.
- Kết quả trả về là một **quan hệ**:
    - Có cùng danh sách thuộc tính với $R$.
    - Có số bộ luôn ít hơn hoặc bằng số bộ của $R$.
> ![image](https://hackmd.io/_uploads/SyedZFjS-x.png)
- Có tính giao hoán: $\sigma_{p_1}(\sigma_{p_2}(R)) = \sigma_{p_2}(\sigma_{p_1}(R)) = \sigma_{p_1 \land p_2}(R)$
> ![image](https://hackmd.io/_uploads/H1K-Gtirbe.png)
> ![image](https://hackmd.io/_uploads/HJDzzYjBWe.png)
> ![image](https://hackmd.io/_uploads/HkoGRy3BWx.png)

## V. Phép chiếu:
- Được dùng để lấy ra một vài cột của quan hệ $R$.
- Ký hiệu: $\pi_{A_1, A_2,...A_k}(R)$
- Kết quả trả về là một **quan hệ**:
    - Có $k$ thuộc tính.
    - Có số bộ luôn ít hơn hoặc bằng số bộ của $R$.
> ![image](https://hackmd.io/_uploads/rJjKMtsB-g.png)
- Phép chiếu không có tính giao hoán: $\pi_{X, Y}(R) \neq \pi_X(\pi_Y(R))$
- $\pi_{A_1, A_2,..., A_n}(\pi_{A_1, A_2,..., A_m}(R)) = \pi_{A_1, A_2,..., A_n}(R)$, với $n \leq m$
> ![image](https://hackmd.io/_uploads/ByGYQKiBWe.png)
> ![image](https://hackmd.io/_uploads/SJvV0Jhr-l.png)

### 1. Phép chiếu tổng quát:
- Mở rộng phép chiếu bằng cách cho phép dùng các phép toán số học trong danh sách thuộc tính.
- Ký hiệu: $\pi_{F_1, F_2,..., F_n}(E)$
    - $E$ là biểu thức đại số quan hệ.
    - $F_1$, $F_2$,..., $F_n$ là các biểu thức số học liên quan đến:
        - Hằng số
        - Thuộc tính trong $E$
> ![image](https://hackmd.io/_uploads/SklqEtsr-g.png)

### 2. Chuỗi các phép toán:
Kết hợp các phép toán đại số quan hệ:
- Lồng các biểu thức lại với nhau: $$\pi_{A_1, A_2,..., A_k}(\sigma_p(R))$$ $$\sigma_p(\pi_{A_1, A_2,..., A_k}(R))$$
- Thực hiện từng phép toán một:
    - B1: $\sigma_p(R)$
    - B2: $\pi_{A_1, A_2,...,A_k}($Quan hệ kết quả ở B1$)$ (Cần đặt tên cho quan hệ).

### 3. Phép gán:
- Được dùng để nhận lấy **kết quả** trả về của một phép toán, thường là kết quả trung gian trong chuỗi các phép toán.
- Ký hiệu: $\leftarrow$
> ![image](https://hackmd.io/_uploads/Hy1WLtirZl.png)

### 4. Phép đổi tên:
Dùng để đổi tên:
- Quan hệ: Xét quan hệ $R(B, C, D)$, $\rho_S(R)$ là đổi tên quan hệ $R$ thành $S$.
- Thuộc tính:
    - $\rho_{X, C, D}(R)$: Đổi tên thuộc tính $B$ thành $X$.
    - $\rho_{S(X, C, D)}(R)$: Đổi tên quan hệ $R$ thành $S$ và thuộc tính $B$ thành $X$.
> ![image](https://hackmd.io/_uploads/SkJywtoHbl.png)
> ![image](https://hackmd.io/_uploads/rJ88RJnrbl.png)

## VI. Phép tích Cartesian:
- Dùng để kết hợp các bộ của các quan hệ lại với nhau.
- Ký hiệu: $R$ x $S = \{t_q | t \in R \land q \in S\}$ với $R(A_1, A_2,..., A_n)$ và $S(B_1, B_2,.., B_m)$
- Kết quả trả về là một quan hệ $Q$:
    - Mỗi bộ của $Q$ là **tổ hợp** giữa một bộ trong $R$ và một bộ trong $S$.
    - Nếu $R$ có $u$ bộ và $S$ có $v$ bộ thì $Q$ sẽ có $u$ x $v$ bộ.
    - Nếu $R$ có $n$ thuộc tính và $Q$ có $m$ thuộc tính thì $Q$ sẽ có $n + m$ thuộc tính ($R^+ \cap Q^+ \neq \varnothing$).
> ![image](https://hackmd.io/_uploads/rJe-OtiSZl.png)
> ![image](https://hackmd.io/_uploads/B1-fdFiHWl.png)
- Thông thường theo sau phép tích Cartesian là phép chọn.
![image](https://hackmd.io/_uploads/H1LSOtir-g.png)
> - Ví dụ 1:
> ![image](https://hackmd.io/_uploads/HJfO_KjSbl.png)
> ![image](https://hackmd.io/_uploads/Bk0_utjrbg.png)
> - Ví dụ 2:
> ![image](https://hackmd.io/_uploads/rJTYdYir-e.png)
> ![image](https://hackmd.io/_uploads/H1acdKjHZe.png)
> - Ví dụ 3:
> ![image](https://hackmd.io/_uploads/rymhOKjSZx.png)
> ![image](https://hackmd.io/_uploads/Hkup_YsSbe.png)

## VII. Phép kết:
- Dùng để tổ hợp hai bộ có liên quan từ hai quan hệ thành một bộ.
- Ký hiệu: $R \bowtie S$
- Kết quả của phép kết $R(A_1, A_2,..., A_n)$ và $S(B_1, B_2,..., B_m)$ là một quan hệ $Q$:
    - Có $n + m$ thuộc tính $Q(A_1, A_2,..., A_n, B_1, B_2,..., B_m)$
    - Mỗi bộ của $Q$ là tổ hợp của hai bộ trong $R$ và $S$, thoả mãn một số **điều kiện kết** nào đó:
        - Có dạng $A_i \theta B_j$
        - $A_i$ là thuộc tính của $R$, $B_j$ là thuộc tính của $S$.
        - $A_i$ và $B_j$ có cùng miền giá trị.
        - $\theta$ là phép so sánh $\neq$, $=$, $<$, $>$, $\geq$, $\leq$.
### 1. Phân loại:
#### a) Kết theta (Theta join)
- Là phép kết có điều kiện:
    - Ký hiệu: $R \bowtie_C S$
    - $C$ gọi là điều kiện liên kết trên thuộc tính.
- Với $R(A_1, A_2,..., A_n)$ và $S(B_1, B_2,..., B_m)$, phép kết thực hiện hai bước:
    - Tích Cartesian: $R$ x $S$
    - Chọn các bộ thoả điều kiện $A \theta B$ với $\theta$ là các phép so sánh. $$R \bowtie_{A \theta B} S = \{ (t,q) \mid t \in R \wedge q \in S \wedge t.A \theta q.B \}$$
    - $R \bowtie_C S = \sigma_C(R \times S)$
> ![image](https://hackmd.io/_uploads/B1tRU03r-g.png)

#### b) Kết bằng (Equi join)
Là phép kết có $\theta$ là điều kiện so sánh bằng.
> - Ví dụ 1:
> ![image](https://hackmd.io/_uploads/rk2lPR3HWx.png)
> - Ví dụ 2:
> ![image](https://hackmd.io/_uploads/BytaDAnrWe.png)
> ![image](https://hackmd.io/_uploads/ryuRv0nSWe.png)
- Trong kết bằng, nếu tên thuộc tính so sánh $A$ của hai quan hệ giống nhau, phép kết được viết lại là:
![image](https://hackmd.io/_uploads/r13bd0hr-l.png)
> ![image](https://hackmd.io/_uploads/SJhMuAhHWl.png)
- Cần quan tâm **ý nghĩa dữ liệu** khi thực hiện phép kết.
> ![image](https://hackmd.io/_uploads/Hkh4OCnB-l.png)

#### c) Kết tự nhiên (Natural join):
- Là **phép kết bằng** và **các cặp thuộc tính so sánh** phải **cùng tên và cùng miền giá trị**.
- Nếu không cùng tên, thực hiện phép đổi tên trước khi kết.
- Ký hiệu $R \bowtie S$ hay $R$ * $S$.
- $R^+ \cap Q^+ \neq \varnothing$
- Kết quả của phép kết bằng bỏ bớt đi một cột giống nhau.
> ![image](https://hackmd.io/_uploads/SkM6OR3HWl.png)
        
### 2. Ví dụ phép kết theta:
> ![image](https://hackmd.io/_uploads/rktFrJnr-e.png)
> - Ví dụ phép kết bằng:
> ![image](https://hackmd.io/_uploads/Bk-jB1hrZx.png)
> - Ví dụ phép kết tự nhiên:
> ![image](https://hackmd.io/_uploads/Byw3HynSbl.png)
> - Ví dụ 1:
> ![image](https://hackmd.io/_uploads/BJeAryhH-l.png)
> - Ví dụ 2:
> ![image](https://hackmd.io/_uploads/Sk-18JnSZx.png)
> - Ví dụ 3:
> ![image](https://hackmd.io/_uploads/SkogI1nBZe.png)

## VIII. Tập đầy đủ các phép toán đại số quan hệ:
Tập các phép toán $\sigma$, $\pi$, x, $-$, $\cup$ được gọi là tập đầy đủ các phép toán đại số quan hệ, nghĩa là phép các phép toán có thể biểu diễn qua chúng.
> $R \cap S = R \cup S - ((R - S) \cup (S - R))$
> $R \bowtie_C S = \sigma_C(R$ x $S)$

## IX. Phép chia:
- Được dùng để lấy ra một số bộ trong quan hệ $R$ sao cho thoả với **tất cả** các bộ trong quan hệ $S$.
- Ký hiệu $R \div S$. $R(Z)$ và $S(X)$:
    - $Z$ là tập thuộc tính của $R$, $X$ là tập thuộc tính của $S$.
    - $X \subseteq Z$
- Kết quả của phép chia là một quan hệ $T(Y)$:
    - Với tập thuộc tính: $Y^+ = Z^+ - X^+$
    - Các bộ trong $Z$ đều khớp với tất cả các bộ trong $X$.
    - Có $t$ là một bộ của $T$ nếu **với mọi bộ** $t_S \in S$, tồn tại bộ $t_R \in R$ thoả hai điều kiện:
        - $t_R(Y) = t$
        - $t_R(X) = t_S(X)$
        ![image](https://hackmd.io/_uploads/SkZbu12r-x.png)
> - Ví dụ 1:
> ![image](https://hackmd.io/_uploads/SkxmuJhH-g.png)
> - Ví dụ 2:
> ![image](https://hackmd.io/_uploads/SkNHa0nHbg.png)
> ![image](https://hackmd.io/_uploads/H1KLa0nS-g.png)
- Biểu diễn phép chia thông qua tập đầy đủ các phép toán quan hệ:
    - $Q_1 \leftarrow \pi_Y(R)$
    - $Q_2 \leftarrow Q_1$ x $S$
    - $Q_3 \leftarrow \pi_Y(Q_2 - R)$
    - $T \leftarrow Q_1 - Q_3$

## X. Các phép toán khác:
### 1. Hàm kết hợp (Agreegation fuction):
Nhận vào tập hợp các giá trị và trả về một **giá trị đơn**:
- `AVG`
- `MIN`
- `MAX`
- `SUM`
- `COUNT`
> ![image](https://hackmd.io/_uploads/SJgGYy2SZl.png)

### 2. Phép gom nhóm (Grouping):
- Dùng để phân chia quan hệ thành nhiều nhóm dựa trên điều kiện gom nhóm nào đó:
- Ký hiệu: $G_1, G_2, \dots, G_n \mathcal{G}_{F_1(A_1), F_2(A_2), \dots, F_n(A_n)}(E)$
    - $E$ là biểu thức đại số quan hệ.
    - $G_1$, $G_2$,..., $G_n$ là các hàm.
    - $A_1$, $A_2$,..., $A_n$ là các thuộc tính toán trong hàm $F$.
> - Ví dụ 1:
> ![image](https://hackmd.io/_uploads/HJwy9JnBZx.png)
> - Ví dụ 2:
> ![image](https://hackmd.io/_uploads/ryHs6C2Hbe.png)
> - Ví dụ 3:
> ![image](https://hackmd.io/_uploads/ry2n6Cnrbx.png)
> - Ví dụ 4:
> ![image](https://hackmd.io/_uploads/HkqATR2r-l.png)
> ![image](https://hackmd.io/_uploads/BJIyCA2r-e.png)

### 3. Phép kết ngoài (Outer Join):
- Mở rộng phép kết để tránh mất mát thông tin:
    - Thực hiện phép kết.
    - Lấy thêm các bộ không thoả điều kiện kết.
- Có ba hình thức:
    - Mở rộng bên trái (Kết ngoài trái - Left Outer Join):
        - Giữ lại các bộ của quan hệ bên trái, các thuộc tính của quan hệ bên phải không có giá trị sẽ mang giá trị null.
        - Ký hiệu: $\bowtie \kern-1em \ltimes$
          
    ![image](https://hackmd.io/_uploads/rJcvo0hrWx.png)
    ![image](https://hackmd.io/_uploads/Bysdo03B-l.png)
    - Mở rộng bên phải (Kết ngoài phải - Right Outer Join): 
        - Giữ lại các bộ của quan hệ bên phải, các thuộc tính của quan hệ bên trái không có giá trị sẽ mang giá trị null.
        - Ký hiệu: $\bowtie \kern-1em \rtimes$
          
    ![image](https://hackmd.io/_uploads/BknojAhHbx.png)
    ![image](https://hackmd.io/_uploads/H1U3i0hHZe.png)
    - Mở rộng hai bên (Kết ngoài đầy đủ - Full Outer Join):
        - Giữ lại các bộ thuộc quan hệ bên phải và trái, các thuộc tính ở quan hệ bên trái và phải mà không có dữ liệu sẽ mang giá trị null.
        - Còn gọi là phép kết trái phải.
        - Ký hiệu: $\ltimes \kern-1em \rtimes$
          
    ![image](https://hackmd.io/_uploads/SyV7sJ3S-e.png)
    ![image](https://hackmd.io/_uploads/Syq-nR3rbx.png)
> ![image](https://hackmd.io/_uploads/SkwRc1hrZe.png)

## XI. Các thao tác cập nhật trên quan hệ:
Nội dung của database có thể được cập nhật bằng các thao tác:
### 1. Thêm (Insertion):
Diễn đạt: $R_{new} \leftarrow R_{old} \cup E$
- $R$ là quan hệ.
- $E$ là một biểu thức đại số quan hệ.
> ![image](https://hackmd.io/_uploads/rJJz2JnHZx.png)

### 2. Xoá (Deletion):
Diễn đạt: $R_{new} \leftarrow R_{old} - E$
- $R$ là quan hệ.
- $E$ là một biểu thức đại số quan hệ.
> ![image](https://hackmd.io/_uploads/HkdN2khS-l.png)

### 3. Sửa (Updating):
Diễn đạt: $R_{new} \leftarrow \pi_{F_1, F_2,..., F_n}(R_{old})$
- $R$ là quan hệ.
- $F_i$ là biểu thức tính toán cho ra giá trị mới của thuộc tính.
> ![image](https://hackmd.io/_uploads/Hkbcn13B-x.png)

### 4. Cách diễn đạt:
Các phép thao tác cập nhật được diễn đạt thông qua phép toán gán: $R_{new} \leftarrow$ Các phép toán trên $R_{old}$
