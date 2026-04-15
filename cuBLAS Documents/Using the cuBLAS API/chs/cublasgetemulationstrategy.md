### 2.4.27. cublasGetEmulationStrategy()

```c++
cublasStatus_t cublasGetEmulationStrategy(cublasHandle_t handle, cublasEmulationStrategy_t *emulationStrategy)
```

此函数获取之前编程到库句柄的值。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 模拟策略返回成功。 |
| CUBLAS_STATUS_INVALID_VALUE | emulationStrategy 为 NULL。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |