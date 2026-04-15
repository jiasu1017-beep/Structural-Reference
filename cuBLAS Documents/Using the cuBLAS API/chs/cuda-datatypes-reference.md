## 2.3. CUDA 数据类型参考


本章介绍由多个 CUDA 库共享并在头文件 `library_types.h` 中定义的数据类型。




### 2.3.1. cudaDataType_t


`cudaDataType_t` 类型是一个枚举值，用于指定数据精度。当数据引用本身不携带类型信息时使用（例如 void *）。


例如，它在例程 cublasSgemmEx() 中使用。


| 值 | 含义 |
| --- | --- |
| CUDA_R_16F | 数据类型为 16 位实数半精度浮点数 |
| CUDA_C_16F | 数据类型为 32 位结构，由两个半精度浮点数组成，表示一个复数 |
| CUDA_R_16BF | 数据类型为 16 位实数 bfloat16 浮点数 |
| CUDA_C_16BF | 数据类型为 32 位结构，由两个 bfloat16 浮点数组成，表示一个复数 |
| CUDA_R_32F | 数据类型为 32 位实数单精度浮点数 |
| CUDA_C_32F | 数据类型为 64 位结构，由两个单精度浮点数组成，表示一个复数 |
| CUDA_R_64F | 数据类型为 64 位实数双精度浮点数 |
| CUDA_C_64F | 数据类型为 128 位结构，由两个双精度浮点数组成，表示一个复数 |
| CUDA_R_8I | 数据类型为 8 位实数有符号整数 |
| CUDA_C_8I | 数据类型为 16 位结构，由两个 8 位有符号整数组成，表示一个复数 |
| CUDA_R_8U | 数据类型为 8 位实数无符号整数 |
| CUDA_C_8U | 数据类型为 16 位结构，由两个 8 位无符号整数组成，表示一个复数 |
| CUDA_R_32I | 数据类型为 32 位实数有符号整数 |
| CUDA_C_32I | 数据类型为 64 位结构，由两个 32 位有符号整数组成，表示一个复数 |
| CUDA_R_8F_E4M3 | 数据类型为 E4M3 格式的 8 位实数浮点数 |
| CUDA_R_8F_E5M2 | 数据类型为 E5M2 格式的 8 位实数浮点数 |
| CUDA_R_4F_E2M1 | 数据类型为 E2M1 格式的 4 位实数浮点数 |





### 2.3.2. cudaEmulationStrategy_t


`cudaEmulationStrategy_t` 是一个参数，用于指定如何利用浮点仿真算法。这相当于 cublasEmulationStrategy_t。





### 2.3.3. cudaEmulationMantissaControl_t


`cudaEmulationMantissaControl_t` 是一个枚举类型，用于指定如何配置浮点仿真算法中尾数位数的计算方式。
请参见 cublasSetFixedPointEmulationMantissaControl() 和 cublasGetFixedPointEmulationMaxMantissaBitCount()。


| 值 | 含义 |
| --- | --- |
| CUDA_EMULATION_MANTISSA_CONTROL_DYNAMIC | 保留的尾数位数在运行时计算，以确保与原生浮点表示相同或更高的精度。 |
| CUDA_EMULATION_MANTISSA_CONTROL_FIXED | 保留的尾数位数在运行时固定。 |





### 2.3.4. cudaEmulationSpecialValuesSupport_t


`cudaEmulationSpecialValuesSupport_t` 是一个枚举类型，用于指定如何配置浮点仿真算法需要支持的浮点特殊值。请参见 cublasSetEmulationSpecialValuesSupport() 和 cublasGetEmulationSpecialValuesSupport()。


| 值 | 含义 |
| --- | --- |
| CUDA_EMULATION_SPECIAL_VALUES_SUPPORT_DEFAULT | 默认的特殊值支持掩码，包含对有符号无穷大和 NaN 值的支持。 |
| CUDA_EMULATION_SPECIAL_VALUES_SUPPORT_NONE | 仿真算法对特殊值没有要求。 |
| CUDA_EMULATION_SPECIAL_VALUES_SUPPORT_INFINITY | 要求仿真算法处理有符号无穷大输入和输出。 |
| CUDA_EMULATION_SPECIAL_VALUES_SUPPORT_NAN | 要求仿真算法处理 NaN 输入和输出。 |


> **注意**

注意
一般来说，cublasSetEmulationSpecialValuesSupport() 函数优先于环境变量设置。
但是，将环境变量 CUBLAS_EMULATION_SPECIAL_VALUES_SUPPORT_MASK 设置为位掩码值将覆盖默认的特殊值支持，即使默认是由函数调用设置的。





### 2.3.5. libraryPropertyType_t


`libraryPropertyType_t` 用作参数，在使用例程 cublasGetProperty() 时指定请求的属性。


| 值 | 含义 |
| --- | --- |
| MAJOR_VERSION | 用于查询主版本号的枚举值 |
| MINOR_VERSION | 用于查询次版本号的枚举值 |
| PATCH_LEVEL | 用于标识补丁级别的数字 |