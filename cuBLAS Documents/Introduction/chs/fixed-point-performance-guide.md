#### 1.5.2.5. 定点性能指南

定点仿真允许用户在性能和精度之间进行权衡，以实现进一步的加速。对于动态尾数控制，用户能够配置自动动态精度框架，使用比原生FP64精度要求更少或更多的位数，通过 `cublasSetFixedPointEmulationMantissaBitOffset()` 实现。定点尾数控制可以通过增加或减少尾数位数来类似地调整，通过 `cublasSetFixedPointEmulationMaxMantissaBitCount()` 实现。

由于定点工作区需求量大，异步分配使用 `cudaMallocAsync()` 完成。在GEMM调用次数不足以分摊内存分配成本的情况下，或者在CUDA流同步非常频繁的情况下，您可以通过以下方式提高性能：

- 减少CUDA流同步次数
- 管理自己的内存并通过 `cublasSetWorkspace()` 提供工作区
- 允许默认内存池在同步之间保留内存