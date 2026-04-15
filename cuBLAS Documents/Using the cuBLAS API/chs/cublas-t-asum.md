### 2.5.3. cublas<t>asum()



```c++

cublasStatus_t  cublasSasum(cublasHandle_t handle, int n,
                            const float           *x, int incx, float  *result)
cublasStatus_t  cublasDasum(cublasHandle_t handle, int n,
                            const double          *x, int incx, double *result)
cublasStatus_t cublasScasum(cublasHandle_t handle, int n,
                            const cuComplex       *x, int incx, float  *result)
cublasStatus_t cublasDzasum(cublasHandle_t handle, int n,
                            const cuDoubleComplex *x, int incx, double *result)


```


此函数支持 64 位整数接口。


此函数计算向量 `x` 元素绝对值之和。因此，结果为 $\left. \sum_{i = 1}^{n} \middle| \mathbf{Im}\left( {x\lbrack j\rbrack} \right) \middle| + \middle| \mathbf{Re}\left( {x\lbrack j\rbrack} \right) \right|$，其中 $j = 1 + \left( {i - 1} \right)*\text{incx}$。请注意，上式反映的是为与 Fortran 兼容而使用的 1 基索引。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS 库上下文的句柄。 |
| n |  | 输入 | 向量 x 中的元素数量。 |
| x | 设备 | 输入 | 包含元素的 <type> 向量。 |
| incx |  | 输入 | x 连续元素之间的步长。 |
| result | 主机或设备 | 输出 | 结果之和，如果 n <= 0 或 incx <= 0，则设置为 0。 |


此函数可能返回的错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |
| CUBLAS_STATUS_ALLOC_FAILED | 无法分配归约缓冲区。 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动。 |
| CUBLAS_STATUS_INVALID_VALUE | result 为 NULL。 |


有关参考信息，请参阅 NETLIB 文档：


[sasum()](http://www.netlib.org/blas/sasum.f)、[dasum()](http://www.netlib.org/blas/dasum.f)、[scasum()](http://www.netlib.org/blas/scasum.f)、[dzasum()](http://www.netlib.org/blas/dzasum.f)