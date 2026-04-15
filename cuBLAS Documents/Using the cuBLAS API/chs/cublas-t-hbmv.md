### 2.6.18. cublas<t>hbmv()

```c++

cublasStatus_t cublasChbmv(cublasHandle_t handle, cublasFillMode_t uplo,
                          int n, int k, const cuComplex       *alpha,
                          const cuComplex       *A, int lda,
                          const cuComplex       *x, int incx,
                          const cuComplex       *beta,
                          cuComplex       *y, int incy)
cublasStatus_t cublasZhbmv(cublasHandle_t handle, cublasFillMode_t uplo,
                          int n, int k, const cuDoubleComplex *alpha,
                          const cuDoubleComplex *A, int lda,
                          const cuDoubleComplex *x, int incx,
                          const cuDoubleComplex *beta,
                          cuDoubleComplex *y, int incy)

```

此函数支持64位整数接口。

此函数执行厄米特带矩阵与向量的乘法运算：

$\textbf{y} = \alpha A\textbf{x} + \beta\textbf{y}$

其中 $A$ 是一个 $n \times n$ 的厄米特带矩阵，具有 $k$ 条次对角线和超对角线，$\mathbf{x}$ 和 $\mathbf{y}$ 是向量，$\alpha$ 和 $\beta$ 是标量。

如果 `uplo == CUBLAS_FILL_MODE_LOWER`，则厄米特带矩阵 $A$ 按列存储，主对角线存储在第 `1` 行，第一个次对角线存储在第 `2` 行（从第一个位置开始），第二个次对角线存储在第 `3` 行（从第一个位置开始），以此类推。因此，一般情况下，元素 $A(i,j)$ 存储在内存位置 `A(1+i-j,j)` 中，其中 $j = 1,\ldots,n$ 且 $i \in \lbrack j,\min(m,j + k)\rbrack$。此外，数组 `A` 中与带矩阵元素在概念上不对应的元素（右下角 $k \times k$ 三角形区域）不会被访问。

如果 `uplo == CUBLAS_FILL_MODE_UPPER`，则厄米特带矩阵 $A$ 按列存储，主对角线存储在第 `k + 1` 行，第一个超对角线存储在第 `k` 行（从第二个位置开始），第二个超对角线存储在第 `k-1` 行（从第三个位置开始），以此类推。因此，一般情况下，元素 $A(i,j)$ 存储在内存位置 `A(1+k+i-j,j)` 中，其中 $j = 1,\ldots,n$ 且 $i \in \lbrack\max(1,j - k),j\rbrack$。此外，数组 `A` 中与带矩阵元素在概念上不对应的元素（左上角 $k \times k$ 三角形区域）不会被访问。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS 库上下文的句柄。 |
| uplo |  | 输入 | 指示矩阵 A 的下三角或上三角部分是否被存储，的另一部分不被引用，且从已存储的元素中推断。 |
| n |  | 输入 | 矩阵 A 的行数和列数。 |
| k |  | 输入 | 矩阵 A 的次对角线和超对角线的数量。 |
| alpha | 主机或设备 | 输入 | 用于乘法的 <type> 标量。 |
| A | 设备 | 输入 | 维度为 lda x n 的 <type> 数组，其中 lda >= k + 1。对角线元素的虚部假定为零。 |
| lda |  | 输入 | 用于存储矩阵 A 的二维数组的主维度。 |
| x | 设备 | 输入 | 包含 n 个元素的 <type> 向量。 |
| incx |  | 输入 | x 中连续元素之间的步长。 |
| beta | 主机或设备 | 输入 | 用于乘法的 <type> 标量。如果 beta == 0，则不必是有效输入。 |
| y | 设备 | 输入/输出 | 包含 n 个元素的 <type> 向量。 |
| incy |  | 输入 | y 中连续元素之间的步长。 |

此函数返回的可能错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0 或 k < 0，或
如果 incx == 0 或 incy == 0，或
如果 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或
如果 lda < (1 + k)，或
如果 alpha 或 beta 为 NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数未能启动 GPU 执行 |

有关参考信息，请参阅 NETLIB 文档：


[chbmv()](http://www.netlib.org/blas/chbmv.f), [zhbmv()](http://www.netlib.org/blas/zhbmv.f)