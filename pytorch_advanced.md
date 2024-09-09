# Advanced PyTorch

## BLAS and LAPACK Operations

Method | Calculus
-----------------
```addbmm($v$, $M_1$, $M_2$, *, beta=1, alpha=1)``` | $out = \beta v + \alpha \sum_{b=0}^{b-1} M_1 \times M_2$
