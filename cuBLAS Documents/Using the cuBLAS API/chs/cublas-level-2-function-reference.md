## 2.6. cuBLAS Level-2 函数参考指南

本章描述了执行矩阵-向量运算的 Level-2 基本线性代数子程序（BLAS2）函数。

### 2.6.1. cublas<t>gbmv()

```c++

cublasStatus_t cublasSgbmv(cublasHandle_t handle, cublasOperation_t trans,
                           int m, int n, int kl, int ku,
                           const float           *alpha,
                           const float           *A, int lda,
                           const float           *x, int incx,
                           const float           *beta,
                           float           *y, int incy)
cublasStatus_t cublasDgbmv(cublasHandle_t handle, cublasOperation_t trans,
                           int m, int n, int kl, int ku,
                           const double          *alpha,
                           const double          *A, int lda,
                           const double          *x, int incx,
                           const double          *beta,
                           double          *y, int incy)
cublasStatus_t cublasCgbmv(cublasHandle_t handle, cublasOperation_t trans,
                           int m, int n, int kl, int ku,
                           const cuComplex       *alpha,
                           const cuComplex       *A, int lda,
                           const cuComplex       *x, int incx,
                           const cuComplex       *beta,
                           cuComplex       *y, int incy)
cublasStatus_t cublasZgbmv(cublasHandle_t handle, cublasOperation_t trans,
                           int m, int n, int kl, int ku,
                           const cuDoubleComplex *alpha,
                           const cuDoubleComplex *A, int lda,
                           const cuDoubleComplex *x, int incx,
                           const cuDoubleComplex *beta,
                           cuDoubleComplex *y, int incy)


```

此函数支持 64 位整数接口。

此函数执行带状矩阵-向量乘法

$\mathbf{y} = \alpha\text{ op}(A)\mathbf{x} + \beta\mathbf{y}$

其中 $A$ 是一个具有 $kl$ 条次对角线和 $ku$ 条超对角线的带状矩阵，$\mathbf{x}$ 和 $\mathbf{y}$ 是向量，$\alpha$ 和 $\beta$ 是标量。此外，对于矩阵 $A$

$\text{ op}(A) = \begin{cases}
A & \text{ if trans == CUBLAS\_OP\_N} \\
A^{T} & \text{ if trans == CUBLAS\_OP\_T} \\
A^{H} & \text{ if trans == CUBLAS\_OP\_C} \\
\end{cases}$

带状矩阵 $A$ 按列存储，主对角线存储在第 $ku + 1$ 行（从第一个位置开始），第一条超对角线存储在第 $ku$ 行（从第二个位置开始），第一条次对角线存储在第 $ku + 2$ 行（从第一个位置开始），以此类推。因此，一般情况下，元素 $A\left( {i,j} \right)$ 存储在内存位置 `A(ku+1+i-j,j)` 中，其中 $j = 1,\ldots,n$ 且 $i \in \left\lbrack {\max\left( {1,j - ku} \right),\min\left( {m,j + kl} \right)} \right\rbrack$。此外，数组 $A$ 中在概念上不对应带状矩阵元素的元素（左上角的 $ku \times ku$ 和右下角的 $kl \times kl$ 三角形区域）不会被访问。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS 库上下文的句柄。 |
| trans |  | input | 操作 op(A)，为非转置或（共轭）转置。 |
| m |  | input | 矩阵 A 的行数。 |
| n |  | input | 矩阵 A 的列数。 |
| kl |  | input | 矩阵 A 的次对角线数。 |
| ku |  | input | 矩阵 A 的超对角线数。 |
| alpha | host 或 device | input | 用于乘法的 <type> 标量。 |
| A | device | input | 维度为 lda x n 的 <type> 数组，其中 lda >= kl + ku + 1。 |
| lda |  | input | 用于存储矩阵 A 的二维数组的主维度。 |
| x | device | input | 当 trans == CUBLAS_OP_N 时为 n 个元素的 <type> 向量，否则为 m 个元素。 |
| incx |  | input | x 中连续元素之间的步长。 |
| beta | host 或 device | input | 用于乘法的 <type> 标量。如果 beta == 0，则 y 不必是有效输入。 |
| y | device | in/out | 当 trans == CUBLAS_OP_N 时为 m 个元素的 <type> 向量，否则为 n 个元素。 |
| incy |  | input | y 中连续元素之间的步长。 |

此函数可能返回的错误值及其含义如下所列。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 m < 0、n < 0、kl < 0 或 ku < 0，或<br>如果 lda < (kl + ku + 1)，或<br>如果 incx == 0 或 incy == 0，或<br>如果 trans 不是 CUBLAS_OP_N、CUBLAS_OP_T、CUBLAS_OP_C 之一，或<br>如果 alpha 或 beta 为 NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |

有关参考文献，请参阅 NETLIB 文档：

