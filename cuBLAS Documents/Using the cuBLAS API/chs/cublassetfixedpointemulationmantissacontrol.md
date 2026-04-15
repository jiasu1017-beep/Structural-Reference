### 2.4.31. cublasSetFixedPointEmulationMantissaControl()

```c++
cublasStatus_t cublasSetFixedPointEmulationMantissaControl(cublasHandle_t handle, cudaEmulationMantissaControl mantissaControl)
```

此函数用于设置之前编程到库句柄的值。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 定点仿真尾数控制设置成功。 |
| CUBLAS_STATUS_INVALID_VALUE | mantissaControl 超出允许范围。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |