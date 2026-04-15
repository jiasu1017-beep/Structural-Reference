### 2.4.1. cublasCreate()

```c++
cublasStatus_t
cublasCreate(cublasHandle_t *handle)
```

此函数初始化 cuBLAS 库并创建一个指向包含 cuBLAS 库上下文的不透明结构的句柄。它在主机和设备上分配硬件资源，必须在其他任何 cuBLAS 库调用之前调用。

cuBLAS 库上下文与当前 CUDA 设备绑定。要在多个设备上使用该库，需要为每个设备创建一个 cuBLAS 句柄。另请参阅 cuBLAS 上下文。

对于给定的设备，可以创建具有不同配置的多个 cuBLAS 句柄。对于从不同线程使用同一设备的多线程应用程序，推荐的编程模型是为每个线程创建一个 cuBLAS 句柄，并在该线程的整个生命周期内使用该 cuBLAS 句柄。

由于 `cublasCreate()` 会分配一些内部资源，而调用 `cublasDestroy()` 释放这些资源时将隐式调用 `cudaDeviceSynchronize()`，因此建议尽量减少调用这些函数的次数。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 初始化成功 |
| CUBLAS_STATUS_NOT_INITIALIZED | CUDA™ Runtime 初始化失败 |
| CUBLAS_STATUS_ALLOC_FAILED | 无法分配资源 |
| CUBLAS_STATUS_INVALID_VALUE | handle 为 NULL |