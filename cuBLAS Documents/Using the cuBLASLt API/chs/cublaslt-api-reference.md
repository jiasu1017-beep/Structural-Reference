## 3.4. cuBLASLt API 参考文档

### 3.4.1. cublasLtCreate()

```c++
cublasStatus_t
      cublasLtCreate(cublasLtHandle_t *lighthandle)
```

此函数初始化 cuBLASLt 库并创建一个指向保存 cuBLASLt 库上下文的不透明结构体的句柄。它在主机和设备上分配轻量级硬件资源，必须在任何其他 cuBLASLt 库调用之前调用。

cuBLASLt 库上下文绑定到当前的 CUDA 设备。要在多个设备上使用该库，必须为每个设备创建一个 cuBLASLt 句柄。此外，在使用绑定到特定设备的句柄调用 cuBLASLt 函数之前，必须将该设备设置为当前设备。

另请参见：cuBLAS Context。

**参数：**

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| lightHandle |  | Output | 指向为创建的 cuBLASLt 上下文所分配的 cuBLASLt 句柄的指针。 |

**返回：**

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 分配成功完成。 |
| CUBLAS_STATUS_NOT_INITIALIZED | cuBLASLt 库未初始化。这通常发生在：<br>未首先调用 cublasLtCreate()、<br>cuBLASLt 例程调用的 CUDA Runtime API 出现错误，或<br>硬件设置错误。 |
| CUBLAS_STATUS_ALLOC_FAILED | cuBLASLt 库内部的资源分配失败。这通常由 cudaMalloc() 失败引起。<br>更正方法：在函数调用之前，尽可能释放先前分配的内存。 |
| CUBLAS_STATUS_INVALID_VALUE | lightHandle 为 NULL |

有关有效返回代码的完整列表，请参见 cublasStatus_t。

### 3.4.2. cublasLtDestroy()

```c++
cublasStatus_t
      cublasLtDestroy(cublasLtHandle_t lightHandle)
```

此函数释放 cuBLASLt 库使用的硬件资源。此函数通常是与特定句柄对 cuBLASLt 库的最后一次调用。因为 cublasLtCreate() 会分配一些内部资源，而调用 cublasLtDestroy() 释放这些资源将隐式调用 `cudaDeviceSynchronize()`，所以建议最小化这些函数的调用次数。

**参数：**

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| lightHandle |  | Input | 指向要销毁的 cuBLASLt 句柄的指针。 |

**返回：**

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | cuBLASLt 上下文已成功销毁。 |
| CUBLAS_STATUS_NOT_INITIALIZED | cuBLASLt 库未初始化。 |
| CUBLAS_STATUS_INVALID_VALUE | lightHandle 为 NULL |

有关有效返回代码的完整列表，请参见 cublasStatus_t。

### 3.4.3. cublasLtDisableCpuInstructionsSetMask()

```c++
unsigned cublasLtDisableCpuInstructionsSetMask(unsigned mask);
```

指示 cuBLASLt 库不要使用 `mask` 中标志指定的 CPU 指令。此函数优先于 `CUBLASLT_DISABLE_CPU_INSTRUCTIONS_MASK` 环境变量。

**参数：** `mask` – 通过按位 OR(|) 运算符组合的标志，用于指定不应使用的 CPU 指令。

支持的标志：

| 值 | 描述 |
| --- | --- |
| 0x1 | x86-64 AVX512 ISA。 |

**返回：** mask 的先前值。

### 3.4.4. cublasLtGetCudartVersion()

```c++
size_t cublasLtGetCudartVersion(void);
```

此函数返回 CUDA Runtime 库的版本号。

**参数：** 无。

**返回：** `size_t` - CUDA Runtime 库的版本号。

### 3.4.5. cublasLtGetProperty()

```c++
cublasStatus_t cublasLtGetProperty(libraryPropertyType type, int *value);
```

此函数通过将请求的属性值写入 value 参数指向的内存位置来返回该属性的值。

**参数：**

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| type |  | Input | libraryPropertyType 类型的属性，其值被请求。请参见 libraryPropertyType_t。 |
| value |  | Output | 指向主机内存位置的指针，所请求的信息应写入该位置。 |

**返回：**

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 请求的 libraryPropertyType 信息已成功写入提供的地址。 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 type 输入参数的值无效，或<br>value 为 NULL |

