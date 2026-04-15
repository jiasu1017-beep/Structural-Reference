### 2.5.2. cublasI<t>amin()

```c++

cublasStatus_t cublasIsamin(cublasHandle_t handle, int n,
                            const float *x, int incx, int *result)
cublasStatus_t cublasIdamin(cublasHandle_t handle, int n,
                            const double *x, int incx, int *result)
cublasStatus_t cublasIcamin(cublasHandle_t handle, int n,
                            const cuComplex *x, int incx, int *result)
cublasStatus_t cublasIzamin(cublasHandle_t handle, int n,
                            const cuDoubleComplex *x, int incx, int *result)


```

此函数支持64位整数接口。

此函数查找最小幅度元素的（最小）索引。因此，结果是第一个满足以下条件的 $i$：对于 $i = 1,\ldots,n$ 和 $j = 1 + \left( {i - 1} \right)*\text{incx}$，使得 $\left| \mathbf{Im}\left( {x\lbrack j\rbrack} \right) \middle| + \middle| \mathbf{Re}\left( {x\lbrack j\rbrack} \right) \right|$ 最小。请注意，上式反映了为与Fortran兼容而使用的1-based索引。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS库上下文的句柄。 |
| n |  | 输入 | 向量x中的元素数量。 |
| x | 设备 | 输入 | 包含元素的<type>类型向量。 |
| incx |  | 输入 | x连续元素之间的步长。 |
| result | 主机或设备 | 输出 | 结果索引，如果n <= 0或incx <= 0，则设置为0。 |


此函数返回的可能错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_ALLOC_FAILED | 无法分配归约缓冲区 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在GPU上启动失败 |
| CUBLAS_STATUS_INVALID_VALUE | result为NULL |


有关参考资料，请参阅NETLIB文档：


[isamin()](http://www.netlib.org/scilib/blass.f)