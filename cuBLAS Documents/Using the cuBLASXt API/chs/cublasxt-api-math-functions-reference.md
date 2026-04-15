## 4.4. cuBLASXt API 数学函数参考

本章介绍 cuBLASXt API 支持的实际线性代数例程。我们将使用 <*type*> 表示类型，<*t*> 表示相应的短类型，以更简洁清晰地展示已实现的函数。除非另有说明，<*type*> 和 <*t*> 具有以下含义：


| <type> | <t> | 含义 |
| --- | --- | --- |
| float | 's' 或 'S' | 实数单精度 |
| double | 'd' 或 'D' | 实数双精度 |
| cuComplex | 'c' 或 'C' | 复数单精度 |
| cuDoubleComplex | 'z' 或 'Z' | 复数双精度 |


缩写 $\mathbf{Re}(\cdot)$ 和 $\mathbf{Im}(\cdot)$ 分别表示一个数的实部和虚部。由于实数不存在虚部，我们将其视为零，通常可以简单地将其从使用它的公式中丢弃。此外，$\bar{\alpha}$ 将表示 $\alpha$ 的复共轭。


一般来说，在整个文档中，小写希腊符号 $\alpha$ 和 $\beta$ 表示标量，小写英文字母粗体 $\mathbf{x}$ 和 $\mathbf{y}$ 表示向量，大写英文字母 $A$、$B$ 和 $C$ 表示矩阵。




### 4.4.1. cublasXt<t>gemm()



```c++

cublasStatus_t cublasXtSgemm(cublasXtHandle_t handle,
                           cublasOperation_t transa, cublasOperation_t transb,
                           size_t m, size_t n, size_t k,
                           const float           *alpha,
                           const float           *A, int lda,
                           const float           *B, int ldb,
                           const float           *beta,
                           float           *C, int ldc)
cublasStatus_t cublasXtDgemm(cublasXtHandle_t handle,
                           cublasOperation_t transa, cublasOperation_t transb,
                           int m, int n, int k,
                           const double          *alpha,
                           const double          *A, int lda,
                           const double          *B, int ldb,
                           const double          *beta,
                           double          *C, int ldc)
cublasStatus_t cublasXtCgemm(cublasXtHandle_t handle,
                           cublasOperation_t transa, cublasOperation_t transb,
                           int m, int n, int k,
                           const cuComplex       *alpha,
                           const cuComplex       *A, int lda,
                           const cuComplex       *B, int ldb,
                           const cuComplex       *beta,
                           cuComplex       *C, int ldc)
cublasStatus_t cublasXtZgemm(cublasXtHandle_t handle,
                           cublasOperation_t transa, cublasOperation_t transb,
                           int m, int n, int k,
                           const cuDoubleComplex *alpha,
                           const cuDoubleComplex *A, int lda,
                           const cuDoubleComplex *B, int ldb,
                           const cuDoubleComplex *beta,
                           cuDoubleComplex *C, int ldc)


```


此函数执行矩阵-矩阵乘法


$C = \alpha\text{op}(A)\text{op}(B) + \beta C$


其中 $\alpha$ 和 $\beta$ 是标量，$A$、$B$ 和 $C$ 是按列主序存储的矩阵，维度分别为 $\text{op}(A)$ $m \times k$、$\text{op}(B)$ $k \times n$ 和 $C$ $m \times n$。此外，对于矩阵 $A$


$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{transa == CUBLAS\_OP\_N}} \\
A^{T} & {\text{if }\textsf{transa == CUBLAS\_OP\_T}} \\
A^{H} & {\text{if }\textsf{transa == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$


$\text{op}(B)$ 对矩阵 $B$ 的定义类似。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLASXt API 上下文的句柄。 |
| transa |  | 输入 | 操作 op(A)，即非转置或（共轭）转置。 |
| transb |  | 输入 | 操作 op(B)，即非转置或（共轭）转置。 |
| m |  | 输入 | 矩阵 op(A) 和 C 的行数。 |
| n |  | 输入 | 矩阵 op(B) 和 C 的列数。 |
| k |  | 输入 | op(A) 的列数和 op(B) 的行数。 |
| alpha | 主机端 | 输入 | 用于乘法的 <type> 标量。 |
| A | 主机端或设备端 | 输入 | <type> 数组，维度为 lda x k，当 transa == CUBLAS_OP_N 时 lda >= max(1, m)；否则为 lda x m，lda >= max(1, k)。 |
| lda |  | 输入 | 用于存储矩阵 A 的二维数组的主维度。 |
| B | 主机端或设备端 | 输入 | <type> 数组，维度为 ldb x n，当 transb == CUBLAS_OP_N 时 ldb >= max(1, k)；否则为 ldb x k，ldb >= max(1, n)。 |
| ldb |  | 输入 | 用于存储矩阵 B 的二维数组的主维度。 |
| beta | 主机端 | 输入 | 用于乘法的 <type> 标量。如果 beta == 0，则 C 不必是有效输入。 |
| C | 主机端或设备端 | 输入/输出 | <type> 数组，维度为 ldc x n，ldc >= max(1, m)。 |
| ldc |  | 输入 | 用于存储矩阵 C 的二维数组的主维度。 |


此函数可能返回的错误值及其含义如下所述。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 参数 m、n、k < 0 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |


参考文献请参阅 NETLIB 文档：


[sgemm()](http://www.netlib.org/blas/sgemm.f)、[dgemm()](http://www.netlib.org/blas/dgemm.f)、[cgemm()](http://www.netlib.org/blas/cgemm.f)、[zgemm()](http://www.netlib.org/blas/zgemm.f)





### 4.4.2. cublasXt<t>hemm()



```c++

cublasStatus_t cublasXtChemm(cublasXtHandle_t handle,
                           cublasSideMode_t side, cublasFillMode_t uplo,
                           size_t m, size_t n,
                           const cuComplex       *alpha,
                           const cuComplex       *A, size_t lda,
                           const cuComplex       *B, size_t ldb,
                           const cuComplex       *beta,
                           cuComplex       *C, size_t ldc)
cublasStatus_t cublasXtZhemm(cublasXtHandle_t handle,
                           cublasSideMode_t side, cublasFillMode_t uplo,
                           size_t m, size_t n,
                           const cuDoubleComplex *alpha,
                           const cuDoubleComplex *A, size_t lda,
                           const cuDoubleComplex *B, size_t ldb,
                           const cuDoubleComplex *beta,
                           cuDoubleComplex *C, size_t ldc)


```


此函数执行 Hermitian 矩阵-矩阵乘法


$C = \left\{ \begin{matrix}
{\alpha AB + \beta C} & {\text{if }\textsf{side == CUBLAS\_SIDE\_LEFT}} \\
{\alpha BA + \beta C} & {\text{if }\textsf{side == CUBLAS\_SIDE\_RIGHT}} \\
\end{matrix} \right.$


其中 $A$ 是按下三角或上三角模式存储的 Hermitian 矩阵，$B$ 和 $C$ 是 $m \times n$ 矩阵，$\alpha$ 和 $\beta$ 是标量。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLASXt API 上下文的句柄。 |
| side |  | 输入 | 指示矩阵 A 在 B 的左侧还是右侧。 |
| uplo |  | 输入 | 指示矩阵 A 的下三角还是上三角部分被存储，另一个 Hermitian 部分未被引用，而是从存储的元素中推断。 |
| m |  | 输入 | 矩阵 C 和 B 的行数，矩阵 A 相应调整大小。 |
| n |  | 输入 | 矩阵 C 和 B 的列数，矩阵 A 相应调整大小。 |
| alpha | 主机端 | 输入 | 用于乘法的 <type> 标量。 |
| A | 主机端或设备端 | 输入 | <type> 数组，当 side = CUBLAS_SIDE_LEFT 时维度为 lda x m，lda >= max(1, m)；否则为 lda x n，lda >= max(1, n)。对角线元素的虚部被假定为零。 |
| lda |  | 输入 | 用于存储矩阵 A 的二维数组的主维度。 |
| B | 主机端或设备端 | 输入 | <type> 数组，维度为 ldb x n，ldb >= max(1, m)。 |
| ldb |  | 输入 | 用于存储矩阵 B 的二维数组的主维度。 |
| beta | 主机端 | 输入 | 用于乘法的 <type> 标量，如果 beta == 0，则 C 不必是有效输入。 |
| C | 主机端或设备端 | 输入/输出 | <type> 数组，维度为 ldc x n，ldc >= max(1, m)。 |
| ldc |  | 输入 | 用于存储矩阵 C 的二维数组的主维度。 |


此函数可能返回的错误值及其含义如下所述。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 参数 m < 0 或 n < 0 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |


参考文献请参阅 NETLIB 文档：


[chemm()](http://www.netlib.org/blas/chemm.f)、[zhemm()](http://www.netlib.org/blas/zhemm.f)





### 4.4.3. cublasXt<t>symm()



```c++

cublasStatus_t cublasXtSsymm(cublasXtHandle_t handle,
                           cublasSideMode_t side, cublasFillMode_t uplo,
                           size_t m, size_t n,
                           const float           *alpha,
                           const float           *A, size_t lda,
                           const float           *B, size_t ldb,
                           const float           *beta,
                           float           *C, size_t ldc)
cublasStatus_t cublasXtDsymm(cublasXtHandle_t handle,
                           cublasSideMode_t side, cublasFillMode_t uplo,
                           size_t m, size_t n,
                           const double          *alpha,
                           const double          *A, size_t lda,
                           const double          *B, size_t ldb,
                           const double          *beta,
                           double          *C, size_t ldc)
cublasStatus_t cublasXtCsymm(cublasXtHandle_t handle,
                           cublasSideMode_t side, cublasFillMode_t uplo,
                           size_t m, size_t n,
                           const cuComplex       *alpha,
                           const cuComplex       *A, size_t lda,
                           const cuComplex       *B, size_t ldb,
                           const cuComplex       *beta,
                           cuComplex       *C, size_t ldc)
cublasStatus_t cublasXtZsymm(cublasXtHandle_t handle,
                           cublasSideMode_t side, cublasFillMode_t uplo,
                           size_t m, size_t n,
                           const cuDoubleComplex *alpha,
                           const cuDoubleComplex *A, size_t lda,
                           const cuDoubleComplex *B, size_t ldb,
                           const cuDoubleComplex *beta,
                           cuDoubleComplex *C, size_t ldc)


```


此函数执行对称矩阵-矩阵乘法


$C = \left\{ \begin{matrix}
{\alpha AB + \beta C} & {\text{if }\textsf{side == CUBLAS\_SIDE\_LEFT}} \\
{\alpha BA + \beta C} & {\text{if }\textsf{side == CUBLAS\_SIDE\_RIGHT}} \\
\end{matrix} \right.$


其中 $A$ 是按下三角或上三角模式存储的对称矩阵，$A$ 和 $A$ 是 $m \times n$ 矩阵，$\alpha$ 和 $\beta$ 是标量。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLASXt API 上下文的句柄。 |
| side |  | 输入 | 指示矩阵 A 在 B 的左侧还是右侧。 |
| uplo |  | 输入 | 指示矩阵 A 的下三角还是上三角部分被存储，另一个对称部分未被引用，而是从存储的元素中推断。 |
| m |  | 输入 | 矩阵 A 和 B 的行数，矩阵 A 相应调整大小。 |
| n |  | 输入 | 矩阵 C 和 A 的列数，矩阵 A 相应调整大小。 |
| alpha | 主机端 | 输入 | 用于乘法的 <type> 标量。 |
| A | 主机端或设备端 | 输入 | <type> 数组，当 side == CUBLAS_SIDE_LEFT 时维度为 lda x m，lda >= max(1, m)；否则为 lda x n，lda >= max(1, n)。 |
| lda |  | 输入 | 用于存储矩阵 A 的二维数组的主维度。 |
| B | 主机端或设备端 | 输入 | <type> 数组，维度为 ldb x n，ldb >= max(1, m)。 |
| ldb |  | 输入 | 用于存储矩阵 B 的二维数组的主维度。 |
| beta | 主机端 | 输入 | 用于乘法的 <type> 标量，如果 beta == 0，则 C 不必是有效输入。 |
| C | 主机端或设备端 | 输入/输出 | <type> 数组，维度为 ldc x n，ldc >= max(1, m)。 |
| ldc |  | 输入 | 用于存储矩阵 C 的二维数组的主维度。 |


此函数可能返回的错误值及其含义如下所述。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 参数 m < 0 或 n < 0 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |


参考文献请参阅 NETLIB 文档：


[ssymm()](http://www.netlib.org/blas/ssymm.f)、[dsymm()](http://www.netlib.org/blas/dsymm.f)、[csymm()](http://www.netlib.org/blas/csymm.f)、[zsymm()](http://www.netlib.org/blas/zsymm.f)





### 4.4.4. cublasXt<t>syrk()



```c++

cublasStatus_t cublasXtSsyrk(cublasXtHandle_t handle,
                           cublasFillMode_t uplo, cublasOperation_t trans,
                           int n, int k,
                           const float           *alpha,
                           const float           *A, int lda,
                           const float           *beta,
                           float           *C, int ldc)
cublasStatus_t cublasXtDsyrk(cublasXtHandle_t handle,
                           cublasFillMode_t uplo, cublasOperation_t trans,
                           int n, int k,
                           const double          *alpha,
                           const double          *A, int lda,
                           const double          *beta,
                           double          *C, int ldc)
cublasStatus_t cublasXtCsyrk(cublasXtHandle_t handle,
                           cublasFillMode_t uplo, cublasOperation_t trans,
                           int n, int k,
                           const cuComplex       *alpha,
                           const cuComplex       *A, int lda,
                           const cuComplex       *beta,
                           cuComplex       *C, int ldc)
cublasStatus_t cublasXtZsyrk(cublasXtHandle_t handle,
                           cublasFillMode_t uplo, cublasOperation_t trans,
                           int n, int k,
                           const cuDoubleComplex *alpha,
                           const cuDoubleComplex *A, int lda,
                           const cuDoubleComplex *beta,
                           cuDoubleComplex *C, int ldc)


```


此函数执行对称秩-$k$ 更新


$C = \alpha\text{op}(A)\text{op}(A)^{T} + \beta C$


其中 $\alpha$ 和 $\beta$ 是标量，$C$ 是按下三角或上三角模式存储的对称矩阵，$A$ 是维度为 $\text{op}(A)$ $n \times k$ 的矩阵。此外，对于矩阵 $A$


$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{transa == CUBLAS\_OP\_N}} \\
A^{T} & {\text{if }\textsf{transa == CUBLAS\_OP\_T}} \\
\end{matrix} \right.$


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLASXt API 上下文的句柄。 |
| uplo |  | 输入 | 指示矩阵 C 的下三角还是上三角部分被存储，另一个对称部分未被引用，而是从存储的元素中推断。 |
| trans |  | 输入 | 操作 op(A)，即非转置或转置。 |
| n |  | 输入 | 矩阵 op(A) 和 C 的行数。 |
| k |  | 输入 | 矩阵 op(A) 的列数。 |
| alpha | 主机端 | 输入 | 用于乘法的 <type> 标量。 |
| A | 主机端或设备端 | 输入 | <type> 数组，当 trans == CUBLAS_OP_N 时维度为 lda x k，lda >= max(1, n)；否则为 lda x n，lda >= max(1, k)。 |
| lda |  | 输入 | 用于存储矩阵 A 的二维数组的主维度。 |
| beta | 主机端 | 输入 | 用于乘法的 <type> 标量，如果 beta == 0，则 C 不必是有效输入。 |
| C | 主机端或设备端 | 输入/输出 | <type> 数组，维度为 ldc x n，ldc >= max(1, n)。 |
| ldc |  | 输入 | 用于存储矩阵 C 的二维数组的主维度。 |


此函数可能返回的错误值及其含义如下所述。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 参数 n < 0 或 k < 0 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |


参考文献请参阅 NETLIB 文档：


[ssyrk()](http://www.netlib.org/blas/ssyrk.f)、[dsyrk()](http://www.netlib.org/blas/dsyrk.f)、[csyrk()](http://www.netlib.org/blas/csyrk.f)、[zsyrk()](http://www.netlib.org/blas/zsyrk.f)





### 4.4.5. cublasXt<t>syr2k()



```c++

cublasStatus_t cublasXtSsyr2k(cublasXtHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            size_t n, size_t k,
                            const float           *alpha,
                            const float           *A, size_t lda,
                            const float           *B, size_t ldb,
                            const float           *beta,
                            float           *C, size_t ldc)
cublasStatus_t cublasXtDsyr2k(cublasXtHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            size_t n, size_t k,
                            const double          *alpha,
                            const double          *A, size_t lda,
                            const double          *B, size_t ldb,
                            const double          *beta,
                            double          *C, size_t ldc)
cublasStatus_t cublasXtCsyr2k(cublasXtHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            size_t n, size_t k,
                            const cuComplex       *alpha,
                            const cuComplex       *A, size_t lda,
                            const cuComplex       *B, size_t ldb,
                            const cuComplex       *beta,
                            cuComplex       *C, size_t ldc)
cublasStatus_t cublasXtZsyr2k(cublasXtHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            size_t n, size_t k,
                            const cuDoubleComplex *alpha,
                            const cuDoubleComplex *A, size_t lda,
                            const cuDoubleComplex *B, size_t ldb,
                            const cuDoubleComplex *beta,
                            cuDoubleComplex *C, size_t ldc)


```


此函数执行对称秩-$2k$ 更新


$C = \alpha(\text{op}(A)\text{op}(B)^{T} + \text{op}(B)\text{op}(A)^{T}) + \beta C$


其中 $\alpha$ 和 $\beta$ 是标量，$C$ 是按下三角或上三角模式存储的对称矩阵，$A$ 和 $B$ 是维度分别为 $\text{op}(A)$ $n \times k$ 和 $\text{op}(B)$ $n \times k$ 的矩阵。此外，对于矩阵 $A$ 和 $B$


$\text{op(}A\text{) and op(}B\text{)} = \left\{ \begin{matrix}
{A\text{ and }B} & {\text{if }\textsf{trans == CUBLAS\_OP\_N}} \\
{A^{T}\text{ and }B^{T}} & {\text{if }\textsf{trans == CUBLAS\_OP\_T}} \\
\end{matrix} \right.$


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLASXt API 上下文的句柄。 |
| uplo |  | 输入 | 指示矩阵 C 的下三角还是上三角部分被存储，另一个对称部分未被引用，而是从存储的元素中推断。 |
| trans |  | 输入 | 操作 op(A)，即非转置或转置。 |
| n |  | 输入 | 矩阵 op(A)、op(B) 和 C 的行数。 |
| k |  | 输入 | 矩阵 op(A) 和 op(B) 的列数。 |
| alpha | 主机端 | 输入 | 用于乘法的 <type> 标量。 |
| A | 主机端或设备端 | 输入 | <type> 数组，当 transa == CUBLAS_OP_N 时维度为 lda x k，lda >= max(1, n)；否则为 lda x n，lda >= max(1, k)。 |
| lda |  | 输入 | 用于存储矩阵 A 的二维数组的主维度。 |
| B | 主机端或设备端 | 输入 | <type> 数组，当 transb == CUBLAS_OP_N 时维度为 ldb x k，ldb >= max(1, n)；否则为 ldb x n，ldb >= max(1, k)。 |
| ldb |  | 输入 | 用于存储矩阵 B 的二维数组的主维度。 |
| beta | 主机端 | 输入 | 用于乘法的 <type> 标量，如果 beta == 0，则 C 不必是有效输入。 |
| C | 主机端或设备端 | 输入/输出 | <type> 数组，维度为 ldc x n，ldc >= max(1, n)。 |
| ldc |  | 输入 | 用于存储矩阵 C 的二维数组的主维度。 |


此函数可能返回的错误值及其含义如下所述。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 参数 n < 0 或 k < 0 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |


参考文献请参阅 NETLIB 文档：


[ssyr2k()](http://www.netlib.org/blas/ssyr2k.f)、[dsyr2k()](http://www.netlib.org/blas/dsyr2k.f)、[csyr2k()](http://www.netlib.org/blas/csyr2k.f)、[zsyr2k()](http://www.netlib.org/blas/zsyr2k.f)





### 4.4.6. cublasXt<t>syrkx()



```c++

cublasStatus_t cublasXtSsyrkx(cublasXtHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            size_t n, size_t k,
                            const float           *alpha,
                            const float           *A, size_t lda,
                            const float           *B, size_t ldb,
                            const float           *beta,
                            float           *C, size_t ldc)
cublasStatus_t cublasXtDsyrkx(cublasXtHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            size_t n, size_t k,
                            const double          *alpha,
                            const double          *A, size_t lda,
                            const double          *B, size_t ldb,
                            const double          *beta,
                            double          *C, size_t ldc)
cublasStatus_t cublasXtCsyrkx(cublasXtHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            size_t n, size_t k,
                            const cuComplex       *alpha,
                            const cuComplex       *A, size_t lda,
                            const cuComplex       *B, size_t ldb,
                            const cuComplex       *beta,
                            cuComplex       *C, size_t ldc)
cublasStatus_t cublasXtZsyrkx(cublasXtHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            size_t n, size_t k,
                            const cuDoubleComplex *alpha,
                            const cuDoubleComplex *A, size_t lda,
                            const cuDoubleComplex *B, size_t ldb,
                            const cuDoubleComplex *beta,
                            cuDoubleComplex *C, size_t ldc)


```


此函数执行对称秩-$k$ 更新的变体


$C = \alpha(\text{op}(A)\text{op}(B)^{T} + \beta C$


其中 $\alpha$ 和 $\beta$ 是标量，$C$ 是按下三角或上三角模式存储的对称矩阵，$A$ 和 $B$ 是维度分别为 $\text{op}(A)$ $n \times k$ 和 $\text{op}(B)$ $n \times k$ 的矩阵。此外，对于矩阵 $A$ 和 $B$


$\text{op(}A\text{) and op(}B\text{)} = \left\{ \begin{matrix}
{A\text{ and }B} & {\text{if }\textsf{trans == CUBLAS\_OP\_N}} \\
{A^{T}\text{ and }B^{T}} & {\text{if }\textsf{trans == CUBLAS\_OP\_T}} \\
\end{matrix} \right.$


当 B 以使得结果保证对称的方式存在时，可以使用此例程。一个常见的例子是当矩阵 B 是矩阵 A 的缩放形式时：这等价于 B 是矩阵 A 与对角矩阵的乘积。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLASXt API 上下文的句柄。 |
| uplo |  | 输入 | 指示矩阵 C 的下三角还是上三角部分被存储，另一个对称部分未被引用，而是从存储的元素中推断。 |
| trans |  | 输入 | 操作 op(A)，即非转置或转置。 |
| n |  | 输入 | 矩阵 op(A)、op(B) 和 C 的行数。 |
| k |  | 输入 | 矩阵 op(A) 和 op(B) 的列数。 |
| alpha | 主机端 | 输入 | 用于乘法的 <type> 标量。 |
| A | 主机端或设备端 | 输入 | <type> 数组，当 transa == CUBLAS_OP_N 时维度为 lda x k，lda >= max(1, n)；否则为 lda x n，lda >= max(1, k)。 |
| lda |  | 输入 | 用于存储矩阵 A 的二维数组的主维度。 |
| B | 主机端或设备端 | 输入 | <type> 数组，当 transb == CUBLAS_OP_N 时维度为 ldb x k，ldb >= max(1, n)；否则为 ldb x n，ldb >= max(1, k)。 |
| ldb |  | 输入 | 用于存储矩阵 B 的二维数组的主维度。 |
| beta | 主机端 | 输入 | 用于乘法的 <type> 标量，如果 beta == 0，则 C 不必是有效输入。 |
| C | 主机端或设备端 | 输入/输出 | <type> 数组，维度为 ldc x n，ldc >= max(1, n)。 |
| ldc |  | 输入 | 用于存储矩阵 C 的二维数组的主维度。 |


此函数可能返回的错误值及其含义如下所述。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 参数 n < 0 或 k < 0 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |


参考文献请参阅 NETLIB 文档：


[ssyrk()](http://www.netlib.org/blas/ssyrk.f)、[dsyrk()](http://www.netlib.org/blas/dsyrk.f)、[csyrk()](http://www.netlib.org/blas/csyrk.f)、[zsyrk()](http://www.netlib.org/blas/zsyrk.f) 和


[ssyr2k()](http://www.netlib.org/blas/ssyr2k.f)、[dsyr2k()](http://www.netlib.org/blas/dsyr2k.f)、[csyr2k()](http://www.netlib.org/blas/csyr2k.f)、[zsyr2k()](http://www.netlib.org/blas/zsyr2k.f)





### 4.4.7. cublasXt<t>herk()



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


此函数执行 Hermitian 秩-$k$ 更新


$C = \alpha\text{op}(A)\text{op}(A)^{H} + \beta C$


其中 $\alpha$ 和 $\beta$ 是标量，$C$ 是按下三角或上三角模式存储的 Hermitian 矩阵，$A$ 是维度为 $\text{op}(A)$ $n \times k$ 的矩阵。此外，对于矩阵 $A$


$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{transa == CUBLAS\_OP\_N}} \\
A^{H} & {\text{if }\textsf{transa == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLASXt API 上下文的句柄。 |
| uplo |  | 输入 | 指示矩阵 C 的下三角还是上三角部分被存储，另一个 Hermitian 部分未被引用。 |
| trans |  | 输入 | 操作 op(A)，即非转置或（共轭）转置。 |
| n |  | 输入 | 矩阵 op(A) 和 C 的行数。 |
| k |  | 输入 | 矩阵 op(A) 的列数。 |
| alpha | 主机端 | 输入 | 用于乘法的 <type> 标量。 |
| A | 主机端或设备端 | 输入 | <type> 数组，当 transa == CUBLAS_OP_N 时维度为 lda x k，lda >= max(1, n)；否则为 lda x n，lda >= max(1, k)。 |
| lda |  | 输入 | 用于存储矩阵 A 的二维数组的主维度。 |
| beta | 主机端 | 输入 | 用于乘法的 <type> 标量，如果 beta == 0，则 C 不必是有效输入。 |
| C | 主机端或设备端 | 输入/输出 | <type> 数组，维度为 ldc x n，ldc >= max(1, n)。对角线元素的虚部被假定并设置为零。 |
| ldc |  | 输入 | 用于存储矩阵 C 的二维数组的主维度。 |


此函数可能返回的错误值及其含义如下所述。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 参数 n < 0 或 k < 0 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |


参考文献请参阅 NETLIB 文档：


[cherk()](http://www.netlib.org/blas/cherk.f)、[zherk()](http://www.netlib.org/blas/zherk.f)





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


此函数执行 Hermitian 秩-$2k$ 更新


$C = \alpha\text{op}(A)\text{op}(B)^{H} + \overset{ˉ}{\alpha}\text{op}(B)\text{op}(A)^{H} + \beta C$


其中 $\alpha$ 和 $\beta$ 是标量，$C$ 是按下三角或上三角模式存储的 Herm