有关有效返回代码的完整列表，请参见 cublasStatus_t。

### 3.4.6. cublasLtGetStatusName()

```c++
const char* cublasLtGetStatusName(cublasStatus_t status);
```

返回给定状态的字符串表示。

**参数：** cublasStatus_t - 状态。

**返回：** `const char*` - NULL 终止的字符串。

### 3.4.7. cublasLtGetStatusString()

```c++
const char* cublasLtGetStatusString(cublasStatus_t status);
```

返回给定状态的描述字符串。

**参数：** cublasStatus_t - 状态。

**返回：** `const char*` - NULL 终止的字符串。

### 3.4.8. cublasLtHeuristicsCacheGetCapacity()

```c++
cublasStatus_t cublasLtHeuristicsCacheGetCapacity(size_t* capacity);
```

返回启发式缓存的容量。

**参数：**

| 参数 | 描述 |
| --- | --- |
| capacity | 指向返回的容量值的指针。 |

**返回：**

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 容量已成功写入。 |
| CUBLAS_STATUS_INVALID_VALUE | 容量已成功设置。 |

### 3.4.9. cublasLtHeuristicsCacheSetCapacity()

```c++
cublasStatus_t cublasLtHeuristicsCacheSetCapacity(size_t capacity);
```

设置启发式缓存的容量。将容量设置为 0 可禁用启发式缓存。

此函数优先于 `CUBLASLT_HEURISTICS_CACHE_CAPACITY` 环境变量。

**参数：**

| 参数 | 描述 |
| --- | --- |
| capacity | 所需的启发式缓存容量。 |

**返回：**

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 容量已成功设置。 |

### 3.4.10. cublasLtGetVersion()

```c++
size_t cublasLtGetVersion(void);
```

此函数返回 cuBLASLt 库的版本号。

**参数：** 无。

**返回：** `size_t` - cuBLASLt 库的版本号。

### 3.4.11. cublasLtLoggerSetCallback()

```c++
cublasStatus_t cublasLtLoggerSetCallback(cublasLtLoggerCallback_t callback);
```

实验性：此函数设置日志回调函数。

**参数：**

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| callback |  | Input | 指向回调函数的指针。请参见 cublasLtLoggerCallback_t。 |

**返回：**

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 回调函数已成功设置。 |

有关有效返回代码的完整列表，请参见 cublasStatus_t。

### 3.4.12. cublasLtLoggerSetFile()

```c++
cublasStatus_t cublasLtLoggerSetFile(FILE* file);
```

实验性：此函数设置日志输出文件。注意：使用此函数调用注册后，提供的文件句柄不得关闭，除非再次调用此函数以切换到不同的文件句柄。

**参数：**

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| file |  | Input | 指向打开的文件的指针。该文件应具有写权限。 |

**返回：**

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 日志文件已成功设置。 |

有关有效返回代码的完整列表，请参见 cublasStatus_t。

### 3.4.13. cublasLtLoggerOpenFile()

```c++
cublasStatus_t cublasLtLoggerOpenFile(const char* logFile);
```

实验性：此函数打开并设置给定路径中的日志输出文件。

**参数：**

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| logFile |  | Input | 日志输出文件的路径。 |

**返回：**

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 日志文件已成功打开。 |

有关有效返回代码的完整列表，请参见 cublasStatus_t。

### 3.4.14. cublasLtLoggerSetLevel()

```c++
cublasStatus_t cublasLtLoggerSetLevel(int level);
```

实验性：此函数设置日志级别的值。

**参数：**

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| level |  | Input | 日志级别的值。请参见 cuBLASLt Logging。 |

**返回：**

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | 如果该值不是有效的日志级别。请参见 cuBLASLt Logging。 |
| CUBLAS_STATUS_SUCCESS | 日志级别已成功设置。 |

有关有效返回代码的完整列表，请参见 cublasStatus_t。

### 3.4.15. cublasLtLoggerSetMask()

```c++
cublasStatus_t cublasLtLoggerSetMask(int mask);
```

实验性：此函数设置日志掩码的值。

**参数：**

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| mask |  | Input | 日志掩码的值。请参见 cuBLASLt Logging。 |

**返回：**

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 日志掩码已成功设置。 |

