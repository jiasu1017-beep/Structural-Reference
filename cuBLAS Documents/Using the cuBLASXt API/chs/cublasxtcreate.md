### 4.3.1. cublasXtCreate()

```c++
cublasStatus_t
cublasXtCreate(cublasXtHandle_t *handle)
```

此函数初始化 cuBLASXt API 并创建一个指向不透明结构的句柄，该结构保存 cuBLASXt API 上下文。它在主机和设备上分配硬件资源，且必须在调用任何其他 cuBLASXt API 之前调用。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 初始化成功 |
| CUBLAS_STATUS_ALLOC_FAILED | 无法分配资源 |
| CUBLAS_STATUS_NOT_SUPPORTED | cuBLASXt API 仅在 64 位平台上受支持 |