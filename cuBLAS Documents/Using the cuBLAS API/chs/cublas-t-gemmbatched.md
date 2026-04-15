### 2.7.3. cublas<t>gemmBatched()



```c++

cublasStatus_t cublasHgemmBatched(cublasHandle_t handle,
                                  cublasOperation_t transa,
                                  cublasOperation_t transb,
                                  int m, int n, int k,
                                  const __half          *alpha,
                                  const __half          *const Aarray[], int lda,
                                  const __half          *const Barray[], int ldb,
                                  const __half          *beta,
                                  __half          *const Carray[], int ldc,
                                  int batchCount)
// 半精度浮点型矩阵批次乘法
cublasStatus_t cublasSgemmBatched(cublasHandle_t handle,
                                  cublasOperation_t transa,
                                  cublasOperation_t transb,
                                  int m, int n, int k,
                                  const float           *alpha,
                                  const float           *const Aarray[], int lda,
                                  const float           *const Barray[], int ldb,
                                  const float           *beta,
                                  float           *const Carray[], int ldc,
                                  int batchCount)
// 单精度浮点型矩阵批次乘法
cublasStatus_t cublasDgemmBatched(cublasHandle_t handle,
                                  cublasOperation_t transa,
                                  cublasOperation_t transb,
                                  int m, int n, int k,
                                  const double          *alpha,
                                  const double          *const Aarray[], int lda,
                                  const double          *const Barray[], int ldb,
                                  const double          *beta,
                                  double          *const Carray[], int ldc,
                                  int batchCount)
// 双精度浮点型矩阵批次乘法
cublasStatus_t cublasCgemmBatched(cublasHandle_t handle,
                                  cublasOperation_t transa,
                                  cublasOperation_t transb,
                                  int m, int n, int k,
                                  const cuComplex       *alpha,
                                  const cuComplex       *const Aarray[], int lda,
                                  const cuComplex       *const Barray[], int ldb,
                                  const cuComplex       *beta,
                                  cuComplex       *const Carray[], int ldc,
                                  int batchCount)
// 复数型矩阵批次乘法
cublasStatus_t cublasZgemmBatched(cublasHandle_t handle,
                                  cublasOperation_t transa,
                                  cublasOperation_t transb,
                                  int m, int n, int k,
                                  const cuDoubleComplex *alpha,
                                  const cuDoubleComplex *const Aarray[], int lda,
                                  const cuDoubleComplex *const Barray[], int ldb,
                                  const cuDoubleComplex *beta,
                                  cuDoubleComplex *const Carray[], int ldc,
                                  int batchCount)
// 双精度复数型矩阵批次乘法


```


此函数支持64位整数接口。

此函数执行矩阵批次的矩阵-矩阵乘法。批次被视为"均匀的"，即所有实例具有相同的维度(m, n, k)、前导维度(lda, ldb, ldc)以及各自A、B和C矩阵的转置(transa, transb)。每个批次实例的输入矩阵和输出矩阵的地址从调用者传递给函数的指针数组中读取。


$C\lbrack i\rbrack = \alpha\text{op}(A\lbrack i\rbrack)\text{op}(B\lbrack i\rbrack) + \beta C\lbrack i\rbrack,\text{ for i } \in \lbrack 0,batchCount - 1\rbrack$


其中$\alpha$和$\beta$是标量，$A$、$B$和$C$是指向矩阵的指针数组，这些矩阵以列主序格式存储，维度分别为$\text{op}(A\lbrack i\rbrack)$ $m \times k$、$\text{op}(B\lbrack i\rbrack)$ $k \times n$和$C\lbrack i\rbrack$ $m \times n$。此外，对于矩阵$A$


$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{transa == CUBLAS\_OP\_N}} \\
A^{T} & {\text{if }\textsf{transa == CUBLAS\_OP\_T}} \\
A^{H} & {\text{if }\textsf{transa == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$


且$\text{op}(B\lbrack i\rbrack)$对矩阵$B\lbrack i\rbrack$的定义类似。


> **注意**

注意
\(C\lbrack i\rbrack\)矩阵不得重叠，即各个gemm操作必须能够独立计算；否则将产生未定义行为。

在某些问题规模下，在不同的CUDA流中多次调用cublas<t>gemm()可能比使用此API更有优势。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS库上下文的句柄。 |
| transa |  | 输入 | op(A[i])操作，即非转置或(共)转置。 |
| transb |  | 输入 | op(B[i])操作，即非转置或(共)转置。 |
| m |  | 输入 | 矩阵op(A[i])和C[i]的行数。 |
| n |  | 输入 | op(B[i])和C[i]的列数。 |
| k |  | 输入 | op(A[i])的列数和op(B[i])的行数。 |
| alpha | 主机或设备 | 输入 | 用于乘法的<type>标量。 |
| Aarray | 设备 | 输入 | 指向<type>数组的指针数组，每个数组维度为lda x k，当transa == CUBLAS_OP_N时lda >= max(1, m)，否则为lda x m且lda >= max(1, k)。
所有指针必须满足特定的对齐要求。请参阅下文了解更多详情。 |
| lda |  | 输入 | 用于存储每个矩阵A[i]的二维数组的前导维度。 |
| Barray | 设备 | 输入 | 指向<type>数组的指针数组，每个数组维度为ldb x n，当transb == CUBLAS_OP_N时ldb >= max(1, k)，否则为ldb x k且ldb >= max(1,n)。
所有指针必须满足特定的对齐要求。请参阅下文了解更多详情。 |
| ldb |  | 输入 | 用于存储每个矩阵B[i]的二维数组的前导维度。 |
| beta | 主机或设备 | 输入 | 用于乘法的<type>标量。如果beta == 0，C不必是有效的输入。 |
| Carray | 设备 | 输入/输出 | 指向<type>数组的指针数组。维度为ldc x n，ldc >= max(1, m)。矩阵C[i]不应重叠；否则将产生未定义行为。
所有指针必须满足特定的对齐要求。请参阅下文了解更多详情。 |
| ldc |  | 输入 | 用于存储每个矩阵C[i]的二维数组的前导维度。 |
| batchCount |  | 输入 | Aarray、Barray和Carray中包含的指针数量。 |


如果数学模式在使用cublasSgemmBatched()时启用了快速数学模式，则放置在GPU内存中的指针（而非指针数组）必须正确对齐以避免未对齐内存访问错误。理想情况下，所有指针应至少对齐到16字节。否则，建议它们满足以下规则：


- 如果k % 4 == 0，则确保intptr_t(ptr) % 16 == 0，


此函数可能返回的错误值及其含义如下所述。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果m < 0或n < 0或k < 0，或
如果transa和transb不是CUBLAS_OP_N、CUBLAS_OP_C、CUBLAS_OP_T之一，或
如果当transa == CUBLAS_OP_N时lda < max(1, m)且否则lda < max(1, k)，或
如果当transb == CUBLAS_OP_N时ldb < max(1, k)且否则ldb < max(1, n)，或
如果ldc < max(1, m) |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在GPU上启动失败 |
| CUBLAS_STATUS_ARCH_MISMATCH | cublasHgemmBatched()仅支持计算能力等于或大于5.3的GPU |