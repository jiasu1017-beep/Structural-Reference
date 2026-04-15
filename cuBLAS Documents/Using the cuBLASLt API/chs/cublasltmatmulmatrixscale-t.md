### 3.3.27. cublasLtMatmulMatrixScale_t

`cublasLtMatmulMatrixScale_t` 是一种枚举类型，用于指定缩放模式，该模式定义了如何解释缩放因子指针。

| Value | Description |
| --- | --- |
| CUBLASLT_MATMUL_MATRIX_SCALE_SCALAR_32F | 缩放因子是应用于整个张量的单精度标量（此模式是 fp8 的默认模式）。当 D 张量使用窄精度数据类型时，这是 CUBLASLT_MATMUL_DESC_D_SCALE_MODE 的唯一有效值。 |
| CUBLASLT_MATMUL_MATRIX_SCALE_VEC16_UE4M3 | 缩放因子是包含专用缩放因子的张量，作为 8 位 CUDA_R_8F_UE4M3 值存储在对应数据张量最内层维度的每个 16 元素块中。 |
| CUBLASLT_MATMUL_MATRIX_SCALE_VEC32_UE8M0 | 缩放因子是包含专用缩放因子的张量，作为 8 位 CUDA_R_8F_UE8M0 值存储在对应数据张量最内层维度的每个 32 元素块中。 |
| CUBLASLT_MATMUL_MATRIX_SCALE_OUTER_VEC_32F | 缩放因子是 CUDA_R_32F 值的向量。此模式仅适用于矩阵 A 和 B，在这种情况下，向量分别预期有 M 和 N 个元素，A 和 B 乘积的每个 (i, j) 元素分别乘以 A 缩放的第 i 个元素和 B 缩放的第 j 个元素。 |
| CUBLASLT_MATMUL_MATRIX_SCALE_VEC128_32F | 缩放因子是包含专用缩放因子的张量，作为 CUDA_R_32F 缩放因子存储在对应数据张量最内层维度的每个 128 元素块中。 |
| CUBLASLT_MATMUL_MATRIX_SCALE_BLK128x128_32F | 缩放因子是包含专用缩放因子的张量，作为 CUDA_R_32F 缩放因子存储在对应数据张量的每个 128x128 元素块中。 |
| CUBLASLT_MATMUL_MATRIX_SCALE_PER_BATCH_SCALAR_32F | 缩放因子是单精度标量，依次应用于批次中的每个矩阵。此模式仅适用于矩阵 A 和 B，在这种情况下，缩放因子预期有 BATCH_COUNT 个元素。 |