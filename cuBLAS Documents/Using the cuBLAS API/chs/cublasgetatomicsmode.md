### 2.4.21. cublasGetAtomicsMode()

```c++
cublasStatus_t cublasGetAtomicsMode(cublasHandle_t handle, cublasAtomicsMode_t *mode)
```

此函数查询特定 cuBLAS 上下文的原子模式。

默认初始化的 `cublasHandle_t` 对象的默认原子模式为 `CUBLAS_ATOMICS_NOT_ALLOWED`。请参阅类型部分了解更多详情。

| Return Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 原子模式查询成功 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 参数 mode 为空指针 |