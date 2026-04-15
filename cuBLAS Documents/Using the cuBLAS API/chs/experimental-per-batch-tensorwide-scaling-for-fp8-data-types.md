#### 3.1.4.2. 实验性：FP8 数据类型的每批次张量范围缩放

当所有 FP8 精度张量的 `CUBLASLT_MATMUL_DESC_{X}_SCALE_MODE` 属性（此处 `X` 代表 `A`、`B`、`C`、`D` 或 `EPILOGUE_AUX`；参见 cublasLtMatmulDescAttributes_t）设置为 `CUBLASLT_MATMUL_MATRIX_SCALE_PER_BATCH_SCALAR_32F` 时，将启用每批次张量范围缩放。

每批次张量范围缩放是张量范围缩放的一种变体，只是批次中的每个矩阵都有其自己的缩放因子。

使用每批次张量范围缩放时，$scale_A$、$scale_B$、$scale_C$、$scale_D$ 和 $scale_{Aux}$ 必须是长度为 `CUBLASLT_MATRIX_LAYOUT_BATCH_COUNT` 的设备指针数组。

> **注意**
>
> 每批次张量范围缩放仅在所有矩阵的 cublasLtBatchMode_t 设置为 CUBLASLT_BATCH_MODE_GROUPED 时才受支持。