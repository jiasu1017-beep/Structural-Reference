### 4.4.7. cublasXt<t>herk()

```c++

cublasStatus_t cublasXtCherk(cublasXtHandle_t handle,
                           cublasFillMode_t uplo, cublasOperation_t trans,
                           int n, int k,
                           const float  *alpha,
                           const cuComplex       *A, int lda,
                           const float  *beta,
                           cuComplex       *C, int ldc)
cublasStatus_t cublasXtZherk(cublasXtHandle_t handle,
                           cublasFillMode_t uplo, cublasOperation_t trans,
                           int n, int k,
                           const double *alpha,
                           const cuDoubleComplex *A, int lda,
                           const double *beta,
                           cuDoubleComplex *C, int ldc)


```


此函数执行 Hermitian k 秩更新


$C = \alpha\text{op}(A)\text{op}(A)^{H} + \beta C$


其中 $\alpha$ 和 $\beta$ 是标量，$C$ 是以 lower 或 upper 模式存储的 Hermitian 矩阵，$A$ 是维度为 $\text{op}(A)$ $n \times k$ 的矩阵。同样，对于矩阵 $A$


$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{transa == CUBLAS\_OP\_N}} \\
A^{H} & {\text{if }\textsf{transa == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLASXt API 上下文的句柄。 |
| uplo |  | 输入 | 指示是否存储矩阵 C 的 lower 或 upper 部分，其他 Hermitian 部分未引用。 |
| trans |  | 输入 | 非转置或（共轭）转置操作 op(A)。 |
| n |  | 输入 | 矩阵 op(A) 和 C 的行数。 |
| k |  | 输入 | 矩阵 op(A) 的列数。 |
| alpha | 主机 | 输入 | 用于乘法的 <type> 标量。 |
| A | 主机或设备 | 输入 | 维度为 lda x k 的 <type> 数组，当 transa == CUBLAS_OP_N 时 lda >= max(1, n)，否则为 lda x n 且 lda >= max(1, k)。 |
| lda |  | 输入 | 用于存储矩阵 A 的二维数组的 leading dimension。 |
| beta | 主机 | 输入 | 用于乘法的 <type> 标量，如果 beta == 0，则 C 不必是有效输入。 |
| C | 主机或设备 | 输入/输出 | 维度为 ldc x n 的 <type> 数组，ldc >= max(1, n)。对角线元素的虚部被假设并设置为零。 |
| ldc |  | 输入 | 用于存储矩阵 C 的二维数组的 leading dimension。 |


此函数返回的可能错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 参数 n < 0 或 k < 0 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数未能启动 GPU 执行 |


有关参考资料，请参阅 NETLIB 文档：


[cherk()](http://www.netlib.org/blas/cherk.f), [zherk()](http://www.netlib.org/blas/zherk.f)