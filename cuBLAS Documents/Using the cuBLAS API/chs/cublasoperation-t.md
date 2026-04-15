### 2.2.3. cublasOperation_t

`cublasOperation_t` 类型用于指定需要对稠密矩阵执行的操作。其取值对应于 Fortran 中的字符 `'N'` 或 `'n'`（非转置）、`'T'` 或 `'t'`（转置）以及 `'C'` 或 `'c'`（共轭转置），这些字符通常作为参数用于传统的 BLAS 实现。

| 值 | 含义 |
| --- | --- |
| CUBLAS_OP_N | 选择非转置操作。 |
| CUBLAS_OP_T | 选择转置操作。 |
| CUBLAS_OP_C | 选择共轭转置操作。 |