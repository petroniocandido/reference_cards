# Advanced PyTorch

## BLAS and LAPACK Operations

Method | Calculus| Description |
| --- | --- |--- |
```addbmm(v, M1, M2, *, beta=1, alpha=1)``` | $out = \beta v + \alpha \sum_{b=0}^{b-1} M_1 \times M_2$ |Batch matrix-matrix product of matrices $M_1 \in \mathrm{R}^{b\times n \times m}$ and $M_2 \in \mathrm{R}^{b\times m \times p}$, with a sum-reduce step, added with $v \in \mathrm{R}^{n \times p}$.