[sgbmv()](http://www.netlib.org/blas/sgbmv.f)、[dgbmv()](http://www.netlib.org/blas/dgbmv.f)、[cgbmv()](http://www.netlib.org/blas/cgbmv.f)、[zgbmv()](http://www.netlib.org/blas/zgbmv.f)

### 2.6.2. cublas<t>gemv()

```c++

cublasStatus_t cublasSgemv(cublasHandle_t handle, cublasOperation_t trans,
                           int m, int n,
                           const float           *alpha,
                           const float           *A, int lda,
                           const float           *x, int incx,
                           const float           *beta,
                           float           *y, int incy)
cublasStatus_t cublasDgemv(cublasHandle_t handle, cublasOperation_t trans,
                           int m, int n,
                           const double          *alpha,
                           const double          *A, int lda,
                           const double          *x, int incx,
                           const double          *beta,
                           double          *y, int incy)
cublasStatus_t cublasCgemv(cublasHandle_t handle, cublasOperation_t trans,
                           int m, int n,
                           const cuComplex       *alpha,
                           const cuComplex       *A, int lda,
                           const cuComplex       *x, int incx,
                           const cuComplex       *beta,
                           cuComplex       *y, int incy)
cublasStatus_t cublasZgemv(cublasHandle_t handle, cublasOperation_t trans,
                           int m, int n,
                           const cuDoubleComplex *alpha,
                           const cuDoubleComplex *A, int lda,
                           const cuDoubleComplex *x, int incx,
                           const cuDoubleComplex *beta,
                           cuDoubleComplex *y, int incy)


```

此函数支持 64 位整数接口。

此函数执行矩阵-向量乘法

$\textbf{y} = \alpha\text{ op}(A)\textbf{x} + \beta\textbf{y}$

其中 $A$ 是一个以列优先格式存储的 $m \times n$ 矩阵，$\mathbf{x}$ 和 $\mathbf{y}$ 是向量，$\alpha$ 和 $\beta$ 是标量。此外，对于矩阵 $A$

$\text{ op}(A) = \begin{cases}
A & \text{ if trans == CUBLAS\_OP\_N} \\
A^{T} & \text{ if trans == CUBLAS\_OP\_T} \\
A^{H} & \text{ if trans == CUBLAS\_OP\_C} \\
\end{cases}$

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS 库上下文的句柄。 |
| trans |  | input | 操作 op(A)，为非转置或（共轭）转置。 |
| m |  | input | 矩阵 A 的行数。 |
| n |  | input | 矩阵 A 的列数。 |
| alpha | host 或 device | input | 用于乘法的 <type> 标量。 |
| A | device | input | 维度为 lda x n 的 <type> 数组，其中 lda >= max(1, m)。进入时，数组 A 的前 m 行 n 列必须包含系数矩阵。退出时不变。 |
| lda |  | input | 用于存储矩阵 A 的二维数组的主维度。lda 必须至少为 max(1, m)。 |
| x | device | input | 当 trans == CUBLAS_OP_N 时至少包含 (1 + (n - 1) * abs(incx)) 个元素的 <type> 向量，否则至少包含 (1 + (m - 1) * abs(incx)) 个元素。 |
| incx |  | input | x 中连续元素之间的步长。 |
| beta | host 或 device | input | 用于乘法的 <type> 标量。如果 beta == 0，则 y 不必是有效输入。 |
| y | device | in/out | 当 trans == CUBLAS_OP_N 时至少包含 (1 + (m - 1) * abs(incy)) 个元素的 <type> 向量，否则至少包含 (1 + (n - 1) * abs(incy)) 个元素。 |
| incy |  | input | y 中连续元素之间的步长 |

此函数可能返回的错误值及其含义如下所列。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 m < 0 或 n < 0，或 incx == 0 或 incy == 0 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |

有关参考文献，请参阅 NETLIB 文档：

[sgemv()](http://www.netlib.org/blas/sgemv.f)、[dgemv()](http://www.netlib.org/blas/dgemv.f)、[cgemv()](http://www.netlib.org/blas/cgemv.f)、[zgemv()](http://www.netlib.org/blas/zgemv.f)

### 2.6.3. cublas<t>ger()

```c++

cublasStatus_t  cublasSger(cublasHandle_t handle, int m, int n,
                           const float           *alpha,
                           const float           *x, int incx,
                           const float           *y, int incy,
                           float           *A, int lda)
cublasStatus_t  cublasDger(cublasHandle_t handle, int m, int n,
                           const double          *alpha,
                           const double          *x, int incx,
                           const double          *y, int incy,
                           double          *A, int lda)
cublasStatus_t cublasCgeru(cublasHandle_t handle, int m, int n,
                           const cuComplex       *alpha,
                           const cuComplex       *x, int incx,
                           const cuComplex       *y, int incy,
                           cuComplex       *A, int lda)
cublasStatus_t cublasCgerc(cublasHandle_t handle, int m, int n,
                           const cuComplex       *alpha,
                           const cuComplex       *x, int incx,
                           const cuComplex       *y, int incy,
                           cuComplex       *A, int lda)
cublasStatus_t cublasZgeru(cublasHandle_t handle, int m, int n,
                           const cuDoubleComplex *alpha,
                           const cuDoubleComplex *x, int incx,
                           const cuDoubleComplex *y, int incy,
                           cuDoubleComplex *A, int lda)
cublasStatus_t cublasZgerc(cublasHandle_t handle, int m, int n,
                           const cuDoubleComplex *alpha,
                           const cuDoubleComplex *x, int incx,
                           const cuDoubleComplex *y, int incy,
                           cuDoubleComplex *A, int lda)


```

此函数支持 64 位整数接口。

此函数执行秩-1 更新

$A = \begin{cases}
{\alpha\mathbf{xy}^{T} + A} & \text{if ger(),geru() is called} \\
{\alpha\mathbf{xy}^{H} + A} & \text{if gerc() is called} \\
\end{cases}$

其中 $A$ 是一个以列优先格式存储的 $m \times n$ 矩阵，$\mathbf{x}$ 和 $\mathbf{y}$ 是向量，$\alpha$ 是标量。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS 库上下文的句柄。 |
| m |  | input | 矩阵 A 的行数。 |
| n |  | input | 矩阵 A 的列数。 |
| alpha | host 或 device | input | 用于乘法的 <type> 标量。 |
| x | device | input | 具有 m 个元素的 <type> 向量。 |
| incx |  | input | x 中连续元素之间的步长。 |
| y | device | input | 具有 n 个元素的 <type> 向量。 |
| incy |  | input | y 中连续元素之间的步长。 |
| A | device | in/out | 维度为 lda x n 的 <type> 数组，其中 lda >= max(1, m)。 |
| lda |  | input | 用于存储矩阵 A 的二维数组的主维度。 |

此函数可能返回的错误值及其含义如下所列。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 m < 0 或 n < 0，或<br>如果 incx == 0 或 incy == 0，或<br>如果 alpha 为 NULL，或<br>如果 lda < max(1, m) |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |

有关参考文献，请参阅 NETLIB 文档：

[sger()](http://www.netlib.org/blas/sger.f)、[dger()](http://www.netlib.org/blas/dger.f)、[cgeru()](http://www.netlib.org/blas/cgeru.f)、[cgerc()](http://www.netlib.org/blas/cgerc.f)、[zgeru()](http://www.netlib.org/blas/zgeru.f)、[zgerc()](http://www.netlib.org/blas/zgerc.f)

### 2.6.4. cublas<t>sbmv()

```c++

cublasStatus_t cublasSsbmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, int k, const float  *alpha,
                           const float  *A, int lda,
                           const float  *x, int incx,
                           const float  *beta, float *y, int incy)
cublasStatus_t cublasDsbmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, int k, const double *alpha,
                           const double *A, int lda,
                           const double *x, int incx,
                           const double *beta, double *y, int incy)


```

此函数支持 64 位整数接口。

此函数执行对称带状矩阵-向量乘法

$\textbf{y} = \alpha A\textbf{x} + \beta\textbf{y}$

其中 $A$ 是一个具有 $k$ 条次对角线和超对角线的 $n \times n$ 对称带状矩阵，$\mathbf{x}$ 和 $\mathbf{y}$ 是向量，$\alpha$ 和 $\beta$ 是标量。

如果 `uplo == CUBLAS_FILL_MODE_LOWER`，则对称带状矩阵 $A$ 按列存储，矩阵的主对角线存储在第 1 行，第一个次对角线存储在第 2 行（从第一个位置开始），第二个次对角线存储在第 3 行（从第一个位置开始），以此类推。因此，一般情况下，元素 $A(i,j)$ 存储在内存位置 `A(1+i-j,j)` 中，其中 $j = 1,\ldots,n$ 且 $i \in \lbrack j,\min(m,j + k)\rbrack$。此外，数组 `A` 中在概念上不对应带状矩阵元素的元素（右下角的 $k \times k$ 三角形区域）不会被访问。

如果 `uplo == CUBLAS_FILL_MODE_UPPER`，则对称带状矩阵 $A$ 按列存储，矩阵的主对角线存储在第 `k + 1` 行，第一个超对角线存储在第 `k` 行（从第二个位置开始），第二个超对角线存储在第 `k-1` 行（从第三个位置开始），以此类推。因此，一般情况下，元素 $A(i,j)$ 存储在内存位置 `A(1+k+i-j,j)` 中，其中 $j = 1,\ldots,n$ 且 $i \in \lbrack\max(1,j - k),j\rbrack$。此外，数组 `A` 中在概念上不对应带状矩阵元素的元素（左上角的 $k \times k$ 三角形区域）不会被访问。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS 库上下文的句柄。 |
| uplo |  | input | 指示存储矩阵 A 的下三角还是上三角部分，另一对称部分不会被访问，但可从存储的元素推断。 |
| n |  | input | 矩阵 A 的行数和列数。 |
| k |  | input | 矩阵 A 的次对角线和超对角线数。 |
| alpha | host 或 device | input | 用于乘法的 <type> 标量。 |
| A | device | input | 维度为 lda x n 的 <type> 数组，其中 lda >= k + 1。 |
| lda |  | input | 用于存储矩阵 A 的二维数组的主维度。 |
| x | device | input | 具有 n 个元素的 <type> 向量。 |
| incx |  | input | x 中连续元素之间的步长。 |
| beta | host 或 device | input | 用于乘法的 <type> 标量。如果 beta == 0，则 y 不必是有效输入。 |
| y | device | in/out | 具有 n 个元素的 <type> 向量。 |
| incy |  | input | y 中连续元素之间的步长。 |

此函数可能返回的错误值及其含义如下所列。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0 或 k < 0，或<br>如果 incx == 0 或 incy == 0，或<br>如果 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或<br>如果 alpha 或 beta 为 NULL，或<br>如果 lda < (1 + k) |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |

有关参考文献，请参阅 NETLIB 文档：

[ssbmv()](http://www.netlib.org/blas/ssbmv.f)、[dsbmv()](http://www.netlib.org/blas/dsbmv.f)

### 2.6.5. cublas<t>spmv()

```c++

cublasStatus_t cublasSspmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const float  *alpha, const float  *AP,
                           const float  *x, int incx, const float  *beta,
                           float  *y, int incy)
cublasStatus_t cublasDspmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const double *alpha, const double *AP,
                           const double *x, int incx, const double *beta,
                           double *y, int incy)


```

此函数支持 64 位整数接口。

此函数执行对称压缩矩阵-向量乘法

$\textbf{y} = \alpha A\textbf{x} + \beta\textbf{y}$

其中 $A$ 是一个以压缩格式存储的 $n \times n$ 对称矩阵，$\mathbf{x}$ 和 $\mathbf{y}$ 是向量，$\alpha$ 和 $\beta$ 是标量。

如果 `uplo == CUBLAS_FILL_MODE_LOWER`，则对称矩阵 $A$ 下三角部分的元素按列打包在一起，中间无间隙，因此元素 $A(i,j)$ 存储在内存位置 `AP[i+((2*n-j+1)*j)/2]` 中，其中 $j = 1,\ldots,n$ 且 $i \geq j$。因此，压缩格式仅需 $\frac{n(n + 1)}{2}$ 个元素进行存储。

如果 `uplo == CUBLAS_FILL_MODE_UPPER`，则对称矩阵 $A$ 上三角部分的元素按列打包在一起，中间无间隙，因此元素 $A(i,j)$ 存储在内存位置 `AP[i+(j*(j+1))/2]` 中，其中 $j = 1,\ldots,n$ 且 $i \leq j$。因此，压缩格式仅需 $\frac{n(n + 1)}{2}$ 个元素进行存储。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS 库上下文的句柄。 |
| uplo |  | input | 指示存储矩阵 \(A\) 的下三角还是上三角部分，另一对称部分不会被访问，但可从存储的元素推断。 |
| n |  | input | 矩阵 \(A\) 的行数和列数。 |
| alpha | host 或 device | input | 用于乘法的 <type> 标量。 |
| AP | device | input | 以压缩格式存储 \(A\) 的 <type> 数组。 |
| x | device | input | 具有 n 个元素的 <type> 向量。 |
| incx |  | input | x 中连续元素之间的步长。 |
| beta | host 或 device | input | 用于乘法的 <type> 标量。如果 beta == 0，则 y 不必是有效输入。 |
| y | device | input | 具有 n 个元素的 <type> 向量。 |
| incy |  | input | y 中连续元素之间的步长。 |

此函数可能返回的错误值及其含义如下所列。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0，或<br>如果 incx == 0 或 incy == 0，或<br>如果 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或<br>如果 alpha 或 beta 为 NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |

有关参考文献，请参阅 NETLIB 文档：

[sspmv()](http://www.netlib.org/blas/sspmv.f)、[dspmv()](http://www.netlib.org/blas/dspmv.f)

### 2.6.6. cublas<t>spr()

```c++

cublasStatus_t cublasSspr(cublasHandle_t handle, cublasFillMode_t uplo,
                          int n, const float  *alpha,
                          const float  *x, int incx, float  *AP)
cublasStatus_t cublasDspr(cublasHandle_t handle, cublasFillMode_t uplo,
                          int n, const double *alpha,
                          const double *x, int incx, double *AP)


```

此函数支持 64 位整数接口。

此函数执行压缩对称秩-1 更新

$A = \alpha\textbf{x}\textbf{x}^{T} + A$

其中 $A$ 是一个以压缩格式存储的 $n \times n$ 对称矩阵，$\mathbf{x}$ 是向量，$\alpha$ 是标量。

如果 `uplo == CUBLAS_FILL_MODE_LOWER`，则对称矩阵 $A$ 下三角部分的元素按列打包在一起，中间无间隙，因此元素 $A(i,j)$ 存储在内存位置 `AP[i+((2*n-j+1)*j)/2]` 中，其中 $j = 1,\ldots,n$ 且 $i \geq j$。因此，压缩格式仅需 $\frac{n(n + 1)}{2}$ 个元素进行存储。

如果 `uplo == CUBLAS_FILL_MODE_UPPER`，则对称矩阵 $A$ 上三角部分的元素按列打包在一起，中间无间隙，因此元素 $A(i,j)$ 存储在内存位置 `AP[i+(j*(j+1))/2]` 中，其中 $j = 1,\ldots,n$ 且 $i \leq j$。因此，压缩格式仅需 $\frac{n(n + 1)}{2}$ 个元素进行存储。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS 库上下文的句柄。 |
| uplo |  | input | 指示存储矩阵 \(A\) 的下三角还是上三角部分，另一对称部分不会被访问，但可从存储的元素推断。 |
| n |  | input | 矩阵 \(A\) 的行数和列数。 |
| alpha | host 或 device | input | 用于乘法的 <type> 标量。 |
| x | device | input | 具有 n 个元素的 <type> 向量。 |
| incx |  | input | x 中连续元素之间的步长。 |
| AP | device | in/out | 以压缩格式存储 \(A\) 的 <type> 数组。 |

此函数可能返回的错误值及其含义如下所列。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0，或<br>如果 incx == 0，或<br>如果 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或<br>如果 alpha 为 NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |

有关参考文献，请参阅 NETLIB 文档：

[sspr()](http://www.netlib.org/blas/sspr.f)、[dspr()](http://www.netlib.org/blas/dspr.f)

### 2.6.7. cublas<t>spr2()

```c++

cublasStatus_t cublasSspr2(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const float  *alpha,
                           const float  *x, int incx,
                           const float  *y, int incy, float  *AP)
cublasStatus_t cublasDspr2(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const double *alpha,
                           const double *x, int incx,
                           const double *y, int incy, double *AP)


```

此函数支持 64 位整数接口。

此函数执行压缩对称秩-2 更新

$A = \alpha\left( {\textbf{x}\textbf{y}^{T} + \textbf{y}\textbf{x}^{T}} \right) + A$

其中 $A$ 是一个以压缩格式存储的 $n \times n$ 对称矩阵，$\mathbf{x}$ 是向量，$\alpha$ 是标量。

如果 `uplo == CUBLAS_FILL_MODE_LOWER`，则对称矩阵 $A$ 下三角部分的元素按列打包在一起，中间无间隙，因此元素 $A(i,j)$ 存储在内存位置 `AP[i+((2*n-j+1)*j)/2]` 中，其中 $j = 1,\ldots,n$ 且 $i \geq j$。因此，压缩格式仅需 $\frac{n(n + 1)}{2}$ 个元素进行存储。

如果 `uplo == CUBLAS_FILL_MODE_UPPER`，则对称矩阵 $A$ 上三角部分的元素按列打包在一起，中间无间隙，因此元素 $A(i,j)$ 存储在内存位置 `AP[i+(j*(j+1))/2]` 中，其中 $j = 1,\ldots,n$ 且 $i \leq j$。因此，压缩格式仅需 $\frac{n(n + 1)}{2}$ 个元素进行存储。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS 库上下文的句柄。 |
| uplo |  | input | 指示存储矩阵 \(A\) 的下三角还是上三角部分，另一对称部分不会被访问，但可从存储的元素推断。 |
| n |  | input | 矩阵 \(A\) 的行数和列数。 |
| alpha | host 或 device | input | 用于乘法的 <type> 标量。 |
| x | device | input | 具有 n 个元素的 <type> 向量。 |
| incx |  | input | x 中连续元素之间的步长。 |
| y | device | input | 具有 n 个元素的 <type> 向量。 |
| incy |  | input | y 中连续元素之间的步长。 |
| AP | device | in/out | 以压缩格式存储 \(A\) 的 <type> 数组。 |

此函数可能返回的错误值及其含义如下所列。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0，或<br>如果 incx == 0 或 incy == 0，或<br>如果 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或<br>如果 alpha 为 NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |

有关参考文献，请参阅 NETLIB 文档：

[sspr2()](http://www.netlib.org/blas/sspr2.f)、[dspr2()](http://www.netlib.org/blas/dspr2.f)

### 2.6.8. cublas<t>symv()

```c++

cublasStatus_t cublasSsymv(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const float           *alpha,
                           const float           *A, int lda,
                           const float           *x, int incx, const float           *beta,
                           float           *y, int incy)
cublasStatus_t cublasDsymv(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const double          *alpha,
                           const double          *A, int lda,
                           const double          *x, int incx, const double          *beta,
                           double          *y, int incy)
cublasStatus_t cublasCsymv(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const cuComplex       *alpha, /* host or device pointer */
                           const cuComplex       *A, int lda,
                           const cuComplex       *x, int incx, const cuComplex       *beta,
                           cuComplex       *y, int incy)
cublasStatus_t cublasZsymv(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const cuDoubleComplex *alpha,
                           const cuDoubleComplex *A, int lda,
                           const cuDoubleComplex *x, int incx, const cuDoubleComplex *beta,
                           cuDoubleComplex *y, int incy)


```

此函数支持 64 位整数接口。

此函数执行对称矩阵-向量乘法。

$\textbf{y} = \alpha A\textbf{x} + \beta\textbf{y}$
其中 $A$ 是一个以列优先格式存储的 $n \times n$ 对称矩阵，$\mathbf{x}$ 和 $\mathbf{y}$ 是向量，$\alpha$ 和 $\beta$ 是标量。

此函数有一个使用原子操作的替代快速实现，可以通过 cublasSetAtomicsMode() 启用。

有关原子操作使用的更多详细信息，请参阅 cublasSetAtomicsMode() 部分。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS 库上下文的句柄。 |
| uplo |  | input | 指示存储矩阵的下三角还是上三角部分，另一对称部分不会被访问，但可从存储的元素推断。 |
| n |  | input | 矩阵 A 的行数和列数。 |
| alpha | host 或 device | input | 用于乘法的 <type> 标量。 |
| A | device | input | 维度为 lda x n 的 <type> 数组，其中 lda >= max(1, n)。 |
| lda |  | input | 用于存储矩阵 A 的二维数组的主维度。 |
| x | device | input | 具有 n 个元素的 <type> 向量。 |
| incx |  | input | x 中连续元素之间的步长。 |
| beta | host 或 device | input | 用于乘法的 <type> 标量。如果 beta == 0，则 y 不必是有效输入。 |
| y | device | in/out | 具有 n 个元素的 <type> 向量。 |
| incy |  | input | y 中连续元素之间的步长。 |

此函数可能返回的错误值及其含义如下所列。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0，或<br>如果 incx == 0 或 incy == 0，或<br>如果 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或<br>如果 lda < n |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |

有关参考文献，请参阅 NETLIB 文档：

[ssymv()](http://www.netlib.org/blas/ssymv.f)、[dsymv()](http://www.netlib.org/blas/dsymv.f)

### 2.6.9. cublas<t>syr()

```c++

cublasStatus_t cublasSsyr(cublasHandle_t handle,



```c++

cublasStatus_t cublasSgbmv(cublasHandle_t handle, cublasOperation_t trans,
                           int m, int n, int kl, int ku,
                           const float           *alpha,
                           const float           *A, int lda,
                           const float           *x, int incx,
                           const float           *beta,
                           float           *y, int incy)
cublasStatus_t cublasDgbmv(cublasHandle_t handle, cublasOperation_t trans,
                           int m, int n, int kl, int ku,
                           const double          *alpha,
                           const double          *A, int lda,
                           const double          *x, int incx,
                           const double          *beta,
                           double          *y, int incy)
cublasStatus_t cublasCgbmv(cublasHandle_t handle, cublasOperation_t trans,
                           int m, int n, int kl, int ku,
                           const cuComplex       *alpha,
                           const cuComplex       *A, int lda,
                           const cuComplex       *x, int incx,
                           const cuComplex       *beta,
                           cuComplex       *y, int incy)
cublasStatus_t cublasZgbmv(cublasHandle_t handle, cublasOperation_t trans,
                           int m, int n, int kl, int ku,
                           const cuDoubleComplex *alpha,
                           const cuDoubleComplex *A, int lda,
                           const cuDoubleComplex *x, int incx,
                           const cuDoubleComplex *beta,
                           cuDoubleComplex *y, int incy)


```


This function supports the 64-bit Integer Interface.


This function performs the banded matrix-vector multiplication


$\mathbf{y} = \alpha\text{ op}(A)\mathbf{x} + \beta\mathbf{y}$


where $A$ is a banded matrix with $kl$ subdiagonals and $ku$ superdiagonals, $\mathbf{x}$ and $\mathbf{y}$ are vectors, and $\alpha$ and $\beta$ are scalars. Also, for matrix $A$


$\text{ op}(A) = \begin{cases}
A & \text{ if trans == CUBLAS\_OP\_N} \\
A^{T} & \text{ if trans == CUBLAS\_OP\_T} \\
A^{H} & \text{ if trans == CUBLAS\_OP\_C} \\
\end{cases}$


The banded matrix $A$ is stored column by column, with the main diagonal stored in row $ku + 1$ (starting in first position), the first superdiagonal stored in row $ku$ (starting in second position), the first subdiagonal stored in row $ku + 2$ (starting in first position), etc. So that in general, the element $A\left( {i,j} \right)$ is stored in the memory location `A(ku+1+i-j,j)` for $j = 1,\ldots,n$ and $i \in \left\lbrack {\max\left( {1,j - ku} \right),\min\left( {m,j + kl} \right)} \right\rbrack$ . Also, the elements in the array $A$ that do not conceptually correspond to the elements in the banded matrix (the top left $ku \times ku$ and bottom right $kl \times kl$ triangles) are not referenced.


| Param. | Memory | In/out | Meaning |
| --- | --- | --- | --- |
| handle |  | input | Handle to the cuBLAS library context. |
| trans |  | input | Operation op(A) that is non- or (conj.) transpose. |
| m |  | input | Number of rows of matrix A. |
| n |  | input | Number of columns of matrix A. |
| kl |  | input | Number of subdiagonals of matrix A. |
| ku |  | input | Number of superdiagonals of matrix A. |
| alpha | host or device | input | <type> scalar used for multiplication. |
| A | device | input | <type> array of dimension lda x n with lda >= kl + ku + 1. |
| lda |  | input | Leading dimension of two-dimensional array used to store matrix A. |
| x | device | input | <type> vector with n elements if trans == CUBLAS_OP_N and m elements otherwise. |
| incx |  | input | Stride between consecutive elements of x. |
| beta | host or device | input | <type> scalar used for multiplication. If beta == 0 then y does not have to be a valid input. |
| y | device | in/out | <type> vector with m elements if trans == CUBLAS_OP_N and n elements otherwise. |
| incy |  | input | Stride between consecutive elements of y. |


The possible error values returned by this function and their meanings are listed below.


| Error Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | The operation completed successfully |
| CUBLAS_STATUS_NOT_INITIALIZED | The library was not initialized |
| CUBLAS_STATUS_INVALID_VALUE | If m < 0,  n < 0, kl < 0 or ku < 0, or
if lda < (kl + ku + 1), or
if incx == 0 or incy == 0, or
if trans is not one of CUBLAS_OP_N, CUBLAS_OP_T, CUBLAS_OP_C, or
if alpha or beta are NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | The function failed to launch on the GPU |


For references please refer to NETLIB documentation:


[sgbmv()](http://www.netlib.org/blas/sgbmv.f), [dgbmv()](http://www.netlib.org/blas/dgbmv.f), [cgbmv()](http://www.netlib.org/blas/cgbmv.f), [zgbmv()](http://www.netlib.org/blas/zgbmv.f)






```c++

cublasStatus_t cublasSgemv(cublasHandle_t handle, cublasOperation_t trans,
                           int m, int n,
                           const float           *alpha,
                           const float           *A, int lda,
                           const float           *x, int incx,
                           const float           *beta,
                           float           *y, int incy)
// 单精度实数矩阵向量乘法
cublasStatus_t cublasDgemv(cublasHandle_t handle, cublasOperation_t trans,
                           int m, int n,
                           const double          *alpha,
                           const double          *A, int lda,
                           const double          *x, int incx,
                           const double          *beta,
                           double          *y, int incy)
// 双精度实数矩阵向量乘法
cublasStatus_t cublasCgemv(cublasHandle_t handle, cublasOperation_t trans,
                           int m, int n,
                           const cuComplex       *alpha,
                           const cuComplex       *A, int lda,
                           const cuComplex       *x, int incx,
                           const cuComplex       *beta,
                           cuComplex       *y, int incy)
// 单精度复数矩阵向量乘法
cublasStatus_t cublasZgemv(cublasHandle_t handle, cublasOperation_t trans,
                           int m, int n,
                           const cuDoubleComplex *alpha,
                           const cuDoubleComplex *A, int lda,
                           const cuDoubleComplex *x, int incx,
                           const cuDoubleComplex *beta,
                           cuDoubleComplex *y, int incy)
// 双精度复数矩阵向量乘法


```


此函数支持64位整数接口。


此函数执行矩阵向量乘法


$\textbf{y} = \alpha\text{ op}(A)\textbf{x} + \beta\textbf{y}$


其中 $A$ 是以列主序格式存储的 $m \times n$ 矩阵，$\mathbf{x}$ 和 $\mathbf{y}$ 是向量，$\alpha$ 和 $\beta$ 是标量。此外，对于矩阵 $A$


$\text{ op}(A) = \begin{cases}
A & \text{ if trans == CUBLAS\_OP\_N} \\
A^{T} & \text{ if trans == CUBLAS\_OP\_T} \\
A^{H} & \text{ if trans == CUBLAS\_OP\_C} \\
\end{cases}$


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS库上下文的句柄。 |
| trans |  | 输入 | 运算 op(A)，可为非转置或（共轭）转置。 |
| m |  | 输入 | 矩阵 A 的行数。 |
| n |  | 输入 | 矩阵 A 的列数。 |
| alpha | 主机或设备 | 输入 | 用于乘法的 <type> 标量。 |
| A | 设备 | 输入 | 维度为 lda x n 的 <type> 数组，lda >= max(1, m)。在调用之前，数组 A 的前 m 行 n 列部分必须包含系数矩阵。退出时保持不变。 |
| lda |  | 输入 | 用于存储矩阵 A 的二维数组的主维。lda 至少为 max(1, m)。 |
| x | 设备 | 输入 | <type> 向量，当 trans == CUBLAS_OP_N 时至少包含 (1 + (n - 1) * abs(incx)) 个元素，否则至少包含 (1 + (m - 1) * abs(incx)) 个元素。 |
| incx |  | 输入 | x 中连续元素之间的步长。 |
| beta | 主机或设备 | 输入 | 用于乘法的 <type> 标量。如果 beta == 0，则 y 不必是有效的输入。 |
| y | 设备 | 输入/输出 | <type> 向量，当 trans == CUBLAS_OP_N 时至少包含 (1 + (m - 1) * abs(incy)) 个元素，否则至少包含 (1 + (n - 1) * abs(incy)) 个元素。 |
| incy |  | 输入 | y 中连续元素之间的步长。 |


此函数可能返回的错误值及其含义如下所述。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 参数 m < 0 或 n < 0，或 incx == 0 或 incy == 0 |
| CUBLAS_STATUS_EXECUTION_FAILED | 该函数在GPU上启动失败 |


有关参考资料，请参阅 NETLIB 文档：


[sgemv()](http://www.netlib.org/blas/sgemv.f), [dgemv()](http://www.netlib.org/blas/dgemv.f), [cgemv()](http://www.netlib.org/blas/cgemv.f), [zgemv()](http://www.netlib.org/blas/zgemv.f)

```c++

cublasStatus_t cublasSgemvBatched(cublasHandle_t handle, cublasOperation_t trans,
                                  int m, int n,
                                  const float           *alpha,
                                  const float           *const Aarray[], int lda,
                                  const float           *const xarray[], int incx,
                                  const float           *beta,
                                  float           *const yarray[], int incy,
                                  int batchCount)
// 单精度实数批处理矩阵-向量乘法
cublasStatus_t cublasDgemvBatched(cublasHandle_t handle, cublasOperation_t trans,
                                  int m, int n,
                                  const double          *alpha,
                                  const double          *const Aarray[], int lda,
                                  const double          *const xarray[], int incx,
                                  const double          *beta,
                                  double          *const yarray[], int incy,
                                  int batchCount)
// 双精度实数批处理矩阵-向量乘法
cublasStatus_t cublasCgemvBatched(cublasHandle_t handle, cublasOperation_t trans,
                                  int m, int n,
                                  const cuComplex       *alpha,
                                  const cuComplex       *const Aarray[], int lda,
                                  const cuComplex       *const xarray[], int incx,
                                  const cuComplex       *beta,
                                  cuComplex       *const yarray[], int incy,
                                  int batchCount)
// 单精度复数批处理矩阵-向量乘法
cublasStatus_t cublasZgemvBatched(cublasHandle_t handle, cublasOperation_t trans,
                                  int m, int n,
                                  const cuDoubleComplex *alpha,
                                  const cuDoubleComplex *const Aarray[], int lda,
                                  const cuDoubleComplex *const xarray[], int incx,
                                  const cuDoubleComplex *beta,
                                  cuDoubleComplex *const yarray[], int incy,
                                  int batchCount)
// 双精度复数批处理矩阵-向量乘法

##if defined(__cplusplus)
cublasStatus_t cublasHSHgemvBatched(cublasHandle_t handle, cublasOperation_t trans,
                                    int m, int n,
                                    const float           *alpha,
                                    const __half          *const Aarray[], int lda,
                                    const __half          *const xarray[], int incx,
                                    const float           *beta,
                                    __half                *const yarray[], int incy,
                                    int batchCount)
// 半精度输入输出批处理矩阵-向量乘法
cublasStatus_t cublasHSSgemvBatched(cublasHandle_t handle, cublasOperation_t trans,
                                    int m, int n,
                                    const float           *alpha,
                                    const __half          *const Aarray[], int lda,
                                    const __half          *const xarray[], int incx,
                                    const float           *beta,
                                    float                 *const yarray[], int incy,
                                    int batchCount)
// 半精度输入单精度输出批处理矩阵-向量乘法
cublasStatus_t cublasTSTgemvBatched(cublasHandle_t handle, cublasOperation_t trans,
                                    int m, int n,
                                    const float           *alpha,
                                    const __nv_bfloat16   *const Aarray[], int lda,
                                    const __nv_bfloat16   *const xarray[], int incx,
                                    const float           *beta,
                                    __nv_bfloat16         *const yarray[], int incy,
                                    int batchCount)
// BF16输入输出批处理矩阵-向量乘法
cublasStatus_t cublasTSSgemvBatched(cublasHandle_t handle, cublasOperation_t trans,
                                    int m, int n,
                                    const float           *alpha,
                                    const __nv_bfloat16   *const Aarray[], int lda,
                                    const __nv_bfloat16   *const xarray[], int incx,
                                    const float           *beta,
                                    float                 *const yarray[], int incy,
                                    int batchCount)
// BF16输入单精度输出批处理矩阵-向量乘法
##endif


```

此函数支持64位整数接口。

此函数执行一批矩阵和向量的矩阵-向量乘法运算。该批次被认为是"均匀的"，即所有实例具有相同的维度(m, n)、主维度(lda)、增量(incx, incy)和转置(trans)，分别对应各自的A矩阵、x和y向量。批次中每个实例的输入矩阵和向量以及输出向量的地址从调用者传递给该函数的指针数组中读取。

$\textbf{y}\lbrack i\rbrack = \alpha\text{op}(A\lbrack i\rbrack)\textbf{x}\lbrack i\rbrack + \beta\textbf{y}\lbrack i\rbrack,\text{ for i} \in \lbrack 0,batchCount - 1\rbrack$

其中 $\alpha$ 和 $\beta$ 是标量，$A$ 是指向矩阵 $A\lbrack i\rbrack$ 的指针数组，以列优先格式存储，维度为 $m \times n$ ，而 $\textbf{x}$ 和 $\textbf{y}$ 是指向向量的指针数组。同样，对于矩阵 $A\lbrack i\rbrack$ ：

$\text{op}(A\lbrack i\rbrack) = \left\{ \begin{matrix}
{A\lbrack i\rbrack} & {\text{if }\textsf{trans == CUBLAS\_OP\_N}} \\
{A\lbrack i\rbrack}^{T} & {\text{if }\textsf{trans == CUBLAS\_OP\_T}} \\
{A\lbrack i\rbrack}^{H} & {\text{if }\textsf{trans == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$

> **注意**

注意
\(\textbf{y}\lbrack i\rbrack\) 向量不得重叠，即各个gemv运算必须能够独立计算；否则将导致未定义行为。

在某些问题规模下，在不同的CUDA流中多次调用cublas<t>gemv()可能比使用此API更有优势。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS库上下文的句柄。 |
| trans |  | 输入 | 运算op(A[i])，即非转置或(共轭)转置。 |
| m |  | 输入 | 矩阵A[i]的行数。 |
| n |  | 输入 | 矩阵A[i]的列数。 |
| alpha | 主机或设备 | 输入 | 用于乘法的<type>标量。 |
| Aarray | 设备 | 输入 | 指向<type>数组的指针数组，每个数组维度为lda x n，其中lda >= max(1, m)。
所有指针必须满足特定的对齐条件。请参阅下文了解更多详情。 |
| lda |  | 输入 | 用于存储每个矩阵A[i]的二维数组的主维度。 |
| xarray | 设备 | 输入 | 指向<type>数组的指针数组，每个维度为n（如果trans == CUBLAS_OP_N）或m（否则）。
所有指针必须满足特定的对齐条件。请参阅下文了解更多详情。 |
| incx |  | 输入 | 每个一维数组x[i]的步长。 |
| beta | 主机或设备 | 输入 | 用于乘法的<type>标量。如果beta == 0，则y不必是有效输入。 |
| yarray | 设备 | 输入/输出 | 指向<type>数组的指针数组。如果trans == CUBLAS_OP_N，其维度为m；否则为n。向量y[i]不应重叠；否则将导致未定义行为。
所有指针必须满足特定的对齐条件。请参阅下文了解更多详情。 |
| incy |  | 输入 | 每个一维数组y[i]的步长。 |
| batchCount |  | 输入 | Aarray、xarray和yarray中包含的指针数量。 |

如果数学模式在使用cublasSgemvBatched()时启用了快速数学模式，则放置在GPU内存中的指针（而非指针数组）必须正确对齐以避免未对齐内存访问错误。理想情况下，所有指针至少对齐到16字节。否则，建议它们满足以下规则：

- 如果k % 4 == 0，则确保intptr_t(ptr) % 16 == 0

此函数可能返回的错误值及其含义如下所列。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | m < 0, n < 0 或 batchCount < 0 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在GPU上启动 |



```c++

cublasStatus_t cublasSgemvStridedBatched(cublasHandle_t handle,
                                         cublasOperation_t trans,
                                         int m, int n,
                                         const float           *alpha,
                                         const float           *A, int lda,
                                         long long int         strideA,
                                         const float           *x, int incx,
                                         long long int         stridex,
                                         const float           *beta,
                                         float                 *y, int incy,
                                         long long int         stridey,
                                         int batchCount)
cublasStatus_t cublasDgemvStridedBatched(cublasHandle_t handle,
                                         cublasOperation_t trans,
                                         int m, int n,
                                         const double          *alpha,
                                         const double          *A, int lda,
                                         long long int         strideA,
                                         const double          *x, int incx,
                                         long long int         stridex,
                                         const double          *beta,
                                         double                *y, int incy,
                                         long long int         stridey,
                                         int batchCount)
cublasStatus_t cublasCgemvStridedBatched(cublasHandle_t handle,
                                         cublasOperation_t trans,
                                         int m, int n,
                                         const cuComplex       *alpha,
                                         const cuComplex       *A, int lda,
                                         long long int         strideA,
                                         const cuComplex       *x, int incx,
                                         long long int         stridex,
                                         const cuComplex       *beta,
                                         cuComplex             *y, int incy,
                                         long long int         stridey,
                                         int batchCount)
cublasStatus_t cublasZgemvStridedBatched(cublasHandle_t handle,
                                         cublasOperation_t trans,
                                         int m, int n,
                                         const cuDoubleComplex *alpha,
                                         const cuDoubleComplex *A, int lda,
                                         long long int         strideA,
                                         const cuDoubleComplex *x, int incx,
                                         long long int         stridex,
                                         const cuDoubleComplex *beta,
                                         cuDoubleComplex       *y, int incy,
                                         long long int         stridey,
                                         int batchCount)
cublasStatus_t cublasHSHgemvStridedBatched(cublasHandle_t handle,
                                           cublasOperation_t trans,
                                           int m, int n,
                                           const float           *alpha,
                                           const __half          *A, int lda,
                                           long long int         strideA,
                                           const __half          *x, int incx,
                                           long long int         stridex,
                                           const float           *beta,
                                           __half                *y, int incy,
                                           long long int         stridey,
                                           int batchCount)
cublasStatus_t cublasHSSgemvStridedBatched(cublasHandle_t handle,
                                           cublasOperation_t trans,
                                           int m, int n,
                                           const float           *alpha,
                                           const __half          *A, int lda,
                                           long long int         strideA,
                                           const __half          *x, int incx,
                                           long long int         stridex,
                                           const float           *beta,
                                           float                 *y, int incy,
                                           long long int         stridey,
                                           int batchCount)
cublasStatus_t cublasTSTgemvStridedBatched(cublasHandle_t handle,
                                           cublasOperation_t trans,
                                           int m, int n,
                                           const float           *alpha,
                                           const __nv_bfloat16   *A, int lda,
                                           long long int         strideA,
                                           const __nv_bfloat16   *x, int incx,
                                           long long int         stridex,
                                           const float           *beta,
                                           __nv_bfloat16         *y, int incy,
                                           long long int         stridey,
                                           int batchCount)
cublasStatus_t cublasTSSgemvStridedBatched(cublasHandle_t handle,
                                           cublasOperation_t trans,
                                           int m, int n,
                                           const float           *alpha,
                                           const __nv_bfloat16   *A, int lda,
                                           long long int         strideA,
                                           const __nv_bfloat16   *x, int incx,
                                           long long int         stridex,
                                           const float           *beta,
                                           float                 *y, int incy,
                                           long long int         stridey,
                                           int batchCount)


```


This function supports the 64-bit Integer Interface.


This function performs the matrix-vector multiplication of a batch of matrices and vectors. The batch is considered to be “uniform”, i.e. all instances have the same dimensions (m, n), leading dimension (lda), increments (incx, incy) and transposition (trans) for their respective A matrix, x and y vectors. Input matrix A and vector x, and output vector y for each instance of the batch are located at fixed offsets in number of elements from their locations in the previous instance. Pointers to A matrix, x and y vectors for the first instance are passed to the function by the user along with offsets in number of elements - strideA, stridex and stridey that determine the locations of input matrices and vectors, and output vectors in future instances.


$\textbf{y} + i*{stridey} = \alpha\text{op}(A + i*{strideA})(\textbf{x} + i*{stridex}) + \beta(\textbf{y} + i*{stridey}),\text{ for i } \in \lbrack 0,batchCount - 1\rbrack$


where $\alpha$ and $\beta$ are scalars, and $A$ is an array of pointers to matrix stored in column-major format with dimension $A\lbrack i\rbrack$ $m \times n$ , and $\textbf{x}$ and $\textbf{y}$ are arrays of pointers to vectors. Also, for matrix $A\lbrack i\rbrack$


$\text{op}(A\lbrack i\rbrack) = \left\{ \begin{matrix}
{A\lbrack i\rbrack} & {\text{if }\textsf{trans == CUBLAS\_OP\_N}} \\
{A\lbrack i\rbrack}^{T} & {\text{if }\textsf{trans == CUBLAS\_OP\_T}} \\
{A\lbrack i\rbrack}^{H} & {\text{if }\textsf{trans == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$


> **Note**

Note
\(\textbf{y}\lbrack i\rbrack\) matrices must not overlap, i.e. the individual gemv operations must be computable independently; otherwise, undefined behavior is expected.


On certain problem sizes, it might be advantageous to make multiple calls to cublas<t>gemv() in different CUDA streams, rather than use this API.


> **Note**

Note
In the table below, we use A[i], x[i], y[i] as notation for A matrix, and x and y vectors in the ith instance of the batch, implicitly assuming they are respectively offsets in number of elements strideA, stridex, stridey away from A[i-1], x[i-1], y[i-1]. The unit for the offset is number of elements and must not be zero .


| Param. | Memory | In/out | Meaning |
| --- | --- | --- | --- |
| handle |  | input | Handle to the cuBLAS library context. |
| trans |  | input | Operation op(A[i]) that is non- or (conj.) transpose. |
| m |  | input | Number of rows of matrix A[i]. |
| n |  | input | Number of columns of matrix A[i]. |
| alpha | host or device | input | <type> scalar used for multiplication. |
| A | device | input | <type>* pointer to the A matrix corresponding to the first instance of the batch, with dimensions lda x n with lda >= max(1, m). |
| lda |  | input | Leading dimension of two-dimensional array used to store each matrix A[i]. |
| strideA |  | input | Value of type long long int that gives the offset in number of elements between A[i] and A[i+1] |
| x | device | input | <type>* pointer to the x vector corresponding to the first instance of the batch, with each dimension n if trans == CUBLAS_OP_N and m otherwise. |
| incx |  | input | Stride of each one-dimensional array x[i]. |
| stridex |  | input | Value of type long long int that gives the offset in number of elements between x[i] and x[i+1] |
| beta | host or device | input | <type> scalar used for multiplication. If beta == 0, y does not have to be a valid input. |
| y | device | in/out | <type>* pointer to the y vector corresponding to the first instance of the batch, with each dimension m if trans == CUBLAS_OP_N and n otherwise. Vectors y[i] should not overlap; otherwise, undefined behavior is expected. |
| incy |  | input | Stride of each one-dimensional array y[i]. |
| stridey |  | input | Value of type long long int that gives the offset in number of elements between y[i] and y[i+1] |
| batchCount |  | input | Number of GEMVs to perform in the batch. |


The possible error values returned by this function and their meanings are listed below.


| Error Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | The operation completed successfully |
| CUBLAS_STATUS_NOT_INITIALIZED | The library was not initialized |
| CUBLAS_STATUS_INVALID_VALUE | m < 0, n < 0, or batchCount < 0 |
| CUBLAS_STATUS_EXECUTION_FAILED | The function failed to launch on the GPU |




```c++

cublasStatus_t  cublasSger(cublasHandle_t handle, int m, int n,
                           const float           *alpha,
                           const float           *x, int incx,
                           const float           *y, int incy,
                           float           *A, int lda)
cublasStatus_t  cublasDger(cublasHandle_t handle, int m, int n,
                           const double          *alpha,
                           const double          *x, int incx,
                           const double          *y, int incy,
                           double          *A, int lda)
cublasStatus_t cublasCgeru(cublasHandle_t handle, int m, int n,
                           const cuComplex       *alpha,
                           const cuComplex       *x, int incx,
                           const cuComplex       *y, int incy,
                           cuComplex       *A, int lda)
cublasStatus_t cublasCgerc(cublasHandle_t handle, int m, int n,
                           const cuComplex       *alpha,
                           const cuComplex       *x, int incx,
                           const cuComplex       *y, int incy,
                           cuComplex       *A, int lda)
cublasStatus_t cublasZgeru(cublasHandle_t handle, int m, int n,
                           const cuDoubleComplex *alpha,
                           const cuDoubleComplex *x, int incx,
                           const cuDoubleComplex *y, int incy,
                           cuDoubleComplex *A, int lda)
cublasStatus_t cublasZgerc(cublasHandle_t handle, int m, int n,
                           const cuDoubleComplex *alpha,
                           const cuDoubleComplex *x, int incx,
                           const cuDoubleComplex *y, int incy,
                           cuDoubleComplex *A, int lda)


```

此函数支持64位整数接口。

此函数执行秩-1更新

$A = \begin{cases}
{\alpha\mathbf{xy}^{T} + A} & \text{if ger(),geru() is called} \\
{\alpha\mathbf{xy}^{H} + A} & \text{if gerc() is called} \\
\end{cases}$

其中，$A$是以列优先格式存储的$m \times n$矩阵，$\mathbf{x}$和$\mathbf{y}$是向量，$\alpha$是标量。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS库上下文的句柄。 |
| m |  | input | 矩阵A的行数。 |
| n |  | input | 矩阵A的列数。 |
| alpha | 主机或设备 | input | 用于乘法的<type>标量。 |
| x | 设备 | input | 包含m个元素的<type>向量。 |
| incx |  | input | x中连续元素之间的步长。 |
| y | 设备 | input | 包含n个元素的<type>向量。 |
| incy |  | input | y中连续元素之间的步长。 |
| A | 设备 | in/out | 维度为lda x n的<type>数组，其中lda >= max(1, m)。 |
| lda |  | input | 用于存储矩阵A的二维数组的主维度。 |


此函数返回的可能错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果m < 0或n < 0，或 |
| 如果incx == 0或incy == 0，或 |
| 如果alpha为NULL，或 |
| 如果lda < max(1, m) |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在GPU上启动失败 |


参考资料请参阅NETLIB文档：


[sger()](http://www.netlib.org/blas/sger.f)、[dger()](http://www.netlib.org/blas/dger.f)、[cgeru()](http://www.netlib.org/blas/cgeru.f)、[cgerc()](http://www.netlib.org/blas/cgerc.f)、[zgeru()](http://www.netlib.org/blas/zgeru.f)、[zgerc()](http://www.netlib.org/blas/zgerc.f)

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

```c++

cublasStatus_t cublasChemv(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const cuComplex       *alpha,
                           const cuComplex       *A, int lda,
                           const cuComplex       *x, int incx,
                           const cuComplex       *beta,
                           cuComplex       *y, int incy)
cublasStatus_t cublasZhemv(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const cuDoubleComplex *alpha,
                           const cuDoubleComplex *A, int lda,
                           const cuDoubleComplex *x, int incx,
                           const cuDoubleComplex *beta,
                           cuDoubleComplex *y, int incy)


```

此函数支持 64 位整数接口。

此函数执行厄米特矩阵向量乘法运算：

$\textbf{y} = \alpha A\textbf{x} + \beta\textbf{y}$

其中，$A$ 是一个以低端或高端模式存储的 $n \times n$ 厄米特矩阵，$\mathbf{x}$ 和 $\mathbf{y}$ 是向量，$\alpha$ 和 $\beta$ 是标量。

此函数有一个使用原子操作的替代快速实现，可以通过以下方式启用：

请参阅关于原子操作使用详情的相关章节。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS 库上下文的句柄。 |
| uplo |  | 输入 | 指定矩阵 A 的下三角或上三角部分是否存储，另一半厄米特部分未引用，由存储的元素推断。 |
| n |  | 输入 | 矩阵 A 的行数和列数。 |
| alpha | 主机或设备 | 输入 | 用于乘法的 <type> 标量。 |
| A | 设备 | 输入 | 维度为 lda x n 的 <type> 数组，lda >= max(1, n)。对角元素的虚部假定为零。 |
| lda |  | 输入 | 用于存储矩阵 A 的二维数组的主维度。 |
| x | 设备 | 输入 | 包含 n 个元素的 <type> 向量。 |
| incx |  | 输入 | x 中连续元素之间的步幅。 |
| beta | 主机或设备 | 输入 | 用于乘法的 <type> 标量。如果 beta == 0，则 y 不必是有效的输入。 |
| y | 设备 | 输入/输出 | 包含 n 个元素的 <type> 向量。 |
| incy |  | 输入 | y 中连续元素之间的步幅。 |

此函数返回的可能错误值及其含义如下所列。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0，或
如果 incx == 0 或 incy == 0，或
如果 uplo != CUBLAS_FILL_MODE_LOWER 且 uplo != CUBLAS_FILL_MODE_UPPER，或
如果 lda < n |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在 GPU 上启动失败 |

有关参考资料，请参阅 NETLIB 文档：

[chemv()](http://www.netlib.org/blas/chemv.f), [zhemv()](http://www.netlib.org/blas/zhemv.f)



```c++

cublasStatus_t cublasCher(cublasHandle_t handle, cublasFillMode_t uplo,
                          int n, const float  *alpha,
                          const cuComplex       *x, int incx,
                          cuComplex       *A, int lda)
cublasStatus_t cublasZher(cublasHandle_t handle, cublasFillMode_t uplo,
                          int n, const double *alpha,
                          const cuDoubleComplex *x, int incx,
                          cuDoubleComplex *A, int lda)


```


This function supports the 64-bit Integer Interface.


This function performs the Hermitian rank-1 update


$A = \alpha\textbf{x}\textbf{x}^{H} + A$


where $A$ is a $n \times n$ Hermitian matrix stored in column-major format, $\mathbf{x}$ is a vector, and $\alpha$ is a scalar.


| Param. | Memory | In/out | Meaning |
| --- | --- | --- | --- |
| handle |  | input | Handle to the cuBLAS library context. |
| uplo |  | input | Indicates if matrix A lower or upper part is stored, the other Hermitian part is not referenced and is inferred from the stored elements. |
| n |  | input | Number of rows and columns of matrix A. |
| alpha | host or device | input | <type> scalar used for multiplication. |
| x | device | input | <type> vector with n elements. |
| incx |  | input | Stride between consecutive elements of x. |
| A | device | in/out | <type> array of dimensions lda x n, with lda >= max(1, n). The imaginary parts of the diagonal elements are assumed and set to zero. |
| lda |  | input | Leading dimension of two-dimensional array used to store matrix A. |


The possible error values returned by this function and their meanings are listed below.


| Error Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | The operation completed successfully |
| CUBLAS_STATUS_NOT_INITIALIZED | The library was not initialized |
| CUBLAS_STATUS_INVALID_VALUE | If n < 0, or
if incx == 0, or
if uplo is not one of CUBLAS_FILL_MODE_LOWER and CUBLAS_FILL_MODE_UPPER, or
if lda < max(1, n), or
if alpha is NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | The function failed to launch on the GPU |


For references please refer to NETLIB documentation:


[cher()](http://www.netlib.org/blas/cher.f), [zher()](http://www.netlib.org/blas/zher.f)






```c++

cublasStatus_t cublasCher2(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const cuComplex       *alpha,
                           const cuComplex       *x, int incx,
                           const cuComplex       *y, int incy,
                           cuComplex       *A, int lda)
cublasStatus_t cublasZher2(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const cuDoubleComplex *alpha,
                           const cuDoubleComplex *x, int incx,
                           const cuDoubleComplex *y, int incy,
                           cuDoubleComplex *A, int lda)


```


This function supports the 64-bit Integer Interface.


This function performs the Hermitian rank-2 update


$A = \alpha\textbf{x}\textbf{y}^{H} + \overset{ˉ}{\alpha}\textbf{y}\textbf{x}^{H} + A$


where $A$ is a $n \times n$ Hermitian matrix stored in column-major format, $\mathbf{x}$ and $\mathbf{y}$ are vectors, and $\alpha$ is a scalar.


| Param. | Memory | In/out | Meaning |
| --- | --- | --- | --- |
| handle |  | input | Handle to the cuBLAS library context. |
| uplo |  | input | Indicates if matrix A lower or upper part is stored, the other Hermitian part is not referenced and is inferred from the stored elements. |
| n |  | input | Number of rows and columns of matrix A. |
| alpha | host or device | input | <type> scalar used for multiplication. |
| x | device | input | <type> vector with n elements. |
| incx |  | input | Stride between consecutive elements of x. |
| y | device | input | <type> vector with n elements. |
| incy |  | input | Stride between consecutive elements of y. |
| A | device | in/out | <type> array of dimension lda x n with lda >= max(1, n). The imaginary parts of the diagonal elements are assumed and set to zero. |
| lda |  | input | Leading dimension of two-dimensional array used to store matrix A. |


The possible error values returned by this function and their meanings are listed below.


| Error Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | The operation completed successfully |
| CUBLAS_STATUS_NOT_INITIALIZED | The library was not initialized |
| CUBLAS_STATUS_INVALID_VALUE | If n < 0, or
if incx == 0, or
if uplo is not one of CUBLAS_FILL_MODE_LOWER and CUBLAS_FILL_MODE_UPPER, or
if lda < max(1, n), or
if alpha is NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | The function failed to launch on the GPU |


For references please refer to NETLIB documentation:


[cher2()](http://www.netlib.org/blas/cher2.f), [zher2()](http://www.netlib.org/blas/zher2.f)






```c++

cublasStatus_t cublasChpmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const cuComplex       *alpha,
                           const cuComplex       *AP,
                           const cuComplex       *x, int incx,
                           const cuComplex       *beta,
                           cuComplex       *y, int incy)
cublasStatus_t cublasZhpmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const cuDoubleComplex *alpha,
                           const cuDoubleComplex *AP,
                           const cuDoubleComplex *x, int incx,
                           const cuDoubleComplex *beta,
                           cuDoubleComplex *y, int incy)


```


此函数支持64位整数接口。


此函数执行Hermitian压缩矩阵向量乘法


$\textbf{y} = \alpha A\textbf{x} + \beta\textbf{y}$


其中 $A$ 是一个以压缩格式存储的 $n \times n$ Hermitian矩阵，$\mathbf{x}$ 和 $\mathbf{y}$ 是向量，$\alpha$ 和 $\beta$ 是标量。


如果 `uplo == CUBLAS_FILL_MODE_LOWER`，则 Hermitian 矩阵 $A$ 下三角部分的元素按列紧凑存储，无间隙，使得元素 $A(i,j)$ 存储在内存位置 `AP[i+((2*n-j+1)*j)/2]` 中，其中 $j = 1,\ldots,n$ 且 $i \geq j$。因此，压缩格式仅需要 $\frac{n(n + 1)}{2}$ 个元素进行存储。


如果 `uplo == CUBLAS_FILL_MODE_UPPER`，则 Hermitian 矩阵 $A$ 上三角部分的元素按列紧凑存储，无间隙，使得元素 $A(i,j)$ 存储在内存位置 `AP[i+(j*(j+1))/2]` 中，其中 $j = 1,\ldots,n$ 且 $i \leq j$。因此，压缩格式仅需要 $\frac{n(n + 1)}{2}$ 个元素进行存储。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS库上下文的句柄。 |
| uplo |  | input | 指示矩阵A的下三角或上三角部分是否被存储，另一半Hermitian部分未引用且从已存储的元素推断。 |
| n |  | input | 矩阵A的行数和列数。 |
| alpha | host或device | input | 用于乘法的<type>标量。 |
| AP | device | input | 以压缩格式存储 $A$ 的<type>数组。对角线元素的虚部假定为零。 |
| x | device | input | 包含n个元素的<type>向量。 |
| incx |  | input | x中连续元素之间的步长。 |
| beta | host或device | input | 用于乘法的<type>标量。如果beta == 0，则y不必是有效输入。 |
| y | device | in/out | 包含n个元素的<type>向量。 |
| incy |  | input | y中连续元素之间的步长。 |


此函数返回的可能错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0，或
如果 incx == 0 或 incy == 0，或
如果 uplo != CUBLAS_FILL_MODE_LOWER 且 uplo != CUBLAS_FILL_MODE_UPPER，或
如果 alpha 或 beta 为 NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在GPU上启动 |


参考文献请参阅NETLIB文档：


[chpmv()](http://www.netlib.org/blas/chpmv.f), [zhpmv()](http://www.netlib.org/blas/zhpmv.f)



```c++

cublasStatus_t cublasChpr(cublasHandle_t handle, cublasFillMode_t uplo,
                          int n, const float *alpha,
                          const cuComplex       *x, int incx,
                          cuComplex       *AP)
cublasStatus_t cublasZhpr(cublasHandle_t handle, cublasFillMode_t uplo,
                          int n, const double *alpha,
                          const cuDoubleComplex *x, int incx,
                          cuDoubleComplex *AP)


```


此函数支持64位整数接口。


此函数执行压缩Hermitian秩1更新


$A = \alpha\textbf{x}\textbf{x}^{H} + A$


其中 $A$ 是以压缩格式存储的 $n \times n$ Hermitian矩阵，$\mathbf{x}$ 是一个向量，$\alpha$ 是一个标量。


如果 `uplo == CUBLAS_FILL_MODE_LOWER`，则Hermitian矩阵 $A$ 下三角部分的元素按列无间隙地打包在一起，使得元素 $A(i,j)$ 存储在内存位置 `AP[i+((2*n-j+1)*j)/2]` 中，其中 $j = 1,\ldots,n$ 且 $i \geq j$。因此，压缩格式仅需要 $\frac{n(n + 1)}{2}$ 个元素进行存储。


如果 `uplo == CUBLAS_FILL_MODE_UPPER`，则Hermitian矩阵 $A$ 上三角部分的元素按列无间隙地打包在一起，使得元素 $A(i,j)$ 存储在内存位置 `AP[i+(j*(j+1))/2]` 中，其中 $j = 1,\ldots,n$ 且 $i \leq j$。因此，压缩格式仅需要 $\frac{n(n + 1)}{2}$ 个元素进行存储。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS库上下文的句柄。 |
| uplo |  | input | 指示矩阵A的下三角或上三角部分是否被存储，另一个Hermitian部分未被引用，并从存储的元素中推断。 |
| n |  | input | 矩阵A的行数和列数。 |
| alpha | 主机或设备 | input | 用于乘法的<type>标量。 |
| x | 设备 | input | 包含n个元素的<type>向量。 |
| incx |  | input | x中连续元素之间的步长。 |
| AP | 设备 | 输入/输出 | 以压缩格式存储 $A$ 的<type>数组。对角元素的虚部被假设为零并设置为零。 |


此函数返回的可能错误值及其含义如下所述。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0，或
如果 incx == 0，或
如果 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或
如果 alpha 为 NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在GPU上启动 |


参考文献请参阅NETLIB文档：


[chpr()](http://www.netlib.org/blas/chpr.f), [zhpr()](http://www.netlib.org/blas/zhpr.f)



```c++

cublasStatus_t cublasChpr2(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const cuComplex       *alpha,
                           const cuComplex       *x, int incx,
                           const cuComplex       *y, int incy,
                           cuComplex       *AP)
cublasStatus_t cublasZhpr2(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const cuDoubleComplex *alpha,
                           const cuDoubleComplex *x, int incx,
                           const cuDoubleComplex *y, int incy,
                           cuDoubleComplex *AP)


```


此函数支持64位整数接口。


此函数执行压缩厄米特秩2更新


$A = \alpha\textbf{x}\textbf{y}^{H} + \overset{ˉ}{\alpha}\textbf{y}\textbf{x}^{H} + A$


其中 $A$ 是以压缩格式存储的 $n \times n$ 厄米特矩阵，$\mathbf{x}$ 和 $\mathbf{y}$ 是向量，$\alpha$ 是标量。


如果 `uplo == CUBLAS_FILL_MODE_LOWER`，则厄米特矩阵 $A$ 下三角部分的元素按列紧密打包，因此元素 $A(i,j)$ 存储在内存位置 `AP[i+((2*n-j+1)*j)/2]` 中，其中 $j = 1,\ldots,n$ 且 $i \geq j$。因此，压缩格式仅需要 $\frac{n(n + 1)}{2}$ 个元素进行存储。


如果 `uplo == CUBLAS_FILL_MODE_UPPER`，则厄米特矩阵 $A$ 上三角部分的元素按列紧密打包，因此元素 $A(i,j)$ 存储在内存位置 `AP[i+(j*(j+1))/2]` 中，其中 $j = 1,\ldots,n$ 且 $i \leq j$。因此，压缩格式仅需要 $\frac{n(n + 1)}{2}$ 个元素进行存储。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS库上下文的句柄。 |
| uplo |  | input | 指示是否存储矩阵A的下三角或上三角部分，其他厄米特部分未引用且从存储的元素推断。 |
| n |  | input | 矩阵A的行数和列数。 |
| alpha | 主机或设备 | input | 用于乘法的 <type> 标量。 |
| x | 设备 | input | 具有n个元素的 <type> 向量。 |
| incx |  | input | x中连续元素之间的步长。 |
| y | 设备 | input | 具有n个元素的 <type> 向量。 |
| incy |  | input | y中连续元素之间的步长。 |
| AP | 设备 | 输入/输出 | 以压缩格式存储 $A$ 的 <type> 数组。假定对角元素的虚部为零并将其设置为零。 |


此函数返回的可能错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0，或
如果 incx == 0，或
如果 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或
如果 alpha 为 NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在GPU上启动失败 |


有关参考信息，请参阅NETLIB文档：


chpr2, zhpr2

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



```c++

cublasStatus_t cublasSspmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const float  *alpha, const float  *AP,
                           const float  *x, int incx, const float  *beta,
                           float  *y, int incy)
cublasStatus_t cublasDspmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const double *alpha, const double *AP,
                           const double *x, int incx, const double *beta,
                           double *y, int incy)


```


此函数支持64位整数接口。


此函数执行对称压缩矩阵向量乘法


$\textbf{y} = \alpha A\textbf{x} + \beta\textbf{y}$


其中 $A$ 是一个以压缩格式存储的 $n \times n$ 对称矩阵，$\mathbf{x}$ 和 $\mathbf{y}$ 是向量，$\alpha$ 和 $\beta$ 是标量。


如果 `uplo == CUBLAS_FILL_MODE_LOWER`，则对称矩阵 $A$ 下三角部分的元素按列紧凑存储，无间隙，因此元素 $A(i,j)$ 存储在内存位置 `AP[i+((2*n-j+1)*j)/2]`，其中 $j = 1,\ldots,n$ 且 $i \geq j$。因此，压缩格式仅需 $\frac{n(n + 1)}{2}$ 个元素存储。


如果 `uplo == CUBLAS_FILL_MODE_UPPER`，则对称矩阵 $A$ 上三角部分的元素按列紧凑存储，无间隙，因此元素 $A(i,j)$ 存储在内存位置 `AP[i+(j*(j+1))/2]`，其中 $j = 1,\ldots,n$ 且 $i \leq j$。因此，压缩格式仅需 $\frac{n(n + 1)}{2}$ 个元素存储。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS 库上下文的句柄。 |
| uplo |  | 输入 | 指示矩阵 $A$ 的下三角或上三角部分是否被存储，另一个对称部分未被引用，且可从已存储的元素推断。 |
| n |  | 输入 | 矩阵 $A$ 的行数和列数。 |
| alpha | 主机或设备 | 输入 | 用于乘法的 <type> 标量。 |
| AP | 设备 | 输入 | 以压缩格式存储 $A$ 的 <type> 数组。 |
| x | 设备 | 输入 | 包含 n 个元素的 <type> 向量。 |
| incx |  | 输入 | x 中连续元素之间的步长。 |
| beta | 主机或设备 | 输入 | 用于乘法的 <type> 标量。如果 beta == 0，则 y 不必是有效输入。 |
| y | 设备 | 输入/输出 | 包含 n 个元素的 <type> 向量。 |
| incy |  | 输入 | y 中连续元素之间的步长。 |


此函数返回的可能错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0，或
如果 incx == 0 或 incy == 0，或
如果 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或
如果 alpha 或 beta 为 NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |


相关参考请参阅 NETLIB 文档：


[sspmv()](http://www.netlib.org/blas/sspmv.f)，[dspmv()](http://www.netlib.org/blas/dspmv.f)



```c++

cublasStatus_t cublasSspr(cublasHandle_t handle, cublasFillMode_t uplo,
                          int n, const float  *alpha,
                          const float  *x, int incx, float  *AP)
cublasStatus_t cublasDspr(cublasHandle_t handle, cublasFillMode_t uplo,
                          int n, const double *alpha,
                          const double *x, int incx, double *AP)


```


This function supports the 64-bit Integer Interface.


This function performs the packed symmetric rank-1 update


$A = \alpha\textbf{x}\textbf{x}^{T} + A$


where $A$ is a $n \times n$ symmetric matrix stored in packed format, $\mathbf{x}$ is a vector, and $\alpha$ is a scalar.


If `uplo == CUBLAS_FILL_MODE_LOWER` then the elements in the lower triangular part of the symmetric matrix $A$ are packed together column by column without gaps, so that the element $A(i,j)$ is stored in the memory location `AP[i+((2*n-j+1)*j)/2]` for $j = 1,\ldots,n$ and $i \geq j$ . Consequently, the packed format requires only $\frac{n(n + 1)}{2}$ elements for storage.


If `uplo == CUBLAS_FILL_MODE_UPPER` then the elements in the upper triangular part of the symmetric matrix $A$ are packed together column by column without gaps, so that the element $A(i,j)$ is stored in the memory location `AP[i+(j*(j+1))/2]` for $j = 1,\ldots,n$ and $i \leq j$ . Consequently, the packed format requires only $\frac{n(n + 1)}{2}$ elements for storage.


| Param. | Memory | In/out | Meaning |
| --- | --- | --- | --- |
| handle |  | input | Handle to the cuBLAS library context. |
| uplo |  | input | Indicates if matrix \(A\) lower or upper part is stored, the other symmetric part is not referenced and is inferred from the stored elements. |
| n |  | input | Number of rows and columns of matrix \(A\) . |
| alpha | host or device | input | <type> scalar used for multiplication. |
| x | device | input | <type> vector with n elements. |
| incx |  | input | Stride between consecutive elements of x. |
| AP | device | in/out | <type> array with \(A\) stored in packed format. |


The possible error values returned by this function and their meanings are listed below.


| Error Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | The operation completed successfully |
| CUBLAS_STATUS_NOT_INITIALIZED | The library was not initialized |
| CUBLAS_STATUS_INVALID_VALUE | If n < 0, or
if incx == 0, or
if uplo is not one of CUBLAS_FILL_MODE_LOWER and CUBLAS_FILL_MODE_UPPER, or
if alpha is NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | The function failed to launch on the GPU |


For references please refer to NETLIB documentation:


[sspr()](http://www.netlib.org/blas/sspr.f), [dspr()](http://www.netlib.org/blas/dspr.f)






```c++

cublasStatus_t cublasSspr2(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const float  *alpha,
                           const float  *x, int incx,
                           const float  *y, int incy, float  *AP)
cublasStatus_t cublasDspr2(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const double *alpha,
                           const double *x, int incx,
                           const double *y, int incy, double *AP)


```


此函数支持64位整数接口。


此函数执行压缩存储对称秩-2更新


$A = \alpha\left( {\textbf{x}\textbf{y}^{T} + \textbf{y}\textbf{x}^{T}} \right) + A$


其中 $A$ 是以压缩格式存储的 $n \times n$ 对称矩阵，$\mathbf{x}$ 是向量，$\alpha$ 是标量。


如果 `uplo == CUBLAS_FILL_MODE_LOWER`，则对称矩阵 $A$ 下三角部分的元素按列紧密排列（无间隙），使得元素 $A(i,j)$ 存储在内存位置 `AP[i+((2*n-j+1)*j)/2]` 中，其中 $j = 1,\ldots,n$ 且 $i \geq j$。因此，压缩格式仅需 $\frac{n(n + 1)}{2}$ 个元素进行存储。


如果 `uplo == CUBLAS_FILL_MODE_UPPER`，则对称矩阵 $A$ 上三角部分的元素按列紧密排列（无间隙），使得元素 $A(i,j)$ 存储在内存位置 `AP[i+(j*(j+1))/2]` 中，其中 $j = 1,\ldots,n$ 且 $i \leq j$。因此，压缩格式仅需 $\frac{n(n + 1)}{2}$ 个元素进行存储。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS 库上下文的句柄。 |
| uplo |  | 输入 | 指示矩阵 $A$ 的下三角或上三角部分是否存储，其他对称部分未被引用且根据存储的元素推断。 |
| n |  | 输入 | 矩阵 $A$ 的行数和列数。 |
| alpha | 主机或设备 | 输入 | 用于乘法的 <type> 标量。 |
| x | 设备 | 输入 | 包含 n 个元素的 <type> 向量。 |
| incx |  | 输入 | x 中连续元素之间的步长。 |
| y | 设备 | 输入 | 包含 n 个元素的 <type> 向量。 |
| incy |  | 输入 | y 中连续元素之间的步长。 |
| AP | 设备 | 输入/输出 | 以压缩格式存储 $A$ 的 <type> 数组。 |


此函数可能返回的错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0，或
如果 incx == 0 或 incy == 0，或
如果 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或
如果 alpha 为 NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |


参考文献请参阅 NETLIB 文档：


[sspr2()](http://www.netlib.org/blas/sspr2.f), [dspr2()](http://www.netlib.org/blas/dspr2.f)



```c++

cublasStatus_t cublasSsymv(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const float           *alpha,
                           const float           *A, int lda,
                           const float           *x, int incx, const float           *beta,
                           float           *y, int incy)
cublasStatus_t cublasDsymv(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const double          *alpha,
                           const double          *A, int lda,
                           const double          *x, int incx, const double          *beta,
                           double          *y, int incy)
cublasStatus_t cublasCsymv(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const cuComplex       *alpha, /* 主机或设备指针 */
                           const cuComplex       *A, int lda,
                           const cuComplex       *x, int incx, const cuComplex       *beta,
                           cuComplex       *y, int incy)
cublasStatus_t cublasZsymv(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const cuDoubleComplex *alpha,
                           const cuDoubleComplex *A, int lda,
                           const cuDoubleComplex *x, int incx, const cuDoubleComplex *beta,
                           cuDoubleComplex *y, int incy)


```


此函数支持64位整数接口。


此函数执行对称矩阵-向量乘法运算。


$\textbf{y} = \alpha A\textbf{x} + \beta\textbf{y}$
其中 $A$ 是一个以低位或高位模式存储的 $n \times n$ 对称矩阵，$\mathbf{x}$ 和 $\mathbf{y}$ 是向量，$\alpha$ 和 $\beta$ 是标量。


此函数有一个使用原子操作的可选更快实现，可以通过 cublasSetAtomicsMode() 启用。


有关原子操作使用的更多详细信息，请参阅 cublasSetAtomicsMode() 函数部分。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS 库上下文的句柄。 |
| uplo |  | 输入 | 指示矩阵的下三角或上三角部分是否被存储，另一对称部分未被引用，且从存储的元素中推断。 |
| n |  | 输入 | 矩阵 A 的行数和列数。 |
| alpha | 主机或设备 | 输入 | 用于乘法的 <type> 标量。 |
| A | 设备 | 输入 | 维度为 lda x n 的 <type> 数组，其中 lda >= max(1, n)。 |
| lda |  | 输入 | 用于存储矩阵 A 的二维数组的主维度。 |
| x | 设备 | 输入 | 具有 n 个元素的 <type> 向量。 |
| incx |  | 输入 | x 中连续元素之间的步长。 |
| beta | 主机或设备 | 输入 | 用于乘法的 <type> 标量。如果 beta == 0，则 y 不必是有效输入。 |
| y | 设备 | 输入/输出 | 具有 n 个元素的 <type> 向量。 |
| incy |  | 输入 | y 中连续元素之间的步长。 |


此函数返回的可能错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0，或
如果 incx == 0 或 incy == 0，或
如果 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或
如果 lda < n。 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数未能在 GPU 上启动。 |


参考文献请参阅 NETLIB 文档：


[ssymv()](http://www.netlib.org/blas/ssymv.f), [dsymv()](http://www.netlib.org/blas/dsymv.f)

```c++
// 执行对称秩-1更新: A = αxx^T + A
cublasStatus_t cublasSsyr(cublasHandle_t handle, cublasFillMode_t uplo,
                          int n, const float           *alpha,
                          const float           *x, int incx, float           *A, int lda)
cublasStatus_t cublasDsyr(cublasHandle_t handle, cublasFillMode_t uplo,
                          int n, const double          *alpha,
                          const double          *x, int incx, double          *A, int lda)
cublasStatus_t cublasCsyr(cublasHandle_t handle, cublasFillMode_t uplo,
                          int n, const cuComplex       *alpha,
                          const cuComplex       *x, int incx, cuComplex       *A, int lda)
cublasStatus_t cublasZsyr(cublasHandle_t handle, cublasFillMode_t uplo,
                          int n, const cuDoubleComplex *alpha,
                          const cuDoubleComplex *x, int incx, cuDoubleComplex *A, int lda)
```

此函数支持64位整数接口。

此函数执行对称秩-1更新

$A = \alpha\textbf{x}\textbf{x}^{T} + A$

其中 $A$ 是一个以列优先格式存储的 $n \times n$ 对称矩阵，$\mathbf{x}$ 是一个向量，$\alpha$ 是一个标量。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS 库上下文的句柄。 |
| uplo |  | 输入 | 指定矩阵 A 的下三角或上三角部分是否被存储，另一对称部分未被引用，且可从已存储的元素推断得出。 |
| n |  | 输入 | 矩阵 A 的行数和列数。 |
| alpha | 主机或设备 | 输入 | 用于乘法的 `<type>` 标量。 |
| x | 设备 | 输入 | 包含 n 个元素的 `<type>` 向量。 |
| incx |  | 输入 | x 中连续元素之间的步长。 |
| A | 设备 | 输入/输出 | 维度为 lda × n 的 `<type>` 数组，lda >= max(1, n)。 |
| lda |  | 输入 | 用于存储矩阵 A 的二维数组的leading dimension。 |

此函数返回的可能错误值及其含义如下所示。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0，或 incx == 0，或 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或 lda < max(1, n)，或 alpha 为 NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |

有关参考资料，请参阅 NETLIB 文档：

[ssyr()](http://www.netlib.org/blas/ssyr.f), [dsyr()](http://www.netlib.org/blas/dsyr.f)

```c++
// 执行对称秩2更新
cublasStatus_t cublasSsyr2(cublasHandle_t handle, cublasFillMode_t uplo, int n,
                           const float           *alpha, const float           *x, int incx,
                           const float           *y, int incy, float           *A, int lda
cublasStatus_t cublasDsyr2(cublasHandle_t handle, cublasFillMode_t uplo, int n,
                           const double          *alpha, const double          *x, int incx,
                           const double          *y, int incy, double          *A, int lda
cublasStatus_t cublasCsyr2(cublasHandle_t handle, cublasFillMode_t uplo, int n,
                           const cuComplex       *alpha, const cuComplex       *x, int incx,
                           const cuComplex       *y, int incy, cuComplex       *A, int lda
cublasStatus_t cublasZsyr2(cublasHandle_t handle, cublasFillMode_t uplo, int n,
                           const cuDoubleComplex *alpha, const cuDoubleComplex *x, int incx,
                           const cuDoubleComplex *y, int incy, cuDoubleComplex *A, int lda
```

此函数支持64位整数接口。

此函数执行对称秩2更新

$A = \alpha\left( {\textbf{x}\textbf{y}^{T} + \textbf{y}\textbf{x}^{T}} \right) + A$

其中 $A$ 是一个以列主序格式存储的 $n \times n$ 对称矩阵，$\mathbf{x}$ 和 $\mathbf{y}$ 是向量，$\alpha$ 是标量。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS 库上下文的句柄。 |
| uplo |  | 输入 | 指示矩阵 A 的下三角或上三角部分是否存储，另一对称部分未引用且从存储的元素推断。 |
| n |  | 输入 | 矩阵 A 的行数和列数。 |
| alpha | 主机或设备 | 输入 | 用于乘法的 <type> 标量。 |
| x | 设备 | 输入 | 包含 n 个元素的 <type> 向量。 |
| incx |  | 输入 | x 中连续元素之间的步长。 |
| y | 设备 | 输入 | 包含 n 个元素的 <type> 向量。 |
| incy |  | 输入 | y 中连续元素之间的步长。 |
| A | 设备 | 输入/输出 | 维度为 lda × n 的 <type> 数组，lda >= max(1,n)。 |
| lda |  | 输入 | 用于存储矩阵 A 的二维数组的主维度。 |

此函数返回的可能错误值及其含义如下所列。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0，或
如果 incx == 0 或 incy == 0，或
如果 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或
如果 alpha 为 NULL，或
如果 lda < max(1, n) |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在 GPU 上启动失败 |

有关参考信息，请参阅 NETLIB 文档：

[ssyr2()](http://www.netlib.org/lapack/explore-html/db/d99/ssyr2_8f_source.html)、[dsyr2()](http://www.netlib.org/lapack/explore-html/de/d41/dsyr2_8f_source.html)



```c++

cublasStatus_t cublasStbmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, int k, const float           *A, int lda,
                           float           *x, int incx)
cublasStatus_t cublasDtbmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, int k, const double          *A, int lda,
                           double          *x, int incx)
cublasStatus_t cublasCtbmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, int k, const cuComplex       *A, int lda,
                           cuComplex       *x, int incx)
cublasStatus_t cublasZtbmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, int k, const cuDoubleComplex *A, int lda,
                           cuDoubleComplex *x, int incx)


```


This function supports the 64-bit Integer Interface.


This function performs the triangular banded matrix-vector multiplication


$\textbf{x} = \text{op}(A)\textbf{x}$


where $A$ is a triangular banded matrix, and $\mathbf{x}$ is a vector. Also, for matrix $A$


$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{trans == CUBLAS\_OP\_N}} \\
A^{T} & {\text{if }\textsf{trans == CUBLAS\_OP\_T}} \\
A^{H} & {\text{if }\textsf{trans == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$


If `uplo == CUBLAS_FILL_MODE_LOWER` then the triangular banded matrix $A$ is stored column by column, with the main diagonal of the matrix stored in row `1`, the first subdiagonal in row `2` (starting at first position), the second subdiagonal in row `3` (starting at first position), etc. So that in general, the element $A(i,j)$ is stored in the memory location `A(1+i-j,j)` for $j = 1,\ldots,n$ and $i \in \lbrack j,\min(m,j + k)\rbrack$ . Also, the elements in the array `A` that do not conceptually correspond to the elements in the banded matrix (the bottom right $k \times k$ triangle) are not referenced.


If `uplo == CUBLAS_FILL_MODE_UPPER` then the triangular banded matrix $A$ is stored column by column, with the main diagonal of the matrix stored in row `k + 1`, the first superdiagonal in row `k` (starting at second position), the second superdiagonal in row `k-1` (starting at third position), etc. So that in general, the element $A(i,j)$ is stored in the memory location `A(1+k+i-j,j)` for $j = 1,\ldots,n$ and $i \in \lbrack\max(1,j - k,j)\rbrack$ . Also, the elements in the array `A` that do not conceptually correspond to the elements in the banded matrix (the top left $k \times k$ triangle) are not referenced.


| Param. | Memory | In/out | Meaning |
| --- | --- | --- | --- |
| handle |  | input | Handle to the cuBLAS library context. |
| uplo |  | input | Indicates if matrix A lower or upper part is stored, the other part is not referenced and is inferred from the stored elements. |
| trans |  | input | Operation op(A) that is non- or (conj.) transpose. |
| diag |  | input | Indicates if the elements on the main diagonal of matrix A are unity and should not be accessed. |
| n |  | input | Number of rows and columns of matrix A. |
| k |  | input | Number of sub- and super-diagonals of matrix . |
| A | device | input | <type> array of dimension lda x n, with lda >= k + 1. |
| lda |  | input | Leading dimension of two-dimensional array used to store matrix A. |
| x | device | in/out | <type> vector with n elements. |
| incx |  | input | Stride between consecutive elements of x. |


The possible error values returned by this function and their meanings are listed below.


| Error Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | The operation completed successfully |
| CUBLAS_STATUS_NOT_INITIALIZED | The library was not initialized |
| CUBLAS_STATUS_INVALID_VALUE | If n < 0 or k < 0, or
if incx == 0, or
if trans is not one of CUBLAS_OP_N, CUBLAS_OP_T and CUBLAS_OP_C, or
if uplo is not one of CUBLAS_FILL_MODE_LOWER and CUBLAS_FILL_MODE_UPPER, or
if diag is not one of CUBLAS_DIAG_UNIT and CUBLAS_DIAG_NON_UNIT, or
if lda < (1 + k) |
| CUBLAS_STATUS_ALLOC_FAILED | The allocation of internal scratch memory failed |
| CUBLAS_STATUS_EXECUTION_FAILED | The function failed to launch on the GPU |


For references please refer to NETLIB documentation:


[stbmv()](http://www.netlib.org/blas/stbmv.f), [dtbmv()](http://www.netlib.org/blas/dtbmv.f), [ctbmv()](http://www.netlib.org/blas/ctbmv.f), [ztbmv()](http://www.netlib.org/blas/ztbmv.f)






```c++

cublasStatus_t cublasStbsv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, int k, const float           *A, int lda,
                           float           *x, int incx)
cublasStatus_t cublasDtbsv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, int k, const double          *A, int lda,
                           double          *x, int incx)
cublasStatus_t cublasCtbsv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, int k, const cuComplex       *A, int lda,
                           cuComplex       *x, int incx)
cublasStatus_t cublasZtbsv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, int k, const cuDoubleComplex *A, int lda,
                           cuDoubleComplex *x, int incx)


