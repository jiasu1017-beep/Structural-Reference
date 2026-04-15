### 4.4.8. cublasXt<t>her2k()



```c++

cublasStatus_t cublasXtCher2k(cublasXtHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            size_t n, size_t k,
                            const cuComplex       *alpha,
                            const cuComplex       *A, size_t lda,
                            const cuComplex       *B, size_t ldb,
                            const float  *beta,
                            cuComplex       *C, size_t ldc)
cublasStatus_t cublasXtZher2k(cublasXtHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            size_t n, size_t k,
                            const cuDoubleComplex *alpha,
                            const cuDoubleComplex *A, size_t lda,
                            const cuDoubleComplex *B, size_t ldb,
                            const double *beta,
                            cuDoubleComplex *C, size_t ldc)


```


此函数执行Hermitian矩阵的2k秩更新


$C = \alpha\text{op}(A)\text{op}(B)^{H} + \overset{ˉ}{\alpha}\text{op}(B)\text{op}(A)^{H} + \beta C$


其中 $\alpha$ 和 $\beta$ 为标量，$C$ 为存储在下三角或上三角模式的Hermitian矩阵，$A$ 和 $B$ 为维度分别为 $\text{op}(A)$ $n \times k$ 和 $\text{op}(B)$ $n \times k$ 的矩阵。同样，对于矩阵 $A$ 和 $B$：


$\text{op(}A\text{) and op(}B\text{)} = \left\{ \begin{matrix}
{A\text{ and }B} & {\text{if }\textsf{trans == CUBLAS\_OP\_N}} \\
{A^{H}\text{ and }B^{H}} & {\text{if }\textsf{trans == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLASXt API上下文的句柄。 |
| uplo |  | input | 指示矩阵C的下三角或上三角部分是否存储，另一半Hermitian部分未被引用。 |
| trans |  | input | 操作 op(A)，即非转置或（共）共轭转置。 |
| n |  | input | 矩阵 op(A)、op(B) 和 C 的行数。 |
| k |  | input | 矩阵 op(A) 和 op(B) 的列数。 |
| alpha | host | input | 用于乘法的 <type> 标量。 |
| A | host or device | input | 维度为 lda x k 的 <type> 数组，当 transa == CUBLAS_OP_N 时 lda >= max(1, n)，否则为 lda x n 且 lda >= max(1, k)。 |
| lda |  | input | 用于存储矩阵A的二维数组的leading dimension。 |
| B | host or device | input | 维度为 ldb x k 的 <type> 数组，当 transb == CUBLAS_OP_N 时 ldb >= max(1, n)，否则为 ldb x n 且 ldb >= max(1, k)。 |
| ldb |  | input | 用于存储矩阵B的二维数组的leading dimension。 |
| beta | host | input | 用于乘法的 <type> 标量，如果 beta == 0 则 C 不必是有效输入。 |
| C | host or device | in/out | 维度为 ldc x n 的 <type> 数组，ldc >= max(1, n)。对角元素的虚部被假定为零并设为零。 |
| ldc |  | input | 用于存储矩阵C的二维数组的leading dimension。 |


此函数可能返回的错误值及其含义如下所示。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 参数 n < 0 或 k < 0 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数未能在GPU上启动 |

有关参考资料请参阅NETLIB文档：


[cher2k()](http://www.netlib.org/blas/cher2k.f), [zher2k()](http://www.netlib.org/blas/zher2k.f)