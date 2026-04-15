### 3.4.23. cublasLtMatmulAlgoGetIds()

```c++

cublasStatus_t cublasLtMatmulAlgoGetIds(
      cublasLtHandle_t lightHandle,
      cublasComputeType_t computeType,
      cudaDataType_t scaleType,
      cudaDataType_t Atype,
      cudaDataType_t Btype,
      cudaDataType_t Ctype,
      cudaDataType_t Dtype,
      int requestedAlgoCount,
      int algoIdsArray[],
      int *returnAlgoCount);


```

此函数检索对于给定输入矩阵 A、B、C 和输出矩阵 D 的数据类型，所有有效的矩阵乘法算法的 ID，这些算法可由 `cublasLtMatmul()` 函数潜在执行。

> **注意**
>
> 注意
> ID 的返回顺序不分先后。为确保最佳算法包含在列表中，请将 `requestedAlgoCount` 设置得足够大以接收完整列表。如果 `returnAlgoCount` < `requestedAlgoCount`，则列表保证是完整的。

**参数**：

| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| lightHandle |  | 输入 | 指向为 cuBLASLt 上下文分配的 cuBLASLt 句柄的指针。请参见 `cublasLtHandle_t`。 |
| computeType、scaleType、Atype、Btype、Ctype 和 Dtype |  | 输入 | 计算类型、缩放因子和操作数矩阵的数据类型。请参见 `cudaDataType_t`。 |
| requestedAlgoCount |  | 输入 | 请求的算法数量。必须 > 0。 |
| algoIdsArray[] |  | 输出 | 包含此函数返回的算法 ID 的数组。 |
| returnAlgoCount |  | 输出 | 此函数实际返回的算法数量。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | 如果 requestedAlgoCount 小于或等于零。 |
| CUBLAS_STATUS_SUCCESS | 如果查询成功。检查 returnAlgoCount 以获取可用的实际 ID 数量。 |

有关有效返回代码的完整列表，请参见 `cublasStatus_t`。