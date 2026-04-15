### 4.2.3. cublasXtBlasOp_t

`cublasXtBlasOp_t` 类型枚举了 cuBLASXt API 支持的 BLAS3 或类 BLAS routine。该枚举类型用作 `cublasXtSetCpuRoutine` 和 `cublasXtSetCpuRatio` 函数的参数，以设置混合配置。

| 值 | 含义 |
| --- | --- |
| CUBLASXT_GEMM | GEMM routine |
| CUBLASXT_SYRK | SYRK routine |
| CUBLASXT_HERK | HERK routine |
| CUBLASXT_SYMM | SYMM routine |
| CUBLASXT_HEMM | HEMM routine |
| CUBLASXT_TRSM | TRSM routine |
| CUBLASXT_SYR2K | SYR2K routine |
| CUBLASXT_HER2K | HER2K routine |
| CUBLASXT_SPMM | SPMM routine |
| CUBLASXT_SYRKX | SYRKX routine |
| CUBLASXT_HERKX | HERKX routine |