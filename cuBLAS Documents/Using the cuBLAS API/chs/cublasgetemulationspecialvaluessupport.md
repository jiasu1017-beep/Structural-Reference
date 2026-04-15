### 2.4.28. cublasGetEmulationSpecialValuesSupport()

```c++
cublasStatus_t cublasGetEmulationSpecialValuesSupport(cublasHandle_t handle, cudaEmulationSpecialValuesSupport *mask)
```

此函数获取之前编程到库句柄的值。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 仿真特殊值支持已成功返回。 |
| CUBLAS_STATUS_INVALID_VALUE | mask 为 NULL。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |