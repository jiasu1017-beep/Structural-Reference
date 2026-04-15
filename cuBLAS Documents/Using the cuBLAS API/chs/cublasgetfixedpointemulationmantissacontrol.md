### 2.4.30. cublasGetFixedPointEmulationMantissaControl()

```c++

cublasStatus_t cublasGetFixedPointEmulationMantissaControl(cublasHandle_t handle, cudaEmulationMantissaControl *mantissaControl)

```

此函数用于获取先前编程到库句柄的值。

| Return Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 定点仿真尾数控制已成功返回。 |
| CUBLAS_STATUS_INVALID_VALUE | mantissaControl 为 NULL。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |