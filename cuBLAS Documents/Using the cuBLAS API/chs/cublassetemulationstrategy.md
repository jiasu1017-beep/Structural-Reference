### 2.4.26. cublasSetEmulationStrategy()

```c++

cublasStatus_t cublasSetEmulationStrategy(cublasHandle_t handle, cublasEmulationStrategy_t emulationStrategy)


```

`cublasSetEmulationStrategy()` 函数使您能够选择库如何使用浮点模拟。更多详细信息，请参阅 `cublasEmulationStrategy_t`。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 模拟策略设置成功。 |
| CUBLAS_STATUS_INVALID_VALUE | 指定的模拟策略值无效。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |