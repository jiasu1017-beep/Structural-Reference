### 2.8.9. cublas<t>tpttr()



```c++

cublasStatus_t cublasStpttr ( cublasHandle_t handle,
                              cublasFillMode_t uplo,
                              int n,
                              const float *AP,
                              float *A,
                              int lda );

cublasStatus_t cublasDtpttr ( cublasHandle_t handle,
                              cublasFillMode_t uplo,
                              int n,
                              const double *AP,
                              double *A,
                              int lda );

cublasStatus_t cublasCtpttr ( cublasHandle_t handle,
                              cublasFillMode_t uplo,
                              int n,
                              const cuComplex *AP,
                              cuComplex *A,
                              int lda );

cublasStatus_t cublasZtpttr ( cublasHandle_t handle,
                              cublasFillMode_t uplo,
                              int n,
                              const cuDoubleComplex *AP,
                              cuDoubleComplex *A,
                              int lda );


```


此函数执行从三角压缩格式到三角格式的转换。


如果 `uplo == CUBLAS_FILL_MODE_LOWER`，则 `AP` 的元素被复制到三角矩阵 `A` 的下三角部分，而 `A` 的上三角部分保持不变。如果 `uplo == CUBLAS_FILL_MODE_UPPER`，则 `AP` 的元素被复制到三角矩阵 `A` 的上三角部分，而 `A` 的下三角部分保持不变。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS 库上下文的句柄。 |
| uplo |  | 输入 | 指示矩阵 AP 是否包含矩阵 A 的下三角部分或上三角部分。 |
| n |  | 输入 | 矩阵 A 的行数和列数。 |
| AP | 设备端 | 输入 | 以压缩格式存储 \(A\) 的 <type> 数组。 |
| A | 设备端 | 输出 | 维度为 lda x n 的 <type> 数组，其中 lda >= max(1, n)。A 的相对侧保持不变。 |
| lda |  | 输入 | 用于存储矩阵 A 的二维数组的主维度。 |


此函数可能返回的错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0，或
如果 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或
如果 lda < max(1, n) |
| CUBLAS_STATUS_EXECUTION_FAILED | 该函数在 GPU 上启动失败 |


有关参考资料，请参阅 NETLIB 文档：


[stpttr()](http://www.netlib.org/lapack/explore-html/d7/d70/stpttr_8f.html)、[dtpttr()](http://www.netlib.org/lapack/explore-html/df/d63/dtpttr_8f.html)、[ctpttr()](http://www.netlib.org/lapack/explore-html/de/d13/ctpttr_8f.html)、[ztpttr()](http://www.netlib.org/lapack/explore-html/d6/dbc/ztpttr_8f.html)