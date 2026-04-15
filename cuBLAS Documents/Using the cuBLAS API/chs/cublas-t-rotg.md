### 2.5.9. cublas<t>rotg()



```c++

cublasStatus_t cublasSrotg(cublasHandle_t handle,
                           float           *a, float           *b,
                           float  *c, float           *s)
cublasStatus_t cublasDrotg(cublasHandle_t handle,
                           double          *a, double          *b,
                           double *c, double          *s)
cublasStatus_t cublasCrotg(cublasHandle_t handle,
                           cuComplex       *a, cuComplex       *b,
                           float  *c, cuComplex       *s)
cublasStatus_t cublasZrotg(cublasHandle_t handle,
                           cuDoubleComplex *a, cuDoubleComplex *b,
                           double *c, cuDoubleComplex *s)


```


此函数支持64位整数接口。


此函数构造Givens旋转矩阵


$G = \begin{pmatrix}
c & s \\
{- s} & c \\
\end{pmatrix}$


用于将$2 \times 1$向量$\left( {a,b} \right)^{T}$的第二个元素置零。


然后，对于实数，我们可以写成


$\begin{pmatrix}
c & s \\
{- s} & c \\
\end{pmatrix}\begin{pmatrix}
a \\
b \\
\end{pmatrix} = \begin{pmatrix}
r \\
0 \\
\end{pmatrix}$


其中$c^{2} + s^{2} = 1$且$r = \pm \sqrt{a^{2} + b^{2}}$。参数$a$和$b$分别被覆盖为$r$和$z$。$z$的值使得$c$和$s$可以通过以下规则恢复：


$\left( {c,s} \right) = \begin{cases}
\left( {\sqrt{1 - z^{2}},z} \right) & {\text{ if }\left| z \middle| < 1 \right.} \\
\left( {0.0,1.0} \right) & {\text{ if }\left| z \middle| = 1 \right.} \\
\left( 1/z,\sqrt{1 - z^{2}} \right) & {\text{ if }\left| z \middle| > 1 \right.} \\
\end{cases}$


对于复数，我们可以写成


$\begin{pmatrix}
c & s \\
{- \bar{s}} & c \\
\end{pmatrix}\begin{pmatrix}
a \\
b \\
\end{pmatrix} = \begin{pmatrix}
r \\
0 \\
\end{pmatrix}$


其中$c^{2} + \left( {\bar{s} \times s} \right) = 1$且$r = \frac{a}{|a|} \times \parallel \left( {a,b} \right)^{T} \parallel_{2}$，其中$\parallel \left( {a,b} \right)^{T} \parallel_{2} = \sqrt{\left| a|^{2} + \middle| B|^{2} \right.}$（当$a \neq 0$时），当$a = 0$时$r = b$。最后，参数$a$在退出时被覆盖为$r$。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS库上下文的句柄。 |
| a | 主机或设备 | 输入/输出 | 被覆盖为\(r\)的<type>标量。 |
| b | 主机或设备 | 输入/输出 | 被覆盖为\(z\)的<type>标量。 |
| c | 主机或设备 | 输出 | 旋转矩阵的余弦元素。 |
| s | 主机或设备 | 输出 | 旋转矩阵的正弦元素。 |


此函数可能返回的错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数未能成功在GPU上启动 |

有关参考文献，请参阅NETLIB文档：


[srotg()](http://www.netlib.org/blas/srotg.f90), [drotg()](http://www.netlib.org/blas/drotg.f90), [crotg()](http://www.netlib.org/blas/crotg.f90), [zrotg()](http://www.netlib.org/blas/zrotg.f90)