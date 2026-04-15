### 2.6.5. cublas<t>spmv()



```c++

cublasStatus_t cublasSspmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const float  *alpha, const float  *AP,
                           const float  *x, int incx, const float  *beta,
                           float  *y, int incy)
cublasStatus_t cublasDspmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const double *alpha, const double *AP,
                           const double *x, int incx, const double *beta,
                           double *y, int incy)


```


此函数支持64位整数接口。


此函数执行对称压缩矩阵向量乘法


$\textbf{y} = \alpha A\textbf{x} + \beta\textbf{y}$


其中 $A$ 是一个以压缩格式存储的 $n \times n$ 对称矩阵，$\mathbf{x}$ 和 $\mathbf{y}$ 是向量，$\alpha$ 和 $\beta$ 是标量。


如果 `uplo == CUBLAS_FILL_MODE_LOWER`，则对称矩阵 $A$ 下三角部分的元素按列紧凑存储，无间隙，因此元素 $A(i,j)$ 存储在内存位置 `AP[i+((2*n-j+1)*j)/2]`，其中 $j = 1,\ldots,n$ 且 $i \geq j$。因此，压缩格式仅需 $\frac{n(n + 1)}{2}$ 个元素存储。


如果 `uplo == CUBLAS_FILL_MODE_UPPER`，则对称矩阵 $A$ 上三角部分的元素按列紧凑存储，无间隙，因此元素 $A(i,j)$ 存储在内存位置 `AP[i+(j*(j+1))/2]`，其中 $j = 1,\ldots,n$ 且 $i \leq j$。因此，压缩格式仅需 $\frac{n(n + 1)}{2}$ 个元素存储。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS 库上下文的句柄。 |
| uplo |  | 输入 | 指示矩阵 $A$ 的下三角或上三角部分是否被存储，另一个对称部分未被引用，且可从已存储的元素推断。 |
| n |  | 输入 | 矩阵 $A$ 的行数和列数。 |
| alpha | 主机或设备 | 输入 | 用于乘法的 <type> 标量。 |
| AP | 设备 | 输入 | 以压缩格式存储 $A$ 的 <type> 数组。 |
| x | 设备 | 输入 | 包含 n 个元素的 <type> 向量。 |
| incx |  | 输入 | x 中连续元素之间的步长。 |
| beta | 主机或设备 | 输入 | 用于乘法的 <type> 标量。如果 beta == 0，则 y 不必是有效输入。 |
| y | 设备 | 输入/输出 | 包含 n 个元素的 <type> 向量。 |
| incy |  | 输入 | y 中连续元素之间的步长。 |


此函数返回的可能错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0，或
如果 incx == 0 或 incy == 0，或
如果 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或
如果 alpha 或 beta 为 NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |


相关参考请参阅 NETLIB 文档：


[sspmv()](http://www.netlib.org/blas/sspmv.f)，[dspmv()](http://www.netlib.org/blas/dspmv.f)