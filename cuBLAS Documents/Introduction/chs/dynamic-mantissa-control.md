#### 1.5.2.1. 动态尾数控制 (Dynamic Mantissa Control)

动态尾数控制代表 cuBLAS 库的默认尾数控制方式。我们的自动动态精度框架会计算维持与 FP64 相同或更高精度所需的适当定点尾数位数。如果所需尾数位数超过了库定义的默认值（参见默认库配置），或超过了用户提供的最大位数（参见 `cublasSetFixedPointEmulationMaxMantissaBitCount()`），该框架将动态调度到原生 FP64。