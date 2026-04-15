### 2.6.7. cublas<t>spr2()



```c++

cublasStatus_t cublasSspr2(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const float  *alpha,
                           const float  *x, int incx,
                           const float  *y, int incy, float  *AP)
cublasStatus_t cublasDspr2(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const double *alpha,
                           const double *x, int incx,
                           const double *y, int incy, double *AP)


```


此函数支持64位整数接口。


此函数执行压缩存储对称秩-2更新


$A = \alpha\left( {\textbf{x}\textbf{y}^{T} + \textbf{y}\textbf{x}^{T}} \right) + A$


其中 $A$ 是以压缩格式存储的 $n \times n$ 对称矩阵，$\mathbf{x}$ 是向量，$\alpha$ 是标量。


如果 `uplo == CUBLAS_FILL_MODE_LOWER`，则对称矩阵 $A$ 下三角部分的元素按列紧密排列（无间隙），使得元素 $A(i,j)$ 存储在内存位置 `AP[i+((2*n-j+1)*j)/2]` 中，其中 $j = 1,\ldots,n$ 且 $i \geq j$。因此，压缩格式仅需 $\frac{n(n + 1)}{2}$ 个元素进行存储。


如果 `uplo == CUBLAS_FILL_MODE_UPPER`，则对称矩阵 $A$ 上三角部分的元素按列紧密排列（无间隙），使得元素 $A(i,j)$ 存储在内存位置 `AP[i+(j*(j+1))/2]` 中，其中 $j = 1,\ldots,n$ 且 $i \leq j$。因此，压缩格式仅需 $\frac{n(n + 1)}{2}$ 个元素进行存储。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS 库上下文的句柄。 |
| uplo |  | 输入 | 指示矩阵 $A$ 的下三角或上三角部分是否存储，其他对称部分未被引用且根据存储的元素推断。 |
| n |  | 输入 | 矩阵 $A$ 的行数和列数。 |
| alpha | 主机或设备 | 输入 | 用于乘法的 <type> 标量。 |
| x | 设备 | 输入 | 包含 n 个元素的 <type> 向量。 |
| incx |  | 输入 | x 中连续元素之间的步长。 |
| y | 设备 | 输入 | 包含 n 个元素的 <type> 向量。 |
| incy |  | 输入 | y 中连续元素之间的步长。 |
| AP | 设备 | 输入/输出 | 以压缩格式存储 $A$ 的 <type> 数组。 |


此函数可能返回的错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0，或
如果 incx == 0 或 incy == 0，或
如果 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或
如果 alpha 为 NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |


参考文献请参阅 NETLIB 文档：


[sspr2()](http://www.netlib.org/blas/sspr2.f), [dspr2()](http://www.netlib.org/blas/dspr2.f)