### 3.3.30. cublasLtEmulationDescAttributes_t

`cublasLtEmulationDescAttributes_t` 是一个枚举类型，用于配置浮点模拟参数。更多信息请参见浮点模拟文档。

| 值 | 描述 | 数据类型 |
| --- | --- | --- |
| CUBLASLT_EMULATION_DESC_STRATEGY | 策略，参见 `cublasEmulationStrategy_t`。定义何时使用浮点模拟算法。默认值：EMULATION_STRATEGY_DEFAULT。 | int32_t |
| CUBLASLT_EMULATION_DESC_SPECIAL_VALUES_SUPPORT | 特殊值支持，参见 `cudaEmulationSpecialValuesSupport_t`。定义浮点表示中必须支持的特殊情况位掩码。默认值：EMULATION_SPECIAL_VALUES_SUPPORT_DEFAULT。 | int32_t |
| CUBLASLT_EMULATION_DESC_FIXEDPOINT_MANTISSA_CONTROL | 尾数控制，参见 `cudaEmulationMantissaControl_t`。对于定点模拟，定义如何计算保留的尾数位数。更多信息请参见浮点模拟文档。 | int32_t |
| CUBLASLT_EMULATION_DESC_FIXEDPOINT_MAX_MANTISSA_BIT_COUNT | 仅适用于定点模拟。一个 int32_t 值，表示在定点模拟期间保留的最大（考虑量化）尾数位数。默认值为 0，允许库根据设备属性选择合理的值。默认值：0。 | int32_t |
| CUBLASLT_EMULATION_DESC_FIXEDPOINT_MANTISSA_BIT_OFFSET | 此参数适用于使用 CUDA_EMULATION_MANTISSA_CONTROL_DYNAMIC 尾数控制（参见 `cudaEmulationMantissaControl_t`）的定点模拟。一个可用于偏移推荐尾数位数的整数。默认值：0。 | int32_t |
| CUBLASLT_EMULATION_DESC_FIXEDPOINT_MANTISSA_BIT_COUNT_POINTER | 此参数适用于定点模拟。一个设备指针，将包含保留的尾数位数。如果未使用模拟，指针将包含 -1。默认值：nullptr。 | int32_t * |