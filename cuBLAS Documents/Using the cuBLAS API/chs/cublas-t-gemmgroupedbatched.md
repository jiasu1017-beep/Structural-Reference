### 2.7.5. cublas<t>gemmGroupedBatched()

```c++
cublasStatus_t cublasSgemmGroupedBatched(cublasHandle_t handle,
                                         const cublasOperation_t transa_array[],
                                         const cublasOperation_t transb_array[],
                                         const int m_array[],
                                         const int n_array[],
                                         const int k_array[],
                                         const float  alpha_array[],
                                         const float *const  Aarray[],
                                         const int lda_array[],
                                         const float *const  Barray[],
                                         const int ldb_array[],
                                         const float  beta_array[],
                                         float *const  Carray[],
                                         const int ldc_array[],
                                         int group_count,
                                         const int group_size[])
cublasStatus_t cublasDgemmGroupedBatched(cublasHandle_t handle,
                                         const cublasOperation_t transa_array[],
                                         const cublasOperation_t transb_array[],
                                         const int m_array[],
                                         const int n_array[],
                                         const int k_array[],
                                         const double alpha_array[],
                                         const double *const Aarray[],
                                         const int lda_array[],
                                         const double *const Barray[],
                                         const int ldb_array[],
                                         const double beta_array[],
                                         double *const Carray[],
                                         const int ldc_array[],
                                         int group_count,
                                         const int group_size[])
```

此函数支持64位整数接口。

此函数对矩阵组执行矩阵-矩阵乘法运算。给定的组被认为是"均匀的"，即同一组内的所有实例具有相同的维度(m, n, k)、前置维度(lda, ldb, ldc)和转置操作(transa, transb)，分别对应各自的A、B和C矩阵。然而，维度、前置维度、转置操作和缩放因子(alpha, beta)可能在不同组之间有所不同。批次中每个实例的输入矩阵和输出矩阵的地址从调用者传递给函数的指针数组中读取。这在功能上等同于以下代码：

```c++
idx = 0;
for i = 0:group_count - 1
    for j = 0:group_size[i] - 1
        gemm(transa_array[i], transb_array[i], m_array[i], n_array[i], k_array[i],
             alpha_array[i], Aarray[idx], lda_array[i], Barray[idx], ldb_array[i],
             beta_array[i], Carray[idx], ldc_array[i]);
        idx += 1;
    end
end
```

其中 $\text{$\mathrm{alpha\_array}$}$ 和 $\text{$\mathrm{beta\_array}$}$ 是缩放因子数组，$\text{Aarray}$、$\text{Barray}$ 和 $\text{Carray}$ 是指向以列优先格式存储的矩阵的指针数组。对于属于组 $i$ 的给定索引 $\text{idx}$，维度如下：

> \(\text{op}(\text{Aarray}\lbrack\text{idx}\rbrack)\): \(\text{$\mathrm{m\_array}$}\lbrack i\rbrack \times \text{$\mathrm{k\_array}$}\lbrack i\rbrack\)
\(\text{op}(\text{Barray}\lbrack\text{idx}\rbrack)\): \(\text{$\mathrm{k\_array}$}\lbrack i\rbrack \times \text{$\mathrm{n\_array}$}\lbrack i\rbrack\)
\(\text{Carray}\lbrack\text{idx}\rbrack\): \(\text{$\mathrm{m\_array}$}\lbrack i\rbrack \times \text{$\mathrm{n\_array}$}\lbrack i\rbrack\)

> **注意**

> 此API采用两种不同长度的数组。维度、前置维度、转置操作和缩放因子的数组长度为group_count，而矩阵数组的长度为problem_count，其中 \(\text{$\mathrm{problem\_count}$} = \sum_{i = 0}^{\text{$\mathrm{group\_count}$} - 1} \text{$\mathrm{group\_size}$}\lbrack i\rbrack\)

对于组 $i$ 中的矩阵 $A[\text{idx}]$