```


This function supports the 64-bit Integer Interface.


This function solves the triangular banded linear system with a single right-hand-side


$\text{op}(A)\textbf{x} = \textbf{b}$


where $A$ is a triangular banded matrix, and $\mathbf{x}$ and $\mathbf{b}$ are vectors. Also, for matrix $A$


$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{trans == CUBLAS\_OP\_N}} \\
A^{T} & {\text{if }\textsf{trans == CUBLAS\_OP\_T}} \\
A^{H} & {\text{if }\textsf{trans == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$


The solution $\mathbf{x}$ overwrites the right-hand-sides $\mathbf{b}$ on exit.


No test for singularity or near-singularity is included in this function.


If `uplo == CUBLAS_FILL_MODE_LOWER` then the triangular banded matrix $A$ is stored column by column, with the main diagonal of the matrix stored in row `1`, the first subdiagonal in row `2` (starting at first position), the second subdiagonal in row `3` (starting at first position), etc. So that in general, the element $A(i,j)$ is stored in the memory location `A(1+i-j,j)` for $j = 1,\ldots,n$ and $i \in \lbrack j,\min(m,j + k)\rbrack$ . Also, the elements in the array `A` that do not conceptually correspond to the elements in the banded matrix (the bottom right $k \times k$ triangle) are not referenced.


If `uplo == CUBLAS_FILL_MODE_UPPER` then the triangular banded matrix $A$ is stored column by column, with the main diagonal of the matrix stored in row `k + 1`, the first superdiagonal in row `k` (starting at second position), the second superdiagonal in row `k-1` (starting at third position), etc. So that in general, the element $A(i,j)$ is stored in the memory location `A(1+k+i-j,j)` for $j = 1,\ldots,n$ and $i \in \lbrack\max(1,j - k,j)\rbrack$ . Also, the elements in the array `A` that do not conceptually correspond to the elements in the banded matrix (the top left $k \times k$ triangle) are not referenced.


| Param. | Memory | In/out | Meaning |
| --- | --- | --- | --- |
| handle |  | input | Handle to the cuBLAS library context. |
| uplo |  | input | Indicates if matrix A lower or upper part is stored, the other part is not referenced and is inferred from the stored elements. |
| trans |  | input | Operation op(A) that is non- or (conj.) transpose. |
| diag |  | input | Indicates if the elements on the main diagonal of matrix A are unity and should not be accessed. |
| n |  | input | Number of rows and columns of matrix A. |
| k |  | input | Number of sub- and super-diagonals of matrix A. |
| A | device | input | <type> array of dimension lda x n, with lda >= k+1. |
| lda |  | input | Leading dimension of two-dimensional array used to store matrix A. |
| x | device | in/out | <type> vector with n elements. |
| incx |  | input | Stride between consecutive elements of x. |


The possible error values returned by this function and their meanings are listed below.


| Error Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | The operation completed successfully |
| CUBLAS_STATUS_NOT_INITIALIZED | The library was not initialized |
| CUBLAS_STATUS_INVALID_VALUE | If n < 0 or k < 0, or
if incx == 0, or
if trans is not one of CUBLAS_OP_N, CUBLAS_OP_T and CUBLAS_OP_C, or
if uplo is not one of CUBLAS_FILL_MODE_LOWER and CUBLAS_FILL_MODE_UPPER, or
if diag is not one of CUBLAS_DIAG_UNIT and CUBLAS_DIAG_NON_UNIT, or
if lda < (1 + k) |
| CUBLAS_STATUS_EXECUTION_FAILED | The function failed to launch on the GPU |


For references please refer to NETLIB documentation:


[stbsv()](http://www.netlib.org/blas/stbsv.f), [dtbsv()](http://www.netlib.org/blas/dtbsv.f), [ctbsv()](http://www.netlib.org/blas/ctbsv.f), [ztbsv()](http://www.netlib.org/blas/ztbsv.f)




```c++
cublasStatus_t cublasStpmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const float           *AP,
                           float           *x, int incx)
