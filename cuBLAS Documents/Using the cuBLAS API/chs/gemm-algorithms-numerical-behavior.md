### 2.1.10. GEMM 算法数值行为

某些 GEMM 算法会沿着 K 维度分割计算以提高 GPU 占用率，特别是当 K 维度相对于 M 和 N 维度较大时。当 cuBLAS 启发式算法选择或用户显式选择这种类型的算法时，每个分割的结果会被确定性求和到结果矩阵中，以获得最终结果。

对于 `cublas<t>gemmEx()` 和 `cublasGemmEx()` 例程，当计算类型大于输出类型时，分块求和可能会导致一些中间溢出，从而产生包含溢出的最终结果矩阵。如果所有点积在最终转换为输出类型之前先在计算类型中进行累积，则这些溢出可能不会发生。当 computeType 为 `CUDA_R_32F` 且 Atype、Btype 和 Ctype 为 `CUDA_R_16F` 时，这种计算副作用很容易暴露。可以使用 `cublasSetMathMode()` 设置计算精度模式 `CUBLAS_MATH_DISALLOW_REDUCED_PRECISION_REDUCTION` 来控制此行为。