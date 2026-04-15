### 4.3.2. cublasXtDestroy()

```c++

cublasStatus_t
cublasXtDestroy(cublasXtHandle_t handle)


```

此函数释放cuBLASXt API上下文使用的硬件资源。GPU资源的释放可能会延迟到应用程序退出时。此函数通常是使用特定句柄调用cuBLASXt API的最后一次调用。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 关闭成功 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |