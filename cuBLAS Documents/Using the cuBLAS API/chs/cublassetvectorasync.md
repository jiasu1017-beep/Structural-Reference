### 2.4.16. cublasSetVectorAsync()

```c++

cublasStatus_t
cublasSetVectorAsync(int n, int elemSize, const void *hostPtr, int incx,
                     void *devicePtr, int incy, cudaStream_t stream)


```

此函数支持64位整数接口。

此函数的功能与`cublasSetVector()`相同，不同之处在于数据传送是使用指定的CUDA™流参数异步执行的（相对于主机）。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_INVALID_VALUE | 参数incx、incy或elemSize不为正数 |
| CUBLAS_STATUS_MAPPING_ERROR | 访问GPU内存时出错 |