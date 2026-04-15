### 3.3.11. cublasLtMatmulInnerShape_t

cublasLtMatmulInnerShape_t 是一种枚举类型，用于配置内部核函数设计的各个方面。这不会影响 CUDA 网格大小。

| Value | Description |
| --- | --- |
| CUBLASLT_MATMUL_INNER_SHAPE_UNDEFINED | 内部形状未定义。 |
| CUBLASLT_MATMUL_INNER_SHAPE_MMA884 | 内部形状为 MMA884。 |
| CUBLASLT_MATMUL_INNER_SHAPE_MMA1684 | 内部形状为 MMA1684。 |
| CUBLASLT_MATMUL_INNER_SHAPE_MMA1688 | 内部形状为 MMA1688。 |
| CUBLASLT_MATMUL_INNER_SHAPE_MMA16816 | 内部形状为 MMA16816。 |