### 3.1.1. 问题规模限制

问题的规模存在固有限制，这是由 CUDA 网格维度的限制所导致的。例如，许多内核不支持大于 65535 的批量大小，这是因为网格 *z* 维度的限制。对于给定的问题，m 和 n 值也存在类似的限制。

在单个内核无法运行某个问题的场景下，cuBLASLt 将尝试将问题分解为多个子问题，并通过在每个子问题上运行内核来求解。

**cuBLASLt 内部问题分解存在一些限制，汇总如下：**
: 不支持 Amax 计算。这意味着必须保持 CUBLASLT_MATMUL_DESC_AMAX_D_POINTER 和 CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_AMAX_POINTER 未设置（参见 cublasLtMatmulDescAttributes_t）
所有矩阵布局必须将 CUBLASLT_MATRIX_LAYOUT_ORDER 设置为 CUBLASLT_ORDER_COL（参见 cublasLtOrder_t）
当 CUBLASLT_MATMUL_DESC_EPILOGUE 设置为 CUBLASLT_EPILOGUE_DRELU_BGRAD 或 CUBLASLT_EPILOGUE_DGELU_BGRAD 时，cuBLASLt 不会沿 n 维度进行分区（参见 cublasLtEpilogue_t）

为了克服这些限制，用户可能希望自行对问题进行分区，为每个子问题启动内核，并计算必要的归约操作以合并结果。