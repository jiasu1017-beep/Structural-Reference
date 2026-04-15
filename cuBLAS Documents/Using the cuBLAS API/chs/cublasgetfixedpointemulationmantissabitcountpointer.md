### 2.4.36. cublasGetFixedPointEmulationMantissaBitCountPointer()

```c++
cublasStatus_t cublasGetFixedPointEmulationMantissaBitCountPointer(cublasHandle_t handle, int **mantissaBitCount)
```

此函数获取之前编程到库句柄的值。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | mantissaBitCount 已成功返回。 |
| CUBLAS_STATUS_INVALID_VALUE | mantissaBitCount 为 NULL。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |