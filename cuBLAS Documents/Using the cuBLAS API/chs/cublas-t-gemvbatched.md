### 2.6.24. cublas<t>gemvBatched()

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

#if defined(__cplusplus)
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
#endif


```

此函数支持64位整数接口。

此函数执行一批矩阵和向量的矩阵-向量乘法运算。该批次被认为是"均匀的"，即所有实例具有相同的维度(m, n)、主维度(lda)、增量(incx, incy)和转置(trans)，分别对应各自的A矩阵、x和y向量。批次中每个实例的输入矩阵和向量以及输出向量的地址从调用者传递给该函数的指针数组中读取。

$\textbf{y}\lbrack i\rbrack = \alpha\text{op}(A\lbrack i\rbrack)\textbf{x}\lbrack i\rbrack + \beta\textbf{y}\lbrack i\rbrack,\text{ for i} \in \lbrack 0,batchCount - 1\rbrack$

其中 $\alpha$ 和 $\beta$ 是标量，$A$ 是指向矩阵 $A\lbrack i\rbrack$ 的指针数组，以列优先格式存储，维度为 $m \times n$ ，而 $\textbf{x}$ 和 $\textbf{y}$ 是指向向量的指针数组。同样，对于矩阵 $A\lbrack i\rbrack$ ：

$\text{op}(A\lbrack i\rbrack) = \left\{ \begin{matrix}
{A\lbrack i\rbrack} & {\text{if }\textsf{trans == $\mathrm{CUBLAS\_OP\_N}$}} \\
{A\lbrack i\rbrack}^{T} & {\text{if }\textsf{trans == $\mathrm{CUBLAS\_OP\_T}$}} \\
{A\lbrack i\rbrack}^{H} & {\text{if }\textsf{trans == $\mathrm{CUBLAS\_OP\_C}$}} \\
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