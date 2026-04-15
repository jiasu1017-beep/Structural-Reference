### 2.8.15. cublasGemmGroupedBatchedEx()

```c++

cublasStatus_t cublasGemmGroupedBatchedEx(cublasHandle_t handle,
                            const cublasOperation_t transa_array[],
                            const cublasOperation_t transb_array[],
                            const int m_array[],
                            const int n_array[],
                            const int k_array[],
                            const void    *alpha_array,
                            const void     *const Aarray[],
                            cudaDataType_t Atype,
                            const int lda_array[],
                            const void     *const Barray[],
                            cudaDataType_t Btype,
                            const int ldb_array[],
                            const void    *beta_array,
                            void           *const Carray[],
                            cudaDataType_t Ctype,
                            const int ldc_array[],
                            int group_count,
                            const int group_size[],
                            cublasComputeType_t computeType)


```

此函数支持 64 位整数接口。

此函数对矩阵组执行矩阵-矩阵乘法。给定的组被认为是"均匀的"，即所有实例对于各自的 A、B 和 C 矩阵具有相同的维度（m, n, k）、前导维度（lda, ldb, ldc）和转置（transa, transb）。但是，维度、前导维度、转置和缩放因子（alpha, beta）可能在不同组之间有所不同。每个批次实例的输入矩阵和输出矩阵的地址从调用者传递给函数的指针数组中读取。这在功能上等价于以下内容：



```c++

idx = 0;
// 遍历所有组
for i = 0:group_count - 1
    // 遍历每个组内的所有实例
    for j = 0:group_size[i] - 1
        gemmEx(transa_array[i], transb_array[i], m_array[i], n_array[i], k_array[i],
               alpha_array[i], Aarray[idx], Atype, lda_array[i], Barray[idx], Btype,
               ldb_array[i], beta_array[i], Carray[idx], Ctype, ldc_array[i],
               computeType, CUBLAS_GEMM_DEFAULT);
        idx += 1;
    end
end


```


其中 $\text{$\mathrm{alpha\_array}$}$ 和 $\text{$\mathrm{beta\_array}$}$ 是缩放因子数组，$\text{Aarray}$、$\text{Barray}$ 和 $\text{Carray}$ 是指向以列主序格式存储的矩阵的指针数组。对于属于组 $i$ 的给定索引 $\text{idx}$，维度如下：


> \(\text{op}(\text{Aarray}\lbrack\text{idx}\rbrack)\)：\(\text{$\mathrm{m\_array}$}\lbrack i\rbrack \times \text{$\mathrm{k\_array}$}\lbrack i\rbrack\)
\(\text{op}(\text{Barray}\lbrack\text{idx}\rbrack)\)：\(\text{$\mathrm{k\_array}$}\lbrack i\rbrack \times \text{$\mathrm{n\_array}$}\lbrack i\rbrack\)
\(\text{Carray}\lbrack\text{idx}\rbrack\)：\(\text{$\mathrm{m\_array}$}\lbrack i\rbrack \times \text{$\mathrm{n\_array}$}\lbrack i\rbrack\)


> **注意**

此 API 接收两种不同长度的数组。维度、前导维度、转置和缩放因子数组的长度为 group_count，矩阵数组的长度为 problem_count，其中 \(\text{$\mathrm{problem\_count}$} = \sum_{i = 0}^{\text{$\mathrm{group\_count}$} - 1} \text{$\mathrm{group\_size}$}\lbrack i\rbrack\)


对于组 $i$ 中的矩阵 $A[\text{idx}]$


