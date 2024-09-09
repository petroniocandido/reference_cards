# Advanced PyTorch

## BLAS and LAPACK Operations

Method | Calculus| Description |
| --- | --- |--- |
```addmm(b, M1, M2, *, beta=1, alpha=1)``` | $o = \alpha (M_1 \times M_2) + \beta b$ |Matrix-matrix product of matrices $M_1 \in \mathbb{R}^{n \times m}$ and $M_2 \in \mathbb{R}^{m \times p}$, with a sum-reduce step, added with $v \in \mathbb{R}^{n \times p}$. Returns $o \in \mathbb{R}^{n \times p}$.
```addbmm(b, M1, M2, *, beta=1, alpha=1)``` | $o = \alpha (\sum_{b=0}^{b-1} M_1 \times M_2)  + \beta b$ |Batch matrix-matrix product of matrices $M_1 \in \mathbb{R}^{b\times n \times m}$ and $M_2 \in \mathbb{R}^{b\times m \times p}$, with a sum-reduce step, added with $v \in \mathbb{R}^{n \times p}$. Returns $o \in \mathbb{R}^{n \times p}$.
```addmv(b, M, v, *, beta=1, alpha=1)``` | $o = \alpha (M \times v) + \beta b$ | matrix-vector product of the matrix $M \in \mathbb{R}^{n \times m}$ and vector $v \in \mathbb{R}^{m}$, with a sum-reduce step, added with $v \in \mathbb{R}^{n}$.  Returns $o \in \mathbb{R}^{n}$.
