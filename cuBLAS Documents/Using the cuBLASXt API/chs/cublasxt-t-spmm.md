### 4.4.12. cublasXt<t>spmm()



```c++

cublasStatus_t cublasXtSspmm( cublasXtHandle_t handle,
                                cublasSideMode_t side,
                                cublasFillMode_t uplo,
                                size_t m,
                                size_t n,
                                const float *alpha,
                                const float *AP,
                                const float *B,
                                size_t ldb,
                                const float *beta,
                                float *C,
                                size_t ldc );

cublasStatus_t cublasXtDspmm( cublasXtHandle_t handle,
                                cublasSideMode_t side,
                                cublasFillMode_t uplo,
                                size_t m,
                                size_t n,
                                const double *alpha,
                                const double *AP,
                                const double *B,
                                size_t ldb,
                                const double *beta,
                                double *C,
                                size_t ldc );

cublasStatus_t cublasXtCspmm( cublasXtHandle_t handle,
                                cublasSideMode_t side,
                                cublasFillMode_t uplo,
                                size_t m,
                                size_t n,
                                const cuComplex *alpha,
                                const cuComplex *AP,
                                const cuComplex *B,
                                size_t ldb,
                                const cuComplex *beta,
                                cuComplex *C,
                                size_t ldc );

cublasStatus_t cublasXtZspmm( cublasXtHandle_t handle,
                                cublasSideMode_t side,
                                cublasFillMode_t uplo,
                                size_t m,
                                size_t n,
                                const cuDoubleComplex *alpha,
                                const cuDoubleComplex *AP,
                                const cuDoubleComplex *B,
                                size_t ldb,
                                const cuDoubleComplex *beta,
                                cuDoubleComplex *C,
                                size_t ldc );


```


此函数执行对称压缩矩阵-矩阵乘法


$C = \left\{ \begin{matrix}
{\alpha AB + \beta C} & {\text{if }\textsf{side == $\mathrm{CUBLAS\_SIDE\_LEFT}$}} \\
{\alpha BA + \beta C} & {\text{if }\textsf{side == $\mathrm{CUBLAS\_SIDE\_RIGHT}$}} \\
\end{matrix} \right.$


其中 $A$ 是一个以压缩格式存储的 $n \times n$ 对称矩阵，$B$ 和 $C$ 是 $m \times n$ 矩阵，$\alpha$ 和 $\beta$ 是标量。


如果 `uplo == CUBLAS_FILL_MODE_LOWER`，则对称矩阵 $A$ 下三角部分的元素按列无间隙地压缩在一起，因此元素 $A(i,j)$ 存储在内存位置 `AP[i+((2*n-j+1)*j)/2]` 中，其中 $j = 1,\ldots,n$ 且 $i \geq j$。因此，压缩格式仅需要 $\frac{n(n + 1)}{2}$ 个元素进行存储。


如果 `uplo == CUBLAS_FILL_MODE_UPPER`，则对称矩阵 $A$ 上三角部分的元素按列无间隙地压缩在一起，因此元素 $A(i,j)$ 存储在内存位置 `AP[i+(j*(j+1))/2]` 中，其中 $j = 1,\ldots,n$ 且 $i \leq j$。因此，压缩格式仅需要 $\frac{n(n + 1)}{2}$ 个元素进行存储。


> **注意**

注意
压缩矩阵 AP 必须位于主机或托管内存中，而其他矩阵可以位于主机或任何 GPU 设备上


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLASXt API 上下文的句柄。 |
| side |  | 输入 | 指示矩阵 A 位于 B 的左侧还是右侧。 |
| uplo |  | 输入 | 指示矩阵 A 的下三角还是上三角部分被存储，另一个对称部分未被引用，而是从存储的元素中推断。 |
| m |  | 输入 | 矩阵 A 和 B 的行数，矩阵 A 相应调整大小。 |
| n |  | 输入 | 矩阵 C 和 A 的列数，矩阵 A 相应调整大小。 |
| alpha | 主机 | 输入 | <type> 标量，用于乘法运算。 |
| AP | 主机 | 输入 | 以压缩格式存储的 <type> 数组 A。 |
| B | 主机或设备 | 输入 | 维度为 ldb x n 的 <type> 数组，ldb >= max(1, m)。 |
| ldb |  | 输入 | 用于存储矩阵 B 的二维数组的主维度。 |
| beta | 主机 | 输入 | <type> 标量，用于乘法运算，如果 beta == 0，则 C 不必是有效输入。 |
| C | 主机或设备 | 输入/输出 | 维度为 ldc x n 的 <type> 数组，ldc >= max(1, m)。 |
| ldc |  | 输入 | 用于存储矩阵 C 的二维数组的主维度。 |


此函数返回的可能错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 参数 m < 0 或 n < 0 |
| CUBLAS_STATUS_NOT_SUPPORTED | 矩阵 AP 位于 GPU 设备上 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在 GPU 上启动失败 |


参考文献请参阅 NETLIB 文档：


[ssymm()](http://www.netlib.org/blas/ssymm.f), [dsymm()](http://www.netlib.org/blas/dsymm.f), [csymm()](http://www.netlib.org/blas/csymm.f), [zsymm()](http://www.netlib.org/blas/zsymm.f)