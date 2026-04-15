## 2.2. cuBLAS 数据类型参考




### 2.2.1. cublasHandle_t


`cublasHandle_t` 类型是指向一个 opaque 结构体的指针类型，该结构体保存了 cuBLAS 库的上下文。cuBLAS 库的上下文必须使用 `cublasCreate()` 进行初始化，并且返回的句柄必须被传递给所有后续的库函数调用。上下文应该在最后使用 `cublasDestroy()` 进行销毁。





### 2.2.2. cublasStatus_t


该类型用于函数状态返回值。所有 cuBLAS 库函数都会返回其状态，状态可以是以下值：


| 值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成。 |
| CUBLAS_STATUS_NOT_INITIALIZED | cuBLAS 库未初始化。这通常是由于之前没有调用 `cublasCreate()`、cuBLAS 例程调用的 CUDA Runtime API 出错，或硬件设置错误造成的。
修复方法：在函数调用之前调用 `cublasCreate()`；并检查硬件、适当版本的驱动程序和 cuBLAS 库是否正确安装。 |
| CUBLAS_STATUS_ALLOC_FAILED | cuBLAS 库内部的资源分配失败。这通常是由 `cudaMalloc()` 失败引起的。
修复方法：在函数调用之前，尽可能多地释放之前分配的内存。 |
| CUBLAS_STATUS_INVALID_VALUE | 向函数传递了不支持的值或参数（例如，负的向量大小）。
修复方法：确保所有传递的参数都具有有效的值。 |
| CUBLAS_STATUS_ARCH_MISMATCH | 函数需要的特性在设备架构上不存在；通常是由于计算能力低于 5.0 造成的。
修复方法：在具有适当计算能力的设备上编译和运行应用程序。 |
| CUBLAS_STATUS_MAPPING_ERROR | 访问 GPU 内存空间失败，这通常是由绑定纹理失败引起的。
修复方法：在函数调用之前，取消绑定任何之前绑定的纹理。 |
| CUBLAS_STATUS_EXECUTION_FAILED | GPU 程序执行失败。这通常是由于内核在 GPU 上的启动失败造成的，可能由多种原因导致。
修复方法：检查硬件、适当版本的驱动程序和 cuBLAS 库是否正确安装。 |
| CUBLAS_STATUS_INTERNAL_ERROR | cuBLAS 内部操作失败。这个错误通常是由 `cudaMemcpyAsync()` 失败引起的。
修复方法：检查硬件、适当版本的驱动程序和 cuBLAS 库是否正确安装。同时，检查传递给例程的内存参数在例程完成之前是否未被释放。 |
| CUBLAS_STATUS_NOT_SUPPORTED | 请求的功能不受支持。 |
| CUBLAS_STATUS_LICENSE_ERROR | 请求的功能需要某些许可证，并且在尝试检查当前许可时检测到错误。如果许可证不存在或已过期，或者环境变量 `NVIDIA_LICENSE_FILE` 设置不正确，可能会发生此错误。 |





### 2.2.3. cublasOperation_t


`cublasOperation_t` 类型指示需要对稠密矩阵执行哪个操作。它的值对应于 Fortran 字符 `'N'` 或 `'n'`（非转置）、`'T'` 或 `'t'`（转置）和 `'C'` 或 `'c'`（共轭转置），这些字符通常用作传统 BLAS 实现的参数。


| 值 | 含义 |
| --- | --- |
| CUBLAS_OP_N | 选中非转置操作。 |
| CUBLAS_OP_T | 选中转置操作。 |
| CUBLAS_OP_C | 选中共轭转置操作。 |





### 2.2.4. cublasFillMode_t


该类型指示稠密矩阵的哪一部分（下半部分或上半部分）被填充，因此应该被函数使用。它的值对应于 Fortran 字符 `L` 或 `l`（下半部分）和 `U` 或 `u`（上半部分），这些字符通常用作传统 BLAS 实现的参数。


| 值 | 含义 |
| --- | --- |
| CUBLAS_FILL_MODE_LOWER | 矩阵的下半部分被填充。 |
| CUBLAS_FILL_MODE_UPPER | 矩阵的上半部分被填充。 |
| CUBLAS_FILL_MODE_FULL | 整个矩阵被填充。 |





### 2.2.5. cublasDiagType_t


该类型指示稠密矩阵的主对角线是否是单位矩阵，因此函数不应该接触或修改它。它的值对应于 Fortran 字符 `'N'` 或 `'n'`（非单位）和 `'U'` 或 `'u'`（单位），这些字符通常用作传统 BLAS 实现的参数。


| 值 | 含义 |
| --- | --- |
| CUBLAS_DIAG_NON_UNIT | 矩阵对角线具有非单位元素。 |
| CUBLAS_DIAG_UNIT | 矩阵对角线具有单位元素。 |





### 2.2.6. cublasSideMode_t


