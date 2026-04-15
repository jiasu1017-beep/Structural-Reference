## 3.3. cuBLASLt 数据类型参考

### 3.3.1. cublasLtClusterShape_t

`cublasLtClusterShape_t` 是一个枚举类型，用于配置线程块集群维度。线程块集群增加了一个可选的层级结构，由线程块组成。与线程块类似，这些集群可以是一维、二维或三维的。另请参阅[线程块集群](https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html#thread-block-clusters)。

| 值 | 描述 |
| --- | --- |
| CUBLASLT_CLUSTER_SHAPE_AUTO | 集群形状自动选择。 |
| CUBLASLT_CLUSTER_SHAPE_1x1x1 | 集群形状为 1 x 1 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_1x2x1 | 集群形状为 1 x 2 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_1x4x1 | 集群形状为 1 x 4 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_2x1x1 | 集群形状为 2 x 1 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_2x2x1 | 集群形状为 2 x 2 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_2x4x1 | 集群形状为 2 x 4 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_4x1x1 | 集群形状为 4 x 1 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_4x2x1 | 集群形状为 4 x 2 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_4x4x1 | 集群形状为 4 x 4 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_1x8x1 | 集群形状为 1 x 8 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_8x1x1 | 集群形状为 8 x 1 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_2x8x1 | 集群形状为 2 x 8 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_8x2x1 | 集群形状为 8 x 2 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_1x16x1 | 集群形状为 1 x 16 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_16x1x1 | 集群形状为 16 x 1 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_1x3x1 | 集群形状为 1 x 3 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_1x5x1 | 集群形状为 1 x 5 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_1x6x1 | 集群形状为 1 x 6 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_1x7x1 | 集群形状为 1 x 7 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_1x9x1 | 集群形状为 1 x 9 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_1x10x1 | 集群形状为 1 x 10 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_1x11x1 | 集群形状为 1 x 11 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_1x12x1 | 集群形状为 1 x 12 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_1x13x1 | 集群形状为 1 x 13 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_1x14x1 | 集群形状为 1 x 14 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_1x15x1 | 集群形状为 1 x 15 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_2x3x1 | 集群形状为 2 x 3 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_2x5x1 | 集群形状为 2 x 5 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_2x6x1 | 集群形状为 2 x 6 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_2x7x1 | 集群形状为 2 x 7 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_3x1x1 | 集群形状为 3 x 1 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_3x2x1 | 集群形状为 3 x 2 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_3x3x1 | 集群形状为 3 x 3 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_3x4x1 | 集群形状为 3 x 4 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_3x5x1 | 集群形状为 3 x 5 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_4x3x1 | 集群形状为 4 x 3 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_5x1x1 | 集群形状为 5 x 1 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_5x2x1 | 集群形状为 5 x 2 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_5x3x1 | 集群形状为 5 x 3 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_6x1x1 | 集群形状为 6 x 1 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_6x2x1 | 集群形状为 6 x 2 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_7x1x1 | 集群形状为 7 x 1 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_7x2x1 | 集群形状为 7 x 2 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_9x1x1 | 集群形状为 9 x 1 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_10x1x1 | 集群形状为 10 x 1 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_11x1x1 | 集群形状为 11 x 1 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_12x1x1 | 集群形状为 12 x 1 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_13x1x1 | 集群形状为 13 x 1 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_14x1x1 | 集群形状为 14 x 1 x 1。 |
| CUBLASLT_CLUSTER_SHAPE_15x1x1 | 集群形状为 15 x 1 x 1。 |

### 3.3.2. cublasLtEpilogue_t

`cublasLtEpilogue_t` 是一个枚举类型，用于设置后处理的收尾选项。

| 值 | 描述 |
| --- | --- |
| CUBLASLT_EPILOGUE_DEFAULT = 1 | 无特殊后处理，仅在必要时对结果进行缩放和量化。 |
| CUBLASLT_EPILOGUE_RELU = 2 | 对结果应用 ReLU 逐点变换（x := max(x, 0)）。 |
| CUBLASLT_EPILOGUE_RELU_AUX = CUBLASLT_EPILOGUE_RELU \| 128 | 对结果应用 ReLU 逐点变换（x := max(x, 0)）。此收尾模式产生一个额外输出，参见 `cublasLtMatmulDescAttributes_t` 中的 `CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER`。 |
| CUBLASLT_EPILOGUE_BIAS = 4 | 应用（广播）来自偏置向量的偏置。偏置向量长度必须与矩阵 D 的行数匹配，且必须是紧凑的（如向量元素之间的步长为 1）。偏置向量被广播到所有列，并在应用最终后处理之前添加。 |
| CUBLASLT_EPILOGUE_RELU_BIAS = CUBLASLT_EPILOGUE_RELU \| CUBLASLT_EPILOGUE_BIAS | 先应用偏置，然后应用 ReLU 变换。 |
| CUBLASLT_EPILOGUE_RELU_AUX_BIAS = CUBLASLT_EPILOGUE_RELU_AUX \| CUBLASLT_EPILOGUE_BIAS | 先应用偏置，然后应用 ReLU 变换。此收尾模式产生一个额外输出，参见 `cublasLtMatmulDescAttributes_t` 中的 `CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER`。 |
| CUBLASLT_EPILOGUE_DRELU = 8 \| 128 | 对矩阵乘法输出应用 ReLU 梯度。在输出矩阵中存储 ReLU 梯度。此收尾模式需要一个额外输入，参见 `cublasLtMatmulDescAttributes_t` 中的 `CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER`。 |
| CUBLASLT_EPILOGUE_DRELU_BGRAD = CUBLASLT_EPILOGUE_DRELU \| 16 | 对矩阵乘法输出独立应用 ReLU 和偏置梯度。在输出矩阵中存储 ReLU 梯度，在偏置缓冲区中存储偏置梯度（参见 `CUBLASLT_MATMUL_DESC_BIAS_POINTER`）。此收尾模式需要一个额外输入，参见 `cublasLtMatmulDescAttributes_t` 中的 `CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER`。 |
| CUBLASLT_EPILOGUE_GELU = 32 | 对结果应用 GELU 逐点变换（x := GELU(x)）。 |
| CUBLASLT_EPILOGUE_GELU_AUX = CUBLASLT_EPILOGUE_GELU \| 128 | 对结果应用 GELU 逐点变换（x := GELU(x)）。此收尾模式将 GELU 输入输出为单独的矩阵（对训练有用）。参见 `cublasLtMatmulDescAttributes_t` 中的 `CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER`。 |
| CUBLASLT_EPILOGUE_GELU_BIAS = CUBLASLT_EPILOGUE_GELU \| CUBLASLT_EPILOGUE_BIAS | 应用偏置然后应用 GELU 变换⁵。 |
| CUBLASLT_EPILOGUE_GELU_AUX_BIAS = CUBLASLT_EPILOGUE_GELU_AUX \| CUBLASLT_EPILOGUE_BIAS | 应用偏置然后应用 GELU 变换⁵。此收尾模式将 GELU 输入输出为单独的矩阵（对训练有用）。参见 `cublasLtMatmulDescAttributes_t` 中的 `CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER`。 |
| CUBLASLT_EPILOGUE_DGELU = 64 \| 128 | 对矩阵乘法输出应用 GELU 梯度。在输出矩阵中存储 GELU 梯度。此收尾模式需要一个额外输入，参见 `cublasLtMatmulDescAttributes_t` 中的 `CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER`。 |
| CUBLASLT_EPILOGUE_DGELU_BGRAD = CUBLASLT_EPILOGUE_DGELU \| 16 | 对矩阵乘法输出独立应用 GELU 和偏置梯度。在输出矩阵中存储 GELU 梯度，在偏置缓冲区中存储偏置梯度（参见 `CUBLASLT_MATMUL_DESC_BIAS_POINTER`）。此收尾模式需要一个额外输入，参见 `cublasLtMatmulDescAttributes_t` 中的 `CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER`。 |
| CUBLASLT_EPILOGUE_BGRADA = 256 | 对输入矩阵 A 应用偏置梯度。偏置大小对应于矩阵 D 的行数。归约发生在 GEMM 的"k"维度上。将偏置梯度存储在偏置缓冲区中，参见 `cublasLtMatmulDescAttributes_t` 中的 `CUBLASLT_MATMUL_DESC_BIAS_POINTER`。 |
| CUBLASLT_EPILOGUE_BGRADB = 512 | 对输入矩阵 B 应用偏置梯度。偏置大小对应于矩阵 D 的列数。归约发生在 GEMM 的"k"维度上。将偏置梯度存储在偏置缓冲区中，参见 `CUBLASLT_MATMUL_DESC_BIAS_POINTER`。 |

**注意事项：**

**⁵(1,2)**
: GELU（高斯误差线性单元）通过以下公式近似：\({0.5}x\left( 1 + \text{tanh}\left( \sqrt{2/\pi}\left( x + {0.044715}x^{3} \right) \right) \right)\)

> **注意**
>
> 注意
> 当任何矩阵的 `cublasLtBatchMode_t` 设置为 `CUBLASLT_BATCH_MODE_POINTER_ARRAY` 时，仅支持 `CUBLASLT_EPILOGUE_DEFAULT`。
> 当任何矩阵的 `cublasLtBatchMode_t` 设置为 `CUBLASLT_BATCH_MODE_GROUPED` 时，仅支持 `CUBLASLT_EPILOGUE_DEFAULT` 和 `CUBLASLT_EPILOGUE_BIAS`。

### 3.3.3. cublasLtHandle_t

`cublasLtHandle_t` 类型是指向保存 cuBLASLt 库上下文的不透明结构体的指针类型。使用 `cublasLtCreate()` 初始化 cuBLASLt 库上下文并返回指向保存 cuBLASLt 库上下文的不透明结构体的句柄，并使用 `cublasLtDestroy()` 销毁先前创建的 cuBLASLt 库上下文描述符并释放资源。

> **注意**
>
> 注意
> cuBLAS 句柄（`cublasHandle_t`）封装了一个 cuBLASLt 句柄。任何有效的 `cublasHandle_t` 都可以通过简单类型转换来替代 `cublasLtHandle_t` 使用。但是，与 cuBLAS 句柄不同，cuBLASLt 句柄不绑定到任何特定的 CUDA 上下文，但绑定到图形上下文的 CUDA 上下文除外（从 CUDA 12.8 开始）。如果在当前 CUDA 上下文绑定到图形上下文时创建了 cuBLASLt 句柄，则 cuBLASLt 会检测相应的共享内存限制并将其记录在句柄中。

### 3.3.4. cublasLtLoggerCallback_t

`cublasLtLoggerCallback_t` 是回调函数指针类型。可以使用 `cublasLtLoggerSetCallback()` 设置回调函数。

**参数**：

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| logLevel |  | 输出 | 参见 cuBLASLt 日志记录。 |
| functionName |  | 输出 | 记录此消息的 API 名称。 |
| message |  | 输出 | 日志消息。 |

### 3.3.5. cublasLtMatmulAlgo_t

`cublasLtMatmulAlgo_t` 是一个不透明结构体，保存矩阵乘法算法的描述。该结构体可以简单地序列化，并在以后与相同版本的 cuBLAS 库一起恢复使用，以避免再次选择正确的配置。

### 3.3.6. cublasLtMatmulAlgoCapAttributes_t

`cublasLtMatmulAlgoCapAttributes_t` 枚举了矩阵乘法算法能力属性，可以使用 `cublasLtMatmulAlgoCapGetAttribute()` 从初始化的 `cublasLtMatmulAlgo_t` 描述符中检索。

| 值 | 描述 | 数据类型 |
| --- | --- | --- |
| CUBLASLT_ALGO_CAP_SPLITK_SUPPORT | Split-K 支持。布尔值（0 或 1）表示是否支持 split-K 实现。0 表示不支持，否则表示支持。参见 `cublasLtMatmulAlgoConfigAttributes_t` 中的 `CUBLASLT_ALGO_CONFIG_SPLITK_NUM`。 | int32_t |
| CUBLASLT_ALGO_CAP_REDUCTION_SCHEME_MASK | 表示支持的归约方案类型的掩码，参见 `cublasLtReductionScheme_t`。如果归约方案未被掩码排除，则表示支持。例如：int isReductionSchemeComputeTypeSupported ? (reductionSchemeMask & CUBLASLT_REDUCTION_SCHEME_COMPUTE_TYPE) == CUBLASLT_REDUCTION_SCHEME_COMPUTE_TYPE ? 1 : 0; | uint32_t |
| CUBLASLT_ALGO_CAP_CTA_SWIZZLING_SUPPORT | CTA-swizzling 支持。布尔值（0 或 1）表示是否支持 CTA-swizzling 实现。0 表示不支持，1 表示支持值 1；其他值保留。另请参见 `cublasLtMatmulAlgoConfigAttributes_t` 中的 `CUBLASLT_ALGO_CONFIG_CTA_SWIZZLING`。 | uint32_t |
| CUBLASLT_ALGO_CAP_STRIDED_BATCH_SUPPORT | 支持步进批处理。0 表示不支持，否则表示支持。 | int32_t |
| CUBLASLT_ALGO_CAP_POINTER_ARRAY_BATCH_SUPPORT | 支持指针数组批处理。0 表示不支持，否则表示支持。 | int32_t |
| CUBLASLT_ALGO_CAP_POINTER_ARRAY_GROUPED_SUPPORT | 实验性：支持指针数组分组批处理。0 表示不支持，否则表示支持。参见 `cublasLtBatchMode_t` 中的 `CUBLASLT_BATCH_MODE_GROUPED`。 | int32_t |
| CUBLASLT_ALGO_CAP_OUT_OF_PLACE_RESULT_SUPPORT | 支持结果原地输出（D ≠ C，公式为 D = alpha.A.B + beta.C）。0 表示不支持，否则表示支持。 | int32_t |
| CUBLASLT_ALGO_CAP_UPLO_SUPPORT | Syrk（对称秩 k 更新）/herk（埃尔米特秩 k 更新）支持（在常规 gemm 之上）。0 表示不支持，否则表示支持。 | int32_t |
| CUBLASLT_ALGO_CAP_TILE_IDS | 可使用的瓦片 ID。参见 `cublasLtMatmulTile_t`。如果不支持任何瓦片 ID，则使用 `CUBLASLT_MATMUL_TILE_UNDEFINED`。使用 `cublasLtMatmulAlgoCapGetAttribute()` 且 `sizeInBytes = 0` 来查询实际数量。 | uint32_t[] |
| CUBLASLT_ALGO_CAP_STAGES_IDS | 可使用的阶段 ID。参见 `cublasLtMatmulStages_t`。如果不支持任何阶段 ID，则使用 `CUBLASLT_MATMUL_STAGES_UNDEFINED`。使用 `cublasLtMatmulAlgoCapGetAttribute()` 且 `sizeInBytes = 0` 来查询实际数量。 | uint32_t[] |
| CUBLASLT_ALGO_CAP_CUSTOM_OPTION_MAX | 自定义选项范围从 0 到 `CUBLASLT_ALGO_CAP_CUSTOM_OPTION_MAX`（包含）。参见 `cublasLtMatmulAlgoConfigAttributes_t` 中的 `CUBLASLT_ALGO_CONFIG_CUSTOM_OPTION`。 | int32_t |
| CUBLASLT_ALGO_CAP_MATHMODE_IMPL | 指示算法使用的是常规计算还是张量运算。0 表示常规计算，1 表示张量运算。
已弃用 | int32_t |
| CUBLASLT_ALGO_CAP_GAUSSIAN_IMPL | 指示算法是否实现了复数矩阵乘法的高斯优化。0 表示常规计算；1 表示高斯。参见 `cublasMath_t`。
已弃用 | int32_t |
| CUBLASLT_ALGO_CAP_CUSTOM_MEMORY_ORDER | 指示算法是否支持自定义（非 COL 或 ROW 内存顺序）。0 表示仅允许 COL 和 ROW 内存顺序，非零值表示算法可能有不同的要求。参见 `cublasLtOrder_t`。 | int32_t |
| CUBLASLT_ALGO_CAP_POINTER_MODE_MASK | 枚举算法支持的指针模式的位掩码。参见 `cublasLtPointerModeMask_t`。 | uint32_t |
| CUBLASLT_ALGO_CAP_EPILOGUE_MASK | 枚举收尾中支持的后处理算法类型的位掩码。参见 `cublasLtEpilogue_t`。 | uint32_t |
| CUBLASLT_ALGO_CAP_LD_NEGATIVE | 所有矩阵支持负前导维度。0 表示不支持，否则表示支持。 | uint32_t |
| CUBLASLT_ALGO_CAP_NUMERICAL_IMPL_FLAGS | 影响算法数值行为的实现细节。参见 `cublasLtNumericalImplFlags_t`。 | uint64_t |
| CUBLASLT_ALGO_CAP_MIN_ALIGNMENT_A_BYTES | A 矩阵所需的最小字节对齐。 | uint32_t |
| CUBLASLT_ALGO_CAP_MIN_ALIGNMENT_B_BYTES | B 矩阵所需的最小字节对齐。 | uint32_t |
| CUBLASLT_ALGO_CAP_MIN_ALIGNMENT_C_BYTES | C 矩阵所需的最小字节对齐。 | uint32_t |
| CUBLASLT_ALGO_CAP_MIN_ALIGNMENT_D_BYTES | D 矩阵所需的最小字节对齐。 | uint32_t |
| CUBLASLT_ALGO_CAP_FLOATING_POINT_EMULATION_SUPPORT | 浮点仿真的支持。参见浮点仿真。 | int32_t |

### 3.3.7. cublasLtMatmulAlgoConfigAttributes_t

`cublasLtMatmulAlgoConfigAttributes_t` 是一个枚举类型，包含 cuBLASLt 矩阵乘法算法的配置属性。配置属性是特定于算法的，可以设置。给定算法的属性配置应与其能力属性一致。使用 `cublasLtMatmulAlgoConfigGetAttribute()` 和 `cublasLtMatmulAlgoConfigSetAttribute()` 获取和设置矩阵乘法算法描述符的属性值。

| 值 | 描述 | 数据类型 |
| --- | --- | --- |
| CUBLASLT_ALGO_CONFIG_ID | 只读属性。算法索引。参见 `cublasLtMatmulAlgoGetIds()`。由 `cublasLtMatmulAlgoInit()` 设置。 | int32_t |
| CUBLASLT_ALGO_CONFIG_TILE_ID | 瓦片 ID。参见 `cublasLtMatmulTile_t`。默认值：`CUBLASLT_MATMUL_TILE_UNDEFINED`。 | uint32_t |
| CUBLASLT_ALGO_CONFIG_STAGES_ID | 阶段 ID，参见 `cublasLtMatmulStages_t`。默认值：`CUBLASLT_MATMUL_STAGES_UNDEFINED`。 | uint32_t |
| CUBLASLT_ALGO_CONFIG_SPLITK_NUM | K 分裂数量。如果 K 分裂数量大于 1，则矩阵乘法的 SPLITK_NUM 部分将并行计算。结果将根据 `CUBLASLT_ALGO_CONFIG_REDUCTION_SCHEME` 进行累积。 | uint32_t |
| CUBLASLT_ALGO_CONFIG_REDUCTION_SCHEME | 当 splitK 值 > 1 时使用的归约方案。默认值：`CUBLASLT_REDUCTION_SCHEME_NONE`。参见 `cublasLtReductionScheme_t`。 | uint32_t |
| CUBLASLT_ALGO_CONFIG_CTA_SWIZZLING | 启用/禁用 CTA swizzling。更改从 CUDA 网格坐标到矩阵部分的映射。可能的值：0 和 1；其他值保留。 | uint32_t |
| CUBLASLT_ALGO_CONFIG_CUSTOM_OPTION | 自定义选项值。每个算法可以支持一些不适合其他配置属性描述的自定义选项。参见 `cublasLtMatmulAlgoCapAttributes_t` 中的 `CUBLASLT_ALGO_CAP_CUSTOM_OPTION_MAX` 以获取特定情况下可接受的范围。 | uint32_t |
| CUBLASLT_ALGO_CONFIG_INNER_SHAPE_ID | 内部形状 ID。参见 `cublasLtMatmulInnerShape_t`。默认值：`CUBLASLT_MATMUL_INNER_SHAPE_UNDEFINED`。 | uint16_t |
| CUBLASLT_ALGO_CONFIG_CLUSTER_SHAPE_ID | 集群形状 ID。参见 `cublasLtClusterShape_t`。默认值：`CUBLASLT_CLUSTER_SHAPE_AUTO`。 | uint16_t |

### 3.3.8. cublasLtMatmulDesc_t

`cublasLtMatmulDesc_t` 是指向不透明结构体的指针，该结构体保存矩阵乘法操作 `cublasLtMatmul()` 的描述。可以通过调用 `cublasLtMatmulDescCreate()` 创建描述符，并通过调用 `cublasLtMatmulDescDestroy()` 销毁描述符。

### 3.3.9. cublasLtMatmulDescAttributes_t

`cublasLtMatmulDescAttributes_t` 是一个描述符结构体，包含定义矩阵乘法操作细节的属性。使用 `cublasLtMatmulDescGetAttribute()` 和 `cublasLtMatmulDescSetAttribute()` 获取和设置矩阵乘法描述符的属性值。

| 值 | 描述 | 数据类型 |
| --- | --- | --- |
| CUBLASLT_MATMUL_DESC_COMPUTE_TYPE | 计算类型。定义用于乘累加操作的数据类型，以及矩阵乘法期间的累加器类型。参见 `cublasComputeType_t`。 | int32_t |
| CUBLASLT_MATMUL_DESC_SCALE_TYPE | 缩放类型。定义缩放因子 alpha 和 beta 的数据类型。累加器值和来自矩阵 C 的值在最终缩放之前通常会转换为缩放类型。然后在存储到内存之前，值会从缩放类型转换为矩阵 D 的类型。默认值取决于 `CUBLASLT_MATMUL_DESC_COMPUTE_TYPE`。参见 `cudaDataType_t`。 | int32_t |
| CUBLASLT_MATMUL_DESC_POINTER_MODE | 指定 alpha 和 beta 是通过引用传递的，它们是主机上的标量、设备上的标量还是设备向量。默认值：`CUBLASLT_POINTER_MODE_HOST`（即在主机上）。参见 `cublasLtPointerMode_t`。 | int32_t |
| CUBLASLT_MATMUL_DESC_TRANSA | 指定应在矩阵 A 上执行的变换操作类型。默认值：`CUBLAS_OP_N`（即非转置操作）。参见 `cublasOperation_t`。 | int32_t |
| CUBLASLT_MATMUL_DESC_TRANSB | 指定应在矩阵 B 上执行的变换操作类型。默认值：`CUBLAS_OP_N`（即非转置操作）。参见 `cublasOperation_t`。 | int32_t |
| CUBLASLT_MATMUL_DESC_TRANSC | 指定应在矩阵 C 上执行的变换操作类型。当前仅支持 `CUBLAS_OP_N`。默认值：`CUBLAS_OP_N`（即非转置操作）。参见 `cublasOperation_t`。 | int32_t |
| CUBLASLT_MATMUL_DESC_FILL_MODE | 指示稠密矩阵的哪一部分被填充，因此应该被函数使用。当前此标志不支持 bfloat16 或 FP8 数据类型，也不支持以下 GPU：Hopper、Blackwell。默认值：`CUBLAS_FILL_MODE_FULL`。参见 `cublasFillMode_t`。 | int32_t |
| CUBLASLT_MATMUL_DESC_EPILOGUE | 收尾函数。参见 `cublasLtEpilogue_t`。默认值：`CUBLASLT_EPILOGUE_DEFAULT`。 | uint32_t |
| CUBLASLT_MATMUL_DESC_BIAS_POINTER | 设备内存中偏置或偏置梯度向量指针。

使用以下收尾之一时：矩阵 D 行数匹配长度的输入向量 `CUBLASLT_EPILOGUE_BIAS`、`CUBLASLT_EPILOGUE_RELU_BIAS`、`CUBLASLT_EPILOGUE_RELU_AUX_BIAS`、`CUBLASLT_EPILOGUE_GELU_BIAS`、`CUBLASLT_EPILOGUE_GELU_AUX_BIAS`。
使用以下收尾之一时：矩阵 D 行数匹配长度的输出向量 `CUBLASLT_EPILOGUE_DRELU_BGRAD`、`CUBLASLT_EPILOGUE_DGELU_BGRAD`、`CUBLASLT_EPILOGUE_BGRADA`。
使用以下收尾之一时：矩阵 D 列数匹配长度的输出向量 `CUBLASLT_EPILOGUE_BGRADB`。

当矩阵 D 数据类型为 `CUDA_R_8I` 时，偏置向量元素类型与 alpha 和 beta 相同（参见本表中的 `CUBLASLT_MATMUL_DESC_SCALE_TYPE`），否则与矩阵 D 数据类型相同。参见 `cublasLtMatmul()` 下的数据类型表以获取详细映射。默认值：NULL。 | void * / const void * |
| CUBLASLT_MATMUL_DESC_BIAS_BATCH_STRIDE | 步进批操作中下一个偏置或偏置梯度向量的步长（以元素为单位）。如果任何矩阵的 `cublasLtBatchMode_t` 设置为 `CUBLASLT_BATCH_MODE_GROUPED` 且 `CUBLASLT_MATMUL_DESC_EPILOGUE` 包含 `CUBLASLT_EPILOGUE_BIAS`，则必须将 `CUBLASLT_MATMUL_DESC_BIAS_BATCH_STRIDE` 设置为 1。默认值为 0。 | int64_t |
| CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER | 收尾辅助缓冲区指针。

使用 `CUBLASLT_EPILOGUE_RELU_AUX` 或 `CUBLASLT_EPILOGUE_RELU_AUX_BIAS` 收尾时，前向传播中的 ReLu 位掩码输出向量。
使用 `CUBLASLT_EPILOGUE_DRELU` 或 `CUBLASLT_EPILOGUE_DRELU_BGRAD` 收尾时，反向传播中的 ReLu 位掩码输入向量。
使用 `CUBLASLT_EPILOGUE_GELU_AUX_BIAS` 收尾时，前向传播中的 GELU 输入矩阵输出。
使用 `CUBLASLT_EPILOGUE_DGELU` 或 `CUBLASLT_EPILOGUE_DGELU_BGRAD` 收尾时，反向传播中的 GELU 输入矩阵输入。

有关辅助数据类型，参见 `CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_DATA_TYPE`。不取消引用此指针的例程（如 `cublasLtMatmulAlgoGetHeuristic()`）依赖于其值来确定预期的指针对齐方式。需要设置 `CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_LD` 属性。 | void * / const void * |
| CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_LD | 收尾辅助缓冲区的前导维度。

使用 `CUBLASLT_EPILOGUE_RELU_AUX`、`CUBLASLT_EPILOGUE_RELU_AUX_BIAS`、`CUBLASLT_EPILOGUE_DRELU_BGRAD` 或 `CUBLASLT_EPILOGUE_DRELU_BGRAD` 收尾时，ReLu 位掩码矩阵的前导维度（以元素/位为单位）。必须能被 128 整除，且不小于输出矩阵的行数。
使用 `CUBLASLT_EPILOGUE_GELU_AUX_BIAS`、`CUBLASLT_EPILOGUE_DGELU` 或 `CUBLASLT_EPILOGUE_DGELU_BGRAD` 收尾时，GELU 输入矩阵的前导维度（以元素为单位）。必须能被 8 整除，且不小于输出矩阵的行数。 | int64_t |
| CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_BATCH_STRIDE | 收尾辅助缓冲区的批处理步长。

使用 `CUBLASLT_EPILOGUE_RELU_AUX`、`CUBLASLT_EPILOGUE_RELU_AUX_BIAS` 或 `CUBLASLT_EPILOGUE_DRELU_BGRAD` 收尾时，ReLu 位掩码矩阵的批处理步长（以元素/位为单位）。必须能被 128 整除。
使用 `CUBLASLT_EPILOGUE_GELU_AUX_BIAS`、`CUBLASLT_EPILOGUE_DRELU` 或 `CUBLASLT_EPILOGUE_DGELU_BGRAD` 收尾时，GELU 输入矩阵的批处理步长（以元素为单位）。必须能被 8 整除。

默认值：0。 | int64_t |
| CUBLASLT_MATMUL_DESC_ALPHA_VECTOR_BATCH_STRIDE | alpha 向量的批处理步长。与 `CUBLASLT_POINTER_MODE_ALPHA_DEVICE_VECTOR_BETA_HOST` 一起使用，当矩阵 D 的 `CUBLASLT_MATRIX_LAYOUT_BATCH_COUNT` 大于 1 时。如果设置了 `CUBLASLT_POINTER_MODE_ALPHA_DEVICE_VECTOR_BETA_ZERO`，则必须将 `CUBLASLT_MATMUL_DESC_ALPHA_VECTOR_BATCH_STRIDE` 设置为 0，因为此模式不支持批处理 alpha 向量。如果任何矩阵的 `cublasLtBatchMode_t` 未设置为 `CUBLASLT_BATCH_MODE_STRIDED`，则必须将 `CUBLASLT_MATMUL_DESC_ALPHA_VECTOR_BATCH_STRIDE` 设置为 0。默认值：0。 | int64_t |
| CUBLASLT_MATMUL_DESC_SM_COUNT_TARGET | 目标并行执行的 SM 数量。当用户期望并发流使用部分设备资源时，优化启发式以在不同的 SM 数量上执行。默认值：0。 | int32_t |
| CUBLASLT_MATMUL_DESC_A_SCALE_POINTER | 设备指针，指向将矩阵 A 中的数据转换为计算数据类型范围的缩放因子值。缩放因子必须与计算类型具有相同的类型。如果未指定或设置为 NULL，则假定缩放因子为 1。如果为不支持的矩阵数据、缩放和计算类型组合设置，调用 `cublasLtMatmul()` 将返回 `CUBLAS_INVALID_VALUE`。默认值：NULL | const void * |
| CUBLASLT_MATMUL_DESC_B_SCALE_POINTER | 与矩阵 B 的 `CUBLASLT_MATMUL_DESC_A_SCALE_POINTER` 等效。默认值：NULL | const void * |
| CUBLASLT_MATMUL_DESC_C_SCALE_POINTER | 与矩阵 C 的 `CUBLASLT_MATMUL_DESC_A_SCALE_POINTER` 等效。默认值：NULL | const void * |
| CUBLASLT_MATMUL_DESC_D_SCALE_POINTER | 与矩阵 D 的 `CUBLASLT_MATMUL_DESC_A_SCALE_POINTER` 等效。默认值：NULL | const void * |
| CUBLASLT_MATMUL_DESC_AMAX_D_POINTER | 设备指针，指向完成后将设置为输出矩阵中绝对值最大位置的内存。计算值的类型与计算类型相同。如果未指定或设置为 NULL，则不计算最大绝对值。如果为不支持的矩阵数据、缩放和计算类型组合设置，调用 `cublasLtMatmul()` 将返回 `CUBLAS_INVALID_VALUE`。默认值：NULL | void * |
| CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_DATA_TYPE | 将存储在 `CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER` 中的数据类型。如果未设置（或设置为默认值 -1），则数据类型设置为输出矩阵元素数据类型（DType），但有例外：

ReLu 使用位掩码。
对于输出类型（DType）为 `CUDA_R_8F_E4M3` 的 FP8 内核，如果满足以下条件，可以将数据类型设置为非默认值：

AType 和 BType 为 `CUDA_R_8F_E4M3`。
偏置类型为 `CUDA_R_16F`。
CType 为 `CUDA_R_16BF` 或 `CUDA_R_16F`
`CUBLASLT_MATMUL_DESC_EPILOGUE` 设置为 `CUBLASLT_EPILOGUE_GELU_AUX`

当 CType 为 `CUDA_R_16F` 时，数据类型可以设置为 `CUDA_R