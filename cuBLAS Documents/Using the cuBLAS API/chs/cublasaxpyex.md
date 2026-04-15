### 2.8.21. cublasAxpyEx()

```c++

cublasStatus_t cublasAxpyEx (cublasHandle_t handle,
                             int n,
                             const void *alpha,
                             cudaDataType alphaType,
                             const void *x,
                             cudaDataType xType,
                             int incx,
                             void *y,
                             cudaDataType yType,
                             int incy,
                             cudaDataType executiontype);


```

此函数支持64位整数接口。

此函数是对cublas<t>axpy() routine的API泛化，允许独立指定输入数据、输出数据和计算类型。

此函数将向量`x`乘以标量$\alpha$，然后加到向量`y`上，用结果覆盖最新的向量。因此，执行的操作是$\mathbf{y}\lbrack j\rbrack = \alpha \times \mathbf{x}\lbrack k\rbrack + \mathbf{y}\lbrack j\rbrack$，其中$i = 1,\ldots,n$，$k = 1 + \left( {i - 1} \right)*\text{incx}$，$j = 1 + \left( {i - 1} \right)*\text{incy}$。注意，最后两个公式反映了为与Fortran兼容而使用的1-based索引。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS库上下文的句柄。 |
| n |  | 输入 | 向量x和y中的元素数量。 |
| alpha | 主机或设备 | 输入 | 用于乘法的<type>标量。 |
| alphaType |  | 输入 | 指定标量alpha数据类型的枚举类型。 |
| x | 设备 | 输入 | 具有n个元素的<type>向量。 |
| xType |  | 输入 | 指定向量x数据类型的枚举类型。 |
| incx |  | 输入 | x中连续元素之间的步长。 |
| y | 设备 | 输入/输出 | 具有n个元素的<type>向量。 |
| yType |  | 输入 | 指定向量y数据类型的枚举类型。 |
| incy |  | 输入 | y中连续元素之间的步长。 |
| executionType |  | 输入 | 指定计算执行数据类型的枚举类型。 |

cublasAxpyEx()当前支持的数据类型组合如下表所示：

| alpha | x | y | execution |
| --- | --- | --- | --- |
| CUDA_R_32F | CUDA_R_16F | CUDA_R_16F | CUDA_R_32F |
| CUDA_R_32F | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_32F |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_32F | CUDA_R_32F |
| CUDA_R_64F | CUDA_R_64F | CUDA_R_64F | CUDA_R_64F |
| CUDA_C_32F | CUDA_C_32F | CUDA_C_32F | CUDA_C_32F |
| CUDA_C_64F | CUDA_C_64F | CUDA_C_64F | CUDA_C_64F |

此函数可能返回的错误值及其含义如下表所列。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |
| CUBLAS_STATUS_NOT_SUPPORTED | xType、yType和executionType的组合不支持。 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在GPU上启动失败。 |
| CUBLAS_STATUS_INVALID_VALUE | alphaType或xType或yType或executionType不支持。 |

有关参考资料，请参阅NETLIB文档：

[saxpy()](http://www.netlib.org/blas/saxpy.f), [daxpy()](http://www.netlib.org/blas/daxpy.f), [caxpy()](http://www.netlib.org/blas/caxpy.f), [zaxpy()](http://www.netlib.org/blas/zaxpy.f)