$\text{op}(A[\text{idx}]) = \left\{ \begin{matrix}
A[\text{idx}] & {\text{if }\textsf{$\mathrm{transa\_array}\lbrack i\rbrack$ == $\mathrm{CUBLAS\_OP\_N}$}} \\
A[\text{idx}]^{T} & {\text{if }\textsf{$\mathrm{transa\_array}\lbrack i\rbrack$ == $\mathrm{CUBLAS\_OP\_T}$}} \\
A[\text{idx}]^{H} & {\text{if }\textsf{$\mathrm{transa\_array}\lbrack i\rbrack$ == $\mathrm{CUBLAS\_OP\_C}$}} \\
\end{matrix} \right.$

对于组 $i$ 中的矩阵 $B[\text{idx}]$，$\text{op}(B[\text{idx}])$ 的定义类似。

> **注意**

> \(C\lbrack\text{idx}\rbrack\) 矩阵不得重叠，即各个gemm运算必须能够独立计算；否则将导致未定义行为。

在某些问题规模下，在不同的CUDA流中多次调用cublas<t>gemmBatched()可能比使用此API更具优势。

| 参数 | 内存位置 | 输入/输出 | 含义 | 数组长度 |
| --- | --- | --- | --- | --- |
| handle |  | input | cuBLAS库上下文的句柄。 |  |
| transa_array | host | input | 每个组的运算op(A[idx])，即非转置或(共轭)转置。 | group_count |
| transb_array | host | input | 每个组的运算op(B[idx])，即非转置或(共轭)转置。 | group_count |
| m_array | host | input | 包含每个组的矩阵op(A[idx])和C[idx]行数的数组。 | group_count |
| n_array | host | input | 包含每个组的op(B[idx])和C[idx]列数的数组。 | group_count |
| k_array | host | input | 包含每个组的op(A[idx])列数和op(B[idx])行数的数组。 | group_count |
| alpha_array | host | input | 包含每个组用于乘法的<type>标量的数组。 | group_count |
| Aarray | device | input | 指向<type>数组的指针数组，每个数组的维度为lda[i] x k[i]，其中lda[i] >= max(1,m[i])（如果transa[i] == CUBLAS_OP_N），否则为lda[i] x m[i]，其中lda[i] >= max(1,k[i])。
所有指针必须满足特定的对齐条件。具体细节请参见下文。 | problem_count |
| lda_array | host | input | 包含每个组用于存储每个矩阵A[idx]的二维数组的前置维度的数组。 | group_count |
| Barray | device | input | 指向<type>数组的指针数组，每个数组的维度为ldb[i] x n[i]，其中ldb[i] >= max(1,k[i])（如果transb[i] == CUBLAS_OP_N），否则为ldb[i] x k[i]，其中ldb[i] >= max(1,n[i])。
所有指针必须满足特定的对齐条件。具体细节请参见下文。 | problem_count |
| ldb_array | host | input | 包含每个组用于存储每个矩阵B[idx]的二维数组的前置维度的数组。 | group_count |
| beta_array | host | input | 包含每个组用于乘法的<type>标量的数组。 | group_count |
| Carray | device | in/out | 指向<type>数组的指针数组。维度为ldc[i] x n[i]，其中ldc[i] >= max(1,m[i])。矩阵C[idx]不应重叠；否则将导致未定义行为。
所有指针必须满足特定的对齐条件。具体细节请参见下文。 | problem_count |
| ldc_array | host | input | 包含每个组用于存储每个矩阵C[idx]的二维数组的前置维度的数组。 | group_count |
| group_count | host | input | 组数 |  |
| group_size | host | input | 包含每个组在Aarray、Barray和Carray中的指针数量的数组。 | group_count |

如果数学模式在using cublasSgemmGroupedBatched()时启用了快速数学模式，则放置在GPU内存中的指针（不是指针数组本身）必须正确对齐以避免未对齐的内存访问错误。理想情况下，所有指针至少对齐到16字节。否则必须满足以下规则：

- 如果k % 4 == 0，则确保intptr_t(ptr) % 16 == 0

此函数可能返回的错误值及其含义如下所列。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果transa_array、transb_array、m_array、n_array、k_array、alpha_array、lda_array、ldb_array、beta_array、ldc_array或group_size为NULL，或
如果group_count < 0，或
如果m_array[i] < 0、n_array[i] < 0、k_array[i] < 0、group_size[i] < 0，或
如果transa_array[i]和transb_array[i]不是CUBLAS_OP_N、CUBLAS_OP_C、CUBLAS_OP_T之一，或
如果transa_array[i] == CUBLAS_OP_N且lda_array[i] < max(1, m_array[i])，否则lda_array[i] < max(1, k_array[i])，或
如果transb_array[i] == CUBLAS_OP_N且ldb_array[i] < max(1, k_array[i])，否则ldb_array[i] < max(1, n_array[i])，或
如果ldc_array[i] < max(1, m_array[i]) |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在GPU上启动失败 |
| CUBLAS_STATUS_NOT_SUPPORTED | 指针模式设置为CUBLAS_POINTER_MODE_DEVICE |