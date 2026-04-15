### 2.4.7. cublasSetStream()

```c++
cublasStatus_t
cublasSetStream(cublasHandle_t handle, cudaStream_t streamId)
```

此函数用于设置 cuBLAS 库的流，后续对 cuBLAS 库函数的所有调用都将在此流中执行。如果未设置 cuBLAS 库的流，则所有内核将使用*默认*的 NULL 流。具体来说，此例程可用于在内核启动之间更改流，然后将 cuBLAS 库的流重置回 NULL。此外，此函数无条件地将 cuBLAS 库的工作空间重置回默认工作空间池（请参阅 cublasSetWorkspace()）。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 流设置成功 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |