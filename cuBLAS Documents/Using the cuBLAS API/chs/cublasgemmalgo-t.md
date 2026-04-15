### 2.2.9. cublasGemmAlgo_t

`cublasGemmAlgo_t` 类型是一个枚举类型，用于指定在 `sm_75` 及以下 GPU 架构上进行矩阵-矩阵乘法的算法。在 `sm_80` 及更新版本的 GPU 架构上，此枚举类型无效。cuBLAS 提供以下算法选项：

| 值 | 含义 |
| --- | --- |
| CUBLAS_GEMM_DEFAULT | 应用启发式方法选择 GEMM 算法 |
| CUBLAS_GEMM_ALGO0 到 CUBLAS_GEMM_ALGO23 | 显式选择算法 0..23。注意：在 NVIDIA Ampere 架构及更新版本的 GPU 上无效。 |
| CUBLAS_GEMM_DEFAULT_TENSOR_OP[已弃用] | 此模式已弃用，将在后续版本中移除。应用启发式方法选择 GEMM 算法，同时允许使用降低精度的 CUBLAS_COMPUTE_32F_FAST_16F 内核（为了向后兼容）。 |
| CUBLAS_GEMM_ALGO0_TENSOR_OP 到 CUBLAS_GEMM_ALGO15_TENSOR_OP[已弃用] | 这些值已弃用，将在后续版本中移除。显式选择张量核 GEMM 算法 0..15。允许使用降低精度的 CUBLAS_COMPUTE_32F_FAST_16F 内核（为了向后兼容）。注意：在 NVIDIA Ampere 架构及更新版本的 GPU 上无效。 |
| CUBLAS_GEMM_AUTOTUNE | [实验性] 库将对多个可用算法进行基准测试，并为给定问题配置选择最优算法。解决方案缓存在 cublas 句柄中，以便后续使用该问题大小的调用将使用缓存的配置。注意：为了避免覆盖用户数据，库将分配与输出大小对应的内存量。注意：在流捕获期间不支持基准测试；如果在给定问题大小的缓存中未找到配置，将在流捕获期间返回 CUBLAS_STATUS_NOT_SUPPORTED。 |