### 4.3.5. cublasXtGetBlockDim()

```c++
cublasXtGetBlockDim(cublasXtHandle_t handle, int *blockDim)
```

此函数允许用户查询用于矩阵平铺的块维度。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 调用成功 |