有关有效返回代码的完整列表，请参见 cublasStatus_t。

### 3.4.16. cublasLtLoggerForceDisable()

```c++
cublasStatus_t cublasLtLoggerForceDisable();
```

实验性：此函数在整个运行期间禁用日志记录。

**返回：**

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 日志记录已成功禁用。 |

有关有效返回代码的完整列表，请参见 cublasStatus_t。

### 3.4.17. cublasLtMatmul()

```c++
cublasStatus_t cublasLtMatmul(
      cublasLtHandle_t               lightHandle,
      cublasLtMatmulDesc_t           computeDesc,
      const void                    *alpha,
      const void                    *A,
      cublasLtMatrixLayout_t         Adesc,
      const void                    *B,
      cublasLtMatrixLayout_t         Bdesc,
      const void                    *beta,
      const void                    *C,
      cublasLtMatrixLayout_t         Cdesc,
      void                          *D,
      cublasLtMatrixLayout_t         Ddesc,
      const cublasLtMatmulAlgo_t    *algo,
      void                          *workspace,
      size_t                         workspaceSizeInBytes,
      cudaStream_t                   stream);
```

此函数根据以下操作计算矩阵 A 和 B 的矩阵乘法以产生输出矩阵 D：

`D = alpha*(A*B) + beta*(C),`

其中 `A`、`B` 和 `C` 是输入矩阵，`alpha` 和 `beta` 是输入标量。

> **注意**
>
> 此函数支持原位矩阵乘法（C == D 且 Cdesc == Ddesc）以及异位矩阵乘法（C != D，两个矩阵必须具有相同的数据类型、行数、列数、批次大小和内存顺序）。在异位情况下，C 的主维度可以与 D 的主维度不同。具体来说，C 的主维度可以为 0 以实现行或列广播。如果省略 Cdesc，则此函数假定其等于 Ddesc。
>
> `workspace` 指针必须至少按 256 字节的倍数对齐。
> 关于 `workspaceSizeInBytes` 的建议与 cublasSetWorkspace() 部分中提到的相同。

**支持的数据类型：**

cublasLtMatmul() 支持以下 computeType、scaleType、Atype/Btype 和 Ctype。脚注可以在本节末尾找到。

| computeType | scaleType | Atype/Btype | Ctype | 偏置类型 6 |
| --- | --- | --- | --- | --- |
| CUBLAS_COMPUTE_16F 或<br>CUBLAS_COMPUTE_16F_PEDANTIC | CUDA_R_16F | CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUBLAS_COMPUTE_32I 或<br>CUBLAS_COMPUTE_32I_PEDANTIC | CUDA_R_32I | CUDA_R_8I | CUDA_R_32I | 不支持后激活。 |
| CUDA_R_32F | CUDA_R_8I | CUDA_R_8I | 不支持后激活。 |
| CUBLAS_COMPUTE_32F 或<br>CUBLAS_COMPUTE_32F_PEDANTIC | CUDA_R_32F | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_8I | CUDA_R_32F | 不支持后激活。 |
| CUDA_R_16BF | CUDA_R_32F | CUDA_R_32F 6 |
| CUDA_R_16F | CUDA_R_32F | CUDA_R_32F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_32F 6 |
| CUDA_C_32F 7 | CUDA_C_8I 7 | CUDA_C_32F 7 | 不支持后激活。 |
| CUDA_C_32F 7 | CUDA_C_32F 7 |
| CUBLAS_COMPUTE_32F_FAST_16F 或<br>CUBLAS_COMPUTE_32F_FAST_16BF 或<br>CUBLAS_COMPUTE_32F_FAST_TF32 或<br>CUBLAS_COMPUTE_32F_EMULATED_16BFX9 | CUDA_R_32F | CUDA_R_32F | CUDA_R_32F | CUDA_R_32F 6 |
| CUDA_C_32F 7 | CUDA_C_32F 7 | CUDA_C_32F 7 | 不支持后激活。 |
| CUBLAS_COMPUTE_64F 或<br>CUBLAS_COMPUTE_64F_PEDANTIC 或<br>CUBLAS_COMPUTE_64F_EMULATED_FIXEDPOINT | CUDA_R_64F | CUDA_R_64F | CUDA_R_64F | CUDA_R_64F 6 |
| CUDA_C_64F 7 | CUDA_C_64F 7 | CUDA_C_64F 7 | 不支持后激活。 |

要使用 IMMA 内核，必须满足以下两组要求中的至少一组，第一组为首选：

1. 使用常规数据顺序：

所有矩阵指针必须 4 字节对齐。为获得更好的性能，此条件应以 16 而非 4 保持。
矩阵 A、B、C 的主维度必须是 4 的倍数。
仅支持"TN"格式 - A 必须转置，B 不转置。
指针模式可以是 CUBLASLT_POINTER_MODE_HOST、CUBLASLT_POINTER_MODE_DEVICE 或 CUBLASLT_POINTER_MODE_ALPHA_DEVICE_VECTOR_BETA_HOST。使用后一种模式时，内核支持 CUBLASLT_MATMUL_DESC_ALPHA_VECTOR_BATCH_STRIDE 属性。
维度 m 和 k 必须是 4 的倍数。

2. 在 Ampere（计算能力 8.0）或 Turing（计算能力 7.5）架构上使用 IMMA 特定的数据顺序（但不在 Hopper（计算能力 9.0）或更高版本上）- 对矩阵 A、C、D 使用 CUBLASLT_ORDER_COL32，对矩阵 B 使用 CUBLASLT_ORDER_COL4_4R2_8C（在 Turing 或 Ampere 架构上）或 CUBLASLT_ORDER_COL32_2R_4R4（在 Ampere 架构上）：

矩阵 A、B、C 的主维度必须满足与内存顺序相关的特定条件（请参见 cublasLtOrder_t）。
Matmul 描述符必须在矩阵 B 上指定 CUBLAS_OP_T，在矩阵 A 和 C 上指定 CUBLAS_OP_N（默认）。
如果使用 scaleType CUDA_R_32I，则 alpha 和 beta 仅支持的值为 0 或 1。
指针模式可以是 CUBLASLT_POINTER_MODE_HOST、CUBLASLT_POINTER_MODE_DEVICE、CUBLASLT_POINTER_MODE_DEVICE_VECTOR 或 CUBLASLT_POINTER_MODE_ALPHA_DEVICE_VECTOR_BETA_ZERO。这些内核不支持 CUBLASLT_MATMUL_DESC_ALPHA_VECTOR_BATCH_STRIDE。
仅支持"NT"格式 - A 不转置，B 转置。

| computeType | scaleType | Atype/Btype | Ctype | 偏置类型 |
| --- | --- | --- | --- | --- |
| CUBLAS_COMPUTE_32I 或<br>CUBLAS_COMPUTE_32I_PEDANTIC | CUDA_R_32I | CUDA_R_8I | CUDA_R_32I | 不支持非默认后激活。 |
| CUDA_R_32F | CUDA_R_8I | CUDA_R_8I | CUDA_R_32F |

要使用张量或块缩放 FP8 内核，必须满足以下一组要求：

- 所有矩阵维度必须满足张量核心使用中列出的最佳要求（即指针和矩阵维度必须支持 16 字节对齐）。
- 缩放模式必须满足缩放模式支持概述表中列出的限制。
- 在 Ada（计算能力 8.9）、Hopper（计算能力 9.0）和 Blackwell GeForce（计算能力 12.x）GPU 上，A 必须转置且 B 不转置（"TN"格式）。
- 计算类型必须是 CUBLAS_COMPUTE_32F。
- 缩放类型必须是 CUDA_R_32F。

使用 FP8 内核时请参见下表：

| AType | BType | CType | DType | 偏置类型 |
| --- | --- | --- | --- | --- |
| CUDA_R_8F_E4M3 | CUDA_R_8F_E4M3 | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_8F_E4M3 8 | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_8F_E4M3 8 | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |
| CUDA_R_8F_E5M2 | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_8F_E4M3 8 | CUDA_R_16BF 6 |
| CUDA_R_8F_E5M2 8 | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_8F_E4M3 8 | CUDA_R_16F 6 |
| CUDA_R_8F_E5M2 8 | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |
| CUDA_R_8F_E5M2 | CUDA_R_8F_E4M3 | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_8F_E4M3 8 | CUDA_R_16BF 6 |
| CUDA_R_8F_E5M2 8 | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_8F_E4M3 8 | CUDA_R_16F 6 |
| CUDA_R_8F_E5M2 8 | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |

要使用块缩放 FP4 内核，必须满足以下一组要求：

- 所有矩阵维度必须满足张量核心使用中列出的最佳要求（即指针和矩阵维度必须支持 16 字节对齐）。
- 缩放模式必须是 CUBLASLT_MATMUL_MATRIX_SCALE_VEC16_UE4M3
- A 必须转置且 B 不转置（"TN"格式）
- 计算类型必须是 CUBLAS_COMPUTE_32F。
- 缩放类型必须是 CUDA_R_32F。

| AType | BType | CType | DType | 偏置类型 |
| --- | --- | --- | --- | --- |
| CUDA_R_4F_E2M1 | CUDA_R_4F_E2M1 | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_4F_E2M1 | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_4F_E2M1 | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |

当 A、B、C、D 是平面复数矩阵（`CUBLASLT_MATRIX_LAYOUT_PLANE_OFFSET != 0`，请参见 cublasLtMatrixLayoutAttribute_t）以利用混合精度张量核心加速时，必须满足以下一组要求：

| computeType | scaleType | Atype/Btype | Ctype |
| --- | --- | --- | --- |
| CUBLAS_COMPUTE_32F | CUDA_C_32F | CUDA_C_16F 7 | CUDA_C_16F 7 |
| CUDA_C_32F 7 |
| CUDA_C_16BF 7 | CUDA_C_16BF 7 |
| CUDA_C_32F 7 |

实验性：要使用 cublasLtMatmul() 与分组矩阵，必须满足以下一组要求：

- 所有矩阵维度必须满足张量核心使用中列出的最佳要求（即指针和矩阵维度必须支持 16 字节对齐）。
- GPU 具有以下计算能力之一：9.0、10.x、11.0。
- 所有矩阵的批次模式必须是 CUBLASLT_BATCH_MODE_GROUPED。
- 所有矩阵的顺序类型必须是 CUBLASLT_ORDER_COL。
- 指针模式必须是 CUBLASLT_POINTER_MODE_HOST 或 CUBLASLT_POINTER_MODE_DEVICE。
- 矩阵 C 和 D 的缩放模式必须是 CUBLASLT_MATMUL_MATRIX_SCALE_SCALAR_32F。
- 在具有计算能力 9.0 的 GPU 上：

  矩阵 A、B 的缩放模式必须是 CUBLASLT_MATMUL_MATRIX_SCALE_SCALAR_32F、CUBLASLT_MATMUL_MATRIX_SCALE_VEC128_32F 或 CUBLASLT_MATMUL_MATRIX_SCALE_BLK128x128_32F（对于 FP8 张量）
  后激活必须是 CUBLASLT_EPILOGUE_DEFAULT
  属性 CUBLASLT_MATMUL_DESC_ALPHA_BATCH_STRIDE 和 CUBLASLT_MATMUL_DESC_BETA_BATCH_STRIDE 必须是 0

- 在具有计算能力 10.x 和 11.0 的 GPU 上：

  矩阵 A、B 的缩放模式必须是 CUBLASLT_MATMUL_MATRIX_SCALE_SCALAR_32F、CUBLASLT_MATMUL_MATRIX_SCALE_VEC32_UE8M0、CUBLASLT_MATMUL_MATRIX_SCALE_PER_BATCH_SCALAR_32F（对于 FP8 张量）或 CUBLASLT_MATMUL_MATRIX_SCALE_VEC16_UE4M3（对于 FP4 张量）
  后激活必须是 CUBLASLT_EPILOGUE_DEFAULT 或 CUBLASLT_EPILOGUE_BIAS

| AType | BType | CType | DType | 偏置类型 |
| --- | --- | --- | --- | --- |
| CUDA_R_8F_E4M3 | CUDA_R_8F_E4M3 | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |
| CUDA_R_8F_E5M2 | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |
| CUDA_R_8F_E5M2 | CUDA_R_8F_E4M3 | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |
| CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |

> **注意**
>
> 由于矩阵的形状信息仅在 GPU 上可用（请参见 CUBLASLT_GROUPED_MATRIX_LAYOUT_ROWS_ARRAY、CUBLASLT_GROUPED_MATRIX_LAYOUT_COLS_ARRAY 和 CUBLASLT_GROUPED_MATRIX_LAYOUT_LD_ARRAY），参数验证非常有限。因此，可能会出现未检测到无效参数的情况，这将导致未定义的行为。

