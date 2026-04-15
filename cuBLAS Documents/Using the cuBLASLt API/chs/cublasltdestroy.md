### 3.4.2. cublasLtDestroy()

```c++
cublasStatus_t
      cublasLtDestroy(cublasLtHandle_t lightHandle)
```

此函数释放 cuBLASLt 库使用的硬件资源。此函数通常是针对特定句柄调用 cuBLASLt 库的最后一次调用。由于 cublasLtCreate() 会分配一些内部资源，而调用 cublasLtDestroy() 释放这些资源时会隐式调用 `cudaDeviceSynchronize()`，因此建议尽量减少调用这些函数的次数。

**参数**：

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| lightHandle |  | 输入 | 指向要销毁的 cuBLASLt 句柄的指针。 |

**返回**：

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | cuBLASLt 上下文已成功销毁。 |
| CUBLAS_STATUS_NOT_INITIALIZED | cuBLASLt 库尚未初始化。 |
| CUBLAS_STATUS_INVALID_VALUE | lightHandle 为 NULL |

有关有效返回代码的完整列表，请参阅 cublasStatus_t。