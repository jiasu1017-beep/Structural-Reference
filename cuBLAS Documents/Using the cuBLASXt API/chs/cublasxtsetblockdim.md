### 4.3.4. cublasXtSetBlockDim()

```c++

cublasXtSetBlockDim(cublasXtHandle_t handle, int blockDim)


```

此函数允许用户设置矩阵平铺分块时使用的块维度。矩阵被分割为 `blockDim x blockDim` 维度的方形块。该函数可以随时调用，对后续的数学函数调用生效。应选择合适的块维度以优化数学操作，并确保 PCI 传输与计算能够良好地重叠。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 调用成功 |
| CUBLAS_STATUS_INVALID_VALUE | blockDim <= 0 |