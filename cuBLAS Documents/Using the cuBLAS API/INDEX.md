# Using the cuBLAS API (2.)

## 文档索引 / Documentation Index

本手册为 NVIDIA cuBLAS 13.2 Using the cuBLAS API 的中文翻译版本。

**来源 / Source:** NVIDIA cuBLAS Library Documentation - Section 2

---

## 双语目录对照 / Bilingual Table of Contents

### 02
*第二章 使用 cuBLAS API*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 2 使用 cuBLAS API | 2. Using the cuBLAS API | [ch02.md](./chs/ch02.md) | [ch02.md](./eng/ch02.md) |
| 2.1 一般描述 | 2.1. General Description | [ch02s01.md](./chs/ch02s01.md) | [ch02s01.md](./eng/ch02s01.md) |
| 2.1.1 错误状态 | 2.1.1. Error Status | [ch02s01s01.md](./chs/ch02s01s01.md) | [ch02s01s01.md](./eng/ch02s01s01.md) |
| 2.1.2 cuBLAS 上下文 | 2.1.2. cuBLAS Context | [ch02s01s02.md](./chs/ch02s01s02.md) | [ch02s01s02.md](./eng/ch02s01s02.md) |
| 2.1.3 线程安全 | 2.1.3. Thread Safety | [ch02s01s03.md](./chs/ch02s01s03.md) | [ch02s01s03.md](./eng/ch02s01s03.md) |
| 2.1.4 结果可重现性 | 2.1.4. Results Reproducibility | [ch02s01s04.md](./chs/ch02s01s04.md) | [ch02s01s04.md](./eng/ch02s01s04.md) |
| 2.1.5 标量参数 | 2.1.5. Scalar Parameters | [ch02s01s05.md](./chs/ch02s01s05.md) | [ch02s01s05.md](./eng/ch02s01s05.md) |
| 2.1.6 流并行 | 2.1.6. Parallelism with Streams | [ch02s01s06.md](./chs/ch02s01s06.md) | [ch02s01s06.md](./eng/ch02s01s06.md) |
| 2.1.7 批处理内核 | 2.1.7. Batching Kernels | [ch02s01s07.md](./chs/ch02s01s07.md) | [ch02s01s07.md](./eng/ch02s01s07.md) |
| 2.1.8 缓存配置 | 2.1.8. Cache Configuration | [ch02s01s08.md](./chs/ch02s01s08.md) | [ch02s01s08.md](./eng/ch02s01s08.md) |
| 2.1.9 静态库支持 | 2.1.9. Static Library Support | [ch02s01s09.md](./chs/ch02s01s09.md) | [ch02s01s09.md](./eng/ch02s01s09.md) |
| 2.1.10 GEMM 算法数值行为 | 2.1.10. GEMM Algorithms Numerical Behavior | [ch02s01s10.md](./chs/ch02s01s10.md) | [ch02s01s10.md](./eng/ch02s01s10.md) |
| 2.1.11 张量核心使用 | 2.1.11. Tensor Core Usage | [ch02s01s11.md](./chs/ch02s01s11.md) | [ch02s01s11.md](./eng/ch02s01s11.md) |
| 2.1.12 CUDA Graphs 支持 | 2.1.12. CUDA Graphs Support | [ch02s01s12.md](./chs/ch02s01s12.md) | [ch02s01s12.md](./eng/ch02s01s12.md) |
| 2.1.13 64位整数接口 | 2.1.13. 64-bit Integer Interface | [ch02s01s13.md](./chs/ch02s01s13.md) | [ch02s01s13.md](./eng/ch02s01s13.md) |

### 02.02
*2.2 cuBLAS 数据类型参考*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 2.2 cuBLAS 数据类型参考 | 2.2. cuBLAS Datatypes Reference | [ch02s02.md](./chs/ch02s02.md) | [ch02s02.md](./eng/ch02s02.md) |
| 2.2.1 cublasHandle_t | 2.2.1. cublasHandle_t | [ch02s02s01.md](./chs/ch02s02s01.md) | [ch02s02s01.md](./eng/ch02s02s01.md) |
| 2.2.2 cublasStatus_t | 2.2.2. cublasStatus_t | [ch02s02s02.md](./chs/ch02s02s02.md) | [ch02s02s02.md](./eng/ch02s02s02.md) |
| 2.2.3 cublasOperation_t | 2.2.3. cublasOperation_t | [ch02s02s03.md](./chs/ch02s02s03.md) | [ch02s02s03.md](./eng/ch02s02s03.md) |
| 2.2.4 cublasFillMode_t | 2.2.4. cublasFillMode_t | [ch02s02s04.md](./chs/ch02s02s04.md) | [ch02s02s04.md](./eng/ch02s02s04.md) |
| 2.2.5 cublasDiagType_t | 2.2.5. cublasDiagType_t | [ch02s02s05.md](./chs/ch02s02s05.md) | [ch02s02s05.md](./eng/ch02s02s05.md) |
| 2.2.6 cublasSideMode_t | 2.2.6. cublasSideMode_t | [ch02s02s06.md](./chs/ch02s02s06.md) | [ch02s02s06.md](./eng/ch02s02s06.md) |
| 2.2.7 cublasPointerMode_t | 2.2.7. cublasPointerMode_t | [ch02s02s07.md](./chs/ch02s02s07.md) | [ch02s02s07.md](./eng/ch02s02s07.md) |
| 2.2.8 cublasAtomicsMode_t | 2.2.8. cublasAtomicsMode_t | [ch02s02s08.md](./chs/ch02s02s08.md) | [ch02s02s08.md](./eng/ch02s02s08.md) |
| 2.2.9 cublasGemmAlgo_t | 2.2.9. cublasGemmAlgo_t | [ch02s02s09.md](./chs/ch02s02s09.md) | [ch02s02s09.md](./eng/ch02s02s09.md) |
| 2.2.10 cublasMath_t | 2.2.10. cublasMath_t | [ch02s02s10.md](./chs/ch02s02s10.md) | [ch02s02s10.md](./eng/ch02s02s10.md) |
| 2.2.11 cublasComputeType_t | 2.2.11. cublasComputeType_t | [ch02s02s11.md](./chs/ch02s02s11.md) | [ch02s02s11.md](./eng/ch02s02s11.md) |
| 2.2.12 cublasEmulationStrategy_t | 2.2.12. cublasEmulationStrategy_t | [ch02s02s12.md](./chs/ch02s02s12.md) | [ch02s02s12.md](./eng/ch02s02s12.md) |

### 02.03
*2.3 CUDA 数据类型参考*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 2.3 CUDA 数据类型参考 | 2.3. CUDA Datatypes Reference | [ch02s03.md](./chs/ch02s03.md) | [ch02s03.md](./eng/ch02s03.md) |
| 2.3.1 cudaDataType_t | 2.3.1. cudaDataType_t | [ch02s03s01.md](./chs/ch02s03s01.md) | [ch02s03s01.md](./eng/ch02s03s01.md) |
| 2.3.2 cudaEmulationStrategy_t | 2.3.2. cudaEmulationStrategy_t | [ch02s03s02.md](./chs/ch02s03s02.md) | [ch02s03s02.md](./eng/ch02s03s02.md) |
| 2.3.3 cudaEmulationMantissaControl_t | 2.3.3. cudaEmulationMantissaControl_t | [ch02s03s03.md](./chs/ch02s03s03.md) | [ch02s03s03.md](./eng/ch02s03s03.md) |
| 2.3.4 cudaEmulationSpecialValuesSupport_t | 2.3.4. cudaEmulationSpecialValuesSupport_t | [ch02s03s04.md](./chs/ch02s03s04.md) | [ch02s03s04.md](./eng/ch02s03s04.md) |
| 2.3.5 libraryPropertyType_t | 2.3.5. libraryPropertyType_t | [ch02s03s05.md](./chs/ch02s03s05.md) | [ch02s03s05.md](./eng/ch02s03s05.md) |

