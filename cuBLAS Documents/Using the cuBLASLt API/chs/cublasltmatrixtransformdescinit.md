### 3.4.44. cublasLtMatrixTransformDescInit()

```c++

cublasStatus_t cublasLtMatrixTransformDescInit(
      cublasLtMatrixTransformDesc_t transformDesc,
      cudaDataType scaleType);


```

此函数用于初始化先前已分配的矩阵变换描述符。

**参数**：

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| transformDesc |  | 输出 | 指向由此函数初始化的矩阵变换描述符结构体的指针。请参见 cublasLtMatrixTransformDesc_t。 |
| scaleType |  | 输入 | 指定此函数初始化的矩阵变换描述符数据精度的枚举值。请参见 cudaDataType_t。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | 如果无法分配内存。 |
| CUBLAS_STATUS_SUCCESS | 如果描述符创建成功。 |

有关有效的返回码完整列表，请参见 cublasStatus_t。