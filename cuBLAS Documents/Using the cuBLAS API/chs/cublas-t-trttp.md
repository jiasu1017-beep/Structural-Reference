### 2.8.10. cublas<t>trttp()

```c++

cublasStatus_t cublasStrttp ( cublasHandle_t handle,
                              cublasFillMode_t uplo,
                              int n,
                              const float *A,
                              int lda,
                              float *AP );

cublasStatus_t cublasDtrttp ( cublasHandle_t handle,
                              cublasFillMode_t uplo,
                              int n,
                              const double *A,
                              int lda,
                              double *AP );

cublasStatus_t cublasCtrttp ( cublasHandle_t handle,
                              cublasFillMode_t uplo,
                              int n,
                              const cuComplex *A,
                              int lda,
                              cuComplex *AP );

cublasStatus_t cublasZtrttp ( cublasHandle_t handle,
                              cublasFillMode_t uplo,
                              int n,
                              const cuDoubleComplex *A,
                              int lda,
                              cuDoubleComplex *AP );

```

此函数执行从三角格式到压缩三角格式的转换。

如果 `uplo == CUBLAS_FILL_MODE_LOWER`，则将三角矩阵 `A` 的下三角部分复制到数组 `AP` 中。如果 `uplo == CUBLAS_FILL_MODE_UPPER`，则将三角矩阵 `A` 的上三角部分复制到数组 `AP` 中。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS 库上下文的句柄。 |
| uplo |  | input | 指示引用矩阵 A 的下三角还是上三角部分。 |
| n |  | input | 矩阵 A 的行数和列数。 |
| A | device | input | 尺寸为 lda × n 的 <type> 数组，其中 lda >= max(1, n)。 |
| lda |  | input | 用于存储矩阵 A 的二维数组的主维。 |
| AP | device | output | 以压缩格式存储 A 的 <type> 数组。 |

此函数返回的可能错误值及其含义如下所示。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0，或 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或 lda < max(1, n)。 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在 GPU 上启动失败。 |

有关参考信息，请参阅 NETLIB 文档：

[strttp()](http://www.netlib.org/lapack/explore-html/d9/def/strttp_8f.html)、[dtrttp()](http://www.netlib.org/lapack/explore-html/d0/daf/dtrttp_8f.html)、[ctrttp()](http://www.netlib.org/lapack/explore-html/d7/d56/ctrttp_8f.html)、[ztrttp()](http://www.netlib.org/lapack/explore-html/da/dc2/ztrttp_8f.html)