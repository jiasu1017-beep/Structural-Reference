### 2.7.14. cublas<t>herk()

```c++

cublasStatus_t cublasCherk(cublasHandle_t handle,
                           cublasFillMode_t uplo, cublasOperation_t trans,
                           int n, int k,
                           const float  *alpha,
                           const cuComplex       *A, int lda,
                           const float  *beta,
                           cuComplex       *C, int ldc)
//此函数支持64位整数接口
cublasStatus_t cublasZherk(cublasHandle_t handle,
                           cublasFillMode_t uplo, cublasOperation_t trans,
                           int n, int k,
                           const double *alpha,
                           const cuDoubleComplex *A, int lda,
                           const double *beta,
                           cuDoubleComplex *C, int ldc)
//此函数支持64位整数接口
```

此函数执行厄米特（Hermitian）秩-k更新操作。

$C = \alpha\text{op}(A)\text{op}(A)^{H} + \beta C$

其中 $\alpha$ 和 $\beta$ 为标量，$C$ 为以下三角模式存储的厄米特矩阵，$A$ 为维度 $\text{op}(A)$ $n \times k$ 的矩阵。此外，对于矩阵 $A$：

$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{transa == CUBLAS\_OP\_N}} \\
A^{H} & {\text{if }\textsf{transa == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS库上下文的句柄 |
| uplo |  | input | 指示矩阵C的下三角或上三角部分是否存储，另一半厄米特部分不被引用 |
| trans |  | input | 非转置或（共轭）转置操作 op(A) |
| n |  | input | 矩阵 op(A) 和 C 的行数 |
| k |  | input | 矩阵 op(A) 的列数 |
| alpha | 主机或设备 | input | 用于乘法运算的 <type> 标量 |
| A | 设备 | input | 维度为 lda x k 的 <type> 数组，当 transa == CUBLAS_OP_N 时 lda >= max(1, n)，否则为 lda x n 且 lda >= max(1, k) |
| lda |  | input | 用于存储矩阵A的二维数组的主维度 |
| beta |  | input | 用于乘法运算的 <type> 标量。如果 beta == 0，则C不必是有效输入 |
| C | 设备 | 输入/输出 | 维度为 ldc x n 的 <type> 数组，ldc >= max(1, n)。对角元素的虚部被假定为零并设置为零 |
| ldc |  | input | 用于存储矩阵C的二维数组的主维度 |

此函数返回的可能错误值及其含义如下。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0 或 k < 0，或如果 trans 不是 CUBLAS_OP_N、CUBLAS_OP_T 和 CUBLAS_OP_C 之一，或如果 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或当 trans == CUBLAS_OP_N 时 lda < max(1, n)，否则 lda < max(1, k)，或 ldc < max(1, n)，或 alpha 或 beta 为 NULL，或当 beta 不为零时 C 为 NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在GPU上启动 |

更多参考信息请参阅NETLIB文档：

[cherk()](http://www.netlib.org/blas/cherk.f), [zherk()](http://www.netlib.org/blas/zherk.f)