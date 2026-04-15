### 2.3.4. cudaEmulationSpecialValuesSupport_t

`cudaEmulationSpecialValuesSupport_t` 是一个枚举类型，用于指定如何配置浮点特殊值的支持方式，这些特殊值需要由浮点仿真算法提供支持。请参阅 `cublasSetEmulationSpecialValuesSupport()` 和 `cublasGetEmulationSpecialValuesSupport()`。

| 值 | 含义 |
| --- | --- |
| CUDA_EMULATION_SPECIAL_VALUES_SUPPORT_DEFAULT | 默认的特殊值支持掩码，包含对有符号无穷大和 NaN 值的支持。 |
| CUDA_EMULATION_SPECIAL_VALUES_SUPPORT_NONE | 对仿真算法支持特殊值没有要求。 |
| CUDA_EMULATION_SPECIAL_VALUES_SUPPORT_INFINITY | 要求仿真算法处理有符号无穷大的输入和输出。 |
| CUDA_EMULATION_SPECIAL_VALUES_SUPPORT_NAN | 要求仿真算法处理 NaN 的输入和输出。 |

> **注意**

注意
通常情况下，`cublasSetEmulationSpecialValuesSupport()` 函数优先于环境变量设置。但是，将环境变量 `CUBLAS_EMULATION_SPECIAL_VALUES_SUPPORT_MASK` 设置为位掩码值将使用指定的掩码覆盖默认的特殊值支持，即使默认设置是由函数调用设置的。