### 02.04
*2.4 cuBLAS 辅助函数参考*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 2.4 cuBLAS 辅助函数参考 | 2.4. cuBLAS Helper Function Reference | [ch02s04.md](./chs/ch02s04.md) | [ch02s04.md](./eng/ch02s04.md) |
| 2.4.1 cublasCreate() | 2.4.1. cublasCreate() | [ch02s04s01.md](./chs/ch02s04s01.md) | [ch02s04s01.md](./eng/ch02s04s01.md) |
| 2.4.2 cublasDestroy() | 2.4.2. cublasDestroy() | [ch02s04s02.md](./chs/ch02s04s02.md) | [ch02s04s02.md](./eng/ch02s04s02.md) |
| 2.4.3 cublasGetVersion() | 2.4.3. cublasGetVersion() | [ch02s04s03.md](./chs/ch02s04s03.md) | [ch02s04s03.md](./eng/ch02s04s03.md) |
| 2.4.4 cublasGetProperty() | 2.4.4. cublasGetProperty() | [ch02s04s04.md](./chs/ch02s04s04.md) | [ch02s04s04.md](./eng/ch02s04s04.md) |
| 2.4.5 cublasGetStatusName() | 2.4.5. cublasGetStatusName() | [ch02s04s05.md](./chs/ch02s04s05.md) | [ch02s04s05.md](./eng/ch02s04s05.md) |
| 2.4.6 cublasGetStatusString() | 2.4.6. cublasGetStatusString() | [ch02s04s06.md](./chs/ch02s04s06.md) | [ch02s04s06.md](./eng/ch02s04s06.md) |
| 2.4.7 cublasSetStream() | 2.4.7. cublasSetStream() | [ch02s04s07.md](./chs/ch02s04s07.md) | [ch02s04s07.md](./eng/ch02s04s07.md) |
| 2.4.8 cublasSetWorkspace() | 2.4.8. cublasSetWorkspace() | [ch02s04s08.md](./chs/ch02s04s08.md) | [ch02s04s08.md](./eng/ch02s04s08.md) |
| 2.4.9 cublasGetStream() | 2.4.9. cublasGetStream() | [ch02s04s09.md](./chs/ch02s04s09.md) | [ch02s04s09.md](./eng/ch02s04s09.md) |
| 2.4.10 cublasGetPointerMode() | 2.4.10. cublasGetPointerMode() | [ch02s04s10.md](./chs/ch02s04s10.md) | [ch02s04s10.md](./eng/ch02s04s10.md) |
| 2.4.11 cublasSetPointerMode() | 2.4.11. cublasSetPointerMode() | [ch02s04s11.md](./chs/ch02s04s11.md) | [ch02s04s11.md](./eng/ch02s04s11.md) |
| 2.4.12 cublasSetVector() | 2.4.12. cublasSetVector() | [ch02s04s12.md](./chs/ch02s04s12.md) | [ch02s04s12.md](./eng/ch02s04s12.md) |
| 2.4.13 cublasGetVector() | 2.4.13. cublasGetVector() | [ch02s04s13.md](./chs/ch02s04s13.md) | [ch02s04s13.md](./eng/ch02s04s13.md) |
| 2.4.14 cublasSetMatrix() | 2.4.14. cublasSetMatrix() | [ch02s04s14.md](./chs/ch02s04s14.md) | [ch02s04s14.md](./eng/ch02s04s14.md) |
| 2.4.15 cublasGetMatrix() | 2.4.15. cublasGetMatrix() | [ch02s04s15.md](./chs/ch02s04s15.md) | [ch02s04s15.md](./eng/ch02s04s15.md) |
| 2.4.16 cublasSetVectorAsync() | 2.4.16. cublasSetVectorAsync() | [ch02s04s16.md](./chs/ch02s04s16.md) | [ch02s04s16.md](./eng/ch02s04s16.md) |
| 2.4.17 cublasGetVectorAsync() | 2.4.17. cublasGetVectorAsync() | [ch02s04s17.md](./chs/ch02s04s17.md) | [ch02s04s17.md](./eng/ch02s04s17.md) |
| 2.4.18 cublasSetMatrixAsync() | 2.4.18. cublasSetMatrixAsync() | [ch02s04s18.md](./chs/ch02s04s18.md) | [ch02s04s18.md](./eng/ch02s04s18.md) |
| 2.4.19 cublasGetMatrixAsync() | 2.4.19. cublasGetMatrixAsync() | [ch02s04s19.md](./chs/ch02s04s19.md) | [ch02s04s19.md](./eng/ch02s04s19.md) |
| 2.4.20 cublasSetAtomicsMode() | 2.4.20. cublasSetAtomicsMode() | [ch02s04s20.md](./chs/ch02s04s20.md) | [ch02s04s20.md](./eng/ch02s04s20.md) |
| 2.4.21 cublasGetAtomicsMode() | 2.4.21. cublasGetAtomicsMode() | [ch02s04s21.md](./chs/ch02s04s21.md) | [ch02s04s21.md](./eng/ch02s04s21.md) |
| 2.4.22 cublasSetMathMode() | 2.4.22. cublasSetMathMode() | [ch02s04s22.md](./chs/ch02s04s22.md) | [ch02s04s22.md](./eng/ch02s04s22.md) |
| 2.4.23 cublasGetMathMode() | 2.4.23. cublasGetMathMode() | [ch02s04s23.md](./chs/ch02s04s23.md) | [ch02s04s23.md](./eng/ch02s04s23.md) |
| 2.4.24 cublasSetSmCountTarget() | 2.4.24. cublasSetSmCountTarget() | [ch02s04s24.md](./chs/ch02s04s24.md) | [ch02s04s24.md](./eng/ch02s04s24.md) |
| 2.4.25 cublasGetSmCountTarget() | 2.4.25. cublasGetSmCountTarget() | [ch02s04s25.md](./chs/ch02s04s25.md) | [ch02s04s25.md](./eng/ch02s04s25.md) |
| 2.4.26 cublasSetEmulationStrategy() | 2.4.26. cublasSetEmulationStrategy() | [ch02s04s26.md](./chs/ch02s04s26.md) | [ch02s04s26.md](./eng/ch02s04s26.md) |
| 2.4.27 cublasGetEmulationStrategy() | 2.4.27. cublasGetEmulationStrategy() | [ch02s04s27.md](./chs/ch02s04s27.md) | [ch02s04s27.md](./eng/ch02s04s27.md) |
| 2.4.28 cublasGetEmulationSpecialValuesSupport() | 2.4.28. cublasGetEmulationSpecialValuesSupport() | [ch02s04s28.md](./chs/ch02s04s28.md) | [ch02s04s28.md](./eng/ch02s04s28.md) |
| 2.4.29 cublasSetEmulationSpecialValuesSupport() | 2.4.29. cublasSetEmulationSpecialValuesSupport() | [ch02s04s29.md](./chs/ch02s04s29.md) | [ch02s04s29.md](./eng/ch02s04s29.md) |
| 2.4.30 cublasGetFixedPointEmulationMantissaControl() | 2.4.30. cublasGetFixedPointEmulationMantissaControl() | [ch02s04s30.md](./chs/ch02s04s30.md) | [ch02s04s30.md](./eng/ch02s04s30.md) |
| 2.4.31 cublasSetFixedPointEmulationMantissaControl() | 2.4.31. cublasSetFixedPointEmulationMantissaControl() | [ch02s04s31.md](./chs/ch02s04s31.md) | [ch02s04s31.md](./eng/ch02s04s31.md) |
| 2.4.32 cublasGetFixedPointEmulationMaxMantissaBitCount() | 2.4.32. cublasGetFixedPointEmulationMaxMantissaBitCount() | [ch02s04s32.md](./chs/ch02s04s32.md) | [ch02s04s32.md](./eng/ch02s04s32.md) |
| 2.4.33 cublasSetFixedPointEmulationMaxMantissaBitCount() | 2.4.33. cublasSetFixedPointEmulationMaxMantissaBitCount() | [ch02s04s33.md](./chs/ch02s04s33.md) | [ch02s04s33.md](./eng/ch02s04s33.md) |
| 2.4.34 cublasGetFixedPointEmulationMantissaBitOffset() | 2.4.34. cublasGetFixedPointEmulationMantissaBitOffset() | [ch02s04s34.md](./chs/ch02s04s34.md) | [ch02s04s34.md](./eng/ch02s04s34.md) |
| 2.4.35 cublasSetFixedPointEmulationMantissaBitOffset() | 2.4.35. cublasSetFixedPointEmulationMantissaBitOffset() | [ch02s04s35.md](./chs/ch02s04s35.md) | [ch02s04s35.md](./eng/ch02s04s35.md) |
| 2.4.36 cublasGetFixedPointEmulationMantissaBitCountPointer() | 2.4.36. cublasGetFixedPointEmulationMantissaBitCountPointer() | [ch02s04s36.md](./chs/ch02s04s36.md) | [ch02s04s36.md](./eng/ch02s04s36.md) |
| 2.4.37 cublasSetFixedPointEmulationMantissaBitCountPointer() | 2.4.37. cublasSetFixedPointEmulationMantissaBitCountPointer() | [ch02s04s37.md](./chs/ch02s04s37.md) | [ch02s04s37.md](./eng/ch02s04s37.md) |
| 2.4.38 cublasLoggerConfigure() | 2.4.38. cublasLoggerConfigure() | [ch02s04s38.md](./chs/ch02s04s38.md) | [ch02s04s38.md](./eng/ch02s04s38.md) |
| 2.4.39 cublasGetLoggerCallback() | 2.4.39. cublasGetLoggerCallback() | [ch02s04s39.md](./chs/ch02s04s39.md) | [ch02s04s39.md](./eng/ch02s04s39.md) |
| 2.4.40 cublasSetLoggerCallback() | 2.4.40. cublasSetLoggerCallback() | [ch02s04s40.md](./chs/ch02s04s40.md) | [ch02s04s40.md](./eng/ch02s04s40.md) |

