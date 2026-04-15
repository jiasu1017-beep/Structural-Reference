### 2.4.34. cublasGetFixedPointEmulationMantissaBitOffset()

```c++

cublasStatus_t cublasGetFixedPointEmulationMantissaBitOffset(cublasHandle_t handle, int *mantissaBitOffset)


```

此函数用于获取之前编程到库句柄的值。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | mantissaBitOffset 已成功返回。 |
| CUBLAS_STATUS_INVALID_VALUE | mantissaBitOffset 为 NULL。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |