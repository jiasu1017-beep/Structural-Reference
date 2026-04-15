### 4.3.7. cublasXtSetCpuRatio()

```c++
cublasXtSetCpuRatio(cublasXtHandle_t handle, cublasXtBlasOp_t blasOp, cublasXtOpType_t type, float ratio )
```

此函数允许用户定义在混合计算中CPU上应完成的工作负载百分比。此函数可与cublasXtSetCpuRoutine()函数结合使用，定义CPU和GPU之间的混合计算。目前混合功能仅支持xGEMM例程。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 调用成功 |
| CUBLAS_STATUS_INVALID_VALUE | blasOp或type定义了无效的组合 |
| CUBLAS_STATUS_NOT_SUPPORTED | 该例程不支持CPU-GPU混合 |