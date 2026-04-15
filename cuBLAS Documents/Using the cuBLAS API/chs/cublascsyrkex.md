### 2.8.16. cublasCsyrkEx()



```c++

cublasStatus_t cublasCsyrkEx(cublasHandle_t handle,
                             cublasFillMode_t uplo,
                             cublasOperation_t trans,
                             int n,
                             int k,
                             const cuComplex *alpha,
                             const void      *A,
                             cudaDataType    Atype,
                             int lda,
                             const cuComplex *beta,
                             cuComplex       *C,
                             cudaDataType    Ctype,
                             int ldc)


```


此函数支持64位整数接口。


此函数是cublasCsyrk()的扩展，其中输入矩阵和输出矩阵可以具有更低的精度，但计算仍然以`cuComplex`类型进行


此函数执行对称秩- $k$ 更新


$C = \alpha\text{op}(A)\text{op}(A)^{T} + \beta C$


其中 $\alpha$ 和 $\beta$ 是标量，$C$ 是以下三角或上三角模式存储的对称矩阵，$A$ 是维度为 $\text{op}(A)$ $n \times k$ 的矩阵。同样，对于矩阵 $A$


$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{transa == CUBLAS\_OP\_N}} \\
A^{T} & {\text{if }\textsf{transa == CUBLAS\_OP\_T}} \\
\end{matrix} \right.$


> **注意**

此例程仅在计算能力大于或等于5.0的GPU上支持。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | 指向cuBLAS库上下文的句柄。 |
| uplo |  | 输入 | 指示矩阵C的下三角或上三角部分是否存储，另一对称部分未引用且从存储的元素推断。 |
| trans |  | 输入 | 非转置或转置的运算op(A)。 |
| n |  | 输入 | 矩阵op(A)和C的行数。 |
| k |  | 输入 | 矩阵op(A)的列数。 |
| alpha | 主机或设备 | 输入 | 用于乘法运算的<类型>标量。 |
| A | 设备 | 输入 | 维度为lda x k的<类型>数组，当trans == CUBLAS_OP_N时lda >= max(1, n)，否则为lda x n且lda >= max(1, k)。 |
| Atype |  | 输入 | 指定矩阵A数据类型的枚举量。 |
| lda |  | 输入 | 用于存储矩阵A的二维数组的leading dimension。 |
| beta | 主机或设备 | 输入 | 用于乘法运算的<类型>标量。如果beta == 0，则C不必是有效输入。 |
| C | 设备 | 输入/输出 | 维度为ldc x n的<类型>数组，ldc >= max(1, n)。 |
| Ctype |  | 输入 | 指定矩阵C数据类型的枚举量。 |
| ldc |  | 输入 | 用于存储矩阵C的二维数组的leading dimension。 |


cublasCsyrkEx()支持的矩阵类型组合如下：


| A | C |
| --- | --- |
| CUDA_C_8I | CUDA_C_32F |
| CUDA_C_32F | CUDA_C_32F |


此函数返回的可能错误值及其含义如下：


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |
| CUBLAS_STATUS_INVALID_VALUE | 如果n < 0或k < 0，或
如果uplo不是CUBLAS_FILL_MODE_LOWER和CUBLAS_FILL_MODE_UPPER之一，或
如果trans不是CUBLAS_OP_N、CUBLAS_OP_T和CUBLAS_OP_C之一，或
如果trans == CUBLAS_OP_N时lda < max(1, n)且否则lda < max(1, k)，或
如果ldc < max(1, n)，或
如果Atype或Ctype不受支持 |
| CUBLAS_STATUS_NOT_SUPPORTED | Atype和Ctype参数的组合不受支持。 |
| CUBLAS_STATUS_ARCH_MISMATCH | 设备的计算能力低于5.0。 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在GPU上启动失败。 |


有关参考，请参阅NETLIB文档：


[ssyrk()](http://www.netlib.org/blas/ssyrk.f), [dsyrk()](http://www.netlib.org/blas/dsyrk.f), [csyrk()](http://www.netlib.org/blas/csyrk.f), [zsyrk()](http://www.netlib.org/blas/zsyrk.f)