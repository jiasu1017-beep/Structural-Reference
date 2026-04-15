## 2.8. 类BLAS扩展

本节描述执行矩阵-矩阵运算的BLAS扩展函数。

### 2.8.1. cublas<t>geam()

```c++

cublasStatus_t cublasSgeam(cublasHandle_t handle,
                          cublasOperation_t transa, cublasOperation_t transb,
                          int m, int n,
                          const float           *alpha,
                          const float           *A, int lda,
                          const float           *beta,
                          const float           *B, int ldb,
                          float           *C, int ldc)
cublasStatus_t cublasDgeam(cublasHandle_t handle,
                          cublasOperation_t transa, cublasOperation_t transb,
                          int m, int n,
                          const double          *alpha,
                          const double          *A, int lda,
                          const double          *beta,
                          const double          *B, int ldb,
                          double          *C, int ldc)
cublasStatus_t cublasCgeam(cublasHandle_t handle,
                          cublasOperation_t transa, cublasOperation_t transb,
                          int m, int n,
                          const cuComplex       *alpha,
                          const cuComplex       *A, int lda,
                          const cuComplex       *beta ,
                          const cuComplex       *B, int ldb,
                          cuComplex       *C, int ldc)
cublasStatus_t cublasZgeam(cublasHandle_t handle,
                          cublasOperation_t transa, cublasOperation_t transb,
                          int m, int n,
                          const cuDoubleComplex *alpha,
                          const cuDoubleComplex *A, int lda,
                          const cuDoubleComplex *beta,
                          const cuDoubleComplex *B, int ldb,
                          cuDoubleComplex *C, int ldc)


```

此函数支持64位整数接口。

此函数执行矩阵-矩阵加法/转置

$C = \alpha\text{op}(A) + \beta\text{op}(B)$

其中 $\alpha$ 和 $\beta$ 是标量，$A$、$B$ 和 $C$ 是按列主序格式存储的矩阵，维度分别为 $\text{op}(A)$ $m \times n$、$\text{op}(B)$ $m \times n$ 和 $C$ $m \times n$。对于矩阵 $A$：

$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{transa == $\mathrm{CUBLAS\_OP\_N}$}} \\
A^{T} & {\text{if }\textsf{transa == $\mathrm{CUBLAS\_OP\_T}$}} \\
A^{H} & {\text{if }\textsf{transa == $\mathrm{CUBLAS\_OP\_C}$}} \\
\end{matrix} \right.$

$\text{op}(B)$ 对于矩阵 $B$ 的定义类似。

如果 C 与 A 或 B 不重叠，则操作为原地外操作。

原地模式支持以下两种操作：

$C = \alpha\text{*}C + \beta\text{op}(B)$

$C = \alpha\text{op}(A) + \beta\text{*}C$

对于原地模式，如果 `C == A`，则 `ldc == lda` 且 `transa == CUBLAS_OP_N`。如果 `C === B`，则 `ldc == ldb` 且 `transb == CUBLAS_OP_N`。如果用户不满足上述要求，则返回 `CUBLAS_STATUS_INVALID_VALUE`。

该操作包括以下特殊情况：

用户可以通过设置 `*alpha = beta = 0` 将矩阵 C 重置为零。

用户可以通过设置 `*alpha = 1 and *beta = 0` 对矩阵 A 进行转置。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS 库上下文的句柄。 |
| transa |  | input | op(A) 的操作，即非转置或（共轭）转置。 |
| transb |  | input | op(B) 的操作，即非转置或（共轭）转置。 |
| m |  | input | 矩阵 op(A) 和 C 的行数。 |
| n |  | input | 矩阵 op(B) 和 C 的列数。 |
| alpha | 主机或设备 | input | 用于乘法的 <type> 标量。如果 *alpha == 0，则 A 不必是有效输入。 |
| A | 设备 | input | <type> 数组，维度为 lda x n，其中当 transa == CUBLAS_OP_N 时 lda >= max(1, m)，否则为 lda x m，lda >= max(1, n)。 |
| lda |  | input | 用于存储矩阵 A 的二维数组的主导维度。 |
| B | 设备 | input | <type> 数组，维度为 ldb x n，其中当 transb == CUBLAS_OP_N 时 ldb >= max(1, m)，否则为 ldb x m，ldb >= max(1, n)。 |
| ldb |  | input | 用于存储矩阵 B 的二维数组的主导维度。 |
| beta | 主机或设备 | input | 用于乘法的 <type> 标量。如果 *beta == 0，则 B 不必是有效输入。 |
| C | 设备 | output | <type> 数组，维度为 ldc x n，ldc >= max(1, m)。 |
| ldc |  | input | 用于存储矩阵 C 的二维数组的主导维度。 |

此函数可能返回的错误值及其含义如下。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 m < 0 或 n < 0，或
如果 transa 不是 CUBLAS_OP_N、CUBLAS_OP_T 和 CUBLAS_OP_C 之一，或
如果 transb 不是 CUBLAS_OP_N、CUBLAS_OP_T 和 CUBLAS_OP_C 之一，或
如果当 transa == CUBLAS_OP_N 时 lda < max(1, m)，否则 lda < max(1, n)，或
如果当 transb == CUBLAS_OP_N 时 ldb < max(1, m)，否则 ldb < max(1, n)，或
如果 ldc < max(1, m)，或
如果 A == C 且 (transa != CUBLAS_OP_N) || (lda != ldc)，或
如果 B == C 且 (transb != CUBLAS_OP_N) || (ldb != ldc)，或
如果 alpha 或 beta 为 NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |

### 2.8.2. cublas<t>dgmm()

```c++

cublasStatus_t cublasSdgmm(cublasHandle_t handle, cublasSideMode_t mode,
                          int m, int n,
                          const float           *A, int lda,
                          const float           *x, int incx,
                          float           *C, int ldc)
cublasStatus_t cublasDdgmm(cublasHandle_t handle, cublasSideMode_t mode,
                          int m, int n,
                          const double          *A, int lda,
                          const double          *x, int incx,
                          double          *C, int ldc)
cublasStatus_t cublasCdgmm(cublasHandle_t handle, cublasSideMode_t mode,
                          int m, int n,
                          const cuComplex       *A, int lda,
                          const cuComplex       *x, int incx,
                          cuComplex       *C, int ldc)
cublasStatus_t cublasZdgmm(cublasHandle_t handle, cublasSideMode_t mode,
                          int m, int n,
                          const cuDoubleComplex *A, int lda,
                          const cuDoubleComplex *x, int incx,
                          cuDoubleComplex *C, int ldc)


```

此函数支持64位整数接口。

此函数执行矩阵-矩阵乘法

$C = \left\{ \begin{matrix}
{A \times diag(X)} & {\text{if }\textsf{mode == $\mathrm{CUBLAS\_SIDE\_RIGHT}$}} \\
{diag(X) \times A} & {\text{if }\textsf{mode == $\mathrm{CUBLAS\_SIDE\_LEFT}$}} \\
\end{matrix} \right.$

其中 $A$ 和 $C$ 是按列主序格式存储的矩阵，维度为 $m \times n$。$X$ 是一个向量，如果 `mode == CUBLAS_SIDE_RIGHT` 则大小为 $n$，如果 `mode == CUBLAS_SIDE_LEFT` 则大小为 $m$。$X$ 从一维数组 x 中按步长 `incx` 聚集。`incx` 的绝对值是步长，`incx` 的符号是步长方向。如果 `incx` 为正，则从第一个元素开始正向遍历 x。否则，从最后一个元素开始向后遍历 x。X 的公式为

$X\lbrack j\rbrack = \left\{ \begin{matrix}
{x\lbrack j \times incx\rbrack} & {\text{if }incx \geq 0} \\
{x\lbrack(\chi - 1) \times |incx| - j \times |incx|\rbrack} & {\text{if }incx < 0} \\
\end{matrix} \right.$

其中，如果 `mode == CUBLAS_SIDE_LEFT` 则 $\chi = m$，如果 `mode == CUBLAS_SIDE_RIGHT` 则 $\chi = n$。

示例 1：如果用户想执行 $diag(diag(B)) \times A$，则 `incx = ldb + 1`，其中 ldb 是矩阵 `B` 的主导维度，无论是行主序还是列主序。

示例 2：如果用户想执行 $\alpha \times A$，则有两种选择：使用 `*beta == 0` 和 `transa == CUBLAS_OP_N` 的 cublas<t>geam()，或使用 `incx == 0` 和 `x[0] == alpha` 的 cublas<t>dgmm()。

该操作为原地外操作。原地操作仅在 `lda == ldc` 时有效。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS 库上下文的句柄。 |
| mode |  | input | 如果 mode == CUBLAS_SIDE_LEFT 则左乘，如果 mode == CUBLAS_SIDE_RIGHT 则右乘 |
| m |  | input | 矩阵 A 和 C 的行数。 |
| n |  | input | 矩阵 A 和 C 的列数。 |
| A | 设备 | input | <type> 数组，维度为 lda x n，lda >= max(1, m) |
| lda |  | input | 用于存储矩阵 A 的二维数组的主导维度。 |
| x | 设备 | input | 一维 <type> 数组，如果 mode == CUBLAS_SIDE_LEFT 则大小为 abs(incx) x m，如果 mode == CUBLAS_SIDE_RIGHT 则大小为 abs(incx) x n |
| incx |  | input | 一维数组 x 的步长。 |
| C | 设备 | in/out | <type> 数组，维度为 ldc x n，ldc >= max(1, m)。 |
| ldc |  | input | 用于存储矩阵 C 的二维数组的主导维度。 |

此函数可能返回的错误值及其含义如下。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 m < 0 或 n < 0，或
如果 mode 不是 CUBLAS_SIDE_LEFT 和 CUBLAS_SIDE_RIGHT 之一，或
如果 lda < max(1, m)，或
如果 ldc < max(1, m) |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |

### 2.8.3. cublas<t>getrfBatched()

```c++

cublasStatus_t cublasSgetrfBatched(cublasHandle_t handle,
                                   int n,
                                   float *const Aarray[],
                                   int lda,
                                   int *PivotArray,
                                   int *infoArray,
                                   int batchSize);

cublasStatus_t cublasDgetrfBatched(cublasHandle_t handle,
                                   int n,
                                   double *const Aarray[],
                                   int lda,
                                   int *PivotArray,
                                   int *infoArray,
                                   int batchSize);

cublasStatus_t cublasCgetrfBatched(cublasHandle_t handle,
                                   int n,
                                   cuComplex *const Aarray[],
                                   int lda,
                                   int *PivotArray,
                                   int *infoArray,
                                   int batchSize);

cublasStatus_t cublasZgetrfBatched(cublasHandle_t handle,
                                   int n,
                                   cuDoubleComplex *const Aarray[],
                                   int lda,
                                   int *PivotArray,
                                   int *infoArray,
                                   int batchSize);


```

`Aarray` 是指向按列主序格式存储的矩阵的指针数组，维度为 `nxn`，主导维度为 `lda`。

此函数对每个 `Aarray[i]`（i = 0, …, `batchSize-1`）执行 LU 分解，公式如下：

$\text{P}\text{*}{Aarray}\lbrack i\rbrack = L\text{*}U$

其中 `P` 是表示带行交换的部分主元选取的置换矩阵。`L` 是单位对角线的下三角矩阵，`U` 是上三角矩阵。

形式上，`P` 可以写成置换矩阵 `Pj`（j = 1,2,...,n）的乘积，即 `P = P1 * P2 * P3 * .... * Pn`。`Pj` 是一个置换矩阵，在执行 `Pj*x` 时交换向量 x 的两行。`Pj` 可以通过以下 Matlab 代码由 `PivotArray[i]` 的第 j 个元素构造：

```c++

// 在 Matlab 中，PivotArray[i] 是基为 1 的数组。
// 在 C 中，PivotArray[i] 是基为 0 的数组。
Pj = eye(n);
交换 Pj(j,:) 和 Pj(PivotArray[i][j]  ,:)


```

`L` 和 `U` 被写回原始矩阵 `A`，`L` 的对角线元素被丢弃。`L` 和 `U` 可以通过以下 Matlab 代码构造：

```c++

// A 是 getrf 后的 nxn 矩阵。
L = eye(n);
for j = 1:n
    L(j+1:n,j) = A(j+1:n,j)
end
U = zeros(n);
for i = 1:n
    U(i,i:n) = A(i,i:n)
end


```

如果矩阵 `A(=Aarray[i])` 是奇异的，getrf 仍然可以工作，`info(=infoArray[i])` 的值报告 LU 分解无法继续的第一行索引。如果 info 为 `k`，则 `U(k,k)` 为零。方程 `P*A == L*U` 仍然成立，但 `L` 和 `U` 的重构需要不同的 Matlab 代码，如下所示：

```c++

// A 是 getrf 后的 nxn 矩阵。
// info 为 k，这意味着 U(k,k) 为零。
L = eye(n);
for j = 1:k-1
    L(j+1:n,j) = A(j+1:n,j)
end
U = zeros(n);
for i = 1:k-1
    U(i,i:n) = A(i,i:n)
end
for i = k:n
    U(i,k:n) = A(i,k:n)
end


```

此函数适用于矩阵尺寸较小、启动开销是重要因素的情况。

如果 `PivotArray` 为 NULL，cublas<t>getrfBatched 支持无主元 LU 分解。

cublas<t>getrfBatched 支持任意维度。

cublas<t>getrfBatched 仅支持计算能力 2.0 及以上版本。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS 库上下文的句柄。 |
| n |  | input | Aarray[i] 的行数和列数。 |
| Aarray | 设备 | input/output | 指向 <type> 数组的指针数组，每个数组维度为 n x n，lda >= max(1, n)。矩阵 Aarray[i] 不应重叠；否则，将产生未定义行为。 |
| lda |  | input | 用于存储每个矩阵 Aarray[i] 的二维数组的主导维度。 |
| PivotArray | 设备 | output | 大小为 n x batchSize 的数组，包含每个 Aarray[i] 分解的主元序列，以线性方式存储。如果 PivotArray 为 NULL，则禁用主元选取。 |
| infoArray | 设备 | output | 大小为 batchSize 的数组，info(=infoArray[i]) 包含 Aarray[i] 分解的信息。
如果 info == 0，执行成功。
如果 info = -j，第 j 个参数有非法值。
如果 info = k，U(k, k) == 0。分解已完成，但 U 是奇异的。 |
| batchSize |  | input | A 中包含的指针数量 |

此函数可能返回的错误值及其含义如下。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | n < 0 或 batchSize < 0 或 lda <0 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |

有关参考信息，请参阅 NETLIB 文档：

[sgeqrf()](http://www.netlib.org/lapack/single/sgetrf.f), [dgeqrf()](http://www.netlib.org/lapack/double/dgetrf.f), [cgeqrf()](http://www.netlib.org/lapack/complex/cgetrf.f), [zgeqrf()](http://www.netlib.org/lapack/complex16/zgetrf.f)

### 2.8.4. cublas<t>getrsBatched()

```c++

cublasStatus_t cublasSgetrsBatched(cublasHandle_t handle,
                                   cublasOperation_t trans,
                                   int n,
                                   int nrhs,
                                   const float *const Aarray[],
                                   int lda,
                                   const int *devIpiv,
                                   float *const Barray[],
                                   int ldb,
                                   int *info,
                                   int batchSize);

cublasStatus_t cublasDgetrsBatched(cublasHandle_t handle,
                                   cublasOperation_t trans,
                                   int n,
                                   int nrhs,
                                   const double *const Aarray[],
                                   int lda,
                                   const int *devIpiv,
                                   double *const Barray[],
                                   int ldb,
                                   int *info,
                                   int batchSize);

cublasStatus_t cublasCgetrsBatched(cublasHandle_t handle,
                                   cublasOperation_t trans,
                                   int n,
                                   int nrhs,
                                   const cuComplex *const Aarray[],
                                   int lda,
                                   const int *devIpiv,
                                   cuComplex *const Barray[],
                                   int ldb,
                                   int *info,
                                   int batchSize);

cublasStatus_t cublasZgetrsBatched(cublasHandle_t handle,
                                   cublasOperation_t trans,
                                   int n,
                                   int nrhs,
                                   const cuDoubleComplex *const Aarray[],
                                   int lda,
                                   const int *devIpiv,
                                   cuDoubleComplex *const Barray[],
                                   int ldb,
                                   int *info,
                                   int batchSize);


```

此函数求解一组线性方程组：

$\text{op}(A\lbrack i \rbrack) X\lbrack i\rbrack = B\lbrack i\rbrack$

其中 $A\lbrack i\rbrack$ 是已经过带主元 LU 分解的矩阵，$X\lbrack i\rbrack$ 和 $B\lbrack i\rbrack$ 是 $n \times {nrhs}$ 矩阵。对于矩阵 $A$：

$\text{op}(A\lbrack i\rbrack) = \left\{ \begin{matrix}
{A\lbrack i\rbrack} & {\text{if }\textsf{trans == $\mathrm{CUBLAS\_OP\_N}$}} \\
{A^{T}\lbrack i\rbrack} & {\text{if }\textsf{trans == $\mathrm{CUBLAS\_OP\_T}$}} \\
{A^{H}\lbrack i\rbrack} & {\text{if }\textsf{trans == $\mathrm{CUBLAS\_OP\_C}$}} \\
\end{matrix} \right.$

此函数适用于矩阵尺寸较小、启动开销是重要因素的情况。

如果 `devIpiv` 为 NULL，cublas<t>getrsBatched() 支持无主元 LU 分解。

cublas<t>getrsBatched() 支持任意维度。

cublas<t>getrsBatched() 仅支持计算能力 2.0 及以上版本。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS 库上下文的句柄。 |
| trans |  | input | op(A) 的操作，即非转置或（共轭）转置。 |
| n |  | input | Aarray[i] 的行数和列数。 |
| nrhs |  | input | Barray[i] 的列数。 |
| Aarray | 设备 | input | 指向 <type> 数组的指针数组，每个数组维度为 n x n，lda >= max(1, n)。 |
| lda |  | input | 用于存储每个矩阵 Aarray[i] 的二维数组的主导维度。 |
| devIpiv | 设备 | input | 大小为 n x batchSize 的数组，包含每个 Aarray[i] 分解的主元序列，以线性方式存储。如果 devIpiv 为 NULL，则忽略所有 Aarray[i] 的主元。 |
| Barray | 设备 | input/output | 指向 <type> 数组的指针数组，每个数组维度为 n x nrhs，ldb >= max(1, n)。矩阵 Barray[i] 不应重叠；否则，将产生未定义行为。 |
| ldb |  | input | 用于存储每个解矩阵 Barray[i] 的二维数组的主导维度。 |
| info | 主机 | output | 如果 info == 0，执行成功。
如果 info = -j，第 j 个参数有非法值。 |
| batchSize |  | input | A 中包含的指针数量 |

此函数可能返回的错误值及其含义如下。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0 或 nrhs < 0，或
如果 trans 不是 CUBLAS_OP_N、CUBLAS_OP_T 和 CUBLAS_OP_C 之一，或
如果 lda < max(1, n)，或
如果 ldb < max(1, n) |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |

有关参考信息，请参阅 NETLIB 文档：

[sgeqrs()](http://www.netlib.org/lapack/single/sgetrs.f), [dgeqrs()](http://www.netlib.org/lapack/double/dgetrs.f), [cgeqrs()](http://www.netlib.org/lapack/complex/cgetrs.f), [zgeqrs()](http://www.netlib.org/lapack/complex16/zgetrs.f)

### 2.8.5. cublas<t>getriBatched()

```c++

cublasStatus_t cublasSgetriBatched(cublasHandle_t handle,
                                   int n,
                                   const float *const Aarray[],
                                   int lda,
                                   int *PivotArray,
                                   float *const Carray[],
                                   int ldc,
                                   int *infoArray,
                                   int batchSize);

cublasStatus_t cublasDgetriBatched(cublasHandle_t handle,
                                   int n,
                                   const double *const Aarray[],
                                   int lda,
                                   int *PivotArray,
                                   double *const Carray[],
                                   int ldc,
                                   int *infoArray,
                                   int batchSize);

cublasStatus_t cublasCgetriBatched(cublasHandle_t handle,
                                   int n,
                                   const cuComplex *const Aarray[],
                                   int lda,
                                   int *PivotArray,
                                   cuComplex *const Carray[],
                                   int ldc,
                                   int *infoArray,
                                   int batchSize);

cublasStatus_t cublasZgetriBatched(cublasHandle_t handle,
                                   int n,
                                   const cuDoubleComplex *const Aarray[],
                                   int lda,
                                   int *PivotArray,
                                   cuDoubleComplex *const Carray[],
                                   int ldc,
                                   int *infoArray,
                                   int batchSize);


```

`Aarray` 和 `Carray` 是指向按列主序格式存储的矩阵的指针数组，维度为 `n*n`，主导维度分别为 `lda` 和 `ldc`。

此函数对矩阵 `A[i]`（i = 0, …, `batchSize-1`）执行求逆。

在调用 cublas<t>getriBatched 之前，矩阵 `A[i]` 必须首先使用 cublas<t>getrfBatched 例程进行分解。在调用 cublas<t>getrfBatched 后，由 `Aarray[i]` 指向的矩阵将包含矩阵 `A[i]` 的 LU 因子，由 `(PivotArray+i)` 指向的向量将包含主元序列。

在 LU 分解之后，cublas<t>getriBatched 使用前向和后向三角求解器完成矩阵 `A[i]`（i = 0, …, `batchSize-1`）的求逆。求逆是原地外操作，因此 Carray[i] 的内存空间不能与 Array[i] 的内存空间重叠。

通常，cublas<t>getrfBatched 中的所有参数都会传入 cublas<t>getriBatched。例如：

```c++

// 步骤 1：执行原地 LU 分解，P*A = L*U。
// Aarray[i] 是 n*n 矩阵 A[i]
    cublasDgetrfBatched(handle, n, Aarray, lda, PivotArray, infoArray, batchSize);
// 检查 infoArray[i] 以查看 A[i] 的分解是否成功。
// Array[i] 包含 A[i] 的 LU 分解

// 步骤 2：执行原地外求逆，Carray[i] = inv(A[i])
    cublasDgetriBatched(handle, n, Aarray, lda, PivotArray, Carray, ldc, infoArray, batchSize);
// 检查 infoArray[i] 以查看 A[i] 的求逆是否成功。


```

用户可以从 cublas<t>getrfBatched 或 cublas<t>getriBatched 检查奇异性。

此函数适用于矩阵尺寸较小、启动开销是重要因素的情况。

如果 cublas<t>getrfBatched 是通过无主元执行的，则 cublas<t>getriBatched 的 `PivotArray` 应为 NULL。

cublas<t>getriBatched 支持任意维度。

cublas<t>getriBatched 仅支持计算能力 2.0 及以上版本。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS 库上下文的句柄。 |
| n |  | input | Aarray[i] 的行数和列数。 |
| Aarray | 设备 | input | 指向 <type> 数组的指针数组，每个数组维度为 n*n，lda >= max(1, n)。 |
| lda |  | input | 用于存储每个矩阵 Aarray[i] 的二维数组的主导维度。 |
| PivotArray | 设备 | output | 大小为 n*batchSize 的数组，包含每个 Aarray[i] 分解的主元序列，以线性方式存储。如果 PivotArray 为 NULL，则禁用主元选取。 |
| Carray | 设备 | output | 指向 <type> 数组的指针数组，每个数组维度为 n*n，ldc >= max(1, n)。矩阵 Carray[i] 不应重叠；否则，将产生未定义行为。 |
| ldc |  | input | 用于存储每个矩阵 Carray[i] 的二维数组的主导维度。 |
| infoArray | 设备 | output | 大小为 batchSize 的数组，info(=infoArray[i]) 包含 A[i] 求逆的信息。
如果 info == 0，执行成功。
如果 info == k，U(k, k) == 0。U 是奇异的，求逆失败。 |
| batchSize |  | input | A 中包含的指针数量 |

此函数可能返回的错误值及其含义如下。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0 或 lda < 0 或 ldc < 0 或 batchSize < 0，或
如果 lda < n 或 ldc < n |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |

### 2.8.6. cublas<t>matinvBatched()

```c++

cublasStatus_t cublasSmatinvBatched(cublasHandle_t handle,
                                    int n,
                                    const float *const A[],
                                    int lda,
                                    float *const Ainv[],
                                    int lda_inv,
                                    int *info,
                                    int batchSize);

cublasStatus_t cublasDmatinvBatched(cublasHandle_t handle,
                                    int n,
                                    const double *const A[],
                                    int lda,
                                    double *const Ainv[],
                                    int lda_inv,
                                    int *info,
                                    int batchSize);

cublasStatus_t cublasCmatinvBatched(cublasHandle_t handle,
                                    int n,
                                    const cuComplex *const A[],
                                    int lda,
                                    cuComplex *const Ainv[],
                                    int lda_inv,
                                    int *info,
                                    int batchSize);

cublasStatus_t cublasZmatinvBatched(cublasHandle_t handle,
                                    int n,
                                    const cuDoubleComplex *const A[],
                                    int lda,
                                    cuDoubleComplex *const Ainv[],
                                    int lda_inv,
                                    int *info,
                                    int batchSize);


```

`A` 和 `Ainv` 是指向按列主序格式存储的矩阵的指针数组，维度为 `n*n`，主导维度分别为 `lda` 和 `lda_inv`。

此函数对矩阵 `A[i]`（i = 0, …, `batchSize-1`）执行求逆。

此函数是 cublas<t>getrfBatched() 加 cublas<t>getriBatched() 的快捷方式。但是，如果 `n` 大于 32，则此函数不起作用。如果不大于 32，用户必须通过 cublas<t>getrfBatched() 和 cublas<t>getriBatched()。

如果矩阵 `A[i]` 是奇异的，则 `info[i]` 报告奇异性，与 cublas<t>getrfBatched() 相同。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS 库上下文的句柄。 |
| n |  | input | A[i] 的行数和列数。 |
| A | 设备 | input | 指向 <type> 数组的指针数组，每个数组维度为 n*n，lda >= max(1, n)。 |
| lda |  | input | 用于存储每个矩阵 A[i] 的二维数组的主导维度。 |
| Ainv | 设备 | output | 指向 <type> 数组的指针数组，每个数组维度为 n*n，lda_inv >= max(1, n)。矩阵 Ainv[i] 不应重叠；否则，将产生未定义行为。 |
| lda_inv |  | input | 用于存储每个矩阵 Ainv[i] 的二维数组的主导维度。 |
| info | 设备 | output | 大小为 batchSize 的数组，info[i] 包含 A[i] 求逆的信息。
如果 info[i] == 0，执行成功。
如果 info[i] == k，则 U(k, k) == 0。U 是奇异的，求逆失败。 |
| batchSize |  | input | A 中包含的指针数量。 |

此函数可能返回的错误值及其含义如下。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0 或 lda < 0 或 lda_inv < 0 或 batchSize < 0，或
如果 lda < n 或 lda_inv < n，或
如果 n > 32 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |

### 2.8.7. cublas<t>geqrfBatched()

```c++

cublasStatus_t cublasSgeqrfBatched( cublasHandle_t handle,
                                    int m,
                                    int n,
                                    float *const Aarray[],
                                    int lda,
                                    float *const TauArray[],
                                    int *info,
                                    int batchSize);

cublasStatus_t cublasDgeqrfBatched( cublasHandle_t handle,
                                    int m,
                                    int n,
                                    double *const Aarray[],
                                    int lda,
                                    double *const TauArray[],
                                    int *info,
                                    int batchSize);

cublasStatus_t cublasCgeqrfBatched( cublasHandle_t handle,
                                    int m,
                                    int n,
                                    cuComplex *const Aarray[],
                                    int lda,
                                    cuComplex *const TauArray[],
                                    int *info,
                                    int batchSize);

cublasStatus_t cublasZgeqrfBatched( cublasHandle_t handle,
                                    int m,
                                    int n,
                                    cuDoubleComplex *const Aarray[],
                                    int lda,
                                    cuDoubleComplex *const TauArray[],
                                    int *info,
                                    int batchSize);


```

`Aarray` 是指向按列主序格式存储的矩阵的指针数组，维度为 `m x n`，主导维度为 `lda`。`TauArray` 是指向向量的指针数组，每个向量维度至少为 `max (1, min(m, n))`。

此函数使用 Householder 反射对每个 `Aarray[i]`（i = 0, ..., batchSize-1）执行 QR 分解。每个矩阵 `Q[i]` 表示为初等反射子的乘积，并存储在每个 `Aarray[i]` 的下半部分，如下所示：

```text

Q[j] = H[j][1] H[j][2] . . . H[j](k)，其中 k = min(m,n)。

```

每个 H[j][i] 的形式为

```text

H[j][i] = I - tau[j] * v * v'

```

其中 `tau[j]` 是实数标量，`v` 是实数向量，`v(1:i-1) = 0` 和 `v(i) = 1`；`v(i+1:m)` 在退出时存储在 `Aarray[j][i+1:m,i]` 中，`tau` 存储在 `TauArray[j][i]` 中。

此函数适用于矩阵尺寸较小、启动开销是重要因素的情况。

cublas<t>geqrfBatched 支持任意维度。

cublas<t>geqrfBatched 仅支持计算能力 2.0 及以上版本。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS 库上下文的句柄。 |
| m |  | input | Aarray[i] 的行数。 |
| n |  | input | Aarray[i] 的列数。 |
| Aarray | 设备 | input | 指向 <type> 数组的指针数组，每个数组维度为 m x n，lda >= max(1, m)。 |
| lda |  | input | 用于存储每个矩阵 Aarray[i] 的二维数组的主导维度。 |
| TauArray | 设备 | output | 指向 <type> 向量的指针数组，每个向量维度为 max(1 ,min(m, n))。 |
| info | 主机 | output | 如果 info == 0，传递给函数的参数有效
如果 info < 