$\text{op}(A[\text{idx}]) = \left\{ \begin{matrix}
A[\text{idx}] & {\text{if }\textsf{$\mathrm{transa\_array}\lbrack i\rbrack$ == $\mathrm{CUBLAS\_OP\_N}$}} \\
A[\text{idx}]^{T} & {\text{if }\textsf{$\mathrm{transa\_array}\lbrack i\rbrack$ == $\mathrm{CUBLAS\_OP\_T}$}} \\
A[\text{idx}]^{H} & {\text{if }\textsf{$\mathrm{transa\_array}\lbrack i\rbrack$ == $\mathrm{CUBLAS\_OP\_C}$}} \\
\end{matrix} \right.$


并且 $\text{op}(B[\text{idx}])$ 对于组 $i$ 中的矩阵 $B[\text{idx}]$ 类似定义。


> **注意**

\(C\lbrack\text{idx}\rbrack\) 矩阵不得重叠，即各个 gemm 操作必须能够独立计算；否则，将产生未定义行为。


在某些问题规模上，在不同的 CUDA 流中多次调用 cublasGemmBatchedEx() 可能比使用此 API 更有优势。


| 参数 | 内存 | 输入/输出 | 含义 | 数组长度 |
| --- | --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS 库上下文的句柄。 |  |
| transa_array | 主机端 | 输入 | 包含每个组的 op(A[idx]) 操作的数组，即非转置或（共轭）转置。 | group_count |
| transb_array | 主机端 | 输入 | 包含每个组的 op(B[idx]) 操作的数组，即非转置或（共轭）转置。 | group_count |
| m_array | 主机端 | 输入 | 包含每个组的矩阵 op(A[idx]) 和 C[idx] 行数的数组。 | group_count |
| n_array | 主机端 | 输入 | 包含每个组的 op(B[idx]) 和 C[idx] 列数的数组。 | group_count |
| k_array | 主机端 | 输入 | 包含每个组的 op(A[idx]) 列数和 op(B[idx]) 行数的数组。 | group_count |
| alpha_array | 主机端 | 输入 | 包含每个组乘法所用 <Scale Type> 标量的数组。 | group_count |
| Aarray | 设备端 | 输入 | 指向 <Atype> 数组的指针数组，每个数组维度为 lda[i] x k[i]，其中当 transa[i] == CUBLAS_OP_N 时 lda[i] >= max(1,m[i])，否则为 lda[i] x m[i]，lda[i] >= max(1,k[i])。
所有指针必须满足特定的对齐要求。请参阅下文了解详情。 | problem_count |
| Atype |  | 输入 | 指定 A 数据类型的枚举值。 |  |
| lda_array | 主机端 | 输入 | 包含每个组用于存储每个矩阵 A[idx] 的二维数组前导维度的数组。 | group_count |
| Barray | 设备端 | 输入 | 指向 <Btype> 数组的指针数组，每个数组维度为 ldb[i] x n[i]，其中当 transb[i] == CUBLAS_OP_N 时 ldb[i] >= max(1,k[i])，否则为 ldb[i] x k[i]，ldb[i] >= max(1,n[i])。
所有指针必须满足特定的对齐要求。请参阅下文了解详情。 | problem_count |
| Btype |  | 输入 | 指定 B 数据类型的枚举值。 |  |
| ldb_array | 主机端 | 输入 | 包含每个组用于存储每个矩阵 B[idx] 的二维数组前导维度的数组。 | group_count |
| beta_array | 主机端 | 输入 | 包含每个组乘法所用 <Scale Type> 标量的数组。 | group_count |
| Carray | 设备端 | 输入/输出 | 指向 <Ctype> 数组的指针数组。维度为 ldc[i] x n[i]，其中 ldc[i] >= max(1,m[i])。矩阵 C[idx] 不应重叠；否则，将产生未定义行为。
所有指针必须满足特定的对齐要求。请参阅下文了解详情。 | problem_count |
| Ctype |  | 输入 | 指定 C 数据类型的枚举值。 |  |
| ldc_array | 主机端 | 输入 | 包含每个组用于存储每个矩阵 C[idx] 的二维数组前导维度的数组。 | group_count |
| group_count | 主机端 | 输入 | 组的数量 |  |
| group_size | 主机端 | 输入 | 包含每个组在 Aarray、Barray 和 Carray 中的指针数量的数组。 | group_count |
| computeType |  | 输入 | 指定计算类型的枚举值。 |  |


cublasGemmGroupedBatchedEx() 支持以下计算类型、缩放类型、Atype/Btype 和 Ctype：


| 计算类型 | 缩放类型（alpha 和 beta） | Atype/Btype | Ctype |
| --- | --- | --- | --- |
| CUBLAS_COMPUTE_32F | CUDA_R_32F | CUDA_R_16BF | CUDA_R_16BF |
| CUDA_R_16F | CUDA_R_16F |
| CUDA_R_32F | CUDA_R_32F |
| CUBLAS_COMPUTE_32F_PEDANTIC | CUDA_R_32F | CUDA_R_32F | CUDA_R_32F |
| CUBLAS_COMPUTE_32F_FAST_TF32 | CUDA_R_32F | CUDA_R_32F | CUDA_R_32F |
| CUBLAS_COMPUTE_64F 或
CUBLAS_COMPUTE_64F_PEDANTIC | CUDA_R_64F | CUDA_R_64F | CUDA_R_64F |


如果 `Atype` 是 `CUDA_R_16F` 或 `CUDA_R_16BF`，或者如果 `computeType` 是任何 `FAST` 选项，则放置在 GPU 内存中的指针（不是指针数组）必须正确对齐以避免未对齐内存访问错误。理想情况下，所有指针至少对齐到 16 字节。否则，它们必须满足以下规则：


- 如果 (k * AtypeSize) % 16 == 0，则确保 intptr_t(ptr) % 16 == 0，
- 如果 (k * AtypeSize) % 4 == 0，则确保 intptr_t(ptr) % 4 == 0。


此函数返回的可能错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 transa_array、transb_array、m_array、n_array、k_array、alpha_array、lda_array、ldb_array、beta_array、ldc_array 或 group_size 为 NULL，或
如果 group_count < 0，或
如果 m_array[i] < 0、n_array[i] < 0、k_array[i] < 0、group_size[i] < 0，或
如果 transa_array[i] 和 transb_array[i] 不是 CUBLAS_OP_N、CUBLAS_OP_C、CUBLAS_OP_T 之一，或
如果 transa_array[i] == CUBLAS_OP_N 且 lda_array[i] < max(1, m_array[i])，否则 lda_array[i] < max(1, k_array[i])，或
如果 transb_array[i] == CUBLAS_OP_N 且 ldb_array[i] < max(1, k_array[i])，否则 ldb_array[i] < max(1, n_array[i])，或
如果 ldc_array[i] < max(1, m_array[i]) |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |
| CUBLAS_STATUS_NOT_SUPPORTED | 指针模式设置为 CUBLAS_POINTER_MODE_DEVICE
Atype 或 Btype 或 Ctype 或 computeType 不受支持 |