### 4.3.6. cublasXtSetCpuRoutine()



```c++

cublasXtSetCpuRoutine(cublasXtHandle_t handle, cublasXtBlasOp_t blasOp, cublasXtOpType_t type, void *blasFunctor)


```


此函数允许用户提供相应BLAS例程的CPU实现。此函数可与函数cublasXtSetCpuRatio()配合使用，以定义CPU与GPU之间的混合计算。目前，混合功能仅支持xGEMM例程。


| Return Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 调用成功 |
| CUBLAS_STATUS_INVALID_VALUE | blasOp或type定义了无效的组合 |
| CUBLAS_STATUS_NOT_SUPPORTED | 该例程不支持CPU-GPU混合 |