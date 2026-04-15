### 2.1.11. Tensor Core 使用说明

Tensor Core 最初随 Volta GPU（计算能力 7.0 及以上）引入，能够显著加速矩阵乘法运算。从 cuBLAS 11.0.0 版本开始，库可以自动利用 Tensor Core 功能（除非通过在 cuBLAS 中选择严格计算模式明确禁用，参见 cublasSetMathMode()、cublasMath_t）。

需要注意的是，库会在确定能够提供最佳性能的情况下选择启用 Tensor Core 的实现。

使用 Tensor Core 时，若矩阵维度和指针满足特定的内存对齐要求，可以获得最佳性能。具体来说，必须满足以下所有条件才能从 Tensor Core 获得最佳性能：

- ((op_A == CUBLAS_OP_N ? m : k) * AtypeSize) % 16 == 0
- ((op_B == CUBLAS_OP_N ? k : n) * BtypeSize) % 16 == 0
- (m * CtypeSize) % 16 == 0
- (lda * AtypeSize) % 16 == 0
- (ldb * BtypeSize) % 16 == 0
- (ldc * CtypeSize) % 16 == 0
- intptr_t(A) % 16 == 0
- intptr_t(B) % 16 == 0
- intptr_t(C) % 16 == 0

使用 FP8 类型进行矩阵乘法（参见 8 位浮点数据类型 (FP8) 使用），必须确保矩阵维度和指针满足上述最优要求。除 FP8 外，使用 Tensor Core 不再有矩阵维度和内存对齐的限制（从 cuBLAS 11.0.0 版本开始）。