### 02.05
*2.5 cuBLAS Level-1 函数参考*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 2.5 cuBLAS Level-1 函数参考 | 2.5. cuBLAS Level-1 Function Reference | [ch02s05.md](./chs/ch02s05.md) | [ch02s05.md](./eng/ch02s05.md) |
| 2.5.1 cublasI<t>amax() | 2.5.1. cublasI<t>amax() | [ch02s05s01.md](./chs/ch02s05s01.md) | [ch02s05s01.md](./eng/ch02s05s01.md) |
| 2.5.2 cublasI<t>amin() | 2.5.2. cublasI<t>amin() | [ch02s05s02.md](./chs/ch02s05s02.md) | [ch02s05s02.md](./eng/ch02s05s02.md) |
| 2.5.3 cublas<t>asum() | 2.5.3. cublas<t>asum() | [ch02s05s03.md](./chs/ch02s05s03.md) | [ch02s05s03.md](./eng/ch02s05s03.md) |
| 2.5.4 cublas<t>axpy() | 2.5.4. cublas<t>axpy() | [ch02s05s04.md](./chs/ch02s05s04.md) | [ch02s05s04.md](./eng/ch02s05s04.md) |
| 2.5.5 cublas<t>copy() | 2.5.5. cublas<t>copy() | [ch02s05s05.md](./chs/ch02s05s05.md) | [ch02s05s05.md](./eng/ch02s05s05.md) |
| 2.5.6 cublas<t>dot() | 2.5.6. cublas<t>dot() | [ch02s05s06.md](./chs/ch02s05s06.md) | [ch02s05s06.md](./eng/ch02s05s06.md) |
| 2.5.7 cublas<t>nrm2() | 2.5.7. cublas<t>nrm2() | [ch02s05s07.md](./chs/ch02s05s07.md) | [ch02s05s07.md](./eng/ch02s05s07.md) |
| 2.5.8 cublas<t>rot() | 2.5.8. cublas<t>rot() | [ch02s05s08.md](./chs/ch02s05s08.md) | [ch02s05s08.md](./eng/ch02s05s08.md) |
| 2.5.9 cublas<t>rotg() | 2.5.9. cublas<t>rotg() | [ch02s05s09.md](./chs/ch02s05s09.md) | [ch02s05s09.md](./eng/ch02s05s09.md) |
| 2.5.10 cublas<t>rotm() | 2.5.10. cublas<t>rotm() | [ch02s05s10.md](./chs/ch02s05s10.md) | [ch02s05s10.md](./eng/ch02s05s10.md) |
| 2.5.11 cublas<t>rotmg() | 2.5.11. cublas<t>rotmg() | [ch02s05s11.md](./chs/ch02s05s11.md) | [ch02s05s11.md](./eng/ch02s05s11.md) |
| 2.5.12 cublas<t>scal() | 2.5.12. cublas<t>scal() | [ch02s05s12.md](./chs/ch02s05s12.md) | [ch02s05s12.md](./eng/ch02s05s12.md) |
| 2.5.13 cublas<t>swap() | 2.5.13. cublas<t>swap() | [ch02s05s13.md](./chs/ch02s05s13.md) | [ch02s05s13.md](./eng/ch02s05s13.md) |

