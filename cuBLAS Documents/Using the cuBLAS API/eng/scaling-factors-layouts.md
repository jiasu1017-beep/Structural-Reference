

3.1.4.5.1. Scaling factors layouts

> **Note**

Note
Starting addresses of scaling factors must be 16B aligned.


> **Note**

Note
\(M\) and \(N\) must be multiples of 4.


Then for the `CUBLASLT_MATMUL_MATRIX_SCALE_VEC128_32F` scaling mode, the scaling factors are:


- \(M\)-major for \(A\) with shape \(M \times L\) (\(M\)-major means that elements along the \(M\) dimension are contiguous in memory),
- \(N\)-major for \(B\) with shape \(N \times L\).


For the `CUBLASLT_MATMUL_MATRIX_SCALE_BLK128x128_32F` scaling mode, the scaling factors are $K$-major and the stride between the consecutive columns must be a multiple of 4. Let $L_4 = \lceil L \rceil_4$, where the $\lceil \cdot \rceil_4$ denotes rounding up to the nearest multiple of 4. Then


- for \(A\), the shape of the scaling factors is \(L_4 \times \lceil \frac{M}{128} \rceil\),
- for \(B\), the shape of the scaling factors is \(L_4 \times \lceil \frac{N}{128} \rceil\).


