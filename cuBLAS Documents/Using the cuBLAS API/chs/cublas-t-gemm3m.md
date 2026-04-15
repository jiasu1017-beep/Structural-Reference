### 2.7.2. cublas<t>gemm3m()



```c++
// 此函数支持64位整数接口

cublasStatus_t cublasCgemm3m(cublasHandle_t handle,
                           cublasOperation_t transa, cublasOperation_t transb,
                           int m, int n, int k,
                           const cuComplex       *alpha,
                           const cuComplex       *A, int lda,
                           const cuComplex       *B, int ldb,
                           const cuComplex       *beta,
                           cuComplex       *C, int ldc)
cublasStatus_t cublasZgemm3m(cublasHandle_t handle,
                           cublasOperation_t transa, cublasOperation_t transb,
                           int m, int n, int k,
                           const cuDoubleComplex *alpha,
                           const cuDoubleComplex *A, int lda,
                           const cuDoubleComplex *B, int ldb,
                           const cuDoubleComplex *beta,
                           cuDoubleComplex *C, int ldc)

```

此函数支持64位整数接口。

该函数使用高斯复杂度归约算法执行复数矩阵-矩阵乘法。这可以将性能提升高达25%。

$C = \alpha\text{op}(A)\text{op}(B) + \beta C$

其中 $\alpha$ 和 $\beta$ 是标量，$A$、$B$ 和 $C$ 是以列优先格式存储的矩阵，维度分别为 $\text{op}(A)$ $m \times k$、$\text{op}(B)$ $k \times n$ 和 $C$ $m \times n$。此外，对于矩阵 $A$：

$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{transa == $\mathrm{CUBLAS\_OP\_N}$}} \\
A^{T} & {\text{if }\textsf{transa == $\mathrm{CUBLAS\_OP\_T}$}} \\
A^{H} & {\text{if }\textsf{transa == $\mathrm{CUBLAS\_OP\_C}$}} \\
\end{matrix} \right.$

而 $\text{op}(B)$ 对矩阵 $B$ 的定义类似。

> **注意**

注意
这两个例程仅在计算能力大于或等于5.0的GPU上支持。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | 指向 cuBLAS 库上下文的句柄。 |
| transa |  | 输入 | op(A) 运算，非转置或（共轭）转置。 |
| transb |  | 输入 | op(B) 运算，非转置或（共轭）转置。 |
| m |  | 输入 | 矩阵 op(A) 和 C 的行数。 |
| n |  | 输入 | 矩阵 op(B) 和 C 的列数。 |
| k |  | 输入 | op(A) 的列数和 op(B) 的行数。 |
| alpha | 主机或设备 | 输入 | 用于乘法的 <type> 标量。 |
| A | 设备 | 输入 | <type> 数组，维度为 lda × k（当 transa == CUBLAS_OP_N 时，lda >= max(1, m)）；或者维度为 lda × m（当 transa != CUBLAS_OP_N 时，lda >= max(1, k)）。 |
| lda |  | 输入 | 用于存储矩阵 A 的二维数组的leading维度。 |
| B | 设备 | 输入 | <type> 数组，维度为 ldb × n（当 transb == CUBLAS_OP_N 时，ldb >= max(1, k)）；或者维度为 ldb × k（当 transb != CUBLAS_OP_N 时，ldb >= max(1, n)）。 |
| ldb |  | 输入 | 用于存储矩阵 B 的二维数组的leading维度。 |
| beta | 主机或设备 | 输入 | 用于乘法的 <type> 标量。如果 beta == 0，则 C 不必是有效输入。 |
| C | 设备 | 输入/输出 | <type> 数组，维度为 ldc × n，其中 ldc >= max(1, m)。 |
| ldc |  | 输入 | 用于存储矩阵 C 的二维数组的leading维度。 |


此函数可能返回的错误值及其含义列于下表：


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 m < 0 或 n < 0 或 k < 0，或如果 transa 和 transb 不是 CUBLAS_OP_N、CUBLAS_OP_C、CUBLAS_OP_T 之一，或如果当 transa == CUBLAS_OP_N 时 lda < max(1, m) 且其他情况下 lda < max(1, k)，或如果当 transb == CUBLAS_OP_N 时 ldb < max(1, k) 且其他情况下 ldb < max(1, n)，或如果 ldc < max(1, m)，或如果 alpha 或 beta 为 NULL，或如果 beta 不为零时 C 为 NULL |
| CUBLAS_STATUS_ARCH_MISMATCH | 设备的计算能力低于5.0。 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在 GPU 上启动失败。 |


有关参考信息，请参阅 NETLIB 文档：


[cgemm()](http://www.netlib.org/blas/cgemm.f), [zgemm()](http://www.netlib.org/blas/zgemm.f)