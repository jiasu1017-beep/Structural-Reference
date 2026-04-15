### 4.2.2. cublasXtOpType_t

`cublasOpType_t` 枚举了 BLAS 例程支持的四种可能的类型。此枚举用作例程 `cublasXtSetCpuRoutine` 和 `cublasXtSetCpuRatio` 的参数，以设置混合配置。

| Value | 含义 |
| --- | --- |
| CUBLASXT_FLOAT | float 或单精度类型 |
| CUBLASXT_DOUBLE | 双精度类型 |
| CUBLASXT_COMPLEX | 单精度复数 |
| CUBLASXT_DOUBLECOMPLEX | 双精度复数 |