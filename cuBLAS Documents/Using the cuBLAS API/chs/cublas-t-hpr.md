### 2.6.22. cublas<t>hpr()



```c++

cublasStatus_t cublasChpr(cublasHandle_t handle, cublasFillMode_t uplo,
                          int n, const float *alpha,
                          const cuComplex       *x, int incx,
                          cuComplex       *AP)
cublasStatus_t cublasZhpr(cublasHandle_t handle, cublasFillMode_t uplo,
                          int n, const double *alpha,
                          const cuDoubleComplex *x, int incx,
                          cuDoubleComplex *AP)


```


此函数支持64位整数接口。


此函数执行压缩Hermitian秩1更新


$A = \alpha\textbf{x}\textbf{x}^{H} + A$


其中 $A$ 是以压缩格式存储的 $n \times n$ Hermitian矩阵，$\mathbf{x}$ 是一个向量，$\alpha$ 是一个标量。


如果 `uplo == CUBLAS_FILL_MODE_LOWER`，则Hermitian矩阵 $A$ 下三角部分的元素按列无间隙地打包在一起，使得元素 $A(i,j)$ 存储在内存位置 `AP[i+((2*n-j+1)*j)/2]` 中，其中 $j = 1,\ldots,n$ 且 $i \geq j$。因此，压缩格式仅需要 $\frac{n(n + 1)}{2}$ 个元素进行存储。


如果 `uplo == CUBLAS_FILL_MODE_UPPER`，则Hermitian矩阵 $A$ 上三角部分的元素按列无间隙地打包在一起，使得元素 $A(i,j)$ 存储在内存位置 `AP[i+(j*(j+1))/2]` 中，其中 $j = 1,\ldots,n$ 且 $i \leq j$。因此，压缩格式仅需要 $\frac{n(n + 1)}{2}$ 个元素进行存储。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS库上下文的句柄。 |
| uplo |  | input | 指示矩阵A的下三角或上三角部分是否被存储，另一个Hermitian部分未被引用，并从存储的元素中推断。 |
| n |  | input | 矩阵A的行数和列数。 |
| alpha | 主机或设备 | input | 用于乘法的<type>标量。 |
| x | 设备 | input | 包含n个元素的<type>向量。 |
| incx |  | input | x中连续元素之间的步长。 |
| AP | 设备 | 输入/输出 | 以压缩格式存储 $A$ 的<type>数组。对角元素的虚部被假设为零并设置为零。 |


此函数返回的可能错误值及其含义如下所述。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0，或
如果 incx == 0，或
如果 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或
如果 alpha 为 NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在GPU上启动 |


参考文献请参阅NETLIB文档：


[chpr()](http://www.netlib.org/blas/chpr.f), [zhpr()](http://www.netlib.org/blas/zhpr.f)