cublasStatus_t cublasDtpmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const double          *AP,
                           double          *x, int incx)
cublasStatus_t cublasCtpmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const cuComplex       *AP,
                           cuComplex       *x, int incx)
cublasStatus_t cublasZtpmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const cuDoubleComplex *AP,
                           cuDoubleComplex *x, int incx)
```

此函数支持64位整数接口。

此函数执行三角压缩矩阵向量乘法

$\textbf{x} = \text{op}(A)\textbf{x}$

其中 $A$ 是以压缩格式存储的三角矩阵，$\mathbf{x}$ 是向量。此外，对于矩阵 $A$

$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{trans == CUBLAS\_OP\_N}} \\
A^{T} & {\text{if }\textsf{trans == CUBLAS\_OP\_T}} \\
A^{H} & {\text{if }\textsf{trans == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$

如果 `uplo == CUBLAS_FILL_MODE_LOWER`，则三角矩阵 $A$ 下三角部分的元素按列紧凑存储，无间隙，因此元素 $A(i,j)$ 存储在内存位置 `AP[i+((2*n-j+1)*j)/2]` 中，其中 $j = 1,\ldots,n$ 且 $i \geq j$。因此，压缩格式仅需 $\frac{n(n + 1)}{2}$ 个元素进行存储。

如果 `uplo == CUBLAS_FILL_MODE_UPPER`，则三角矩阵 $A$ 上三角部分的元素按列紧凑存储，无间隙，因此元素 $A(i,j)$ 存储在内存位置 `AP[i+(j*(j+1))/2]` 中，适用于 $A(i,j)$ 且 $i \leq j$。因此，压缩格式仅需 $\frac{n(n + 1)}{2}$ 个元素进行存储。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS 库上下文的句柄。 |
| uplo |  | input | 指示矩阵 A 的下三角或上三角部分是否被存储，另一部分不被引用，并从存储的元素推断。 |
| trans |  | input | 操作 op(A)，即非转置或（共轭）转置。 |
| diag |  | input | 指示矩阵 A 主对角线上的元素是否为单位1，且不应被访问。 |
| n |  | input | 矩阵 A 的行数和列数。 |
| AP | device | input | 以压缩格式存储 $A$ 的 <type> 数组。 |
| x | device | in/out | 具有 n 个元素的 <type> 向量。 |
| incx |  | input | x 中连续元素之间的步长。 |

此函数返回的可能错误值及其含义如下所述。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0，或 incx == 0，或 trans 不是 CUBLAS_OP_N、CUBLAS_OP_T 和 CUBLAS_OP_C 之一，或 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或 diag 不是 CUBLAS_DIAG_UNIT 和 CUBLAS_DIAG_NON_UNIT 之一 |
| CUBLAS_STATUS_ALLOC_FAILED | 内部临时内存的分配失败 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在 GPU 上启动失败 |

有关参考文献，请参阅 NETLIB 文档：

[stpmv()](http://www.netlib.org/blas/stpmv.f), [dtpmv()](http://www.netlib.org/blas/dtpmv.f), [ctpmv()](http://www.netlib.org/blas/ctpmv.f), [ztpmv()](http://www.netlib.org/blas/ztpmv.f)

```c++

