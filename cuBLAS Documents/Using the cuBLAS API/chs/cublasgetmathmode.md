### 2.4.23. cublasGetMathMode()

```c++
cublasStatus_t cublasGetMathMode(cublasHandle_t handle, cublasMath_t *mode)
// 此函数返回库例程使用的数学模式
```

此函数返回库例程使用的数学模式。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 数学类型已成功返回。 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 mode 为 NULL。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |