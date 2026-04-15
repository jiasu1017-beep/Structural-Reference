### 3.3.10. cublasLtMatmulHeuristicResult_t

`cublasLtMatmulHeuristicResult_t` 是一个描述符，用于保存配置好的矩阵乘法算法描述符及其运行时属性。

| 成员 | 描述 |
| --- | --- |
| `cublasLtMatmulAlgo_t algo` | 如果首选项 `CUBLASLT_MATMUL_PERF_SEARCH_MODE` 设置为 `CUBLASLT_SEARCH_LIMITED_BY_ALGO_ID`，则必须使用 `cublasLtMatmulAlgoInit()` 进行初始化。请参阅 `cublasLtMatmulSearch_t`。 |
| `size_t workspaceSize;` | 所需工作区内存的实际大小。 |
| `cublasStatus_t state;` | 结果状态。只有在调用 `cublasLtMatmulAlgoGetHeuristic()` 后此成员设置为 `CUBLAS_STATUS_SUCCESS` 时，其他字段才有效。 |
| `float wavesCount;` | Waves 计数是一个设备利用率指标。wavesCount 值为 1.0f 表示当内核启动时将完全占用 GPU。 |
| `int reserved[4];` | 保留字段。 |