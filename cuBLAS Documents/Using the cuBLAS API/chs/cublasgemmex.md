### 2.8.12. cublasGemmEx()

```c++
// 计算类型为 cudaDataType 的版本
cublasStatus_t cublasGemmEx(cublasHandle_t handle,
                           cublasOperation_t transa,
                           cublasOperation_t transb,
                           int m,
                           int n,
                           int k,
                           const void    *alpha,
                           const void     *A,
                           cudaDataType_t Atype,
                           int lda,
                           const void     *B,
                           cudaDataType_t Btype,
                           int ldb,
                           const void    *beta,
                           void           *C,
                           cudaDataType_t Ctype,
                           int ldc,
                           cublasComputeType_t computeType,
                           cublasGemmAlgo_t algo)

// C++ 版本，计算类型为 cudaDataType
#if defined(__cplusplus)
cublasStatus_t cublasGemmEx(cublasHandle_t handle,
                           cublasOperation_t transa,
                           cublasOperation_t transb,
                           int m,
                           int n,
                           int k,
                           const void     *alpha,
                           const void     *A,
                           cudaDataType   Atype,
                           int lda,
                           const void     *B,
                           cudaDataType   Btype,
                           int ldb,
                           const void     *beta,
                           void           *C,
                           cudaDataType   Ctype,
                           int ldc,
                           cudaDataType   computeType,
                           cublasGemmAlgo_t algo)
#endif
```

此函数支持 64 位整数接口。

此函数是 `cublas<t>gemm()` 的扩展，允许用户单独指定 A、B 和 C 矩阵的数据类型、计算精度以及要运行的 GEMM 算法。支持的参数组合列在本节的后面部分。

> **注意**
>
> 提供 `cublasGemmEx()` 函数的第二个变体是为了与 C++ 应用程序代码向后兼容，其中 computeType 参数的类型为 `cudaDataType` 而非 `cublasComputeType_t`。C 应用程序仍可使用更新后的函数签名进行编译。

此函数仅在计算能力为 5.0 或更高版本的设备上支持。

$C = \alpha\text{op}(A)\text{op}(B) + \beta C$

其中 $\alpha$ 和 $\beta$ 是标量，A、B 和 C 是按列优先格式存储的矩阵，维度分别为 $\text{op}(A)$ $m \times k$、$\text{op}(B)$ $k \times n$ 和 $C$ $m \times n$。此外，对于矩阵 A：

