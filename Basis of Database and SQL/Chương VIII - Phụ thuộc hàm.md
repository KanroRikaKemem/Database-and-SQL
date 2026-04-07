> Các vấn đề gặp phải khi tổ chức database:
> ![image](https://hackmd.io/_uploads/S1i9zHiL-g.png)
> ![image](https://hackmd.io/_uploads/r1vsfSoUbg.png)
> ![image](https://hackmd.io/_uploads/ByP2fHiUbg.png)
> ![image](https://hackmd.io/_uploads/ByQTzBs8Zx.png)
> ![image](https://hackmd.io/_uploads/Sk6TMSoI-g.png)

## I. Định nghĩa:
- Phụ thuộc hàm:
    - Là sự biểu diễn ràng buộc toàn vẹn dưới hình thức toán học.
    - Bảo đảm thông tin không bị tổn thất khi phân rã hoặc kết nối giữa các quan hệ.
- Phụ thuộc hàm trên quan hệ $R$ biểu diễn **mối liên hệ giữa các tập thuộc tính** trong $R$.
- Quan hệ $R$ được định nghĩa trên tập thuộc tính $U = \{A_1, A_2,..., A_n\}$.
- $A, B \subset U$ là hai tập con của tập thuộc tính $U$.
- Nếu tồn tại một ánh xạ $f: A \rightarrow B$ thì nói rằng $A$ xác định hàm $B$, hay $B$ phụ thuộc hàm vào $A$.
- Ký hiệu: $A \rightarrow B$
- Định nghĩa hình thức của phụ thuộc hàm:
    - Quan hệ $Q(A, B, C)$ có phụ thuộc hàm $A$ xác định $B$ (Ký hiệu là $A ? B$) nếu:
    - $q, q' \in Q$, sao cho $q.A = q'.A$ thì $q.B = q'.B$
- Nghĩa là: **Ứng với một giá trị của $A$ thì có một giá trị duy nhất của $B$**.
- $A$ là vế trái của phụ thuộc hàm, $B$ là vế phải của phụ thuộc hàm.
- Phụ thuộc hàm $A \rightarrow A$ được gọi là phụ thuộc hàm hiển nhiên.
- Có nhiều phụ thuộc hàm trên một quan hệ, tập phụ thuộc hàm được ký hiệu là $F$.
> ![image](https://hackmd.io/_uploads/HyWBfNo8be.png)
> ![image](https://hackmd.io/_uploads/Skl8M4iU-e.png)

## II. Biểu diễn phụ thuộc hàm bằng đồ thị:
- Phụ thuộc hàm có thể biểu diễn bằng đồ thị có hướng, các nút trong đồ thị chia thành hai loại:
    - Nút thuộc tính: Biểu diễn bằng tên thuộc tính.
    - Nút phụ thuộc hàm: Biểu diễn bằng hình tròn có số thứ tự của phụ thuộc hàm.
- Các cung trong đồ thị cũng có hai loại:
    - Cung đến phụ thuộc hàm: Xuất phát từ các thuộc tính ở vế trái của phụ thuộc hàm.
    - Cung rời phụ thuộc hàm: Hướng đến các thuộc tính ở vế phải của các phụ thuộc hàm.
> ![image](https://hackmd.io/_uploads/BkB1Q4iU-e.png)
> ![image](https://hackmd.io/_uploads/SyfxX4iLZl.png)

## III. Suy diễn logic các phụ thuộc hàm:
Cho lược đồ quan hệ $R$ với tập thuộc tính $U$ và tập các phụ thuộc hàm $F$:
- $X \rightarrow Y$ là một phụ  thuộc hàm, $X, Y \subseteq$
- Ta nói rằng $X \rightarrow Y$ được suy diễn logic từ $F$ nếu: **$\forall r \in R$, nếu $r$ thoả tất cả các phụ thuộc hàm trong $F$ thì $r$ cũng thoả $X \rightarrow Y$**
- Ký hiệu: $F |= X \rightarrow Y$
> ![image](https://hackmd.io/_uploads/SkBRmNi8We.png)

## IV. Hệ tiên đề Amstrong:
- Năm 1974, Amstrong đã đưa ra hệ tiên đề (gọi là hệ luật dẫn Amstrong): Cho lược đồ quan hệ $Q$ với tập thuộc tính $U$ và $X, Y, X, W \subseteq U$. Phụ thuộc hàm có các tính chất **cơ bản**:
    - (1) Tính phản xạ: **Nếu $Y \subseteq X$ thì $X \rightarrow Y$** (Phụ thuộc hàm hiển nhiên)
    - (2) Tính tăng trưởng: **Nếu $X \rightarrow Y$ thì $XZ \rightarrow YZ (Z \subseteq)$**
    - (3) Tính bắc cầu: **Nếu $X \rightarrow Y$ và $Y \rightarrow Z$ thì $X \rightarrow Z$**
> ![image](https://hackmd.io/_uploads/B1ayHNsUZx.png)
- Các tính chất bổ sung:
    - (4) Tính giả bắc cầu: **Nếu $X \rightarrow Y$ và $YZ \rightarrow W$ thì $XZ \rightarrow W$**
    - (5) Tính kết hợp: **Nếu $X \rightarrow Y$ và $X \rightarrow Z$ thì $X \rightarrow YZ$**
    - (6) Tính phân rã/tách: **Nếu $X \rightarrow YZ$ thì $X \rightarrow Y$ và $X \rightarrow Z$**
> ![image](https://hackmd.io/_uploads/ry0CSNiLZg.png)
> ![image](https://hackmd.io/_uploads/S1PJIEiU-l.png)

## V. Bao đóng (Closure):
- Gọi $F^+$ là bao đóng của $F$, tức là tập các phụ thuộc hàm được suy diễn logic từ $F$.
- Nếu $F = F^+$ thì ta nói $F$ là họ đầy đủ (full family) của các phụ thuộc hàm.
- **Bài toán thành viên (MemberShip):** Kiểm tra phụ thuộc hàm $X \rightarrow Y$ có được suy diễn logic từ $F$ không? (Tức là $X \rightarrow Y \in F^+)$
    - Đây là bài toán khó giải.
    - Đòi hỏi phải có một hệ luật dẫn để suy diễn logic các phụ thuộc hàm.
> ![image](https://hackmd.io/_uploads/SJoAL4oUbe.png)

## VI. Bao đóng của tập thuộc tính:
- Định nghĩa:
    - Bao đóng của tập thuộc tính $X$ đối với tập các phụ thuộc hàm $F$ (Ký hiệu: $F^+_F$) là tập tất cả các thuộc tính $A$ có thể suy dẫn từ $X$ nhờ tập bao đóng của $F(F^+)$.
    - $X^+_F = \{A | X \rightarrow A \in F^+\}$
- Nhận xét:
    - $X \subseteq X^+_F$
    - $X \rightarrow A \in F^+ \leftrightarrow A \subseteq X^+_F$
- Thuật toán Tìm bao đóng của tập thuộc tính:
    - Phụ thuộc hàm $F$ trên $U$ & $X \subseteq U$.
    - Output: $X^+_F$
    - Phương pháp: Tính liên tiếp $X_0$, $X_1$, $X_2$,... theo quy tắc:
        - B1: $X_0 = X$
        - B2: $X_{i + 1} = X_i \cup A$ sao cho $\exists (Y \rightarrow Z) \in D$, $A \in Z$ và $Y \in X_i$
        - B3: Cho đến khi $X_{i + 1} = X_i$ (Vì $X = X_0 \subseteq X_1 \subseteq X_2 \subseteq ... \subseteq U$, mà $U$ hữu hạn cho nên sẽ tồn tại một chỉ số $i$ nào đó mà $X_{i + 1} = X_i$), khi đó $X^+_F = X_i$
> - Ví dụ 1:
> ![image](https://hackmd.io/_uploads/BJUSKNiLbe.png)
> ![image](https://hackmd.io/_uploads/HJHIt4sUWg.png)
> ![image](https://hackmd.io/_uploads/SkWwYEiUZx.png)
> - Ví dụ 2:
> ![image](https://hackmd.io/_uploads/HJADYNoUbg.png)

## VII. Khoá - Thuật toán tìm khoá:
### 1. Định nghĩa:
- $R$ là lược đồ quan hệ định nghĩa trên tập các thuộc tính $U = \{A_1, A_2,..., A_n\}$
- Tập các phụ thuộc hàm $F = \{f_1, f_2,..., f_m\}$ xác định trên $R$.
- $K \subseteq U$ là khoá của $R$ nếu thoả mã hai điều kiện:
    - $K \rightarrow U$, với $K$ là siêu khoá.
    - $\overline{\exists} K' \subset K$ mà $K' \rightarrow U$.

### 2. Bài toán tìm khoá:
- Xác định tất cả các khoá của một lược đồ quan hệ.
- Được giải quyết qua hai giai đoạn:
    - Xây dựng tập $S$ chứa tất cả các siêu khoá của $R$.
    - Xây dựng tập $K$ chứa tất cả các khoá của $R$ từ tập $S$ bằng cách loại bỏ khỏi $S$ những siêu khoá không tối thiểu.
- Để xác định tất cả các siêu khoá của một lược đồ quan hệ $R$, ta lần lược xét $(2^n - 1)$ tập con của $R^+: X_1, X_2,...$.
- Nếu một tập con của $X_i$ của $R^+$ có bao đóng bằng đúng $R^+$ thì tập con $X_i$ chính là một siêu khoá.
- Nếu $R$ chỉ có một siêu khoá $S$ thì siêu khoá đó cũng là khoá của lược đồ quan hệ $R$.
- Trong trường hợp $R$ có nhiều hơn một siêu khoá (hữu hạn), để xác định tất cả các khoá chỉ định, ta so sánh một cặp siêu khoá $S_i$ và $S_j$. Nếu $S_i \subset S_j$, ta loại $S_j$ và giữ lại $S_i$.
- Lần lượt so sánh từng cặp siêu khoá để loại bỏ tập lớn, cuối cùng thu được tập các khoá chỉ định của $R$.

$\rightarrow$ Thuật toán không khả thi khi $n$ lớn, ta sẽ cải tiến thuật toán dựa trên việc phân loại tập thuộc tính $R^+$.

#### Thuật toán cải tiến:
- $A$ gọi là thuộc tính nguồn nếu $A$ không xuất hiện ở vế phải của bất kì phụ thuộc hàm không hiển nhiên nào của $F$.
- Tập các thuộc tính nguồn ký hiệu là $N$.
- $A$ gọi là thuộc tính đích nếu $A$ không phải thuộc tính nguồn và $A$ không xuất hiện ở vế trái của bất kỳ phụ thuộc hàm không hiển nhiên nào của $F$.
- Tập các thuộc tính đích ký hiệu là $D$.
- Tập hợp các thuộc tính không phải nguồn và không phải đích gọi là tập trung gian, ký hiệu là $L$.
- Các tập hợp $N$, $D$, $L$ rời nhau từng đôi một và $N \cup D \cup L = R^+$.
- Nhận xét: Nếu $K$ là khoá của $R$ thì $K$ chứa tất cả các thuộc tính nguồn và không chứa bất kỳ thuộc tính đích nào.
- Thuật toán cải tiến:
    - B1: Xây dựng $2^v$ tập con của $L: L_1, L_2,...$ bằng phương pháp đường chạy nhị phân.
    - B2: Xây dựng tập $K$ chứa các siêu khoá:
        - $K = \varnothing$
        - $\forall L_i, X_i = N \cup L_i$
        - Tính $(X_i)^+_F$. Nếu $(X_i)^+_F = R^+$ thì $K = K \cup X_j$
    - B3: Loại bỏ dần các siêu khoá lớn.
> - Ví dụ 1:
> ![image](https://hackmd.io/_uploads/rJvL0EiIZg.png)
> ![image](https://hackmd.io/_uploads/S1Vw0Ej8Zx.png)
> ![image](https://hackmd.io/_uploads/SJYK0VoLZg.png)
> - Ví dụ 2:
> ![image](https://hackmd.io/_uploads/BygHqCEjUWl.png)
> ![image](https://hackmd.io/_uploads/HkHoCVo8Zg.png)
> ![image](https://hackmd.io/_uploads/Bk0jCNsI-l.png)

## VIII. Phủ tối thiểu:
- Phụ thuộc hàm tương đương:
    - Gọi $F$ và $G$ là các tập phụ thuộc hàm. Ta nói rằng $F$ và $G$ là tương đương nếu $F^+ = G^+$.
    - Nếu $F$ và $G$ là tương đương, đôi khi nói $F$ phủ $G$ hay $G$ phủ $F$.
- Gọi $F$ là phủ tối thiểu nếu:
    - Mỗi vế phải của một phụ thuộc hàm $\in F$ chỉ có một thuộc tính.
    - Không tồn tại một phụ thuộc hàm $X \rightarrow A$ thuộc $F$, mà $F^+ = (F - \{X \rightarrow A\})^+$
    - Không tồn tại một phụ thuộc hàm $X \rightarrow A$ thuộc $F$ và một tập con $Z$ của $X$ mà $F^+ = (F - \{X \rightarrow A\} \cup \{Z \rightarrow A\})^+$
> - Ví dụ 1:
> ![image](https://hackmd.io/_uploads/S1aGGSoIbg.png)
> - Ví dụ 2:
> ![image](https://hackmd.io/_uploads/rJt7MroIWg.png)
