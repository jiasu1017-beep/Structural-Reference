## 4.3. cuBLASXt API 辅助函数参考

### 4.3.1. cublasXtCreate()

```c++
cublasStatus_t
cublasXtCreate(cublasXtHandle_t *handle)
```

此函数用于初始化 cuBLASXt API 并创建一个指向保存 cuBLASXt API 上下文的不透明结构的句柄。它在主机和设备上分配硬件资源，必须在任何其他 cuBLASXt API 调用之前调用。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 初始化成功 |
| CUBLAS_STATUS_ALLOC_FAILED | 无法分配资源 |
| CUBLAS_STATUS_NOT_SUPPORTED | cuBLASXt API 仅在 64 位平台上受支持 |

### 4.3.2. cublasXtDestroy()

```c++
cublasStatus_t
cublasXtDestroy(cublasXtHandle_t handle)
```

此函数用于释放 cuBLASXt API 上下文所使用的硬件资源。GPU 资源的释放可能会延迟到应用程序退出。此函数通常是对特定 cuBLASXt API 句柄的最后一次调用。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 关闭成功 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |

### 4.3.3. cublasXtDeviceSelect()

```c++
cublasXtDeviceSelect(cublasXtHandle_t handle, int nbDevices, int deviceId[])
```

此函数允许用户指定将参与后续 cuBLASXt API 数学函数调用的 GPU 设备数量及其各自的 ID。此函数将为列表中提供的每个 GPU 创建一个 cuBLAS 上下文。当前设备配置是静态的，在数学函数调用之间无法更改。因此，此函数应在 `cublasXtCreate` 之后仅调用一次。要运行多个配置，应创建多个 cuBLASXt API 上下文。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 用户调用成功 |
| CUBLAS_STATUS_INVALID_VALUE | 无法访问至少一个设备，或无法在至少一个设备上创建 cuBLAS 上下文 |
| CUBLAS_STATUS_ALLOC_FAILED | 某些资源无法分配 |

### 4.3.4. cublasXtSetBlockDim()

```c++
cublasXtSetBlockDim(cublasXtHandle_t handle, int blockDim)
```

此函数允许用户设置用于矩阵分块的块维度，以用于后续的数学函数调用。矩阵被分割为 blockDim x blockDim 维的正方形块。此函数可以随时调用，并对后续的数学函数调用生效。应选择合适的块维度以优化数学运算，并确保 PCI 传输与计算良好地重叠。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 调用成功 |
| CUBLAS_STATUS_INVALID_VALUE | blockDim <= 0 |

### 4.3.5. cublasXtGetBlockDim()

```c++
cublasXtGetBlockDim(cublasXtHandle_t handle, int *blockDim)
```

此函数允许用户查询用于矩阵分块的块维度。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 调用成功 |

### 4.3.6. cublasXtSetCpuRoutine()

```c++
cublasXtSetCpuRoutine(cublasXtHandle_t handle, cublasXtBlasOp_t blasOp, cublasXtOpType_t type, void *blasFunctor)
```

此函数允许用户提供相应 BLAS 例程的 CPU 实现。此函数可与函数 cublasXtSetCpuRatio() 配合使用，以定义 CPU 与 GPU 之间的混合计算。当前混合功能仅支持 xGEMM 例程。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 调用成功 |
| CUBLAS_STATUS_INVALID_VALUE | blasOp 或 type 定义了无效组合 |
| CUBLAS_STATUS_NOT_SUPPORTED | 该例程不支持 CPU-GPU 混合 |

### 4.3.7. cublasXtSetCpuRatio()

```c++
cublasXtSetCpuRatio(cublasXtHandle_t handle, cublasXtBlasOp_t blasOp, cublasXtOpType_t type, float ratio )
```

此函数允许用户在混合计算的上下文中定义应在 CPU 上完成的工作负载百分比。此函数可与函数 cublasXtSetCpuRoutine() 配合使用，以定义 CPU 与 GPU 之间的混合计算。当前混合功能仅支持 xGEMM 例程。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 调用成功 |
| CUBLAS_STATUS_INVALID_VALUE | blasOp 或 type 定义了无效组合 |
| CUBLAS_STATUS_NOT_SUPPORTED | 该例程不支持 CPU-GPU 混合 |

### 4.3.8. cublasXtSetPinningMemMode()

```c++
cublasXtSetPinningMemMode(cublasXtHandle_t handle, cublasXtPinningMemMode_t mode)
```

此函数允许用户启用或禁用内存固定（Pinning Memory）模式。启用后，后续 cuBLASXt API 调用中传入的矩阵如果尚未被固定，将使用 CUDART 例程 `cudaHostRegister()` 和 `cudaHostUnregister()` 分别进行固定/取消固定操作。如果矩阵恰好已被部分固定，也不会被固定。内存固定可以提高 PCI 传输性能，并允许 PCI 内存传输与计算重叠。然而，固定/取消固定内存需要一定时间，可能无法摊销。建议用户自行使用 `cudaMallocHost()` 或 `cudaHostRegister()` 固定内存，并在计算序列完成时取消固定。默认情况下，内存固定模式是禁用的。

> **Note**
>
> 注意
> 当用于不同 cuBLASXt API 调用的矩阵存在重叠时，不应启用内存固定模式。cuBLASXt 通过使用 cudaHostGetFlags() 检查矩阵首地址是否被固定来判断矩阵是否被固定，因此无法知道矩阵是否已被部分固定。这在多线程应用程序中尤为重要，因为在一个线程访问内存时，另一个线程可能正在对该内存进行部分或完全固定/取消固定操作。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 调用成功 |
| CUBLAS_STATUS_INVALID_VALUE | mode 值与 CUBLASXT_PINNING_DISABLED 和 CUBLASXT_PINNING_ENABLED 都不同 |

### 4.3.9. cublasXtGetPinningMemMode()

```c++
cublasXtGetPinningMemMode(cublasXtHandle_t handle, cublasXtPinningMemMode_t *mode)
```

此函数允许用户查询内存固定模式的状态。默认情况下，内存固定模式是禁用的。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 调用成功 |