cublasStatus_t cublasStpsv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const float           *AP,
                           float           *x, int incx)
cublasStatus_t cublasDtpsv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const double          *AP,
                           double          *x, int incx)
cublasStatus_t cublasCtpsv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const cuComplex       *AP,
                           cuComplex       *x, int incx)
cublasStatus_t cublasZtpsv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const cuDoubleComplex *AP,
                           cuDoubleComplex *x, int incx)


```

此函数支持 64 位整数接口。

此函数求解压缩格式三角线性方程组（包含单个右端项）

$\text{op}(A)\textbf{x} = \textbf{b}$

其中 $A$ 是以压缩格式存储的三角矩阵，$\mathbf{x}$ 和 $\mathbf{b}$ 是向量。此外，对于矩阵 $A$

$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{trans == CUBLAS\_OP\_N}} \\
A^{T} & {\text{if }\textsf{trans == CUBLAS\_OP\_T}} \\
A^{H} & {\text{if }\textsf{trans == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$

解 $\mathbf{x}$ 会在退出时覆盖右端项 $\mathbf{b}$。

此函数不包含奇异性或近似奇异性的检测。

如果 `uplo == CUBLAS_FILL_MODE_LOWER`，则三角矩阵 $A$ 下三角部分的元素按列紧凑存储（无间隙），使得元素 $A(i,j)$ 存储在内存位置 `AP[i+((2*n-j+1)*j)/2]` 中，其中 $j = 1,\ldots,n$ 且 $i \geq j$。因此，压缩格式仅需要 $\frac{n(n + 1)}{2}$ 个元素进行存储。

如果 `uplo == CUBLAS_FILL_MODE_UPPER`，则三角矩阵 $A$ 上三角部分的元素按列紧凑存储（无间隙），使得元素 $A(i,j)$ 存储在内存位置 `AP[i+(j*(j+1))/2]` 中，其中 $j = 1,\ldots,n$ 且 $i \leq j$。因此，压缩格式仅需要 $\frac{n(n + 1)}{2}$ 个元素进行存储。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS 库上下文的句柄。 |
| uplo |  | 输入 | 指示矩阵 A 的下三角或上三角部分是否被存储，另一部分未被引用且从存储的元素中推断。 |
| trans |  | 输入 | 操作 op(A)，可为非转置或（共）转置。 |
| diag |  | 输入 | 指示矩阵主对角线上的元素是否为单元（1），且不应被访问。 |
| n |  | 输入 | 矩阵 A 的行数和列数。 |
| AP | 设备端 | 输入 | 以压缩格式存储 $A$ 的 `<type>` 数组。 |
| x | 设备端 | 输入/输出 | 包含 n 个元素的 `<type>` 向量。 |
| incx |  | 输入 | x 中连续元素之间的步长。 |

此函数可能返回的错误值及其含义如下所述。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0，或
如果 incx == 0，或
如果 trans 不是 CUBLAS_OP_N、CUBLAS_OP_T 和 CUBLAS_OP_C 之一，或
如果 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或
如果 diag 不是 CUBLAS_DIAG_UNIT 和 CUBLAS_DIAG_NON_UNIT 之一 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在 GPU 上启动失败 |

有关参考文献，请参阅 NETLIB 文档：

[stpsv()](http://www.netlib.org/blas/stpsv.f), [dtpsv()](http://www.netlib.org/blas/dtpsv.f), [ctpsv()](http://www.netlib.org/blas/ctpsv.f), [ztpsv()](http://www.netlib.org/blas/ztpsv.f)

```c++
cublasStatus_t cublasStrmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const float           *A, int lda,
                           float           *x, int incx)
cublasStatus_t cublasDtrmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const double          *A, int lda,
                           double          *x, int incx)
cublasStatus_t cublasCtrmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const cuComplex       *A, int lda,
                           cuComplex       *x, int incx)
cublasStatus_t cublasZtrmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const cuDoubleComplex *A, int lda,
                           cuDoubleComplex *x, int incx)
```

此函数支持64位整数接口。

此函数执行三角矩阵与向量的乘法运算

$\textbf{x} = \text{op}(A)\textbf{x}$

其中 $A$ 是以_lower_或_upper_模式存储的三角矩阵，可包含或不包含主对角线，$\mathbf{x}$ 是向量。此外，对于矩阵 $A$

$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{trans == CUBLAS\_OP\_N}} \\
A^{T} & {\text{if }\textsf{trans == CUBLAS\_OP\_T}} \\
A^{H} & {\text{if }\textsf{trans == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS库上下文的句柄 |
| uplo |  | 输入 | 指示矩阵A的下三角或上三角部分是否被存储，另一部分未被引用，根据已存储的元素进行推断 |
| trans |  | 输入 | 运算op(A)，即非转置或（共轭）转置 |
| diag |  | 输入 | 指示矩阵A主对角线上的元素是否为单位1，以及是否应该被访问 |
| n |  | 输入 | 矩阵A的行数和列数 |
| A | 设备 | 输入 | 维度为lda x n的<type>数组，lda >= max(1, n) |
| lda |  | 输入 | 用于存储矩阵A的二维数组的主导维度 |
| x | 设备 | 输入/输出 | 包含n个元素的<type>向量 |
| incx |  | 输入 | x中连续元素之间的步长 |

此函数返回的可能错误值及其含义如下所列。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果n < 0，或incx == 0，或trans不是CUBLAS_OP_N、CUBLAS_OP_T和CUBLAS_OP_C之一，或uplo不是CUBLAS_FILL_MODE_LOWER和CUBLAS_FILL_MODE_UPPER之一，或diag不是CUBLAS_DIAG_UNIT和CUBLAS_DIAG_NON_UNIT之一，或lda < max(1, n) |
| CUBLAS_STATUS_ALLOC_FAILED | 内部临时内存的分配失败 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在GPU上启动执行 |

参考文献请参阅NETLIB文档：

[strmv()](http://www.netlib.org/blas/strmv.f)、[dtrmv()](http://www.netlib.org/blas/dtrmv.f)、[ctrmv()](http://www.netlib.org/blas/ctrmv.f)、[ztrmv()](http://www.netlib.org/blas/ztrmv.f)



```c++
// 64位整数接口支持
cublasStatus_t cublasStrsv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const float           *A, int lda,
                           float           *x, int incx)
