### 3.4.19. cublasLtMatmulAlgoCheck()

```c++

cublasStatus_t cublasLtMatmulAlgoCheck(
      cublasLtHandle_t lightHandle,
      cublasLtMatmulDesc_t operationDesc,
      cublasLtMatrixLayout_t Adesc,
      cublasLtMatrixLayout_t Bdesc,
      cublasLtMatrixLayout_t Cdesc,
      cublasLtMatrixLayout_t Ddesc,
      const cublasLtMatmulAlgo_t *algo,
      cublasLtMatmulHeuristicResult_t *result);


```

此函数对矩阵乘法操作 `cublasLtMatmul()` 函数的矩阵乘法算法描述符进行正确性检查，输入矩阵为 A、B 和 C，输出矩阵为 D。它检查该描述符在当前设备上是否受支持，并返回包含所需工作区大小和计算波计数的结果。

> **注意**
>
> `CUBLAS_STATUS_SUCCESS` 并不能完全保证算法能够运行。例如，如果缓冲区未正确对齐，算法将失败。但是，如果 `cublasLtMatmulAlgoCheck()` 失败，算法将不会运行。

**参数**：

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| lightHandle |  | 输入 | 指向为 cuBLASLt 上下文分配的 cuBLASLt 句柄的指针。请参见 `cublasLtHandle_t`。 |
| operationDesc |  | 输入 | 指向先前创建的矩阵乘法描述符（类型为 `cublasLtMatmulDesc_t`）的句柄。 |
| Adesc、Bdesc、Cdesc 和 Ddesc |  | 输入 | 指向先前创建的矩阵布局描述符（类型为 `cublasLtMatrixLayout_t`）的句柄。 |
| algo |  | 输入 | 指定应使用哪种矩阵乘法算法的描述符。请参见 `cublasLtMatmulAlgo_t`。可以指向 `result->algo`。 |
| result |  | 输出 | 指向此函数返回结果结构的指针。结果包含所需的工作区大小和计算的波计数。`algo` 字段不会被更新。请参见 `cublasLtMatmulHeuristicResult_t`。 |

**返回**：

| 返回值 | 描述 |
| --- | --- |
| `CUBLAS_STATUS_INVALID_VALUE` | 如果矩阵布局描述符或操作描述符与算法描述符不匹配。 |
| `CUBLAS_STATUS_NOT_SUPPORTED` | 如果当前设备上不支持该算法配置或数据类型组合。 |
| `CUBLAS_STATUS_ARCH_MISMATCH` | 如果所选设备无法运行该算法配置。 |
| `CUBLAS_STATUS_SUCCESS` | 如果检查成功。 |

有关完整的有效返回代码列表，请参见 `cublasStatus_t`。