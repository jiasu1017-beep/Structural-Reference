### 3.3.2. cublasLtEpilogue_t

`cublasLtEpilogue_t` 是一个枚举类型，用于设置后处理选项。

| 值 | 描述 |
| --- | --- |
| CUBLASLT_EPILOGUE_DEFAULT = 1 | 无特殊后处理，仅在必要时对结果进行缩放和量化。 |
| CUBLASLT_EPILOGUE_RELU = 2 | 对结果应用 ReLU 点式变换 (x := max(x, 0))。 |
| CUBLASLT_EPILOGUE_RELU_AUX = CUBLASLT_EPILOGUE_RELU | 128 | 对结果应用 ReLU 点式变换 (x := max(x, 0))。此尾端模式产生一个额外输出，参见 cublasLtMatmulDescAttributes_t 中的 CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER。 |
| CUBLASLT_EPILOGUE_BIAS = 4 | 应用来自偏置向量的（广播）偏置。偏置向量长度必须与矩阵 D 的行数匹配，且必须为压缩格式（即向量元素之间的步幅为 1）。偏置被广播到所有列，并在最终后处理之前添加。 |
| CUBLASLT_EPILOGUE_RELU_BIAS = CUBLASLT_EPILOGUE_RELU = CUBLASLT_EPILOGUE_BIAS | 先应用偏置，然后应用 ReLU 变换。 |
| CUBLASLT_EPILOGUE_RELU_AUX_BIAS = CUBLASLT_EPILOGUE_RELU_AUX = CUBLASLT_EPILOGUE_BIAS | 先应用偏置，然后应用 ReLU 变换。此尾端模式产生一个额外输出，参见 cublasLtMatmulDescAttributes_t 中的 CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER。 |
| CUBLASLT_EPILOGUE_DRELU = 8 | 128 | 将 ReLU 梯度应用于 matmul 输出。将 ReLU 梯度存储在输出矩阵中。此尾端模式需要一个额外输入，参见 cublasLtMatmulDescAttributes_t 中的 CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER。 |
| CUBLASLT_EPILOGUE_DRELU_BGRAD = CUBLASLT_EPILOGUE_DRELU | 16 | 独立地将 ReLU 和偏置梯度应用于 matmul 输出。将 ReLU 梯度存储在输出矩阵中，并将偏置梯度存储在偏置缓冲区中（参见 CUBLASLT_MATMUL_DESC_BIAS_POINTER）。此尾端模式需要一个额外输入，参见 cublasLtMatmulDescAttributes_t 中的 CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER。 |
| CUBLASLT_EPILOGUE_GELU = 32 | 对结果应用 GELU 点式变换 (x := GELU(x))。 |
| CUBLASLT_EPILOGUE_GELU_AUX = CUBLASLT_EPILOGUE_GELU | 128 | 对结果应用 GELU 点式变换 (x := GELU(x))。此尾端模式将 GELU 输入作为单独矩阵输出（用于训练）。参见 cublasLtMatmulDescAttributes_t 中的 CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER。 |
| CUBLASLT_EPILOGUE_GELU_BIAS = CUBLASLT_EPILOGUE_GELU | CUBLASLT_EPILOGUE_BIAS | 应用偏置，然后应用 GELU 变换⁵。 |
| CUBLASLT_EPILOGUE_GELU_AUX_BIAS = CUBLASLT_EPILOGUE_GELU_AUX | CUBLASLT_EPILOGUE_BIAS | 应用偏置，然后应用 GELU 变换⁵。此尾端模式将 GELU 输入作为单独矩阵输出（用于训练）。参见 cublasLtMatmulDescAttributes_t 中的 CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER。 |
| CUBLASLT_EPILOGUE_DGELU = 64 | 128 | 将 GELU 梯度应用于 matmul 输出。将 GELU 梯度存储在输出矩阵中。此尾端模式需要一个额外输入，参见 cublasLtMatmulDescAttributes_t 中的 CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER。 |
| CUBLASLT_EPILOGUE_DGELU_BGRAD = CUBLASLT_EPILOGUE_DGELU | 16 | 独立地将 GELU 和偏置梯度应用于 matmul 输出。将 GELU 梯度存储在输出矩阵中，并将偏置梯度存储在偏置缓冲区中（参见 CUBLASLT_MATMUL_DESC_BIAS_POINTER）。此尾端模式需要一个额外输入，参见 cublasLtMatmulDescAttributes_t 中的 CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER。 |
| CUBLASLT_EPILOGUE_BGRADA = 256 | 将偏置梯度应用于输入矩阵 A。偏置大小对应于矩阵 D 的行数。归约发生在 GEMM 的 "k" 维度上。将偏置梯度存储在偏置缓冲区中，参见 cublasLtMatmulDescAttributes_t 中的 CUBLASLT_MATMUL_DESC_BIAS_POINTER。 |
| CUBLASLT_EPILOGUE_BGRADB = 512 | 将偏置梯度应用于输入矩阵 B。偏置大小对应于矩阵 D 的列数。归约发生在 GEMM 的 "k" 维度上。将偏置梯度存储在偏置缓冲区中，参见 cublasLtMatmulDescAttributes_t 中的 CUBLASLT_MATMUL_DESC_BIAS_POINTER。 |


**注意事项：**


**⁵(1,2)**
: GELU（高斯误差线性单元）由以下公式近似：\({0.5}x\left( 1 + \text{tanh}\left( \sqrt{2/\pi}\left( x + {0.044715}x^{3} \right) \right) \right)\)



> **注意**

当任何矩阵的 `cublasLtBatchMode_t` 设置为 `CUBLASLT_BATCH_MODE_POINTER_ARRAY` 时，仅支持 `CUBLASLT_EPILOGUE_DEFAULT`。
当任何矩阵的 `cublasLtBatchMode_t` 设置为 `CUBLASLT_BATCH_MODE_GROUPED` 时，仅支持 `CUBLASLT_EPILOGUE_DEFAULT` 和 `CUBLASLT_EPILOGUE_BIAS`。