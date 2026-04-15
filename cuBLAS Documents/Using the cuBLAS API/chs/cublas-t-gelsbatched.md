### 2.8.8. cublas<t>gelsBatched()



```c++

cublasStatus_t cublasSgelsBatched( cublasHandle_t handle,
                                   cublasOperation_t trans,
                                   int m,
                                   int n,
                                   int nrhs,
                                   float *const Aarray[],
                                   int lda,
                                   float *const Carray[],
                                   int ldc,
                                   int *info,
                                   int *devInfoArray,
                                   int batchSize );

cublasStatus_t cublasDgelsBatched( cublasHandle_t handle,
                                   cublasOperation_t trans,
                                   int m,
                                   int n,
                                   int nrhs,
                                   double *const Aarray[],
                                   int lda,
                                   double *const Carray[],
                                   int ldc,
                                   int *info,
                                   int *devInfoArray,
                                   int batchSize );

cublasStatus_t cublasCgelsBatched( cublasHandle_t handle,
                                   cublasOperation_t trans,
                                   int m,
                                   int n,
                                   int nrhs,
                                   cuComplex *const Aarray[],
                                   int lda,
                                   cuComplex *const Carray[],
                                   int ldc,
                                   int *info,
                                   int *devInfoArray,
                                   int batchSize );

cublasStatus_t cublasZgelsBatched( cublasHandle_t handle,
                                   cublasOperation_t trans,
                                   int m,
                                   int n,
                                   int nrhs,
                                   cuDoubleComplex *const Aarray[],
                                   int lda,
                                   cuDoubleComplex *const Carray[],
                                   int ldc,
                                   int *info,
                                   int *devInfoArray,
                                   int batchSize );


```


`Aarray` 是一个指向以列优先格式存储的矩阵的指针数组。`Carray` 是一个指向以列优先格式存储的矩阵的指针数组。


此函数求解一批超定系统的最小二乘解：它求解如下所述的最小二乘问题：



```c++

minimize  || Carray[i] - Aarray[i]*Xarray[i] || , with i = 0, ...,batchSize-1


```


退出时，每个 `Aarray[i]` 被其 QR 分解覆盖，每个 `Carray[i]` 被最小二乘解覆盖。


cublas<t>gelsBatched 仅支持非转置操作，且仅求解超定系统（m >= n）。


cublas<t>gelsBatched 仅支持计算能力 2.0 或更高版本。


此函数旨在用于矩阵规模较小且启动开销较大的场景。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | 指向 cuBLAS 库上下文的句柄。 |
| trans |  | 输入 | op(Aarray[i]) 的操作，即非转置或（共轭）转置。当前仅支持非转置操作。 |
| m |  | 输入 | 每个 Aarray[i] 和 Carray[i] 的行数（当 trans == CUBLAS_OP_N 时），否则为每个 Aarray[i] 的列数（当前不支持）。 |
| n |  | 输入 | 每个 Aarray[i] 的列数（当 trans == CUBLAS_OP_N 时），否则为每个 Aarray[i] 和 Carray[i] 的行数（当前不支持）。 |
| nrhs |  | 输入 | 每个 Carray[i] 的列数。 |
| Aarray | 设备 | 输入/输出 | 指向 <type> 数组的指针数组，每个数组维度为 m x n（当 trans == CUBLAS_OP_N 时，lda >= max(1, m)），否则为 n x m（lda >= max(1, n)）（当前不支持）。矩阵 Aarray[i] 不应重叠；否则行为未定义。 |
| lda |  | 输入 | 用于存储每个矩阵 Aarray[i] 的二维数组的主导维度。 |
| Carray | 设备 | 输入/输出 | 指向 <type> 数组的指针数组，每个数组维度为 m x nrhs（当 trans == CUBLAS_OP_N 时，ldc >= max(1, m)），否则为 n x nrhs（lda >= max(1, n)）（当前不支持）。矩阵 Carray[i] 不应重叠；否则行为未定义。 |
| ldc |  | 输入 | 用于存储每个矩阵 Carray[i] 的二维数组的主导维度。 |
| info | 主机 | 输出 | 如果 info == 0，则传递给函数的参数有效
如果 info < 0，则位置 -info 处的参数无效 |
| devInfoArray | 设备 | 输出 | 可选的整数数组，维度为 batchsize。
如果非空，devInfoArray[i] == V 的每个元素具有以下含义：
V == 0：第 i 个问题已成功求解
V > 0：Aarray[i] 的第 V 个对角元素为零。Aarray[i] 不是满秩的。 |
| batchSize |  | 输入 | Aarray 和 Carray 中包含的指针数量 |


此函数返回的可能错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 m < 0 或 n < 0 或 nrhs < 0 或 batchSize < 0，或
如果 lda < max(1, m) 或 ldc < max(1, m) |
| CUBLAS_STATUS_NOT_SUPPORTED | 参数 m < n 或 trans 与非转置不同。 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在 GPU 上启动失败 |


有关参考信息，请参阅 NETLIB 文档：


[sgels()](http://www.netlib.org/lapack/single/sgels.f), [dgels()](http://www.netlib.org/lapack/double/dgels.f), [cgels()](http://www.netlib.org/lapack/complex/cgels.f), [zgels()](http://www.netlib.org/lapack/complex16/zgels.f)