### 02.06
*2.6 cuBLAS Level-2 函数参考*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 2.6 cuBLAS Level-2 函数参考 | 2.6. cuBLAS Level-2 Function Reference | [ch02s06.md](./chs/ch02s06.md) | [ch02s06.md](./eng/ch02s06.md) |
| 2.6.1 cublas<t>gbmv() | 2.6.1. cublas<t>gbmv() | [ch02s06s01.md](./chs/ch02s06s01.md) | [ch02s06s01.md](./eng/ch02s06s01.md) |
| 2.6.2 cublas<t>gemv() | 2.6.2. cublas<t>gemv() | [ch02s06s02.md](./chs/ch02s06s02.md) | [ch02s06s02.md](./eng/ch02s06s02.md) |
| 2.6.3 cublas<t>ger() | 2.6.3. cublas<t>ger() | [ch02s06s03.md](./chs/ch02s06s03.md) | [ch02s06s03.md](./eng/ch02s06s03.md) |
| 2.6.4 cublas<t>sbmv() | 2.6.4. cublas<t>sbmv() | [ch02s06s04.md](./chs/ch02s06s04.md) | [ch02s06s04.md](./eng/ch02s06s04.md) |
| 2.6.5 cublas<t>spmv() | 2.6.5. cublas<t>spmv() | [ch02s06s05.md](./chs/ch02s06s05.md) | [ch02s06s05.md](./eng/ch02s06s05.md) |
| 2.6.6 cublas<t>spr() | 2.6.6. cublas<t>spr() | [ch02s06s06.md](./chs/ch02s06s06.md) | [ch02s06s06.md](./eng/ch02s06s06.md) |
| 2.6.7 cublas<t>spr2() | 2.6.7. cublas<t>spr2() | [ch02s06s07.md](./chs/ch02s06s07.md) | [ch02s06s07.md](./eng/ch02s06s07.md) |
| 2.6.8 cublas<t>symv() | 2.6.8. cublas<t>symv() | [ch02s06s08.md](./chs/ch02s06s08.md) | [ch02s06s08.md](./eng/ch02s06s08.md) |
| 2.6.9 cublas<t>syr() | 2.6.9. cublas<t>syr() | [ch02s06s09.md](./chs/ch02s06s09.md) | [ch02s06s09.md](./eng/ch02s06s09.md) |
| 2.6.10 cublas<t>syr2() | 2.6.10. cublas<t>syr2() | [ch02s06s10.md](./chs/ch02s06s10.md) | [ch02s06s10.md](./eng/ch02s06s10.md) |
| 2.6.11 cublas<t>tbmv() | 2.6.11. cublas<t>tbmv() | [ch02s06s11.md](./chs/ch02s06s11.md) | [ch02s06s11.md](./eng/ch02s06s11.md) |
| 2.6.12 cublas<t>tbsv() | 2.6.12. cublas<t>tbsv() | [ch02s06s12.md](./chs/ch02s06s12.md) | [ch02s06s12.md](./eng/ch02s06s12.md) |
| 2.6.13 cublas<t>tpmv() | 2.6.13. cublas<t>tpmv() | [ch02s06s13.md](./chs/ch02s06s13.md) | [ch02s06s13.md](./eng/ch02s06s13.md) |
| 2.6.14 cublas<t>tpsv() | 2.6.14. cublas<t>tpsv() | [ch02s06s14.md](./chs/ch02s06s14.md) | [ch02s06s14.md](./eng/ch02s06s14.md) |
| 2.6.15 cublas<t>trmv() | 2.6.15. cublas<t>trmv() | [ch02s06s15.md](./chs/ch02s06s15.md) | [ch02s06s15.md](./eng/ch02s06s15.md) |
| 2.6.16 cublas<t>trsv() | 2.6.16. cublas<t>trsv() | [ch02s06s16.md](./chs/ch02s06s16.md) | [ch02s06s16.md](./eng/ch02s06s16.md) |
| 2.6.17 cublas<t>hemv() | 2.6.17. cublas<t>hemv() | [ch02s06s17.md](./chs/ch02s06s17.md) | [ch02s06s17.md](./eng/ch02s06s17.md) |
| 2.6.18 cublas<t>hbmv() | 2.6.18. cublas<t>hbmv() | [ch02s06s18.md](./chs/ch02s06s18.md) | [ch02s06s18.md](./eng/ch02s06s18.md) |
| 2.6.19 cublas<t>hpmv() | 2.6.19. cublas<t>hpmv() | [ch02s06s19.md](./chs/ch02s06s19.md) | [ch02s06s19.md](./eng/ch02s06s19.md) |
| 2.6.20 cublas<t>her() | 2.6.20. cublas<t>her() | [ch02s06s20.md](./chs/ch02s06s20.md) | [ch02s06s20.md](./eng/ch02s06s20.md) |
| 2.6.21 cublas<t>her2() | 2.6.21. cublas<t>her2() | [ch02s06s21.md](./chs/ch02s06s21.md) | [ch02s06s21.md](./eng/ch02s06s21.md) |
| 2.6.22 cublas<t>hpr() | 2.6.22. cublas<t>hpr() | [ch02s06s22.md](./chs/ch02s06s22.md) | [ch02s06s22.md](./eng/ch02s06s22.md) |
| 2.6.23 cublas<t>hpr2() | 2.6.23. cublas<t>hpr2() | [ch02s06s23.md](./chs/ch02s06s23.md) | [ch02s06s23.md](./eng/ch02s06s23.md) |
| 2.6.24 cublas<t>gemvBatched() | 2.6.24. cublas<t>gemvBatched() | [ch02s06s24.md](./chs/ch02s06s24.md) | [ch02s06s24.md](./eng/ch02s06s24.md) |
| 2.6.25 cublas<t>gemvStridedBatched() | 2.6.25. cublas<t>gemvStridedBatched() | [ch02s06s25.md](./chs/ch02s06s25.md) | [ch02s06s25.md](./eng/ch02s06s25.md) |

