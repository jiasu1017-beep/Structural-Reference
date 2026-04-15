

### 1.5.3. Default Library Configurations


Library default values for emulation are subject to change.


| API | Mantissa Control | Default Behavior |
| --- | --- | --- |
| cublasGetEmulationStrategy() | Not applicable | CUBLAS_EMULATION_STRATEGY_DEFAULT |
| cublasGetEmulationSpecialValuesSupport() | Not applicable | CUBLAS_EMULATION_SPECIAL_VALUES_SUPPORT_DEFAULT |
| cublasGetFixedPointEmulationMantissaControl() | Not applicable | CUDA_EMULATION_MANTISSA_CONTROL_DYNAMIC |
| cublasGetFixedPointEmulationMaxMantissaBitCount() | CUDA_EMULATION_MANTISSA_CONTROL_DYNAMIC | 79 |
| cublasGetFixedPointEmulationMaxMantissaBitCount() | CUDA_EMULATION_MANTISSA_CONTROL_FIXED | 55 |
| cublasGetFixedPointEmulationMantissaBitOffset() | Not applicable | 0 |
| cublasGetFixedPointEmulationMantissaBitCountPointer() | Not applicable | NULL |


