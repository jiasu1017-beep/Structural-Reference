### 2.8.24. cublasScalEx()

```c++

cublasStatus_t  cublasScalEx(cublasHandle_t handle,
                             int n,
                             const void *alpha,
                             cudaDataType alphaType,
                             void *x,
                             cudaDataType xType,
                             int incx,
                             cudaDataType executionType);


```

此函数支持 64 位整数接口。

此函数将向量 `x` 按标量 $\alpha$ 进行缩放，并将结果覆盖回 `x`。因此，执行的操作为 $\mathbf{x}\lbrack j\rbrack = \alpha \times \mathbf{x}\lbrack j\rbrack$，其中 $i = 1,\ldots,n$ 且 $j = 1 + \left( {i - 1} \right)*\text{incx}$。请注意，上述两个公式使用的是 1-based 索引，这是为了与 Fortran 保持兼容。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS 库上下文的句柄。 |
| n |  | input | 向量 x 中的元素数量。 |
| alpha | host 或 device | input | 用于乘法的 <type> 标量。 |
| alphaType |  | input | 指定标量 alpha 数据类型的枚举常量。 |
| x | device | in/out | 具有 n 个元素的 <type> 向量。 |
| xType |  | input | 指定向量 x 数据类型的枚举常量。 |
| incx |  | input | 向量 x 中连续元素之间的步长。 |
| executionType |  | input | 指定执行计算所使用的数据类型的枚举常量。 |

以下是 cublasScalEx() 当前支持的数据类型组合：

| alpha | x | execution |
| --- | --- | --- |
| CUDA_R_32F | CUDA_R_16F | CUDA_R_32F |
| CUDA_R_32F | CUDA_R_16BF | CUDA_R_32F |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_32F |
| CUDA_R_64F | CUDA_R_64F | CUDA_R_64F |
| CUDA_C_32F | CUDA_C_32F | CUDA_C_32F |
| CUDA_C_64F | CUDA_C_64F | CUDA_C_64F |

以下是此函数可能返回的错误值及其含义：

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_NOT_SUPPORTED | xType 和 executionType 的组合不支持 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在 GPU 上启动失败 |
| CUBLAS_STATUS_INVALID_VALUE | alphaType 或 xType 或 executionType 不支持 |

有关参考信息，请参阅 NETLIB 文档：

[sscal()](http://www.netlib.org/blas/sscal.f), [dscal()](http://www.netlib.org/blas/dscal.f), [csscal()](http://www.netlib.org/blas/csscal.f), [cscal()](http://www.netlib.org/blas/cscal.f), [zdscal()](http://www.netlib.org/blas/zdscal.f), [zscal()](http://www.netlib.org/blas/zscal.f)