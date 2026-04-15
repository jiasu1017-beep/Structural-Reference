### 2.6.9. cublas<t>syr()

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