该类型指示在特定函数求解的矩阵方程中，稠密矩阵是在左边还是右边。它的值对应于 Fortran 字符 `'L'` 或 `'l'`（左边）和 `'R'` 或 `'r'`（右边），这些字符通常用作传统 BLAS 实现的参数。


| 值 | 含义 |
| --- | --- |
| CUBLAS_SIDE_LEFT | 矩阵在方程的左边。 |
| CUBLAS_SIDE_RIGHT | 矩阵在方程的右边。 |





### 2.2.7. cublasPointerMode_t


`cublasPointerMode_t` 类型指示标量值是通过主机还是设备上的引用传递的。需要特别指出的是，如果函数调用中存在多个标量值，它们必须都遵循相同的单一指针模式。指针模式可以分别使用 `cublasSetPointerMode()` 和 `cublasGetPointerMode()` 例程进行设置和检索。


| 值 | 含义 |
| --- | --- |
| CUBLAS_POINTER_MODE_HOST | 标量通过主机上的引用传递。 |
| CUBLAS_POINTER_MODE_DEVICE | 标量通过设备上的引用传递。 |





### 2.2.8. cublasAtomicsMode_t


该类型指示是否可以使用具有原子操作替代实现的 cuBLAS 例程。原子操作模式可以分别使用 `cublasSetAtomicsMode()` 和 `cublasGetAtomicsMode()` 例程进行设置和查询。


| 值 | 含义 |
| --- | --- |
| CUBLAS_ATOMICS_NOT_ALLOWED | 不允许使用原子操作。 |
| CUBLAS_ATOMICS_ALLOWED | 允许使用原子操作。 |





### 2.2.9. cublasGemmAlgo_t


`cublasGemmAlgo_t` 类型是一个枚举，用于指定在 `sm_75` 及之前 GPU 架构上进行矩阵-矩阵乘法的算法。在 `sm_80` 及更新的 GPU 架构上，此枚举没有效果。cuBLAS 具有以下算法选项：


| 值 | 含义 |
| --- | --- |
| CUBLAS_GEMM_DEFAULT | 应用启发式方法来选择 GEMM 算法 |
| CUBLAS_GEMM_ALGO0 到 CUBLAS_GEMM_ALGO23 | 显式选择算法 0..23。注意：在 NVIDIA Ampere 架构 GPU 及更新版本上没有效果。 |
| CUBLAS_GEMM_DEFAULT_TENSOR_OP[已弃用] | 此模式已弃用，将在未来的版本中移除。应用启发式方法来选择 GEMM 算法，同时允许使用降低精度的 CUBLAS_COMPUTE_32F_FAST_16F 内核（为了向后兼容）。 |
| CUBLAS_GEMM_ALGO0_TENSOR_OP 到 CUBLAS_GEMM_ALGO15_TENSOR_OP[已弃用] | 这些值已弃用，将在未来的版本中移除。显式选择 Tensor Core GEMM 算法 0..15。允许使用降低精度的 CUBLAS_COMPUTE_32F_FAST_16F 内核（为了向后兼容）。注意：在 NVIDIA Ampere 架构 GPU 及更新版本上没有效果。 |
| CUBLAS_GEMM_AUTOTUNE | [实验性] 库将对若干可用算法进行基准测试，并为给定的 проблем配置选择最优的算法。解决方案会缓存在 cublas 句柄中，以便下次使用相同大小的 проблем时使用缓存的配置。注意：为了避免覆盖用户数据，库将分配与输出大小对应的内存量。注意：在流捕获期间不支持基准测试；如果在缓存中找不到给定大小的配置，将返回 CUBLAS_STATUS_NOT_SUPPORTED。 |





### 2.2.10. cublasMath_t


`cublasMath_t` 枚举类型在 `cublasSetMathMode()` 中用于选择计算精度模式，如下表所定义。由于此设置不直接控制 Tensor Core 的使用，`CUBLAS_TENSOR_OP_MATH` 模式已被弃用，将在未来的版本中移除。


| 值 | 含义 |
| --- | --- |
| CUBLAS_DEFAULT_MATH | 这是默认的也是最高性能的模式，使用至少具有与请求相同尾数和指数位数的计算和中间存储精度。Tensor Core 将在可能时被使用。 |
| CUBLAS_PEDANTIC_MATH | 此模式对所有计算阶段使用规定的精度和标准化算术，主要用于数值稳健性研究、测试和调试。此模式的性能可能不如其他模式。 |
| CUBLAS_TF32_TENSOR_OP_MATH | 使用 TF32 tensor core 加速单精度例程。注意：输入转换四舍五入到最近的偶数。 |
| CUBLAS_FP32_EMULATED_BF16X9_MATH | 使用 BF16x9 算法加速单精度例程。有关更多详细信息，请参阅浮点仿真。由于单精度 GEMM 例程，cuBLAS 将使用 CUBLAS_COMPUTE_32F_EMULATED_16BFX9 计算类型。 |
| CUBLAS_FP64_EMULATED_FIXEDPOINT_MATH | 使用定点仿真算法加速双精度例程。有关更多详细信息，请参阅浮点仿真。 |
| CUBLAS_MATH_DISALLOW_REDUCED_PRECISION_REDUCTION | 强制矩阵乘法期间的任何归约操作使用累加器类型（即计算类型），而不是输出类型，以防混合精度例程中输出类型精度低于计算类型精度。这是一个可以使用按位或操作与其他值一起设置的标志。 |
| CUBLAS_TENSOR_OP_MATH [已弃用] | 此模式已弃用，将在未来的版本中移除。允许库在可能时使用 Tensor Core 操作。对于单精度 GEMM 例程，cuBLAS 将使用 CUBLAS_COMPUTE_32F_FAST_16F 计算类型。 |





