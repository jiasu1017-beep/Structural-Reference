### 2.7.15. cublas<t>her2k()

```c++

cublasStatus_t cublasCher2k(cublasHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            int n, int k,
                            const cuComplex       *alpha,
                            const cuComplex       *A, int lda,
                            const cuComplex       *B, int ldb,
                            const float  *beta,
                            cuComplex       *C, int ldc)
cublasStatus_t cublasZher2k(cublasHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            int n, int k,
                            const cuDoubleComplex *alpha,
                            const cuDoubleComplex *A, int lda,
                            const cuDoubleComplex *B, int ldb,
                            const double *beta,
                            cuDoubleComplex *C, int ldc)


```


此函数支持64位整数接口。


此函数执行埃尔米特2k阶更新


$C = \alpha\text{op}(A)\text{op}(B)^{H} + \overset{ˉ}{\alpha}\text{op}(B)\text{op}(A)^{H} + \beta C$


其中 $\alpha$ 和 $\beta$ 是标量，$C$ 是以下三角或上三角模式存储的埃尔米特矩阵，$A$ 和 $B$ 是维度分别为 $\text{op}(A)$ $n \times k$ 和 $\text{op}(B)$ $n \times k$ 的矩阵。同样，对于矩阵 $A$ 和 $B$


$\text{op(}A\text{) and op(}B\text{)} = \left\{ \begin{matrix}
{A\text{ and }B} & {\text{if }\textsf{trans == CUBLAS\_OP\_N}} \\
{A^{H}\text{ and }B^{H}} & {\text{if }\textsf{trans == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | 指向cuBLAS库上下文的句柄。 |
| uplo |  | 输入 | 指定矩阵C的下三角或上三角部分是否存储，另一埃尔米特部分不被引用。 |
| trans |  | 输入 | 运算op(A)，非转置或（共轭）转置。 |
| n |  | 输入 | 矩阵op(A)、op(B)和C的行数。 |
| k |  | 输入 | 矩阵op(A)和op(B)的列数。 |
| alpha | 主机或设备 | 输入 | 用于乘法的<type>标量。 |
| A | 设备 | 输入 | <type>数组，维度为lda x k（当transa == CUBLAS_OP_N且lda >= max(1, n)时），否则为lda x n（lda >= max(1, k)）。 |
| lda |  | 输入 | 用于存储矩阵A的二维数组的主维度。 |
| B | 设备 | 输入 | <type>数组，维度为ldb x k（当transb == CUBLAS_OP_N且ldb >= max(1, n)时），否则为ldb x n（ldb >= max(1, k)）。 |
| ldb |  | 输入 | 用于存储矩阵B的二维数组的主维度。 |
| beta | 主机或设备 | 输入 | 用于乘法的<type>标量。如果beta == 0，则C不必是有效输入。 |
| C | 设备 | 输入/输出 | <type>数组，维度为ldc x n，ldc >= max(1, n)。对角线元素的虚部被假定为零并设置为零。 |
| ldc |  | 输入 | 用于存储矩阵C的二维数组的主维度。 |


此函数可能返回的错误值及其含义如下所述。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果n < 0或k < 0，或
如果trans不是CUBLAS_OP_N、CUBLAS_OP_T和CUBLAS_OP_C之一，或
如果uplo不是CUBLAS_FILL_MODE_LOWER和CUBLAS_FILL_MODE_UPPER之一，或
如果trans == CUBLAS_OP_N时lda < max(1, n)，否则lda < max(1, k)，或
如果ldc < max(1, n)，或
如果alpha或beta为NULL，或
如果beta不为零时C为NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在GPU上启动失败 |


有关参考文献，请参阅NETLIB文档：


[cher2k()](http://www.netlib.org/blas/cher2k.f), [zher2k()](http://www.netlib.org/blas/zher2k.f)