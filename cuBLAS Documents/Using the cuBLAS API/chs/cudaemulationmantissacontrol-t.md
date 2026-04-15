### 2.3.3. cudaEmulationMantissaControl_t

`cudaEmulationMantissaControl_t` 是一个枚举类型，用于指定如何配置浮点模拟算法中尾数位数的计算方式。
请参见 `cublasSetFixedPointEmulationMantissaControl()` 和 `cublasGetFixedPointEmulationMaxMantissaBitCount()`。

| 值 | 含义 |
| --- | --- |
| CUDA_EMULATION_MANTISSA_CONTROL_DYNAMIC | 保留的尾数位数在运行时计算，以确保与原生浮点表示相同或更高的精度。 |
| CUDA_EMULATION_MANTISSA_CONTROL_FIXED | 保留的尾数位数在运行时固定。 |