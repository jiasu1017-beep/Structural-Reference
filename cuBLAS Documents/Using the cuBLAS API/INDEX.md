# Using the cuBLAS API

## 使用 cuBLAS API

**来源 / Source:** NVIDIA cuBLAS Library Documentation - Using the cuBLAS API

---

## 双语目录对照 / Bilingual Table of Contents

| 章节号 | 中文 Chinese | 英文 English |
|--------|--------------|--------------|
| 2 | [Using the cuBLAS API](./chs/using-the-cublas-api.md) | [Using the cuBLAS API](./eng/using-the-cublas-api.md) |
| 2.1 | [General Description](./chs/using-the-cublas-api.md) | [General Description](./eng/using-the-cublas-api.md) |
| 2.1.1 | [Error Status](./chs/using-the-cublas-api.md) | [Error Status](./eng/using-the-cublas-api.md) |
| 2.1.2 | [cuBLAS Context](./chs/using-the-cublas-api.md) | [cuBLAS Context](./eng/using-the-cublas-api.md) |
| 2.1.3 | [Thread Safety](./chs/using-the-cublas-api.md) | [Thread Safety](./eng/using-the-cublas-api.md) |
| 2.1.4 | [Results Reproducibility](./chs/using-the-cublas-api.md) | [Results Reproducibility](./eng/using-the-cublas-api.md) |
| 2.1.5 | [Scalar Parameters](./chs/using-the-cublas-api.md) | [Scalar Parameters](./eng/using-the-cublas-api.md) |
| 2.1.6 | [Parallelism with Streams](./chs/using-the-cublas-api.md) | [Parallelism with Streams](./eng/using-the-cublas-api.md) |
| 2.1.7 | [Batching Kernels](./chs/using-the-cublas-api.md) | [Batching Kernels](./eng/using-the-cublas-api.md) |
| 2.1.8 | [Cache Configuration](./chs/using-the-cublas-api.md) | [Cache Configuration](./eng/using-the-cublas-api.md) |
| 2.1.9 | [Static Library Support](./chs/using-the-cublas-api.md) | [Static Library Support](./eng/using-the-cublas-api.md) |
| 2.1.10 | [GEMM Algorithms Numerical Behavior](./chs/using-the-cublas-api.md) | [GEMM Algorithms Numerical Behavior](./eng/using-the-cublas-api.md) |
| 2.1.11 | [Tensor Core Usage](./chs/using-the-cublas-api.md) | [Tensor Core Usage](./eng/using-the-cublas-api.md) |
| 2.1.12 | [CUDA Graphs Support](./chs/using-the-cublas-api.md) | [CUDA Graphs Support](./eng/using-the-cublas-api.md) |
| 2.1.13 | [64-bit Integer Interface](./chs/using-the-cublas-api.md) | [64-bit Integer Interface](./eng/using-the-cublas-api.md) |
| 2.2 | [cuBLAS Datatypes Reference](./chs/using-the-cublas-api.md) | [cuBLAS Datatypes Reference](./eng/using-the-cublas-api.md) |
| 2.2.1 | [cublasHandle_t](./chs/using-the-cublas-api.md) | [cublasHandle_t](./eng/using-the-cublas-api.md) |
| 2.2.2 | [cublasStatus_t](./chs/using-the-cublas-api.md) | [cublasStatus_t](./eng/using-the-cublas-api.md) |
| 2.2.3 | [cublasOperation_t](./chs/using-the-cublas-api.md) | [cublasOperation_t](./eng/using-the-cublas-api.md) |
| 2.2.4 | [cublasFillMode_t](./chs/using-the-cublas-api.md) | [cublasFillMode_t](./eng/using-the-cublas-api.md) |
| 2.2.5 | [cublasDiagType_t](./chs/using-the-cublas-api.md) | [cublasDiagType_t](./eng/using-the-cublas-api.md) |
| 2.2.6 | [cublasSideMode_t](./chs/using-the-cublas-api.md) | [cublasSideMode_t](./eng/using-the-cublas-api.md) |
| 2.2.7 | [cublasPointerMode_t](./chs/using-the-cublas-api.md) | [cublasPointerMode_t](./eng/using-the-cublas-api.md) |
| 2.2.8 | [cublasAtomicsMode_t](./chs/using-the-cublas-api.md) | [cublasAtomicsMode_t](./eng/using-the-cublas-api.md) |
| 2.2.9 | [cublasGemmAlgo_t](./chs/using-the-cublas-api.md) | [cublasGemmAlgo_t](./eng/using-the-cublas-api.md) |
| 2.2.10 | [cublasMath_t](./chs/using-the-cublas-api.md) | [cublasMath_t](./eng/using-the-cublas-api.md) |
| 2.2.11 | [cublasComputeType_t](./chs/using-the-cublas-api.md) | [cublasComputeType_t](./eng/using-the-cublas-api.md) |
| 2.2.12 | [cublasEmulationStrategy_t](./chs/using-the-cublas-api.md) | [cublasEmulationStrategy_t](./eng/using-the-cublas-api.md) |
| 2.3 | [CUDA Datatypes Reference](./chs/using-the-cublas-api.md) | [CUDA Datatypes Reference](./eng/using-the-cublas-api.md) |
| 2.3.1 | [cudaDataType_t](./chs/using-the-cublas-api.md) | [cudaDataType_t](./eng/using-the-cublas-api.md) |
| 2.3.2 | [cudaEmulationStrategy_t](./chs/using-the-cublas-api.md) | [cudaEmulationStrategy_t](./eng/using-the-cublas-api.md) |
| 2.3.3 | [cudaEmulationMantissaControl_t](./chs/using-the-cublas-api.md) | [cudaEmulationMantissaControl_t](./eng/using-the-cublas-api.md) |
| 2.3.4 | [cudaEmulationSpecialValuesSupport_t](./chs/using-the-cublas-api.md) | [cudaEmulationSpecialValuesSupport_t](./eng/using-the-cublas-api.md) |
| 2.3.5 | [libraryPropertyType_t](./chs/using-the-cublas-api.md) | [libraryPropertyType_t](./eng/using-the-cublas-api.md) |
| 2.4 | [cuBLAS Helper Function Reference](./chs/using-the-cublas-api.md) | [cuBLAS Helper Function Reference](./eng/using-the-cublas-api.md) |
| 2.4.1 | [cublasCreate()](./chs/using-the-cublas-api.md) | [cublasCreate()](./eng/using-the-cublas-api.md) |
| 2.4.2 | [cublasDestroy()](./chs/using-the-cublas-api.md) | [cublasDestroy()](./eng/using-the-cublas-api.md) |
| 2.4.3 | [cublasGetVersion()](./chs/using-the-cublas-api.md) | [cublasGetVersion()](./eng/using-the-cublas-api.md) |
| 2.4.4 | [cublasGetProperty()](./chs/using-the-cublas-api.md) | [cublasGetProperty()](./eng/using-the-cublas-api.md) |
| 2.4.5 | [cublasGetStatusName()](./chs/using-the-cublas-api.md) | [cublasGetStatusName()](./eng/using-the-cublas-api.md) |
| 2.4.6 | [cublasGetStatusString()](./chs/using-the-cublas-api.md) | [cublasGetStatusString()](./eng/using-the-cublas-api.md) |
| 2.4.7 | [cublasSetStream()](./chs/using-the-cublas-api.md) | [cublasSetStream()](./eng/using-the-cublas-api.md) |
| 2.4.8 | [cublasSetWorkspace()](./chs/using-the-cublas-api.md) | [cublasSetWorkspace()](./eng/using-the-cublas-api.md) |
| 2.4.9 | [cublasGetStream()](./chs/using-the-cublas-api.md) | [cublasGetStream()](./eng/using-the-cublas-api.md) |
| 2.4.10 | [cublasGetPointerMode()](./chs/using-the-cublas-api.md) | [cublasGetPointerMode()](./eng/using-the-cublas-api.md) |
| 2.4.11 | [cublasSetPointerMode()](./chs/using-the-cublas-api.md) | [cublasSetPointerMode()](./eng/using-the-cublas-api.md) |
| 2.4.12 | [cublasSetVector()](./chs/using-the-cublas-api.md) | [cublasSetVector()](./eng/using-the-cublas-api.md) |
| 2.4.13 | [cublasGetVector()](./chs/using-the-cublas-api.md) | [cublasGetVector()](./eng/using-the-cublas-api.md) |
| 2.4.14 | [cublasSetMatrix()](./chs/using-the-cublas-api.md) | [cublasSetMatrix()](./eng/using-the-cublas-api.md) |
| 2.4.15 | [cublasGetMatrix()](./chs/using-the-cublas-api.md) | [cublasGetMatrix()](./eng/using-the-cublas-api.md) |
| 2.4.16 | [cublasSetVectorAsync()](./chs/using-the-cublas-api.md) | [cublasSetVectorAsync()](./eng/using-the-cublas-api.md) |
| 2.4.17 | [cublasGetVectorAsync()](./chs/using-the-cublas-api.md) | [cublasGetVectorAsync()](./eng/using-the-cublas-api.md) |
| 2.4.18 | [cublasSetMatrixAsync()](./chs/using-the-cublas-api.md) | [cublasSetMatrixAsync()](./eng/using-the-cublas-api.md) |
| 2.4.19 | [cublasGetMatrixAsync()](./chs/using-the-cublas-api.md) | [cublasGetMatrixAsync()](./eng/using-the-cublas-api.md) |
| 2.4.20 | [cublasSetAtomicsMode()](./chs/using-the-cublas-api.md) | [cublasSetAtomicsMode()](./eng/using-the-cublas-api.md) |
| 2.4.21 | [cublasGetAtomicsMode()](./chs/using-the-cublas-api.md) | [cublasGetAtomicsMode()](./eng/using-the-cublas-api.md) |
| 2.4.22 | [cublasSetMathMode()](./chs/using-the-cublas-api.md) | [cublasSetMathMode()](./eng/using-the-cublas-api.md) |
| 2.4.23 | [cublasGetMathMode()](./chs/using-the-cublas-api.md) | [cublasGetMathMode()](./eng/using-the-cublas-api.md) |
| 2.4.24 | [cublasSetSmCountTarget()](./chs/using-the-cublas-api.md) | [cublasSetSmCountTarget()](./eng/using-the-cublas-api.md) |
| 2.4.25 | [cublasGetSmCountTarget()](./chs/using-the-cublas-api.md) | [cublasGetSmCountTarget()](./eng/using-the-cublas-api.md) |
| 2.4.26 | [cublasSetEmulationStrategy()](./chs/using-the-cublas-api.md) | [cublasSetEmulationStrategy()](./eng/using-the-cublas-api.md) |
| 2.4.27 | [cublasGetEmulationStrategy()](./chs/using-the-cublas-api.md) | [cublasGetEmulationStrategy()](./eng/using-the-cublas-api.md) |
| 2.4.28 | [cublasGetEmulationSpecialValuesSupport()](./chs/using-the-cublas-api.md) | [cublasGetEmulationSpecialValuesSupport()](./eng/using-the-cublas-api.md) |
| 2.4.29 | [cublasSetEmulationSpecialValuesSupport()](./chs/using-the-cublas-api.md) | [cublasSetEmulationSpecialValuesSupport()](./eng/using-the-cublas-api.md) |
| 2.4.30 | [cublasGetFixedPointEmulationMantissaControl()](./chs/using-the-cublas-api.md) | [cublasGetFixedPointEmulationMantissaControl()](./eng/using-the-cublas-api.md) |
| 2.4.31 | [cublasSetFixedPointEmulationMantissaControl()](./chs/using-the-cublas-api.md) | [cublasSetFixedPointEmulationMantissaControl()](./eng/using-the-cublas-api.md) |
| 2.4.32 | [cublasGetFixedPointEmulationMaxMantissaBitCount()](./chs/using-the-cublas-api.md) | [cublasGetFixedPointEmulationMaxMantissaBitCount()](./eng/using-the-cublas-api.md) |
| 2.4.33 | [cublasSetFixedPointEmulationMaxMantissaBitCount()](./chs/using-the-cublas-api.md) | [cublasSetFixedPointEmulationMaxMantissaBitCount()](./eng/using-the-cublas-api.md) |
| 2.4.34 | [cublasGetFixedPointEmulationMantissaBitOffset()](./chs/using-the-cublas-api.md) | [cublasGetFixedPointEmulationMantissaBitOffset()](./eng/using-the-cublas-api.md) |
| 2.4.35 | [cublasSetFixedPointEmulationMantissaBitOffset()](./chs/using-the-cublas-api.md) | [cublasSetFixedPointEmulationMantissaBitOffset()](./eng/using-the-cublas-api.md) |
| 2.4.36 | [cublasGetFixedPointEmulationMantissaBitCountPointer()](./chs/using-the-cublas-api.md) | [cublasGetFixedPointEmulationMantissaBitCountPointer()](./eng/using-the-cublas-api.md) |
| 2.4.37 | [cublasSetFixedPointEmulationMantissaBitCountPointer()](./chs/using-the-cublas-api.md) | [cublasSetFixedPointEmulationMantissaBitCountPointer()](./eng/using-the-cublas-api.md) |
| 2.4.38 | [cublasLoggerConfigure()](./chs/using-the-cublas-api.md) | [cublasLoggerConfigure()](./eng/using-the-cublas-api.md) |
| 2.4.39 | [cublasGetLoggerCallback()](./chs/using-the-cublas-api.md) | [cublasGetLoggerCallback()](./eng/using-the-cublas-api.md) |
| 2.4.40 | [cublasSetLoggerCallback()](./chs/using-the-cublas-api.md) | [cublasSetLoggerCallback()](./eng/using-the-cublas-api.md) |
| 2.5 | [cuBLAS Level-1 Function Reference](./chs/using-the-cublas-api.md) | [cuBLAS Level-1 Function Reference](./eng/using-the-cublas-api.md) |
| 2.5.1 | [cublasI<t>amax()](./chs/using-the-cublas-api.md) | [cublasI<t>amax()](./eng/using-the-cublas-api.md) |
| 2.5.2 | [cublasI<t>amin()](./chs/using-the-cublas-api.md) | [cublasI<t>amin()](./eng/using-the-cublas-api.md) |
| 2.5.3 | [cublas<t>asum()](./chs/using-the-cublas-api.md) | [cublas<t>asum()](./eng/using-the-cublas-api.md) |
| 2.5.4 | [cublas<t>axpy()](./chs/using-the-cublas-api.md) | [cublas<t>axpy()](./eng/using-the-cublas-api.md) |
| 2.5.5 | [cublas<t>copy()](./chs/using-the-cublas-api.md) | [cublas<t>copy()](./eng/using-the-cublas-api.md) |
| 2.5.6 | [cublas<t>dot()](./chs/using-the-cublas-api.md) | [cublas<t>dot()](./eng/using-the-cublas-api.md) |
| 2.5.7 | [cublas<t>nrm2()](./chs/using-the-cublas-api.md) | [cublas<t>nrm2()](./eng/using-the-cublas-api.md) |
| 2.5.8 | [cublas<t>rot()](./chs/using-the-cublas-api.md) | [cublas<t>rot()](./eng/using-the-cublas-api.md) |
| 2.5.9 | [cublas<t>rotg()](./chs/using-the-cublas-api.md) | [cublas<t>rotg()](./eng/using-the-cublas-api.md) |
| 2.5.10 | [cublas<t>rotm()](./chs/using-the-cublas-api.md) | [cublas<t>rotm()](./eng/using-the-cublas-api.md) |
| 2.5.11 | [cublas<t>rotmg()](./chs/using-the-cublas-api.md) | [cublas<t>rotmg()](./eng/using-the-cublas-api.md) |
| 2.5.12 | [cublas<t>scal()](./chs/using-the-cublas-api.md) | [cublas<t>scal()](./eng/using-the-cublas-api.md) |
| 2.5.13 | [cublas<t>swap()](./chs/using-the-cublas-api.md) | [cublas<t>swap()](./eng/using-the-cublas-api.md) |
| 2.6 | [cuBLAS Level-2 Function Reference](./chs/using-the-cublas-api.md) | [cuBLAS Level-2 Function Reference](./eng/using-the-cublas-api.md) |
| 2.6.1 | [cublas<t>gbmv()](./chs/using-the-cublas-api.md) | [cublas<t>gbmv()](./eng/using-the-cublas-api.md) |
| 2.6.2 | [cublas<t>gemv()](./chs/using-the-cublas-api.md) | [cublas<t>gemv()](./eng/using-the-cublas-api.md) |
| 2.6.3 | [cublas<t>ger()](./chs/using-the-cublas-api.md) | [cublas<t>ger()](./eng/using-the-cublas-api.md) |
| 2.6.4 | [cublas<t>sbmv()](./chs/using-the-cublas-api.md) | [cublas<t>sbmv()](./eng/using-the-cublas-api.md) |
| 2.6.5 | [cublas<t>spmv()](./chs/using-the-cublas-api.md) | [cublas<t>spmv()](./eng/using-the-cublas-api.md) |
| 2.6.6 | [cublas<t>spr()](./chs/using-the-cublas-api.md) | [cublas<t>spr()](./eng/using-the-cublas-api.md) |
| 2.6.7 | [cublas<t>spr2()](./chs/using-the-cublas-api.md) | [cublas<t>spr2()](./eng/using-the-cublas-api.md) |
| 2.6.8 | [cublas<t>symv()](./chs/using-the-cublas-api.md) | [cublas<t>symv()](./eng/using-the-cublas-api.md) |
| 2.6.9 | [cublas<t>syr()](./chs/using-the-cublas-api.md) | [cublas<t>syr()](./eng/using-the-cublas-api.md) |
| 2.6.10 | [cublas<t>syr2()](./chs/using-the-cublas-api.md) | [cublas<t>syr2()](./eng/using-the-cublas-api.md) |
| 2.6.11 | [cublas<t>tbmv()](./chs/using-the-cublas-api.md) | [cublas<t>tbmv()](./eng/using-the-cublas-api.md) |
| 2.6.12 | [cublas<t>tbsv()](./chs/using-the-cublas-api.md) | [cublas<t>tbsv()](./eng/using-the-cublas-api.md) |
| 2.6.13 | [cublas<t>tpmv()](./chs/using-the-cublas-api.md) | [cublas<t>tpmv()](./eng/using-the-cublas-api.md) |
| 2.6.14 | [cublas<t>tpsv()](./chs/using-the-cublas-api.md) | [cublas<t>tpsv()](./eng/using-the-cublas-api.md) |
| 2.6.15 | [cublas<t>trmv()](./chs/using-the-cublas-api.md) | [cublas<t>trmv()](./eng/using-the-cublas-api.md) |
| 2.6.16 | [cublas<t>trsv()](./chs/using-the-cublas-api.md) | [cublas<t>trsv()](./eng/using-the-cublas-api.md) |
| 2.6.17 | [cublas<t>hemv()](./chs/using-the-cublas-api.md) | [cublas<t>hemv()](./eng/using-the-cublas-api.md) |
| 2.6.18 | [cublas<t>hbmv()](./chs/using-the-cublas-api.md) | [cublas<t>hbmv()](./eng/using-the-cublas-api.md) |
| 2.6.19 | [cublas<t>hpmv()](./chs/using-the-cublas-api.md) | [cublas<t>hpmv()](./eng/using-the-cublas-api.md) |
| 2.6.20 | [cublas<t>her()](./chs/using-the-cublas-api.md) | [cublas<t>her()](./eng/using-the-cublas-api.md) |
| 2.6.21 | [cublas<t>her2()](./chs/using-the-cublas-api.md) | [cublas<t>her2()](./eng/using-the-cublas-api.md) |
| 2.6.22 | [cublas<t>hpr()](./chs/using-the-cublas-api.md) | [cublas<t>hpr()](./eng/using-the-cublas-api.md) |
| 2.6.23 | [cublas<t>hpr2()](./chs/using-the-cublas-api.md) | [cublas<t>hpr2()](./eng/using-the-cublas-api.md) |
| 2.6.24 | [cublas<t>gemvBatched()](./chs/using-the-cublas-api.md) | [cublas<t>gemvBatched()](./eng/using-the-cublas-api.md) |
| 2.6.25 | [cublas<t>gemvStridedBatched()](./chs/using-the-cublas-api.md) | [cublas<t>gemvStridedBatched()](./eng/using-the-cublas-api.md) |
| 2.7 | [cuBLAS Level-3 Function Reference](./chs/using-the-cublas-api.md) | [cuBLAS Level-3 Function Reference](./eng/using-the-cublas-api.md) |
| 2.7.1 | [cublas<t>gemm()](./chs/using-the-cublas-api.md) | [cublas<t>gemm()](./eng/using-the-cublas-api.md) |
| 2.7.2 | [cublas<t>gemm3m()](./chs/using-the-cublas-api.md) | [cublas<t>gemm3m()](./eng/using-the-cublas-api.md) |
| 2.7.3 | [cublas<t>gemmBatched()](./chs/using-the-cublas-api.md) | [cublas<t>gemmBatched()](./eng/using-the-cublas-api.md) |
| 2.7.4 | [cublas<t>gemmStridedBatched()](./chs/using-the-cublas-api.md) | [cublas<t>gemmStridedBatched()](./eng/using-the-cublas-api.md) |
| 2.7.5 | [cublas<t>gemmGroupedBatched()](./chs/using-the-cublas-api.md) | [cublas<t>gemmGroupedBatched()](./eng/using-the-cublas-api.md) |
| 2.7.6 | [cublas<t>symm()](./chs/using-the-cublas-api.md) | [cublas<t>symm()](./eng/using-the-cublas-api.md) |
| 2.7.7 | [cublas<t>syrk()](./chs/using-the-cublas-api.md) | [cublas<t>syrk()](./eng/using-the-cublas-api.md) |
| 2.7.8 | [cublas<t>syr2k()](./chs/using-the-cublas-api.md) | [cublas<t>syr2k()](./eng/using-the-cublas-api.md) |
| 2.7.9 | [cublas<t>syrkx()](./chs/using-the-cublas-api.md) | [cublas<t>syrkx()](./eng/using-the-cublas-api.md) |
| 2.7.10 | [cublas<t>trmm()](./chs/using-the-cublas-api.md) | [cublas<t>trmm()](./eng/using-the-cublas-api.md) |
| 2.7.11 | [cublas<t>trsm()](./chs/using-the-cublas-api.md) | [cublas<t>trsm()](./eng/using-the-cublas-api.md) |
| 2.7.12 | [cublas<t>trsmBatched()](./chs/using-the-cublas-api.md) | [cublas<t>trsmBatched()](./eng/using-the-cublas-api.md) |
| 2.7.13 | [cublas<t>hemm()](./chs/using-the-cublas-api.md) | [cublas<t>hemm()](./eng/using-the-cublas-api.md) |
| 2.7.14 | [cublas<t>herk()](./chs/using-the-cublas-api.md) | [cublas<t>herk()](./eng/using-the-cublas-api.md) |
| 2.7.15 | [cublas<t>her2k()](./chs/using-the-cublas-api.md) | [cublas<t>her2k()](./eng/using-the-cublas-api.md) |
| 2.7.16 | [cublas<t>herkx()](./chs/using-the-cublas-api.md) | [cublas<t>herkx()](./eng/using-the-cublas-api.md) |
| 2.8 | [BLAS-like Extension](./chs/using-the-cublas-api.md) | [BLAS-like Extension](./eng/using-the-cublas-api.md) |
| 2.8.1 | [cublas<t>geam()](./chs/using-the-cublas-api.md) | [cublas<t>geam()](./eng/using-the-cublas-api.md) |
| 2.8.2 | [cublas<t>dgmm()](./chs/using-the-cublas-api.md) | [cublas<t>dgmm()](./eng/using-the-cublas-api.md) |
| 2.8.3 | [cublas<t>getrfBatched()](./chs/using-the-cublas-api.md) | [cublas<t>getrfBatched()](./eng/using-the-cublas-api.md) |
| 2.8.4 | [cublas<t>getrsBatched()](./chs/using-the-cublas-api.md) | [cublas<t>getrsBatched()](./eng/using-the-cublas-api.md) |
| 2.8.5 | [cublas<t>getriBatched()](./chs/using-the-cublas-api.md) | [cublas<t>getriBatched()](./eng/using-the-cublas-api.md) |
| 2.8.6 | [cublas<t>matinvBatched()](./chs/using-the-cublas-api.md) | [cublas<t>matinvBatched()](./eng/using-the-cublas-api.md) |
| 2.8.7 | [cublas<t>geqrfBatched()](./chs/using-the-cublas-api.md) | [cublas<t>geqrfBatched()](./eng/using-the-cublas-api.md) |
| 2.8.8 | [cublas<t>gelsBatched()](./chs/using-the-cublas-api.md) | [cublas<t>gelsBatched()](./eng/using-the-cublas-api.md) |
| 2.8.9 | [cublas<t>tpttr()](./chs/using-the-cublas-api.md) | [cublas<t>tpttr()](./eng/using-the-cublas-api.md) |
| 2.8.10 | [cublas<t>trttp()](./chs/using-the-cublas-api.md) | [cublas<t>trttp()](./eng/using-the-cublas-api.md) |
| 2.8.11 | [cublas<t>gemmEx()](./chs/using-the-cublas-api.md) | [cublas<t>gemmEx()](./eng/using-the-cublas-api.md) |
| 2.8.12 | [cublasGemmEx()](./chs/using-the-cublas-api.md) | [cublasGemmEx()](./eng/using-the-cublas-api.md) |
| 2.8.13 | [cublasGemmBatchedEx()](./chs/using-the-cublas-api.md) | [cublasGemmBatchedEx()](./eng/using-the-cublas-api.md) |
| 2.8.14 | [cublasGemmStridedBatchedEx()](./chs/using-the-cublas-api.md) | [cublasGemmStridedBatchedEx()](./eng/using-the-cublas-api.md) |
| 2.8.15 | [cublasGemmGroupedBatchedEx()](./chs/using-the-cublas-api.md) | [cublasGemmGroupedBatchedEx()](./eng/using-the-cublas-api.md) |
| 2.8.16 | [cublasCsyrkEx()](./chs/using-the-cublas-api.md) | [cublasCsyrkEx()](./eng/using-the-cublas-api.md) |
| 2.8.17 | [cublasCsyrk3mEx()](./chs/using-the-cublas-api.md) | [cublasCsyrk3mEx()](./eng/using-the-cublas-api.md) |
| 2.8.18 | [cublasCherkEx()](./chs/using-the-cublas-api.md) | [cublasCherkEx()](./eng/using-the-cublas-api.md) |
| 2.8.19 | [cublasCherk3mEx()](./chs/using-the-cublas-api.md) | [cublasCherk3mEx()](./eng/using-the-cublas-api.md) |
| 2.8.20 | [cublasNrm2Ex()](./chs/using-the-cublas-api.md) | [cublasNrm2Ex()](./eng/using-the-cublas-api.md) |
| 2.8.21 | [cublasAxpyEx()](./chs/using-the-cublas-api.md) | [cublasAxpyEx()](./eng/using-the-cublas-api.md) |
| 2.8.22 | [cublasDotEx()](./chs/using-the-cublas-api.md) | [cublasDotEx()](./eng/using-the-cublas-api.md) |
| 2.8.23 | [cublasRotEx()](./chs/using-the-cublas-api.md) | [cublasRotEx()](./eng/using-the-cublas-api.md) |
| 2.8.24 | [cublasScalEx()](./chs/using-the-cublas-api.md) | [cublasScalEx()](./eng/using-the-cublas-api.md) |

---

## 翻译状态 / Translation Status

| 状态 Status | 数量 Count |
|-------------|------------|
| ✅ 已完成 / Completed | 157 |
| ⏳ 未转换 / Not converted | 0 |
| **总计 Total** | **157** |

---

## 版权声明 / Copyright Notice

本翻译仅供学习研究使用，原文档版权归 NVIDIA Corporation 所有。

This translation is for study and research purposes only. Original documentation copyright NVIDIA Corporation.
