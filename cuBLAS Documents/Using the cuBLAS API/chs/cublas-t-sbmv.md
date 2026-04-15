### 2.6.4. cublas<t>sbmv()

```c++
cublasStatus_t cublasSsbmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, int k, const float  *alpha,
                           const float  *A, int lda,
                           const float  *x, int incx,
                           const float  *beta, float *y, int incy)
// 执行单精度对称带状矩阵-向量乘法 y = alpha * A * x + beta * y

cublasStatus_t cublasDsbmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, int k, const double *alpha,
                           const double *A, int lda,
                           const double *x, int incx,
                           const double *beta, double *y, int incy)
// 执行双精度对称带状矩阵-向量乘法 y = alpha * A * x + beta * y
```

此函数支持64位整数接口。

此函数执行对称带状矩阵-向量乘法

$\textbf{y} = \alpha A\textbf{x} + \beta\textbf{y}$

其中，$A$是一个具有$k$条次对角线和超对角线的$n \times n$对称带状矩阵，$\mathbf{x}$和$\mathbf{y}$是向量，$\alpha$和$\beta$是标量。

如果 `uplo == CUBLAS_FILL_MODE_LOWER`，则对称带状矩阵$A$按列存储，矩阵的主对角线存储在第1行，第一个次对角线存储在第2行（从第一个位置开始），第二个次对角线存储在第3行（从第一个位置开始），以此类推。因此，通常情况下，元素$A(i,j)$存储在内存位置 `A(1+i-j,j)`，其中$j = 1,\ldots,n$ 且 $i \in \lbrack j,\min(m,j + k)\rbrack$。此外，数组`A`中在概念上不对应带状矩阵元素的元素（左下角$k \times k$三角形）不会被引用。

如果 `uplo == CUBLAS_FILL_MODE_UPPER`，则对称带状矩阵$A$按列存储，矩阵的主对角线存储在第`k + 1`行，第一个超对角线存储在第`k`行（从第二个位置开始），第二个超对角线存储在第`k-1`行（从第三个位置开始），以此类推。因此，通常情况下，元素$A(i,j)$存储在内存位置 `A(1+k+i-j,j)`，其中$j = 1,\ldots,n$ 且 $i \in \lbrack\max(1,j - k),j\rbrack$。此外，数组`A`中在概念上不对应带状矩阵元素的元素（右上角$k \times k$三角形）不会被引用。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS库上下文的句柄。 |
| uplo |  | 输入 | 指示是否存储矩阵A的下部分或上部分，另一个对称部分不被引用，并从存储的元素中推断。 |
| n |  | 输入 | 矩阵A的行数和列数。 |
| k |  | 输入 | 矩阵A的次对角线和超对角线数量。 |
| alpha | 主机或设备 | 输入 | 用于乘法的<type>标量。 |
| A | 设备 | 输入 | 维度为lda x n的<type>数组，其中lda >= k + 1。 |
| lda |  | 输入 | 用于存储矩阵A的二维数组的主维度。 |
| x | 设备 | 输入 | 具有n个元素的<type>向量。 |
| incx |  | 输入 | x连续元素之间的步长。 |
| beta | 主机或设备 | 输入 | 用于乘法的<type>标量。如果beta == 0，则y不必是有效输入。 |
| y | 设备 | 输入/输出 | 具有n个元素的<type>向量。 |
| incy |  | 输入 | y连续元素之间的步长。 |

此函数返回的可能错误值及其含义如下所列。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果n < 0或k < 0，或如果incx == 0或incy == 0，或如果uplo不是CUBLAS_FILL_MODE_LOWER和CUBLAS_FILL_MODE_UPPER之一，或如果alpha或beta为NULL，或如果lda < (1 + k) |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在GPU上启动失败 |

有关参考资料，请参阅NETLIB文档：

[ssbmv()](http://www.netlib.org/blas/ssbmv.f), [dsbmv()](http://www.netlib.org/blas/dsbmv.f)