### 2.2.11. cublasComputeType_t


`cublasComputeType_t` 枚举类型在 `cublasGemmEx()` 和 `cublasLtMatmul()`（包括所有批处理和跨步批处理变体）中用于选择计算精度模式，如下所定义。


| 值 | 含义 |
| --- | --- |
| CUBLAS_COMPUTE_16F | 这是 16 位半精度浮点和所有至少具有 16 位半精度的计算和中间存储精度的默认和最高性能模式。Tensor Core 将在可能时被使用。 |
| CUBLAS_COMPUTE_16F_PEDANTIC | 此模式对所有计算阶段使用 16 位半精度浮点标准化算术，主要用于数值稳健性研究、测试和调试。由于禁用了 tensor core 的使用，此模式的性能可能不如其他模式。 |
| CUBLAS_COMPUTE_32F | 这是默认的 32 位单精度浮点，使用至少 32 位的计算和中间存储精度。 |
| CUBLAS_COMPUTE_32F_PEDANTIC | 对所有计算阶段使用 32 位单精度浮点算术，并禁用高斯复杂度归约（3M）等算法优化。 |
| CUBLAS_COMPUTE_32F_FAST_16F | 允许库使用 Tensor Core 进行自动向下转换和 16 位半精度计算，用于 32 位输入和输出矩阵。 |
| CUBLAS_COMPUTE_32F_FAST_16BF | 允许库使用 Tensor Core 进行自动向下转换和 bfloat16 计算，用于 32 位输入和输出矩阵。有关 bfloat16 的更多详细信息，请参阅备用浮点部分。 |
| CUBLAS_COMPUTE_32F_FAST_TF32 | 允许库使用 Tensor Core 和 TF32 计算，用于 32 位浮点输入和输出矩阵。注意：输入转换四舍五入到最近的偶数。有关 TF32 计算的更多详细信息，请参阅备用浮点部分。 |
| CUBLAS_COMPUTE_32F_EMULATED_16BFX9 | 允许库使用 BF16x9 浮点仿真算法进行 32 位浮点算术运算。有关更多详细信息，请参阅浮点仿真。 |
| CUBLAS_COMPUTE_64F | 这是默认的 64 位双精度浮点，使用至少 64 位的计算和中间存储精度。 |
| CUBLAS_COMPUTE_64F_EMULATED_FIXEDPOINT | 允许库使用定点仿真算法进行 64 位双精度浮点算术运算。有关更多详细信息，请参阅浮点仿真。 |
| CUBLAS_COMPUTE_64F_PEDANTIC | 对所有计算阶段使用 64 位双精度浮点算术，并禁用高斯复杂度归约（3M）等算法优化。 |
| CUBLAS_COMPUTE_32I | 这是默认的 32 位整数模式，使用至少 32 位的计算和中间存储精度。 |
| CUBLAS_COMPUTE_32I_PEDANTIC | 对所有计算阶段使用 32 位整数算术。 |


> **注意**

注意
设置环境变量 `NVIDIA_TF32_OVERRIDE = 0` 将覆盖 NVIDIA 库的任何默认设置或程序化配置，因此 cuBLAS 将不会使用 TF32 tensor core 加速单精度计算。





### 2.2.12. cublasEmulationStrategy_t


`cublasEmulationStrategy_t` 枚举类型在 `cublasSetEmulationStrategy()` 中用于选择如何利用浮点仿真算法。


| 值 | 含义 |
| --- | --- |
| CUBLAS_EMULATION_STRATEGY_DEFAULT | 这是默认的仿真策略，等效于 `CUBLAS_EMULATION_STRATEGY_PERFORMANT`，除非设置了 `CUBLAS_EMULATION_STRATEGY` 环境变量。 |
| CUBLAS_EMULATION_STRATEGY_PERFORMANT | 一种只要仿真能提供性能优势就使用仿真的策略。 |
| CUBLAS_EMULATION_STRATEGY_EAGER | 一种尽可能使用仿真的策略。 |


> **注意**

注意
一般来说，`cublasSetEmulationStrategy()` 函数优先于环境变量设置。
但是，将环境变量 `CUBLAS_EMULATION_STRATEGY` 设置为 performant 或 eager 将用相应的仿真策略覆盖默认的仿真策略，即使默认策略是由函数调用设置的。