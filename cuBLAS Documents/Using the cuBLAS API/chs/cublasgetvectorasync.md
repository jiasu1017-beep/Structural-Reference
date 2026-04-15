### 2.4.17. cublasGetVectorAsync()

```c++
cublasStatus_t
cublasGetVectorAsync(int n, int elemSize, const void *devicePtr, int incx,
                     void *hostPtr, int incy, cudaStream_t stream)
```

此函数支持 64 位整数接口。

此函数的功能与 `cublasGetVector()` 相同，区别在于数据传送是使用给定的 CUDA™ 流参数异步（相对于主机）完成的。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_INVALID_VALUE | 参数 incx、incy 或 elemSize 不为正数 |
| CUBLAS_STATUS_MAPPING_ERROR | 访问 GPU 内存时出错 |