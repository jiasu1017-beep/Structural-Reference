### 2.6.23. cublas<t>hpr2()



```c++

cublasStatus_t cublasChpr2(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const cuComplex       *alpha,
                           const cuComplex       *x, int incx,
                           const cuComplex       *y, int incy,
                           cuComplex       *AP)
cublasStatus_t cublasZhpr2(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const cuDoubleComplex *alpha,
                           const cuDoubleComplex *x, int incx,
                           const cuDoubleComplex *y, int incy,
                           cuDoubleComplex *AP)


```


此函数支持64位整数接口。


此函数执行压缩厄米特秩2更新


$A = \alpha\textbf{x}\textbf{y}^{H} + \overset{ˉ}{\alpha}\textbf{y}\textbf{x}^{H} + A$


其中 $A$ 是以压缩格式存储的 $n \times n$ 厄米特矩阵，$\mathbf{x}$ 和 $\mathbf{y}$ 是向量，$\alpha$ 是标量。


如果 `uplo == CUBLAS_FILL_MODE_LOWER`，则厄米特矩阵 $A$ 下三角部分的元素按列紧密打包，因此元素 $A(i,j)$ 存储在内存位置 `AP[i+((2*n-j+1)*j)/2]` 中，其中 $j = 1,\ldots,n$ 且 $i \geq j$。因此，压缩格式仅需要 $\frac{n(n + 1)}{2}$ 个元素进行存储。


如果 `uplo == CUBLAS_FILL_MODE_UPPER`，则厄米特矩阵 $A$ 上三角部分的元素按列紧密打包，因此元素 $A(i,j)$ 存储在内存位置 `AP[i+(j*(j+1))/2]` 中，其中 $j = 1,\ldots,n$ 且 $i \leq j$。因此，压缩格式仅需要 $\frac{n(n + 1)}{2}$ 个元素进行存储。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS库上下文的句柄。 |
| uplo |  | input | 指示是否存储矩阵A的下三角或上三角部分，其他厄米特部分未引用且从存储的元素推断。 |
| n |  | input | 矩阵A的行数和列数。 |
| alpha | 主机或设备 | input | 用于乘法的 <type> 标量。 |
| x | 设备 | input | 具有n个元素的 <type> 向量。 |
| incx |  | input | x中连续元素之间的步长。 |
| y | 设备 | input | 具有n个元素的 <type> 向量。 |
| incy |  | input | y中连续元素之间的步长。 |
| AP | 设备 | 输入/输出 | 以压缩格式存储 $A$ 的 <type> 数组。假定对角元素的虚部为零并将其设置为零。 |


此函数返回的可能错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0，或
如果 incx == 0，或
如果 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或
如果 alpha 为 NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在GPU上启动失败 |


有关参考信息，请参阅NETLIB文档：


chpr2, zhpr2