**注释：**

**6(1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41,42,43,44,45,46)**
: 当 D 矩阵的内存顺序定义为 CUBLASLT_ORDER_ROW 时，不支持将 ReLU、dReLu、GELU 或 dGELU 与偏置组合的后激活模式（请参见 cublasLtMatmulDescAttributes_t 中的 CUBLASLT_MATMUL_DESC_EPILOGUE）。使用偏置向量时，为获得最佳性能，请指定零 beta 并将指针模式设置为 CUBLASLT_POINTER_MODE_HOST。

**7(1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17)**
: 除非所有 A、B、C 和 D 矩阵都使用 CUBLAS_ORDER_ROW 顺序，否则不支持将 CUBLAS_ORDER_ROW 与 CUBLAS_OP_C（厄米特算子）一起使用。

**8(1,2,3,4,5,6,7,8,9,10)**
: 当缩放模式为 CUBLASLT_MATMUL_MATRIX_SCALE_OUTER_VEC_32F、CUBLASLT_MATMUL_MATRIX_SCALE_VEC128_32F 和 CUBLASLT_MATMUL_MATRIX_SCALE_BLK128x128_32F 之一时，不支持 FP8 DType。

**参数：**

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| lightHandle |  | Input | 指向为 cuBLASLt 上下文分配的 cuBLASLt 句柄的指针。请参见 cublasLtHandle_t。 |
| computeDesc |  | Input | 指向先前创建的矩阵乘法描述符（类型为 cublasLtMatmulDesc_t）的句柄。 |
| alpha, beta | 设备或主机 | Input | 指向乘法中使用的标量的指针。 |
| A、B 和 C | 设备 | Input | 指向与相应描述符 Adesc、Bdesc 和 Cdesc 关联的 GPU 内存的指针。 |
| Adesc、Bdesc 和 Cdesc |  | Input | 指向先前创建的 cublasLtMatrixLayout_t 类型描述符的句柄。 |
| D | 设备 | Output | 指向与描述符 Ddesc 关联的 GPU 内存的指针。 |
| Ddesc |  | Input | 指向先前创建的 cublasLtMatrixLayout_t 类型描述符的句柄。 |
| algo |  | Input | 要使用的矩阵乘法算法的句柄。请参见 cublasLtMatmulAlgo_t。当为 NULL 时，将执行带有默认搜索偏好的隐式启发式查询，以确定要使用的实际算法。 |
| workspace | 设备 |  | 指向在 GPU 内存中分配的工作区缓冲区的指针。必须 256 字节对齐（即地址的最低 8 位必须为 0）。 |
| workspaceSizeInBytes |  | Input | 工作区的大小。 |
| stream | 主机 | Input | 所有 GPU 工作将被提交到的 CUDA 流。 |

**返回：**

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_NOT_INITIALIZED | cuBLASLt 句柄未初始化。 |
| CUBLAS_STATUS_INVALID_VALUE | 参数意外为 NULL、冲突或处于不可能的配置。例如，当 workspaceSizeInBytes 小于配置的 algo 所需的工作区时。 |
| CUBLAS_STATUS_NOT_SUPPORTED | 当前设备上的实现不支持配置的操作。 |
| CUBLAS_STATUS_ARCH_MISMATCH | 配置的操作无法使用所选设备运行。 |
| CUBLAS_STATUS_EXECUTION_FAILED | CUDA 报告设备执行错误。 |
| CUBLAS_STATUS_SUCCESS | 操作成功完成。 |

有关有效返回代码的完整列表，请参见 cublasStatus_t。

### 3.4.18. cublasLtMatmulAlgoCapGetAttribute()

```c++
cublasStatus_t cublasLtMatmulAlgoCapGetAttribute(
      const cublasLtMatmulAlgo_t *algo,
      cublasLtMatmulAlgoCapAttributes_t attr,
      void *buf,
      size_t sizeInBytes,
      size_t *sizeWritten);
```

此函数返回已初始化的 cublasLtMatmulAlgo_t 描述符结构的查询能力属性的值。能力属性值从 cublasLtMatmulAlgoCapAttributes_t 枚举类型中检索。

例如，获取支持的 Tile ID 列表：

```c++
// 获取支持的 Tile ID 列表
cublasLtMatmulTile_t tiles[CUBLASLT_MATMUL_TILE_END];
size_t num_tiles, size_written;
if (cublasLtMatmulAlgoCapGetAttribute(algo, CUBLASLT_ALGO_CAP_TILE_IDS, tiles, sizeof(tiles), &size_written) == CUBLAS_STATUS_SUCCESS) {
  num_tiles = size_written / sizeof(tiles[0]);}
```

**参数：**

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| algo |  | Input | 指向先前创建的不透明结构的指针，该结构保存矩阵乘法算法描述符。请参见 cublasLtMatmulAlgo_t。 |
| attr |  | Input | 将由此函数检索其值的能力属性。请参见 cublasLtMatmulAlgoCapAttributes_t。 |
| buf |  | Output | 此函数返回的属性值。 |
| sizeInBytes |  | Input | buf 缓冲区的大小（以字节为单位），用于验证。 |
| sizeWritten |  | Output | 仅在返回值为 CUBLAS_STATUS_SUCCESS 时有效。如果 sizeInBytes 非零：则 sizeWritten 是实际写入的字节数；如果 sizeInBytes 为零：则 sizeWritten 是写入完整内容所需的字节数。 |

**返回：**

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | 如果 sizeInBytes 为 0 且 sizeWritten 为 NULL，或<br>如果 sizeInBytes 非零且 buf 为 NULL，或<br>如果 sizeInBytes 与所选属性内部存储的大小不匹配 |
| CUBLAS_STATUS_SUCCESS | 属性值已成功写入用户内存。 |

有关有效返回代码的完整列表，请参见 cublasStatus_t。

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

此函数对给定输入矩阵 A、B 和 C 以及输出矩阵 D 的矩阵乘法操作 cublasLtMatmul() 函数的矩阵乘法算法描述符执行正确性检查。它检查描述符是否在当前设备上受支持，并返回包含所需工作区和计算波数的结果。

> **注意**
>
> CUBLAS_STATUS_SUCCESS 不能完全保证 algo 会运行。例如，如果缓冲区未正确对齐，algo 将失败。但是，如果 cublasLtMatmulAlgoCheck() 失败，algo 将不会运行。

**参数：**

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| lightHandle |  | Input | 指向为 cuBLASLt 上下文分配的 cuBLASLt 句柄的指针。请参见 cublasLtHandle_t。 |
| operationDesc |  | Input | 指向先前创建的矩阵乘法描述符（类型为 cublasLtMatmulDesc_t）的句柄。 |
| Adesc、Bdesc、Cdesc 和 Ddesc |  | Input | 指向先前创建的 cublasLtMatrixLayout_t 类型矩阵布局描述符的句柄。 |
| algo |  | Input | 指定应使用哪种矩阵乘法算法的描述符。请参见 cublasLtMatmulAlgo_t。可以指向 result->algo。 |
| result |  | Output | 指向此函数返回结果的结构的指针。结果包括所需的工作区和计算的波数。algo 字段永远不会更新。请参见 cublasLtMatmulHeuristicResult_t。 |

**返回：**

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | 矩阵布局描述符或操作描述符与 algo 描述符不匹配。 |
| CUBLAS_STATUS_NOT_SUPPORTED | algo 配置或数据类型组合在给定设备上当前不受支持。 |
| CUBLAS_STATUS_ARCH_MISMATCH | algo 配置无法使用所选设备运行。 |
| CUBLAS_STATUS_SUCCESS | 检查成功。 |

有关有效返回代码的完整列表，请参见 cublasStatus_t。

### 3.4.20. cublasLtMatmulAlgoConfigGetAttribute()

```c++
cublasStatus_t cublasLtMatmulAlgoConfigGetAttribute(
      const cublasLtMatmulAlgo_t *algo,
      cublasLtMatmulAlgoConfigAttributes_t attr,
      void *buf,
      size_t sizeInBytes,
      size_t *sizeWritten);
```

此函数返回已初始化的 cublasLtMatmulAlgo_t 描述符的查询配置属性的值。配置属性值从 cublasLtMatmulAlgoConfigAttributes_t 枚举类型中检索。

**参数：**

| 参数 | 内存 | 输入/输出 |