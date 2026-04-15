### 3.4.25. cublasLtMatmulDescCreate()



```c++

cublasStatus_t cublasLtMatmulDescCreate( cublasLtMatmulDesc_t *matmulDesc,
                                         cublasComputeType_t computeType,
                                         cudaDataType_t scaleType);

```


此函数通过分配用于保存其不透明结构的内存来创建矩阵乘法描述符。


**参数**：


| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| matmulDesc |  | 输出 | 指向由此函数创建的矩阵乘法描述符所保存结构的指针。参见 cublasLtMatmulDesc_t。 |
| computeType |  | 输入 | 枚举类型，指定此函数创建的矩阵乘法描述符的数据精度。参见 cublasComputeType_t。 |
| scaleType |  | 输入 | 枚举类型，指定此函数创建的矩阵变换描述符的数据精度。参见 cudaDataType_t。 |


**返回值**：


| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | 如果无法分配内存。 |
| CUBLAS_STATUS_SUCCESS | 如果描述符创建成功。 |


有关有效返回代码的完整列表，请参见 cublasStatus_t。