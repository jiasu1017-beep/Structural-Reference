### 3.4.43. cublasLtMatrixTransformDescCreate()

```c++

cublasStatus_t cublasLtMatrixTransformDescCreate(
      cublasLtMatrixTransformDesc_t *transformDesc,
      cudaDataType scaleType);


```

此函数通过分配保存其不透明结构所需的内存来创建矩阵变换描述符。

**参数**：

| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| transformDesc |  | 输出 | 指向由此函数创建的矩阵变换描述符结构体的指针。请参阅 cublasLtMatrixTransformDesc_t。 |
| scaleType |  | 输入 | 指定此函数创建的矩阵变换描述符数据精度的枚举值。请参阅 cudaDataType_t。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | 如果无法分配内存。 |
| CUBLAS_STATUS_SUCCESS | 如果描述符创建成功。 |

有关有效返回代码的完整列表，请参阅 cublasStatus_t。