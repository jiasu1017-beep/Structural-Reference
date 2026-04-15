### 2.4.11. cublasSetPointerMode()

```c++
cublasStatus_t
cublasSetPointerMode(cublasHandle_t handle, cublasPointerMode_t mode)
```

此函数设置 cuBLAS 库使用的指针模式。*默认*情况下，值通过主机上的引用传递。请参阅 cublasPointerMode_t 类型部分以了解更多详细信息。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 指针模式设置成功 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | mode 不是 CUBLAS_POINTER_MODE_HOST 或 CUBLAS_POINTER_MODE_DEVICE |