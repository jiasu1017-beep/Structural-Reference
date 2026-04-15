### 2.4.29. cublasSetEmulationSpecialValuesSupport()

```c++

cublasStatus_t cublasSetEmulationSpecialValuesSupport(cublasHandle_t handle, cudaEmulationSpecialValuesSupport mask)


```

此函数设置之前编程到库句柄的值。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 仿真特殊值支持已成功设置。 |
| CUBLAS_STATUS_INVALID_VALUE | mask 超出允许范围。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |