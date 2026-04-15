### 1.5.3. 默认库配置

仿真模式的库默认值可能会发生变化。

| API | 尾数控制 | 默认行为 |
| --- | --- | --- |
| `cublasGetEmulationStrategy()` | 不适用 | `CUBLAS_EMULATION_STRATEGY_DEFAULT` |
| `cublasGetEmulationSpecialValuesSupport()` | 不适用 | `CUBLAS_EMULATION_SPECIAL_VALUES_SUPPORT_DEFAULT` |
| `cublasGetFixedPointEmulationMantissaControl()` | 不适用 | `CUDA_EMULATION_MANTISSA_CONTROL_DYNAMIC` |
| `cublasGetFixedPointEmulationMaxMantissaBitCount()` | `CUDA_EMULATION_MANTISSA_CONTROL_DYNAMIC` | 79 |
| `cublasGetFixedPointEmulationMaxMantissaBitCount()` | `CUDA_EMULATION_MANTISSA_CONTROL_FIXED` | 55 |
| `cublasGetFixedPointEmulationMantissaBitOffset()` | 不适用 | 0 |
| `cublasGetFixedPointEmulationMantissaBitCountPointer()` | 不适用 | `NULL` |