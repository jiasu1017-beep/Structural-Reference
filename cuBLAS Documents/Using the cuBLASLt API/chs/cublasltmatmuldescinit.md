### 3.4.26. cublasLtMatmulDescInit()

```c++

cublasStatus_t cublasLtMatmulDescInit( cublasLtMatmulDesc_t matmulDesc,
                                       cublasComputeType_t computeType,
                                       cudaDataType_t scaleType);


```


此函数初始化之前分配的矩阵乘法描述符。


**参数**：


| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| matmulDesc |  | 输出 | 指向保存此函数初始化的矩阵乘法描述符的结构的指针。参见 cublasLtMatmulDesc_t。 |
| computeType |  | 输入 | 指定此函数初始化的矩阵乘法描述符的数据精度的枚举值。参见 cublasComputeType_t。 |
| scaleType |  | 输入 | 指定此函数初始化的矩阵变换描述符的数据精度的枚举值。参见 cudaDataType_t。 |


**返回值**：


| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | 如果无法分配内存。 |
| CUBLAS_STATUS_SUCCESS | 如果描述符创建成功。 |


有关有效返回码的完整列表，请参见 cublasStatus_t。