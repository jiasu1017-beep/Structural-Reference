### 2.2.8. cublasAtomicsMode_t

该类型指示是否可以使用具有原子操作替代实现的 cuBLAS 例程。原子操作模式可以分别使用 `cublasSetAtomicsMode()` 和 `cublasGetAtomicsMode()` 例程进行设置和查询。

| 值 | 含义 |
| --- | --- |
| `CUBLAS_ATOMICS_NOT_ALLOWED` | 不允许使用原子操作。 |
| `CUBLAS_ATOMICS_ALLOWED` | 允许使用原子操作。 |