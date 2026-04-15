### 2.4.32. cublasGetFixedPointEmulationMaxMantissaBitCount()

```c++

cublasStatus_t cublasGetFixedPointEmulationMaxMantissaBitCount(cublasHandle_t handle, int *maxMantissaBitCount)

```

此函数获取先前编程到库句柄的值。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 成功返回 maxMantissaBitCount。 |
| CUBLAS_STATUS_INVALID_VALUE | maxMantissaBitCount 为 NULL。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |