### 2.4.37. cublasSetFixedPointEmulationMantissaBitCountPointer()

```c++
cublasStatus_t cublasSetFixedPointEmulationMantissaBitCountPointer(cublasHandle_t handle, int *mantissaBitCount)
```

此函数设置之前编程到库句柄的值。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | mantissaBitCount 设置成功。 |
| CUBLAS_STATUS_INVALID_VALUE | mantissaBitCount 超出允许范围。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |