### 2.5.10. cublas<t>rotm()

```c++
// 应用修改的Givens变换到向量 x 和 y
cublasStatus_t cublasSrotm(cublasHandle_t handle, int n, float  *x, int incx,
                           float  *y, int incy, const float*  param)
cublasStatus_t cublasDrotm(cublasHandle_t handle, int n, double *x, int incx,
                           double *y, int incy, const double* param)
```

此函数支持64位整数接口。

此函数将改进的Givens变换

$H = \begin{pmatrix}
h_{11} & h_{12} \\
h_{21} & h_{22} \\
\end{pmatrix}$

应用于向量 `x` 和 `y`。

因此，结果为 $\mathbf{x}\lbrack k\rbrack = h_{11} \times \mathbf{x}\lbrack k\rbrack + h_{12} \times \mathbf{y}\lbrack j\rbrack$ 和 $\mathbf{y}\lbrack j\rbrack = h_{21} \times \mathbf{x}\lbrack k\rbrack + h_{22} \times \mathbf{y}\lbrack j\rbrack$，其中 $k = 1 + \left( {i - 1} \right)*\text{incx}$ 且 $j = 1 + \left( {i - 1} \right)*\text{incy}$。请注意，最后两个等式反映了为与Fortran兼容而使用的1-based索引。

矩阵 $H$ 的元素 $h_{11}$、$h_{12}$、$h_{21}$ 和 $h_{22}$ 分别存储在 `param[1]`、`param[2]`、`param[3]` 和 `param[4]` 中。`flag = param[0]` 定义了矩阵 $H$ 条目的以下预定义值：

| flag == -1.0 | flag == 0.0 | flag == 1.0 | flag == -2.0 |
| --- | --- | --- | --- |
| \(\begin{pmatrix}
h_{11} & h_{12} \\
h_{21} & h_{22} \\
\end{pmatrix}\) | \(\begin{pmatrix}
{1.0} & h_{12} \\
h_{21} & {1.0} \\
\end{pmatrix}\) | \(\begin{pmatrix}
h_{11} & {1.0} \\
{- 1.0} & h_{22} \\
\end{pmatrix}\) | \(\begin{pmatrix}
{1.0} & {0.0} \\
{0.0} & {1.0} \\
\end{pmatrix}\) |

请注意，flag隐含的-1.0、0.0和1.0值不会存储在param中。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS库上下文的句柄。 |
| n |  | input | 向量x和y中的元素数量。 |
| x | device | in/out | 包含n个元素的<type>向量。 |
| incx |  | input | x中连续元素之间的步长。 |
| y | device | in/out | 包含n个元素的<type>向量。 |
| incy |  | input | y中连续元素之间的步长。 |
| param | host or device | input | 包含5个元素的<type>向量，其中param[0]和param[1..4]分别包含flag和矩阵\(H\)。 |

此函数返回的可能错误值及其含义如下所列。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在GPU上启动 |

有关参考，请参阅NETLIB文档：

[srotm()](http://www.netlib.org/blas/srotm.f), [drotm()](http://www.netlib.org/blas/drotm.f)