$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{transa == CUBLAS\_OP\_N}} \\
A^{T} & {\text{if }\textsf{transa == CUBLAS\_OP\_T}} \\
A^{H} & {\text{if }\textsf{transa == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$

对于矩阵 B，$\text{op}(B)$ 的定义类似。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS 库上下文的句柄。 |
| transa |  | 输入 | 操作 op(A)，即非转置或（共轭）转置。 |
| transb |  | 输入 | 操作 op(B)，即非转置或（共轭）转置。 |
| m |  | 输入 | 矩阵 op(A) 和 C 的行数。 |
| n |  | 输入 | 矩阵 op(B) 和 C 的列数。 |
| k |  | 输入 | op(A) 的列数或 op(B) 的行数。 |
| alpha | 主机或设备 | 输入 | A*B 的缩放因子，类型对应于 computeType 和 Ctype，详见下表。 |
| A | 设备 | 输入 | 维度为 lda × k 的 <type> 数组，当 transa == CUBLAS_OP_N 时 lda >= max(1, m)，否则为 lda × m，lda >= max(1, k)。 |
| Atype |  | 输入 | 指定矩阵 A 数据类型的枚举量。 |
| lda |  | 输入 | 用于存储矩阵 A 的二维数组的主维度。 |
| B | 设备 | 输入 | 维度为 ldb × n 的 <type> 数组，当 transb == CUBLAS_OP_N 时 ldb >= max(1, k)，否则为 ldb × k，ldb >= max(1, n)。 |
| Btype |  | 输入 | 指定矩阵 B 数据类型的枚举量。 |
| ldb |  | 输入 | 用于存储矩阵 B 的二维数组的主维度。 |
| beta | 主机或设备 | 输入 | C 的缩放因子，类型对应于 computeType 和 Ctype，详见下表。如果 beta == 0，C 不必是有效的输入。 |
| C | 设备 | 输入/输出 | 维度为 ldc × n 的 <type> 数组，ldc >= max(1, m)。 |
| Ctype |  | 输入 | 指定矩阵 C 数据类型的枚举量。 |
| ldc |  | 输入 | 用于存储矩阵 C 的二维数组的主维度。 |
| computeType |  | 输入 | 指定计算类型的枚举量。 |
| algo |  | 输入 | 指定算法的枚举量。参见 `cublasGemmAlgo_t`。 |

`cublasGemmEx()` 支持以下计算类型、缩放类型、Atype/Btype 和 Ctype：

| 计算类型 | 缩放类型（alpha 和 beta） | Atype/Btype | Ctype |
| --- | --- | --- | --- |
| CUBLAS_COMPUTE_16F 或
CUBLAS_COMPUTE_16F_PEDANTIC | CUDA_R_16F | CUDA_R_16F | CUDA_R_16F |
| CUBLAS_COMPUTE_32I 或
CUBLAS_COMPUTE_32I_PEDANTIC | CUDA_R_32I | CUDA_R_8I | CUDA_R_32I |
| CUBLAS_COMPUTE_32F 或
CUBLAS_COMPUTE_32F_PEDANTIC | CUDA_R_32F | CUDA_R_16BF | CUDA_R_16BF |
| CUDA_R_16F | CUDA_R_16F |
| CUDA_R_8I | CUDA_R_32F |
| CUDA_R_16BF | CUDA_R_32F |
| CUDA_R_16F | CUDA_R_32F |
| CUDA_R_32F | CUDA_R_32F |
| CUDA_C_32F | CUDA_C_8I | CUDA_C_32F |
| CUDA_C_32F | CUDA_C_32F |
| CUBLAS_COMPUTE_32F_FAST_16F 或
CUBLAS_COMPUTE_32F_FAST_16BF 或
CUBLAS_COMPUTE_32F_FAST_TF32 或
CUBLAS_COMPUTE_32F_EMULATED_16BFX9 | CUDA_R_32F | CUDA_R_32F | CUDA_R_32F |
| CUDA_C_32F | CUDA_C_32F | CUDA_C_32F |
| CUBLAS_COMPUTE_64F 或
CUBLAS_COMPUTE_64F_PEDANTIC | CUDA_R_64F | CUDA_R_64F | CUDA_R_64F |
| CUDA_C_64F | CUDA_C_64F | CUDA_C_64F | CUDA_C_64F |

> **注意**
>
> CUBLAS_COMPUTE_32I 和 CUBLAS_COMPUTE_32I_PEDANTIC 计算类型仅支持 A、B 为 4 字节对齐且 lda、ldb 为 4 的倍数的情况。为获得更好的性能，建议也满足此处列出的 IMMA 内核对常规数据顺序的要求。

此函数返回的可能错误值及其含义列于下表：

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |
| CUBLAS_STATUS_ARCH_MISMATCH | cublasGemmEx() 仅支持计算能力等于或大于 5.0 的 GPU。 |
| CUBLAS_STATUS_NOT_SUPPORTED | Atype、Btype 和 Ctype 的参数组合或算法 algo 不受支持。 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 m < 0 或 n < 0 或 k < 0，或
transa 和 transb 不是 CUBLAS_OP_N、CUBLAS_OP_C、CUBLAS_OP_T 之一，或
当 transa == CUBLAS_OP_N 时 lda < max(1, m)，否则 lda < max(1, k)，或
当 transb == CUBLAS_OP_N 时 ldb < max(1, k)，否则 ldb < max(1, n)，或
ldc < max(1, m)，或
alpha 或 beta 为 NULL，或
当 beta 不为零时 C 为 NULL
Atype 或 Btype 或 Ctype 或 algo 不受支持 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在 GPU 上启动失败。 |

从 11.2 版本开始，使用类型化函数而非扩展函数（`cublas**Ex()`）有助于在链接静态 cuBLAS 库时减小二进制文件大小。

另请参阅：[sgemm()](http://www.netlib.org/blas/sgemm.f)

有关某些 GEMM 算法数值行为的更多信息，请参阅 GEMM 算法数值行为部分。