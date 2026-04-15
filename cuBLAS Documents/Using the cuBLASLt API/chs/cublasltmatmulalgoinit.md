### 3.4.24. cublasLtMatmulAlgoInit()

```c++

cublasStatus_t cublasLtMatmulAlgoInit(
      cublasLtHandle_t lightHandle,
      cublasComputeType_t computeType,
      cudaDataType_t scaleType,
      cudaDataType_t Atype,
      cudaDataType_t Btype,
      cudaDataType_t Ctype,
      cudaDataType_t Dtype,
      int algoId,
      cublasLtMatmulAlgo_t *algo);


```

此函数为 cublasLtMatmul() 初始化矩阵乘法算法结构，针对指定的矩阵乘法算法以及输入矩阵 A、B 和 C，以及输出矩阵 D。

**参数**：

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| lightHandle |  | Input | 指向为 cuBLASLt 上下文分配的 cuBLASLt 句柄的指针。请参阅 cublasLtHandle_t。 |
| computeType |  | Input | 计算类型。请参阅 cublasLtMatmulDescAttributes_t 的 CUBLASLT_MATMUL_DESC_COMPUTE_TYPE。 |
| scaleType |  | Input | 缩放类型。请参阅 cublasLtMatmulDescAttributes_t 的 CUBLASLT_MATMUL_DESC_SCALE_TYPE。通常与 computeType 相同。 |
| Atype, Btype, Ctype, and Dtype |  | Input | 输入和输出矩阵的数据类型精度。请参阅 cudaDataType_t。 |
| algoId |  | Input | 指定正在初始化的算法。应为 cublasLtMatmulAlgoGetIds() 函数返回的有效 algoId。 |
| algo |  | Input | 指向要初始化的不透明结构的指针。请参阅 cublasLtMatmulAlgo_t。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | 如果 algo 为 NULL 或 algoId 超出可识别范围。 |
| CUBLAS_STATUS_NOT_SUPPORTED | 如果 algoId 对于给定的数据类型组合不支持。 |
| CUBLAS_STATUS_SUCCESS | 如果结构体已成功初始化。 |

有关有效返回码的完整列表，请参阅 cublasStatus_t。