### 3.4.1. cublasLtCreate()



```c++
cublasStatus_t
      cublasLtCreate(cublasLtHandle_t *lighthandle)
```

此函数用于初始化 cuBLASLt 库并创建一个指向保存 cuBLASLt 库上下文的不透明结构体的句柄。它会在主机和设备上分配轻量级硬件资源，并且必须在调用任何其他 cuBLASLt 库函数之前调用。

cuBLASLt 库上下文与当前 CUDA 设备绑定。若要在多个设备上使用该库，必须为每个设备创建一个 cuBLASLt 句柄。此外，在使用与某个设备绑定的句柄调用 cuBLASLt 函数之前，必须先将该设备设置为当前设备。

另请参阅：cuBLAS Context。

**参数：**

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| lightHandle |  | Output | 指向所创建的 cuBLASLt 上下文的已分配 cuBLASLt 句柄的指针。 |

**返回值：**

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 分配成功完成。 |
| CUBLAS_STATUS_NOT_INITIALIZED | cuBLASLt 库未初始化。发生此情况的原因通常是：

- 未首先调用 cublasLtCreate()
- cuBLASLt 例程调用的 CUDA Runtime API 发生错误，或
- 硬件设置错误。 |
| CUBLAS_STATUS_ALLOC_FAILED | cuBLASLt 库内部的资源分配失败。这通常是由 cudaMalloc() 失败导致的。
解决方法：在调用此函数之前，尽可能释放先前分配的内存。 |
| CUBLAS_STATUS_INVALID_VALUE | lighthandle 为 NULL |

有关有效返回码的完整列表，请参阅 cublasStatus_t。