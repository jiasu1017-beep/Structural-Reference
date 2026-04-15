### 3.3.26. cublasLtReductionScheme_t

cublasLtReductionScheme_t 是一个枚举类型，用于指定并行计算点积部分时的归约方案（即"Split-K"）。

| 值 | 描述 |
| --- | --- |
| CUBLASLT_REDUCTION_SCHEME_NONE | 不应用归约。点积将按一个序列执行。 |
| CUBLASLT_REDUCTION_SCHEME_INPLACE | 使用输出缓冲区"原地"执行归约，各部分以输出数据类型相加。仅使用工作区来存储确保顺序性的计数器。 |
| CUBLASLT_REDUCTION_SCHEME_COMPUTE_TYPE | 在用户提供的 workspace 中以计算数据类型存储中间结果，并在单独的步骤中进行归约。 |
| CUBLASLT_REDUCTION_SCHEME_OUTPUT_TYPE | 在用户提供的 workspace 中以输出数据类型存储中间结果，并在单独的步骤中进行归约。 |
| CUBLASLT_REDUCTION_SCHEME_MASK | 允许所有归约方案。 |