### 2.4.10. cublasGetPointerMode()

```c++
cublasStatus_t
cublasGetPointerMode(cublasHandle_t handle, cublasPointerMode_t *mode)
```

此函数用于获取cuBLAS库使用的指针模式。有关更多详细信息，请参阅关于`cublasPointerMode_t`类型的章节。

| Return Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 指针模式获取成功 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | mode为NULL |