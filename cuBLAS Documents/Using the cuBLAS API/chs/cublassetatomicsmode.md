### 2.4.20. cublasSetAtomicsMode()



```c++

cublasStatus_t cublasSetAtomicsMode(cublasHandlet handle, cublasAtomicsMode_t mode)


```


某些例程（如 `cublas<t>symv()` 和 `cublas<t>hemv()`）具有使用原子操作（atomics）累积结果的替代实现。这种实现通常速度明显更快，但可能在多次运行中产生不完全相同的结果。从数学角度来看，这些差异并不显著，但在调试时可能造成不利影响。


此函数允许或禁止在 cuBLAS 库中对所有具有替代实现的例程使用原子操作。如果在 cuBLAS 例程的文档中未明确说明，则表示该例程没有使用原子操作的替代实现。当禁用原子模式时，在同一硬件上使用相同参数调用时，每个 cuBLAS 例程应产生相同的结果。


默认初始化的 `cublasHandle_t` 对象的原子模式为 `CUBLAS_ATOMICS_NOT_ALLOWED`。请参阅类型部分了解更多详情。


| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 原子模式设置成功 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |