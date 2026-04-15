### 2.8.20. cublasNrm2Ex()

```c++
cublasStatus_t  cublasNrm2Ex( cublasHandle_t handle,
                              int n,
                              const void *x,
                              cudaDataType xType,
                              int incx,
                              void *result,
                              cudaDataType resultType,
                              cudaDataType executionType)
```


此函数支持64位整数接口。

此函数是例程cublas<t>nrm2()的API泛化版本，其中输入数据、输出数据和计算类型可以独立指定。

此函数计算向量`x`的欧几里得范数。该代码使用多阶段累积模型来避免中间的下溢和溢出，其结果等价于 $\sqrt{\sum_{i = 1}^{n}\left( {\mathbf{x}\lbrack j\rbrack \times \mathbf{x}\lbrack j\rbrack} \right)}$，其中 $j = 1 + \left( {i - 1} \right)*\text{incx}$（精确算术）。请注意，最后一个公式反映了为与Fortran兼容而使用的1-based索引。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS库上下文的句柄。 |
| n |  | input | 向量x中的元素数量。 |
| x | device | input | 包含n个元素的<type>向量。 |
| xType |  | input | 指定向量x数据类型的枚举符。 |
| incx |  | input | 向量x中连续元素之间的步长。 |
| result | host or device | output | 计算得到的范数，如果n <= 0或incx <= 0则设置为0。 |
| resultType |  | input | 指定结果数据类型的枚举符。 |
| executionType |  | input | 指定执行计算所使用的数据类型的枚举符。 |

cublasNrm2Ex()当前支持的数据类型组合如下：

| x | result | execution |
| --- | --- | --- |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_32F |
| CUDA_R_16BF | CUDA_R_16BF | CUDA_R_32F |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_32F |
| CUDA_C_32F | CUDA_R_32F | CUDA_R_32F |
| CUDA_R_64F | CUDA_R_64F | CUDA_R_64F |
| CUDA_C_64F | CUDA_R_64F | CUDA_R_64F |

此函数可能返回的错误值及其含义如下：

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_ALLOC_FAILED | 无法分配归约缓冲区 |
| CUBLAS_STATUS_NOT_SUPPORTED | xType、resultType和executionType的组合不支持 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在GPU上启动 |
| CUBLAS_STATUS_INVALID_VALUE | 如果xType、resultType或executionType不支持，或者result为NULL |

有关参考文献，请参阅NETLIB文档：

[snrm2()](http://www.netlib.org/blas/snrm2.f90), [dnrm2()](http://www.netlib.org/blas/dnrm2.f90), [scnrm2()](http://www.netlib.org/blas/scnrm2.f90), [dznrm2()](http://www.netlib.org/blas/dznrm2.f90)