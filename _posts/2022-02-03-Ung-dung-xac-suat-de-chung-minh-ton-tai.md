---
title: Ứng dụng xác suất trong chứng minh tồn tại
tags: [probability, math]
---

Bài toán trích từ bài toán 88, chương 7 của cuốn sách [Introduction to Probability 2nd](https://drive.google.com/file/d/1VmkAAGOYCTORq1wxSQqy255qLJjTNvBI/view)

# Đề bài
Một đồ thị không có hướng bao gồm $n$ đỉnh, giữa 2 đỉnh có thể có cạnh nối 2 đỉnh đó và không có khuyên. Một clique là đồ thị con đầy đủ có $k$ đỉnh. Tương tự, một anticlique là đồ thị con có $k$ đỉnh và không có cạnh nào cả. Cho rằng $n\choose k<2^{k\choose 2 - 1}$. Chứng minh rằng tồn tại một đồ thị gồm $n$ đỉnh không có chứa clique và anticlique.

# Tiếp cận
Cách giải thông thường nhất sẽ là chỉ ra cách xây dựng một đồ thị thỏa đề. Tuy nhiên cách làm này không hề dễ dàng. Chúng ta sẽ đi một đường vòng khác bằng cách xây dựng ra đồ thị ngẫu nhiên và chỉ ra xác suất tồn tại đồ thị thỏa đề lớn hơn $0$, như vậy, theo lí thuyết xác suất, mặc dù ta không biết chính xác đồ thị ấy được tạo như thế nào, nhưng ta biết nó tồn tại.

## Lời giải
Đầu tiên, ta sẽ xây dựng đồ thị ngẫu nhiên. Với mỗi cặp điểm $\{i, j\}$, xác suất tồn tại cạnh giữa 2 điểm này là $\frac12$ và các cạnh độc lập với nhau.

Gọi $S$ là tập các đồ thị con gồm $k$ đỉnh. Nếu đồ thị con thứ $i$ của $S$ không phải là clique hoặc anticlique thì $A_i = 1$, ngược lại $A_i = 0$. Ta cần chứng minh
$$
P\left(\bigcap_{i=1}^{n\choose k} A_i = 1\right) > 0
$$
Gọi $A_i^C$ là phần bù của $A_i$, nghĩa là $A_i^C = 1$ khi đồ thị con thứ $i$ là clique hoặc là anticlique. Ta có:
$$
P\left(\bigcap_{i=1}^{n\choose k} A_i = 1\right) > 0\\
\Leftrightarrow P\left(\bigcup_{i=1}^{n\choose k} A_i^C=1\right) < 1\\
$$
Ta cos
$$
P\left(\bigcup_{i=1}^{n\choose k} A_i^C=1\right) < \sum_{i=1}^{n\choose k}P(A_i^C=1)
$$
Với mỗi đồ thị con thứ $i$ của $S$, vì các cạnh độc lập, nên xác suất nó là clique là là $2^{-k\choose 2}, tương tự xác suất nó là anticlique là $2^{-k\choose 2}.

Suy ra:
$$
P(A_i^C) = 2^{-k\choose 2} + 2^{-k\choose 2} = 2^{-k\choose 2 - 1}\\
\Rightarrow \sum_{i=1}^{n\choose k}P(A_i^C=1) = n\choose k 2^{-k\choose 2 + 1}
$$
Lại có $n\choose k <2^{k\choose 2 - 1}$, suy ra
$$
P\left(\bigcup_{i=1}^{n\choose k} A_i^C=1\right)<n\choose k 2^{-k\choose 2 + 1}<1
$$
Hay
$$
P\left(\bigcap_{i=1}^{n\choose k} A_i = 1\right) > 0
$$

Vậy tồn tại một đồ thị gồm $n$ đỉnh và không chứa clique và anticlique.
# Nhận xét
Bài này mình thấy khá hay, nếu ta tiếp cận trực tiếp bằng cách xây dựng đồ thị thì rất khó. Bài này cho ta một cách tiếp cận mới trong chứng minh tồn tại
