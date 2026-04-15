### 2.6.19. cublas<t>hpmv()



```c++

cublasStatus_t cublasChpmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const cuComplex       *alpha,
                           const cuComplex       *AP,
                           const cuComplex       *x, int incx,
                           const cuComplex       *beta,
                           cuComplex       *y, int incy)
cublasStatus_t cublasZhpmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const cuDoubleComplex *alpha,
                           const cuDoubleComplex *AP,
                           const cuDoubleComplex *x, int incx,
                           const cuDoubleComplex *beta,
                           cuDoubleComplex *y, int incy)


```


此函数支持64位整数接口。


此函数执行Hermitian压缩矩阵向量乘法


$\textbf{y} = \alpha A\textbf{x} + \beta\textbf{y}$


其中 $A$ 是一个以压缩格式存储的 $n \times n$ Hermitian矩阵，$\mathbf{x}$ 和 $\mathbf{y}$ 是向量，$\alpha$ 和 $\beta$ 是标量。


如果 `uplo == CUBLAS_FILL_MODE_LOWER`，则 Hermitian 矩阵 $A$ 下三角部分的元素按列紧凑存储，无间隙，使得元素 $A(i,j)$ 存储在内存位置 `AP[i+((2*n-j+1)*j)/2]` 中，其中 $j = 1,\ldots,n$ 且 $i \geq j$。因此，压缩格式仅需要 $\frac{n(n + 1)}{2}$ 个元素进行存储。


如果 `uplo == CUBLAS_FILL_MODE_UPPER`，则 Hermitian 矩阵 $A$ 上三角部分的元素按列紧凑存储，无间隙，使得元素 $A(i,j)$ 存储在内存位置 `AP[i+(j*(j+1))/2]` 中，其中 $j = 1,\ldots,n$ 且 $i \leq j$。因此，压缩格式仅需要 $\frac{n(n + 1)}{2}$ 个元素进行存储。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS库上下文的句柄。 |
| uplo |  | input | 指示矩阵A的下三角或上三角部分是否被存储，另一半Hermitian部分未引用且从已存储的元素推断。 |
| n |  | input | 矩阵A的行数和列数。 |
| alpha | host或device | input | 用于乘法的<type>标量。 |
| AP | device | input | 以压缩格式存储 $A$ 的<type>数组。对角线元素的虚部假定为零。 |
| x | device | input | 包含n个元素的<type>向量。 |
| incx |  | input | x中连续元素之间的步长。 |
| beta | host或device | input | 用于乘法的<type>标量。如果beta == 0，则y不必是有效输入。 |
| y | device | in/out | 包含n个元素的<type>向量。 |
| incy |  | input | y中连续元素之间的步长。 |


此函数返回的可能错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0，或
如果 incx == 0 或 incy == 0，或
如果 uplo != CUBLAS_FILL_MODE_LOWER 且 uplo != CUBLAS_FILL_MODE_UPPER，或
如果 alpha 或 beta 为 NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在GPU上启动 |


参考文献请参阅NETLIB文档：


[chpmv()](http://www.netlib.org/blas/chpmv.f), [zhpmv()](http://www.netlib.org/blas/zhpmv.f)