cublasStatus_t cublasDtrsv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const double          *A, int lda,
                           double          *x, int incx)
cublasStatus_t cublasCtrsv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const cuComplex       *A, int lda,
                           cuComplex       *x, int incx)
cublasStatus_t cublasZtrsv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const cuDoubleComplex *A, int lda,
                           cuDoubleComplex *x, int incx)


```


此函数支持64位整数接口。


此函数求解带有单个右侧向量的三角线性系统


$\text{op}(A)\textbf{x} = \textbf{b}$


其中 $A$ 是以下三角矩阵：按下或上三角模式存储，可带或不带主对角线，$\mathbf{x}$ 和 $\mathbf{b}$ 为向量。此外，对于矩阵 $A$


$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{transa == CUBLAS\_OP\_N}} \\
A^{T} & {\text{if }\textsf{transa == CUBLAS\_OP\_T}} \\
A^{H} & {\text{if }\textsf{transa == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$


解 $\mathbf{x}$ 在退出时覆盖右侧向量 $\mathbf{b}$。


此函数不包含奇异性或近奇异性测试。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS 库上下文的句柄。 |
| uplo |  | input | 指示矩阵 A 的下三角或上三角部分是否存储，另一部分未被引用且根据存储的元素推断。 |
| trans |  | input | 操作 op(A)，即非转置或（共轭）转置。 |
| diag |  | input | 指示矩阵 A 主对角线上的元素是否为单位一，且不应被访问。 |
| n |  | input | 矩阵 A 的行数和列数。 |
| A | device | input | 维度为 lda x n 的 <type> 数组，lda >= max(1, n)。 |
| lda |  | input | 用于存储矩阵 A 的二维数组的主维度。 |
| x | device | in/out | 具有 n 个元素的 <type> 向量。 |
| incx |  | input | x 中连续元素之间的步长。 |


此函数可能返回的错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0，或
如果 incx == 0，或
如果 trans 不是 CUBLAS_OP_N、CUBLAS_OP_T 和 CUBLAS_OP_C 之一，或
如果 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或
如果 diag 不是 CUBLAS_DIAG_UNIT 和 CUBLAS_DIAG_NON_UNIT 之一，或
如果 lda < max(1, n) |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |


相关参考文献请参阅 NETLIB 文档：


[strsv()](http://www.netlib.org/blas/strsv.f), [dtrsv()](http://www.netlib.org/blas/dtrsv.f), [ctrsv()](http://www.netlib.org/blas/ctrsv.f), [ztrsv()](http://www.netlib.org/blas/ztrsv.f)