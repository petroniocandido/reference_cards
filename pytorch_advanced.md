# Advanced PyTorch

### Vector-Vector
Method | Calculus| Description |
| --- | --- |--- |
```addr(B, v1, v2, *, beta=1, alpha=1)``` | $O = \alpha (v_1 \otimes v_2) + \beta B$ | Outer-product of vectors $v_1 \in \mathbb{R}^{n}$ and $v_2 \in \mathbb{R}^{m}$ and adds it to the matrix $B \in \mathbb{R}^{n \times m}$.  Returns $O \in \mathbb{R}^{n \times m}$.
```cdist(v1, v2, p=2.0)``` | $D = \Vert v_1 - v_2\Vert_p$  | batched the p-norm distance between each pair of the two collections of row vectors $v_1 \in \mathbb{R}^{b \times p \times n}$, with $p$ vectors of size $m$ and $v_2 \in \mathbb{R}^{b \times q \times n}$ with $q$ vectors of size $n$, resulting in a batched matrix of distances Returns $D \in \mathbb{R}^{b \times p \times q}$.
```inner(v1, v2)``` | $a = v_1 \cdot v_2$ = \sum_{i=1}^n v_{1i} \cdot v_{2i}  | Dot product for 1D tensors $v_1 \in \mathbb{R}^{n}$ and $v_2 \in \mathbb{R}^{n}$.  Returns $a \in \mathbb{R}$.
```outer(v1, v2)``` | $O = v_1 \otimes v_2 \rightarrow O_{ij} = v_{1i} \cdot v_{2j}$ | Outer-product of vectors $v_1 \in \mathbb{R}^{n}$ and $v_2 \in \mathbb{R}^{m}$.  Returns $O \in \mathbb{R}^{n \times m}$.
```cross(v1, v2)``` | $v = v_1 \times v_2 = \Vert v_1\Vert \cdot \Vert v_2 \Vert sin(\theta) n$ | Batched Cross-product of vectors $v_1 \in \mathbb{R}^{b \times n}$ and $v_2 \in \mathbb{R}^{b \times n}$.  Returns $v \in \mathbb{R}^{b \times n}$.


### Vector-Matrix
Method | Calculus| Description |
| --- | --- |--- |
```addmv(b, M, v, *, beta=1, alpha=1)``` | $o = \alpha (M \times v) + \beta b$ | matrix-vector product of the matrix $M \in \mathbb{R}^{n \times m}$ and vector $v \in \mathbb{R}^{m}$, with a sum-reduce step, added with $v \in \mathbb{R}^{n}$.  Returns $o \in \mathbb{R}^{n}$.
```mv(M, v)``` | $o = M \times v$ |  Non-batched matrix multiplication of the matrix $M \in \mathbb{R}^{n \times m}$ and the vector $v \in \mathbb{R}^{m}$. Returns $o \in \mathbb{R}^{n}$.

### Matrix-Matrix
Method | Calculus| Description |
| --- | --- |--- |
```addmm(b, M1, M2, *, beta=1, alpha=1)``` | $o = \alpha (M_1 \times M_2) + \beta b$ |Matrix-matrix product of matrices $M_1 \in \mathbb{R}^{n \times m}$ and $M_2 \in \mathbb{R}^{m \times p}$, with a sum-reduce step, added with $v \in \mathbb{R}^{n \times p}$. Returns $o \in \mathbb{R}^{n \times p}$.
```addbmm(B, M1, M2, *, beta=1, alpha=1)``` | $O = \alpha (\sum_{b=0}^{b-1} M_1 \times M_2)  + \beta B$ |Batch matrix-matrix product of matrices $M_1 \in \mathbb{R}^{b\times n \times m}$ and $M_2 \in \mathbb{R}^{b\times m \times p}$, with a sum-reduce step, added with $B \in \mathbb{R}^{n \times p}$. Returns $O \in \mathbb{R}^{n \times p}$.
```baddbmm(B, M1, M2, *, beta=1, alpha=1)``` | $O = \alpha (\sum_{b=0}^{b-1} M_1 \times M_2)  + \beta B$ |Batch matrix-matrix product of matrices $M_1 \in \mathbb{R}^{b\times n \times m}$ and $M_2 \in \mathbb{R}^{b\times m \times p}$, with a sum-reduce step, added with $B \in \mathbb{R}^{b \times n \times p}$. Returns $O \in \mathbb{R}^{b \times n \times p}$.
```bmm(M1, M2)``` | $O = M_1 \times M_2$ |  Batched matrix multiplication of the matrices $M_1 \in \mathbb{R}^{b \times n \times m}$ and $M_2 \in \mathbb{R}^{b \times m \times p}$. Returns $O \in \mathbb{R}^{b \times n \times p}$.
```mm(M1, M2)``` | $O = M_1 \times M_2$ |  Non-batched matrix multiplication of the matrices $M_1 \in \mathbb{R}^{n \times m}$ and $M_2 \in \mathbb{R}^{m \times p}$. Returns $O \in \mathbb{R}^{n \times p}$.
```chain_matmul(M1, ..., Mn)``` | $O = \prod_{i=1}^{n} M_i$ | The matrix product of the n 2D matrices $M_i \in \mathbb{R}^{a \times b}$. Returns $O \in \mathbb{R}^{a \times b}$.