### 02.07
*2.7 cuBLAS Level-3 函数参考*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 2.7 cuBLAS Level-3 函数参考 | 2.7. cuBLAS Level-3 Function Reference | [ch02s07.md](./chs/ch02s07.md) | [ch02s07.md](./eng/ch02s07.md) |
| 2.7.1 cublas<t>gemm() | 2.7.1. cublas<t>gemm() | [ch02s07s01.md](./chs/ch02s07s01.md) | [ch02s07s01.md](./eng/ch02s07s01.md) |
| 2.7.2 cublas<t>gemm3m() | 2.7.2. cublas<t>gemm3m() | [ch02s07s02.md](./chs/ch02s07s02.md) | [ch02s07s02.md](./eng/ch02s07s02.md) |
| 2.7.3 cublas<t>gemmBatched() | 2.7.3. cublas<t>gemmBatched() | [ch02s07s03.md](./chs/ch02s07s03.md) | [ch02s07s03.md](./eng/ch02s07s03.md) |
| 2.7.4 cublas<t>gemmStridedBatched() | 2.7.4. cublas<t>gemmStridedBatched() | [ch02s07s04.md](./chs/ch02s07s04.md) | [ch02s07s04.md](./eng/ch02s07s04.md) |
| 2.7.5 cublas<t>gemmGroupedBatched() | 2.7.5. cublas<t>gemmGroupedBatched() | [ch02s07s05.md](./chs/ch02s07s05.md) | [ch02s07s05.md](./eng/ch02s07s05.md) |
| 2.7.6 cublas<t>symm() | 2.7.6. cublas<t>symm() | [ch02s07s06.md](./chs/ch02s07s06.md) | [ch02s07s06.md](./eng/ch02s07s06.md) |
| 2.7.7 cublas<t>syrk() | 2.7.7. cublas<t>syrk() | [ch02s07s07.md](./chs/ch02s07s07.md) | [ch02s07s07.md](./eng/ch02s07s07.md) |
| 2.7.8 cublas<t>syr2k() | 2.7.8. cublas<t>syr2k() | [ch02s07s08.md](./chs/ch02s07s08.md) | [ch02s07s08.md](./eng/ch02s07s08.md) |
| 2.7.9 cublas<t>syrkx() | 2.7.9. cublas<t>syrkx() | [ch02s07s09.md](./chs/ch02s07s09.md) | [ch02s07s09.md](./eng/ch02s07s09.md) |
| 2.7.10 cublas<t>trmm() | 2.7.10. cublas<t>trmm() | [ch02s07s10.md](./chs/ch02s07s10.md) | [ch02s07s10.md](./eng/ch02s07s10.md) |
| 2.7.11 cublas<t>trsm() | 2.7.11. cublas<t>trsm() | [ch02s07s11.md](./chs/ch02s07s11.md) | [ch02s07s11.md](./eng/ch02s07s11.md) |
| 2.7.12 cublas<t>trsmBatched() | 2.7.12. cublas<t>trsmBatched() | [ch02s07s12.md](./chs/ch02s07s12.md) | [ch02s07s12.md](./eng/ch02s07s12.md) |
| 2.7.13 cublas<t>hemm() | 2.7.13. cublas<t>hemm() | [ch02s07s13.md](./chs/ch02s07s13.md) | [ch02s07s13.md](./eng/ch02s07s13.md) |
| 2.7.14 cublas<t>herk() | 2.7.14. cublas<t>herk() | [ch02s07s14.md](./chs/ch02s07s14.md) | [ch02s07s14.md](./eng/ch02s07s14.md) |
| 2.7.15 cublas<t>her2k() | 2.7.15. cublas<t>her2k() | [ch02s07s15.md](./chs/ch02s07s15.md) | [ch02s07s15.md](./eng/ch02s07s15.md) |
| 2.7.16 cublas<t>herkx() | 2.7.16. cublas<t>herkx() | [ch02s07s16.md](./chs/ch02s07s16.md) | [ch02s07s16.md](./eng/ch02s07s16.md) |

### 02.08
*2.8 cuBLAS BLAS-extension 函数参考*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 2.8 cuBLAS BLAS-extension 函数参考 | 2.8. cuBLAS BLAS-ex Function Reference | [ch02s08.md](./chs/ch02s08.md) | [ch02s08.md](./eng/ch02s08.md) |
| 2.8.1 cublas<t>geam() | 2.8.1. cublas<t>geam() | [ch02s08s01.md](./chs/ch02s08s01.md) | [ch02s08s01.md](./eng/ch02s08s01.md) |
| 2.8.2 cublas<t>dgmm() | 2.8.2. cublas<t>dgmm() | [ch02s08s02.md](./chs/ch02s08s02.md) | [ch02s08s02.md](./eng/ch02s08s02.md) |
| 2.8.3 cublas<t>getrfBatched() | 2.8.3. cublas<t>getrfBatched() | [ch02s08s03.md](./chs/ch02s08s03.md) | [ch02s08s03.md](./eng/ch02s08s03.md) |
| 2.8.4 cublas<t>getrsBatched() | 2.8.4. cublas<t>getrsBatched() | [ch02s08s04.md](./chs/ch02s08s04.md) | [ch02s08s04.md](./eng/ch02s08s04.md) |
| 2.8.5 cublas<t>getriBatched() | 2.8.5. cublas<t>getriBatched() | [ch02s08s05.md](./chs/ch02s08s05.md) | [ch02s08s05.md](./eng/ch02s08s05.md) |
| 2.8.6 cublas<t>matinvBatched() | 2.8.6. cublas<t>matinvBatched() | [ch02s08s06.md](./chs/ch02s08s06.md) | [ch02s08s06.md](./eng/ch02s08s06.md) |
| 2.8.7 cublas<t>geqrfBatched() | 2.8.7. cublas<t>geqrfBatched() | [ch02s08s07.md](./chs/ch02s08s07.md) | [ch02s08s07.md](./eng/ch02s08s07.md) |
| 2.8.8 cublas<t>gelsBatched() | 2.8.8. cublas<t>gelsBatched() | [ch02s08s08.md](./chs/ch02s08s08.md) | [ch02s08s08.md](./eng/ch02s08s08.md) |
| 2.8.9 cublas<t>tpttr() | 2.8.9. cublas<t>tpttr() | [ch02s08s09.md](./chs/ch02s08s09.md) | [ch02s08s09.md](./eng/ch02s08s09.md) |
| 2.8.10 cublas<t>trttp() | 2.8.10. cublas<t>trttp() | [ch02s08s10.md](./chs/ch02s08s10.md) | [ch02s08s10.md](./eng/ch02s08s10.md) |
| 2.8.11 cublas<t>gemmEx() | 2.8.11. cublas<t>gemmEx() | [ch02s08s11.md](./chs/ch02s08s11.md) | [ch02s08s11.md](./eng/ch02s08s11.md) |
| 2.8.12 cublasGemmEx() | 2.8.12. cublasGemmEx() | [ch02s08s12.md](./chs/ch02s08s12.md) | [ch02s08s12.md](./eng/ch02s08s12.md) |
| 2.8.13 cublasGemmBatchedEx() | 2.8.13. cublasGemmBatchedEx() | [ch02s08s13.md](./chs/ch02s08s13.md) | [ch02s08s13.md](./eng/ch02s08s13.md) |
| 2.8.14 cublasGemmStridedBatchedEx() | 2.8.14. cublasGemmStridedBatchedEx() | [ch02s08s14.md](./chs/ch02s08s14.md) | [ch02s08s14.md](./eng/ch02s08s14.md) |
| 2.8.15 cublasGemmGroupedBatchedEx() | 2.8.15. cublasGemmGroupedBatchedEx() | [ch02s08s15.md](./chs/ch02s08s15.md) | [ch02s08s15.md](./eng/ch02s08s15.md) |
| 2.8.16 cublasCsyrkEx() | 2.8.16. cublasCsyrkEx() | [ch02s08s16.md](./chs/ch02s08s16.md) | [ch02s08s16.md](./eng/ch02s08s16.md) |
| 2.8.17 cublasCsyrk3mEx() | 2.8.17. cublasCsyrk3mEx() | [ch02s08s17.md](./chs/ch02s08s17.md) | [ch02s08s17.md](./eng/ch02s08s17.md) |
| 2.8.18 cublasCherkEx() | 2.8.18. cublasCherkEx() | [ch02s08s18.md](./chs/ch02s08s18.md) | [ch02s08s18.md](./eng/ch02s08s18.md) |
| 2.8.19 cublasCherk3mEx() | 2.8.19. cublasCherk3mEx() | [ch02s08s19.md](./chs/ch02s08s19.md) | [ch02s08s19.md](./eng/ch02s08s19.md) |
| 2.8.20 cublasNrm2Ex() | 2.8.20. cublasNrm2Ex() | [ch02s08s20.md](./chs/ch02s08s20.md) | [ch02s08s20.md](./eng/ch02s08s20.md) |
| 2.8.21 cublasAxpyEx() | 2.8.21. cublasAxpyEx() | [ch02s08s21.md](./chs/ch02s08s21.md) | [ch02s08s21.md](./eng/ch02s08s21.md) |
| 2.8.22 cublasDotEx() | 2.8.22. cublasDotEx() | [ch02s08s22.md](./chs/ch02s08s22.md) | [ch02s08s22.md](./eng/ch02s08s22.md) |
| 2.8.23 cublasRotEx() | 2.8.23. cublasRotEx() | [ch02s08s23.md](./chs/ch02s08s23.md) | [ch02s08s23.md](./eng/ch02s08s23.md) |
| 2.8.24 cublasScalEx() | 2.8.24. cublasScalEx() | [ch02s08s24.md](./chs/ch02s08s24.md) | [ch02s08s24.md](./eng/ch02s08s24.md) |

---

## 转换状态统计 / Conversion Status Summary

| 状态 Status | 数量 Count |
|-------------|------------|
| ✅ 已完成 / Completed | 0 |
| ⏳ 翻译中 / Translating | 0 |
| ⏳ 未转换 / Not converted | 137 |
| **总计 Total** | **137** |

---

## 版权声明 / Copyright Notice

本翻译仅供学习研究使用，原文档版权归 NVIDIA Corporation 所有。

This translation is for study and research purposes only. Original documentation copyright NVIDIA Corporation.
