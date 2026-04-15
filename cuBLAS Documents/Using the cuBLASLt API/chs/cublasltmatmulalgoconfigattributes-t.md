### 3.3.7. cublasLtMatmulAlgoConfigAttributes_t

`cublasLtMatmulAlgoConfigAttributes_t` 是一个枚举类型，包含 cuBLASLt 矩阵乘法算法的配置属性。配置属性是算法特定的，可以进行设置。给定算法的属性配置应与其能力属性一致。使用 `cublasLtMatmulAlgoConfigGetAttribute()` 和 `cublasLtMatmulAlgoConfigSetAttribute()` 获取和设置矩阵乘法算法描述符的属性值。

| 值 | 描述 | 数据类型 |
| --- | --- | --- |
| CUBLASLT_ALGO_CONFIG_ID | 只读属性。算法索引。参见 `cublasLtMatmulAlgoGetIds()`。由 `cublasLtMatmulAlgoInit()` 设置。 | int32_t |
| CUBLASLT_ALGO_CONFIG_TILE_ID | 瓦片ID。参见 `cublasLtMatmulTile_t`。默认值：CUBLASLT_MATMUL_TILE_UNDEFINED。 | uint32_t |
| CUBLASLT_ALGO_CONFIG_STAGES_ID | stages ID，参见 `cublasLtMatmulStages_t`。默认值：CUBLASLT_MATMUL_STAGES_UNDEFINED。 | uint32_t |
| CUBLASLT_ALGO_CONFIG_SPLITK_NUM | K 分割数量。如果 K 分割数量大于一，矩阵乘法的 SPLITK_NUM 部分将被并行计算。结果将根据 `CUBLASLT_ALGO_CONFIG_REDUCTION_SCHEME` 进行归约。 | uint32_t |
| CUBLASLT_ALGO_CONFIG_REDUCTION_SCHEME | 当 splitK 值 > 1 时使用的归约方案。默认值：CUBLASLT_REDUCTION_SCHEME_NONE。参见 `cublasLtReductionScheme_t`。 | uint32_t |
| CUBLASLT_ALGO_CONFIG_CTA_SWIZZLING | 启用/禁用 CTA 混洗。更改 CUDA 网格坐标到矩阵部分的映射。可能的值：0 和 1；其他值保留。 | uint32_t |
| CUBLASLT_ALGO_CONFIG_CUSTOM_OPTION | 自定义选项值。每个算法可以支持一些不适合其他配置属性描述的自定义选项。参见 `cublasLtMatmulAlgoCapAttributes_t` 的 `CUBLASLT_ALGO_CAP_CUSTOM_OPTION_MAX` 以获取特定情况下的可接受范围。 | uint32_t |
| CUBLASLT_ALGO_CONFIG_INNER_SHAPE_ID | 内部形状ID。参见 `cublasLtMatmulInnerShape_t`。默认值：CUBLASLT_MATMUL_INNER_SHAPE_UNDEFINED。 | uint16_t |
| CUBLASLT_ALGO_CONFIG_CLUSTER_SHAPE_ID | 簇形状ID。参见 `cublasLtClusterShape_t`。默认值：CUBLASLT_CLUSTER_SHAPE_AUTO。 | uint16_t |