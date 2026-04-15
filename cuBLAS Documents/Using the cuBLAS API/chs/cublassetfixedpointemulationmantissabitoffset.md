### 2.4.35. cublasSetFixedPointEmulationMantissaBitOffset()

```c++
cublasStatus_t cublasSetFixedPointEmulationMantissaBitOffset(cublasHandle_t handle, int mantissaBitOffset)
```

此函数用于设置之前编程到库句柄的值。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | mantissaBitOffset 已成功设置。 |
| CUBLAS_STATUS_INVALID_VALUE | mantissaBitOffset 超出允许范围。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |