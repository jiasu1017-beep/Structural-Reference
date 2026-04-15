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
A & \text{ if trans == $\mathrm{CUBLAS\_OP\_N}$} \\
A^{T} & \text{ if trans == $\mathrm{CUBLAS\_OP\_T}$} \\
A^{H} & \text{ if trans == $\mathrm{CUBLAS\_OP\_C}$} \\
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
A & \text{ if trans == $\mathrm{CUBLAS\_OP\_N}$} \\
A^{T} & \text{ if trans == $\mathrm{CUBLAS\_OP\_T}$} \\
A^{H} & \text{ if trans == $\mathrm{CUBLAS\_OP\_C}$} \\
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