### 2.5.7. cublas<t>nrm2()



```c++

cublasStatus_t  cublasSnrm2(cublasHandle_t handle, int n,
                            const float           *x, int incx, float  *result)
cublasStatus_t  cublasDnrm2(cublasHandle_t handle, int n,
                            const double          *x, int incx, double *result)
cublasStatus_t cublasScnrm2(cublasHandle_t handle, int n,
                            const cuComplex       *x, int incx, float  *result)
cublasStatus_t cublasDznrm2(cublasHandle_t handle, int n,
                            const cuDoubleComplex *x, int incx, double *result)


```


此函数支持64位整数接口。


此函数计算向量 `x` 的欧几里得范数。该代码使用多阶段累积模型来避免中间的下溢和溢出，其结果等价于 $\sqrt{\sum_{i = 1}^{n}\left( {\mathbf{x}\lbrack j\rbrack \times \mathbf{x}\lbrack j\rbrack} \right)}$，其中 $j = 1 + \left( {i - 1} \right)*\text{incx}$ 在精确算术中。请注意，最后一个公式反映了为与Fortran兼容而使用的1-based索引。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS库上下文的句柄。 |
| n |  | 输入 | 向量x中元素的个数。 |
| x | device | 输入 | 具有n个元素的<type>类型向量。 |
| incx |  | 输入 | 向量x中连续元素之间的步长。 |
| result | host或device | 输出 | 计算得到的范数，如果 n <= 0 或 incx <= 0，则设置为0。 |


此函数可能返回的错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_ALLOC_FAILED | 无法分配归约缓冲区 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在GPU上启动失败 |
| CUBLAS_STATUS_INVALID_VALUE | result为NULL |


有关参考资料，请参阅NETLIB文档：


[snrm2()](http://www.netlib.org/blas/snrm2.f90), [dnrm2()](http://www.netlib.org/blas/dnrm2.f90), [scnrm2()](http://www.netlib.org/blas/scnrm2.f90), [dznrm2()](http://www.netlib.org/blas/dznrm2.f90)