### 2.4.18. cublasSetMatrixAsync()

```c++

cublasStatus_t
cublasSetMatrixAsync(int rows, int cols, int elemSize, const void *A,
                     int lda, void *B, int ldb, cudaStream_t stream)


```

此函数支持64位整数接口。

此函数的功能与 `cublasSetMatrix()` 相同，区别在于数据传送是通过给定的 CUDA™ 流参数异步执行的（相对于主机而言）。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_INVALID_VALUE | 参数 `rows` 或 `cols` 为负数，或 `elemSize`、`lda`、`ldb` 不为正数。 |
| CUBLAS_STATUS_MAPPING_ERROR | 访问 GPU 内存时发生错误 |