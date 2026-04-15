# Using the cuBLAS API

## 使用 cuBLAS API

**来源 / Source:** NVIDIA cuBLAS Library Documentation - Using the cuBLAS API

---

## 双语目录对照 / Bilingual Table of Contents

| 章节号 | 中文 Chinese | 英文 English |
|--------|--------------|--------------|
| 2 | [Using the cuBLAS API](./chs/ch02.md) | [Using the cuBLAS API](./eng/ch02.md) |
| 2 | [Using the cuBLAS API](./chs/using-the-cublas-api.md) | [Using the cuBLAS API](./eng/using-the-cublas-api.md) |
| 2.1 | [General Description](./chs/general-description.md) | [General Description](./eng/general-description.md) |
| 2.1.1 | [错误状态](./chs/error-status.md) | [Error Status](./eng/error-status.md) |
| 2.1.3 | [线程安全性](./chs/thread-safety.md) | [Thread Safety](./eng/thread-safety.md) |
| 2.1.5 | [标量参数（Scalar Parameters）](./chs/scalar-parameters.md) | [Scalar Parameters](./eng/scalar-parameters.md) |
| 2.1.6 | [流并行性](./chs/parallelism-with-streams.md) | [Parallelism with Streams](./eng/parallelism-with-streams.md) |
| 2.1.7 | [Batching Kernels](./chs/batching-kernels.md) | [Batching Kernels](./eng/batching-kernels.md) |
| 2.1.8 | [Cache Configuration](./chs/cache-configuration.md) | [Cache Configuration](./eng/cache-configuration.md) |
| 2.1.9 | [静态库支持](./chs/static-library-support.md) | [Static Library Support](./eng/static-library-support.md) |
| 2.1.10 | [GEMM 算法数值行为](./chs/gemm-algorithms-numerical-behavior.md) | [GEMM Algorithms Numerical Behavior](./eng/gemm-algorithms-numerical-behavior.md) |
| 2.1.11 | [Tensor Core 使用说明](./chs/tensor-core-usage.md) | [Tensor Core Usage](./eng/tensor-core-usage.md) |
| 2.1.12 | [CUDA Graphs 支持](./chs/cuda-graphs-support.md) | [CUDA Graphs Support](./eng/cuda-graphs-support.md) |
| 2.1.13 | [64位整数接口](./chs/bit-integer-interface.md) | [64-bit Integer Interface](./eng/bit-integer-interface.md) |
| 2.2 | [cuBLAS 数据类型参考](./chs/cublas-datatypes-reference.md) | [cuBLAS Datatypes Reference](./eng/cublas-datatypes-reference.md) |
| 2.2.1 | [cublasHandle_t](./chs/cublashandle-t.md) | [cublasHandle_t](./eng/cublashandle-t.md) |
| 2.2.2 | [cublasStatus_t](./chs/cublasstatus-t.md) | [cublasStatus_t](./eng/cublasstatus-t.md) |
| 2.2.3 | [cublasOperation_t](./chs/cublasoperation-t.md) | [cublasOperation_t](./eng/cublasoperation-t.md) |
| 2.2.4 | [cublasFillMode_t](./chs/cublasfillmode-t.md) | [cublasFillMode_t](./eng/cublasfillmode-t.md) |
| 2.2.5 | [cublasDiagType_t](./chs/cublasdiagtype-t.md) | [cublasDiagType_t](./eng/cublasdiagtype-t.md) |
| 2.2.6 | [cublasSideMode_t](./chs/cublassidemode-t.md) | [cublasSideMode_t](./eng/cublassidemode-t.md) |
| 2.2.7 | [cublasPointerMode_t](./chs/cublaspointermode-t.md) | [cublasPointerMode_t](./eng/cublaspointermode-t.md) |
| 2.2.8 | [cublasAtomicsMode_t](./chs/cublasatomicsmode-t.md) | [cublasAtomicsMode_t](./eng/cublasatomicsmode-t.md) |
| 2.2.9 | [cublasGemmAlgo_t](./chs/cublasgemmalgo-t.md) | [cublasGemmAlgo_t](./eng/cublasgemmalgo-t.md) |
| 2.2.10 | [cublasMath_t](./chs/cublasmath-t.md) | [cublasMath_t](./eng/cublasmath-t.md) |
| 2.2.11 | [cublasComputeType_t](./chs/cublascomputetype-t.md) | [cublasComputeType_t](./eng/cublascomputetype-t.md) |
| 2.2.12 | [cublasEmulationStrategy_t](./chs/cublasemulationstrategy-t.md) | [cublasEmulationStrategy_t](./eng/cublasemulationstrategy-t.md) |
| 2.3 | [CUDA 数据类型参考](./chs/cuda-datatypes-reference.md) | [CUDA Datatypes Reference](./eng/cuda-datatypes-reference.md) |
| 2.3.1 | [cudaDataType_t](./chs/cudadatatype-t.md) | [cudaDataType_t](./eng/cudadatatype-t.md) |
| 2.3.2 | [cudaEmulationStrategy_t](./chs/cudaemulationstrategy-t.md) | [cudaEmulationStrategy_t](./eng/cudaemulationstrategy-t.md) |
| 2.3.3 | [cudaEmulationMantissaControl_t](./chs/cudaemulationmantissacontrol-t.md) | [cudaEmulationMantissaControl_t](./eng/cudaemulationmantissacontrol-t.md) |
| 2.3.4 | [cudaEmulationSpecialValuesSupport_t](./chs/cudaemulationspecialvaluessupport-t.md) | [cudaEmulationSpecialValuesSupport_t](./eng/cudaemulationspecialvaluessupport-t.md) |
| 2.3.5 | [libraryPropertyType_t](./chs/librarypropertytype-t.md) | [libraryPropertyType_t](./eng/librarypropertytype-t.md) |
| 2.4 | [cuBLAS 辅助函数参考](./chs/cublas-helper-function-reference.md) | [cuBLAS Helper Function Reference](./eng/cublas-helper-function-reference.md) |
| 2.4.1 | [cublasCreate()](./chs/cublascreate.md) | [cublasCreate()](./eng/cublascreate.md) |
| 2.4.2 | [cublasDestroy()](./chs/cublasdestroy.md) | [cublasDestroy()](./eng/cublasdestroy.md) |
| 2.4.3 | [cublasGetVersion()](./chs/cublasgetversion.md) | [cublasGetVersion()](./eng/cublasgetversion.md) |
| 2.4.4 | [cublasGetProperty()](./chs/cublasgetproperty.md) | [cublasGetProperty()](./eng/cublasgetproperty.md) |
| 2.4.5 | [cublasGetStatusName()](./chs/cublasgetstatusname.md) | [cublasGetStatusName()](./eng/cublasgetstatusname.md) |
| 2.4.6 | [cublasGetStatusString()](./chs/cublasgetstatusstring.md) | [cublasGetStatusString()](./eng/cublasgetstatusstring.md) |
| 2.4.7 | [cublasSetStream()](./chs/cublassetstream.md) | [cublasSetStream()](./eng/cublassetstream.md) |
| 2.4.8 | [cublasSetWorkspace()](./chs/cublassetworkspace.md) | [cublasSetWorkspace()](./eng/cublassetworkspace.md) |
| 2.4.9 | [cublasGetStream()](./chs/cublasgetstream.md) | [cublasGetStream()](./eng/cublasgetstream.md) |
| 2.4.10 | [cublasGetPointerMode()](./chs/cublasgetpointermode.md) | [cublasGetPointerMode()](./eng/cublasgetpointermode.md) |
| 2.4.11 | [cublasSetPointerMode()](./chs/cublassetpointermode.md) | [cublasSetPointerMode()](./eng/cublassetpointermode.md) |
| 2.4.12 | [cublasSetVector()](./chs/cublassetvector.md) | [cublasSetVector()](./eng/cublassetvector.md) |
| 2.4.13 | [cublasGetVector()](./chs/cublasgetvector.md) | [cublasGetVector()](./eng/cublasgetvector.md) |
| 2.4.14 | [cublasSetMatrix()](./chs/cublassetmatrix.md) | [cublasSetMatrix()](./eng/cublassetmatrix.md) |
| 2.4.15 | [cublasGetMatrix()](./chs/cublasgetmatrix.md) | [cublasGetMatrix()](./eng/cublasgetmatrix.md) |
| 2.4.16 | [cublasSetVectorAsync()](./chs/cublassetvectorasync.md) | [cublasSetVectorAsync()](./eng/cublassetvectorasync.md) |
| 2.4.17 | [cublasGetVectorAsync()](./chs/cublasgetvectorasync.md) | [cublasGetVectorAsync()](./eng/cublasgetvectorasync.md) |
| 2.4.18 | [cublasSetMatrixAsync()](./chs/cublassetmatrixasync.md) | [cublasSetMatrixAsync()](./eng/cublassetmatrixasync.md) |
| 2.4.19 | [cublasGetMatrixAsync()](./chs/cublasgetmatrixasync.md) | [cublasGetMatrixAsync()](./eng/cublasgetmatrixasync.md) |
| 2.4.20 | [cublasSetAtomicsMode()](./chs/cublassetatomicsmode.md) | [cublasSetAtomicsMode()](./eng/cublassetatomicsmode.md) |
| 2.4.21 | [cublasGetAtomicsMode()](./chs/cublasgetatomicsmode.md) | [cublasGetAtomicsMode()](./eng/cublasgetatomicsmode.md) |
| 2.4.22 | [cublasSetMathMode()](./chs/cublassetmathmode.md) | [cublasSetMathMode()](./eng/cublassetmathmode.md) |
| 2.4.23 | [cublasGetMathMode()](./chs/cublasgetmathmode.md) | [cublasGetMathMode()](./eng/cublasgetmathmode.md) |
| 2.4.24 | [cublasSetSmCountTarget()](./chs/cublassetsmcounttarget.md) | [cublasSetSmCountTarget()](./eng/cublassetsmcounttarget.md) |
| 2.4.25 | [cublasGetSmCountTarget()](./chs/cublasgetsmcounttarget.md) | [cublasGetSmCountTarget()](./eng/cublasgetsmcounttarget.md) |
| 2.4.26 | [cublasSetEmulationStrategy()](./chs/cublassetemulationstrategy.md) | [cublasSetEmulationStrategy()](./eng/cublassetemulationstrategy.md) |
| 2.4.27 | [cublasGetEmulationStrategy()](./chs/cublasgetemulationstrategy.md) | [cublasGetEmulationStrategy()](./eng/cublasgetemulationstrategy.md) |
| 2.4.28 | [cublasGetEmulationSpecialValuesSupport()](./chs/cublasgetemulationspecialvaluessupport.md) | [cublasGetEmulationSpecialValuesSupport()](./eng/cublasgetemulationspecialvaluessupport.md) |
| 2.4.29 | [cublasSetEmulationSpecialValuesSupport()](./chs/cublassetemulationspecialvaluessupport.md) | [cublasSetEmulationSpecialValuesSupport()](./eng/cublassetemulationspecialvaluessupport.md) |
| 2.4.30 | [cublasGetFixedPointEmulationMantissaControl()](./chs/cublasgetfixedpointemulationmantissacontrol.md) | [cublasGetFixedPointEmulationMantissaControl()](./eng/cublasgetfixedpointemulationmantissacontrol.md) |
| 2.4.31 | [cublasSetFixedPointEmulationMantissaControl()](./chs/cublassetfixedpointemulationmantissacontrol.md) | [cublasSetFixedPointEmulationMantissaControl()](./eng/cublassetfixedpointemulationmantissacontrol.md) |
| 2.4.32 | [cublasGetFixedPointEmulationMaxMantissaBitCount()](./chs/cublasgetfixedpointemulationmaxmantissabitcount.md) | [cublasGetFixedPointEmulationMaxMantissaBitCount()](./eng/cublasgetfixedpointemulationmaxmantissabitcount.md) |
| 2.4.33 | [cublasSetFixedPointEmulationMaxMantissaBitCount()](./chs/cublassetfixedpointemulationmaxmantissabitcount.md) | [cublasSetFixedPointEmulationMaxMantissaBitCount()](./eng/cublassetfixedpointemulationmaxmantissabitcount.md) |
| 2.4.34 | [cublasGetFixedPointEmulationMantissaBitOffset()](./chs/cublasgetfixedpointemulationmantissabitoffset.md) | [cublasGetFixedPointEmulationMantissaBitOffset()](./eng/cublasgetfixedpointemulationmantissabitoffset.md) |
| 2.4.35 | [cublasSetFixedPointEmulationMantissaBitOffset()](./chs/cublassetfixedpointemulationmantissabitoffset.md) | [cublasSetFixedPointEmulationMantissaBitOffset()](./eng/cublassetfixedpointemulationmantissabitoffset.md) |
| 2.4.36 | [cublasGetFixedPointEmulationMantissaBitCountPointer()](./chs/cublasgetfixedpointemulationmantissabitcountpointer.md) | [cublasGetFixedPointEmulationMantissaBitCountPointer()](./eng/cublasgetfixedpointemulationmantissabitcountpointer.md) |
| 2.4.37 | [cublasSetFixedPointEmulationMantissaBitCountPointer()](./chs/cublassetfixedpointemulationmantissabitcountpointer.md) | [cublasSetFixedPointEmulationMantissaBitCountPointer()](./eng/cublassetfixedpointemulationmantissabitcountpointer.md) |
| 2.4.38 | [cublasLoggerConfigure()](./chs/cublasloggerconfigure.md) | [cublasLoggerConfigure()](./eng/cublasloggerconfigure.md) |
| 2.4.39 | [cublasGetLoggerCallback()](./chs/cublasgetloggercallback.md) | [cublasGetLoggerCallback()](./eng/cublasgetloggercallback.md) |
| 2.4.40 | [cublasSetLoggerCallback()](./chs/cublassetloggercallback.md) | [cublasSetLoggerCallback()](./eng/cublassetloggercallback.md) |
| 2.5 | [cuBLAS Level-1 Function Reference](./chs/cublas-level-1-function-reference.md) | [cuBLAS Level-1 Function Reference](./eng/cublas-level-1-function-reference.md) |
| 2.5.1 | [cublasI<t>amax()](./chs/cublasi-t-amax.md) | [cublasI<t>amax()](./eng/cublasi-t-amax.md) |
| 2.5.2 | [cublasI<t>amin()](./chs/cublasi-t-amin.md) | [cublasI<t>amin()](./eng/cublasi-t-amin.md) |
| 2.5.3 | [cublas<t>asum()](./chs/cublas-t-asum.md) | [cublas<t>asum()](./eng/cublas-t-asum.md) |
| 2.5.4 | [cublas<t>axpy()](./chs/cublas-t-axpy.md) | [cublas<t>axpy()](./eng/cublas-t-axpy.md) |
| 2.5.5 | [cublas<t>copy()](./chs/cublas-t-copy.md) | [cublas<t>copy()](./eng/cublas-t-copy.md) |
| 2.5.6 | [cublas<t>dot()](./chs/cublas-t-dot.md) | [cublas<t>dot()](./eng/cublas-t-dot.md) |
| 2.5.7 | [cublas<t>nrm2()](./chs/cublas-t-nrm2.md) | [cublas<t>nrm2()](./eng/cublas-t-nrm2.md) |
| 2.5.8 | [cublas<t>rot()](./chs/cublas-t-rot.md) | [cublas<t>rot()](./eng/cublas-t-rot.md) |
| 2.5.9 | [cublas<t>rotg()](./chs/cublas-t-rotg.md) | [cublas<t>rotg()](./eng/cublas-t-rotg.md) |
| 2.5.10 | [cublas<t>rotm()](./chs/cublas-t-rotm.md) | [cublas<t>rotm()](./eng/cublas-t-rotm.md) |
| 2.5.11 | [cublas<t>rotmg()](./chs/cublas-t-rotmg.md) | [cublas<t>rotmg()](./eng/cublas-t-rotmg.md) |
| 2.5.12 | [cublas<t>scal()](./chs/cublas-t-scal.md) | [cublas<t>scal()](./eng/cublas-t-scal.md) |
| 2.5.13 | [cublas<t>swap()](./chs/cublas-t-swap.md) | [cublas<t>swap()](./eng/cublas-t-swap.md) |
| 2.6 | [cuBLAS Level-2 函数参考指南](./chs/cublas-level-2-function-reference.md) | [cuBLAS Level-2 Function Reference](./eng/cublas-level-2-function-reference.md) |
| 2.6.1 | [cublas<t>gbmv()](./chs/cublas-t-gbmv.md) | [cublas<t>gbmv()](./eng/cublas-t-gbmv.md) |
| 2.6.2 | [cublas<t>gemv()](./chs/cublas-t-gemv.md) | [cublas<t>gemv()](./eng/cublas-t-gemv.md) |
| 2.6.3 | [cublas<t>ger()](./chs/cublas-t-ger.md) | [cublas<t>ger()](./eng/cublas-t-ger.md) |
| 2.6.4 | [cublas<t>sbmv()](./chs/cublas-t-sbmv.md) | [cublas<t>sbmv()](./eng/cublas-t-sbmv.md) |
| 2.6.5 | [cublas<t>spmv()](./chs/cublas-t-spmv.md) | [cublas<t>spmv()](./eng/cublas-t-spmv.md) |
| 2.6.6 | [cublas<t>spr()](./chs/cublas-t-spr.md) | [cublas<t>spr()](./eng/cublas-t-spr.md) |
| 2.6.7 | [cublas<t>spr2()](./chs/cublas-t-spr2.md) | [cublas<t>spr2()](./eng/cublas-t-spr2.md) |
| 2.6.8 | [cublas<t>symv()](./chs/cublas-t-symv.md) | [cublas<t>symv()](./eng/cublas-t-symv.md) |
| 2.6.9 | [cublas<t>syr()](./chs/cublas-t-syr.md) | [cublas<t>syr()](./eng/cublas-t-syr.md) |
| 2.6.10 | [cublas<t>syr2()](./chs/cublas-t-syr2.md) | [cublas<t>syr2()](./eng/cublas-t-syr2.md) |
| 2.6.11 | [cublas<t>tbmv()](./chs/cublas-t-tbmv.md) | [cublas<t>tbmv()](./eng/cublas-t-tbmv.md) |
| 2.6.12 | [cublas<t>tbsv()](./chs/cublas-t-tbsv.md) | [cublas<t>tbsv()](./eng/cublas-t-tbsv.md) |
| 2.6.13 | [cublas<t>tpmv()](./chs/cublas-t-tpmv.md) | [cublas<t>tpmv()](./eng/cublas-t-tpmv.md) |
| 2.6.14 | [cublas<t>tpsv()](./chs/cublas-t-tpsv.md) | [cublas<t>tpsv()](./eng/cublas-t-tpsv.md) |
| 2.6.15 | [cublas<t>trmv()](./chs/cublas-t-trmv.md) | [cublas<t>trmv()](./eng/cublas-t-trmv.md) |
| 2.6.16 | [cublas<t>trsv()](./chs/cublas-t-trsv.md) | [cublas<t>trsv()](./eng/cublas-t-trsv.md) |
| 2.6.17 | [cublas<t>hemv()](./chs/cublas-t-hemv.md) | [cublas<t>hemv()](./eng/cublas-t-hemv.md) |
| 2.6.18 | [cublas<t>hbmv()](./chs/cublas-t-hbmv.md) | [cublas<t>hbmv()](./eng/cublas-t-hbmv.md) |
| 2.6.19 | [cublas<t>hpmv()](./chs/cublas-t-hpmv.md) | [cublas<t>hpmv()](./eng/cublas-t-hpmv.md) |
| 2.6.20 | [cublas<t>her()](./chs/cublas-t-her.md) | [cublas<t>her()](./eng/cublas-t-her.md) |
| 2.6.21 | [cublas<t>her2()](./chs/cublas-t-her2.md) | [cublas<t>her2()](./eng/cublas-t-her2.md) |
| 2.6.22 | [cublas<t>hpr()](./chs/cublas-t-hpr.md) | [cublas<t>hpr()](./eng/cublas-t-hpr.md) |
| 2.6.23 | [cublas<t>hpr2()](./chs/cublas-t-hpr2.md) | [cublas<t>hpr2()](./eng/cublas-t-hpr2.md) |
| 2.6.24 | [cublas<t>gemvBatched()](./chs/cublas-t-gemvbatched.md) | [cublas<t>gemvBatched()](./eng/cublas-t-gemvbatched.md) |
| 2.6.25 | [cublas<t>gemvStridedBatched()](./chs/cublas-t-gemvstridedbatched.md) | [cublas<t>gemvStridedBatched()](./eng/cublas-t-gemvstridedbatched.md) |
| 2.7 | [cuBLAS Level-3 函数参考](./chs/cublas-level-3-function-reference.md) | [cuBLAS Level-3 Function Reference](./eng/cublas-level-3-function-reference.md) |
| 2.7.1 | [cublas<t>gemm()](./chs/cublas-t-gemm.md) | [cublas<t>gemm()](./eng/cublas-t-gemm.md) |
| 2.7.2 | [cublas<t>gemm3m()](./chs/cublas-t-gemm3m.md) | [cublas<t>gemm3m()](./eng/cublas-t-gemm3m.md) |
| 2.7.3 | [cublas<t>gemmBatched()](./chs/cublas-t-gemmbatched.md) | [cublas<t>gemmBatched()](./eng/cublas-t-gemmbatched.md) |
| 2.7.4 | [cublas<t>gemmStridedBatched()](./chs/cublas-t-gemmstridedbatched.md) | [cublas<t>gemmStridedBatched()](./eng/cublas-t-gemmstridedbatched.md) |
| 2.7.5 | [cublas<t>gemmGroupedBatched()](./chs/cublas-t-gemmgroupedbatched.md) | [cublas<t>gemmGroupedBatched()](./eng/cublas-t-gemmgroupedbatched.md) |
| 2.7.6 | [cublas<t>symm()](./chs/cublas-t-symm.md) | [cublas<t>symm()](./eng/cublas-t-symm.md) |
| 2.7.7 | [cublas<t>syrk()](./chs/cublas-t-syrk.md) | [cublas<t>syrk()](./eng/cublas-t-syrk.md) |
| 2.7.8 | [cublas<t>syr2k()](./chs/cublas-t-syr2k.md) | [cublas<t>syr2k()](./eng/cublas-t-syr2k.md) |
| 2.7.9 | [cublas<t>syrkx()](./chs/cublas-t-syrkx.md) | [cublas<t>syrkx()](./eng/cublas-t-syrkx.md) |
| 2.7.10 | [cublas<t>trmm()](./chs/cublas-t-trmm.md) | [cublas<t>trmm()](./eng/cublas-t-trmm.md) |
| 2.7.11 | [cublas<t>trsm()](./chs/cublas-t-trsm.md) | [cublas<t>trsm()](./eng/cublas-t-trsm.md) |
| 2.7.12 | [cublas<t>trsmBatched()](./chs/cublas-t-trsmbatched.md) | [cublas<t>trsmBatched()](./eng/cublas-t-trsmbatched.md) |
| 2.7.13 | [cublas<t>hemm()](./chs/cublas-t-hemm.md) | [cublas<t>hemm()](./eng/cublas-t-hemm.md) |
| 2.7.14 | [cublas<t>herk()](./chs/cublas-t-herk.md) | [cublas<t>herk()](./eng/cublas-t-herk.md) |
| 2.7.15 | [cublas<t>her2k()](./chs/cublas-t-her2k.md) | [cublas<t>her2k()](./eng/cublas-t-her2k.md) |
| 2.7.16 | [cublas<t>herkx()](./chs/cublas-t-herkx.md) | [cublas<t>herkx()](./eng/cublas-t-herkx.md) |
| 2.8.1 | [cublas<t>geam()](./chs/cublas-t-geam.md) | [cublas<t>geam()](./eng/cublas-t-geam.md) |
| 2.8.2 | [cublas<t>dgmm()](./chs/cublas-t-dgmm.md) | [cublas<t>dgmm()](./eng/cublas-t-dgmm.md) |
| 2.8.3 | [cublas<t>getrfBatched()](./chs/cublas-t-getrfbatched.md) | [cublas<t>getrfBatched()](./eng/cublas-t-getrfbatched.md) |
| 2.8.4 | [cublas<t>getrsBatched()](./chs/cublas-t-getrsbatched.md) | [cublas<t>getrsBatched()](./eng/cublas-t-getrsbatched.md) |
| 2.8.5 | [cublas<t>getriBatched()](./chs/cublas-t-getribatched.md) | [cublas<t>getriBatched()](./eng/cublas-t-getribatched.md) |
| 2.8.6 | [cublas<t>matinvBatched()](./chs/cublas-t-matinvbatched.md) | [cublas<t>matinvBatched()](./eng/cublas-t-matinvbatched.md) |
| 2.8.7 | [cublas<t>geqrfBatched()](./chs/cublas-t-geqrfbatched.md) | [cublas<t>geqrfBatched()](./eng/cublas-t-geqrfbatched.md) |
| 2.8.8 | [cublas<t>gelsBatched()](./chs/cublas-t-gelsbatched.md) | [cublas<t>gelsBatched()](./eng/cublas-t-gelsbatched.md) |
| 2.8.9 | [cublas<t>tpttr()](./chs/cublas-t-tpttr.md) | [cublas<t>tpttr()](./eng/cublas-t-tpttr.md) |
| 2.8.10 | [cublas<t>trttp()](./chs/cublas-t-trttp.md) | [cublas<t>trttp()](./eng/cublas-t-trttp.md) |
| 2.8.11 | [cublas<t>gemmEx()](./chs/cublas-t-gemmex.md) | [cublas<t>gemmEx()](./eng/cublas-t-gemmex.md) |
| 2.8.12 | [cublasGemmEx()](./chs/cublasgemmex.md) | [cublasGemmEx()](./eng/cublasgemmex.md) |
| 2.8.13 | [cublasGemmBatchedEx()](./chs/cublasgemmbatchedex.md) | [cublasGemmBatchedEx()](./eng/cublasgemmbatchedex.md) |
| 2.8.14 | [cublasGemmStridedBatchedEx()](./chs/cublasgemmstridedbatchedex.md) | [cublasGemmStridedBatchedEx()](./eng/cublasgemmstridedbatchedex.md) |
| 2.8.15 | [cublasGemmGroupedBatchedEx()](./chs/cublasgemmgroupedbatchedex.md) | [cublasGemmGroupedBatchedEx()](./eng/cublasgemmgroupedbatchedex.md) |
| 2.8.16 | [cublasCsyrkEx()](./chs/cublascsyrkex.md) | [cublasCsyrkEx()](./eng/cublascsyrkex.md) |
| 2.8.17 | [cublasCsyrk3mEx()](./chs/cublascsyrk3mex.md) | [cublasCsyrk3mEx()](./eng/cublascsyrk3mex.md) |
| 2.8.18 | [cublasCherkEx()](./chs/cublascherkex.md) | [cublasCherkEx()](./eng/cublascherkex.md) |
| 2.8.19 | [cublasCherk3mEx()](./chs/cublascherk3mex.md) | [cublasCherk3mEx()](./eng/cublascherk3mex.md) |
| 2.8.20 | [cublasNrm2Ex()](./chs/cublasnrm2ex.md) | [cublasNrm2Ex()](./eng/cublasnrm2ex.md) |
| 2.8.21 | [cublasAxpyEx()](./chs/cublasaxpyex.md) | [cublasAxpyEx()](./eng/cublasaxpyex.md) |
| 2.8.22 | [cublasDotEx()](./chs/cublasdotex.md) | [cublasDotEx()](./eng/cublasdotex.md) |
| 2.8.23 | [cublasRotEx()](./chs/cublasrotex.md) | [cublasRotEx()](./eng/cublasrotex.md) |
| 2.8.24 | [cublasScalEx()](./chs/cublasscalex.md) | [cublasScalEx()](./eng/cublasscalex.md) |
| 3.1 | [General Description](./chs/id16.md) | [General Description](./eng/id16.md) |
| 3.1.1 | [问题规模限制](./chs/problem-size-limitations.md) | [Problem Size Limitations](./eng/problem-size-limitations.md) |
| 3.1.2 | [启发式缓存 (Heuristics Cache)](./chs/heuristics-cache.md) | [Heuristics Cache](./eng/heuristics-cache.md) |
| 3.1.4 | [窄精度数据类型用法](./chs/narrow-precision-data-types-usage.md) | [Narrow Precision Data Types Usage](./eng/narrow-precision-data-types-usage.md) |
| 3.1.4.1 | [FP8数据类型的逐张量缩放](./chs/tensorwide-scaling-for-fp8-data-types.md) | [Tensorwide Scaling For FP8 Data Types](./eng/tensorwide-scaling-for-fp8-data-types.md) |
| 3.1.4.2 | [实验性：FP8 数据类型的每批次张量范围缩放](./chs/experimental-per-batch-tensorwide-scaling-for-fp8-data-types.md) | [Experimental: Per-batch Tensorwide Scaling For FP8 Data Types](./eng/experimental-per-batch-tensorwide-scaling-for-fp8-data-types.md) |
| 3.1.4.3 | [FP8数据类型的外部向量缩放](./chs/outer-vector-scaling-for-fp8-data-types.md) | [Outer Vector Scaling for FP8 Data Types](./eng/outer-vector-scaling-for-fp8-data-types.md) |
| 3.1.4.4 | [FP8 和 FP4 数据类型的 16/32 元素 1D 块缩放](./chs/element-1d-block-scaling-for-fp8-and-fp4-data-types.md) | [16/32-Element 1D Block Scaling for FP8 and FP4 Data Types](./eng/element-1d-block-scaling-for-fp8-and-fp4-data-types.md) |
| 3.1.4.4.1 | [一维块量化](./chs/d-block-quantization.md) | [1D Block Quantization](./eng/d-block-quantization.md) |
| 3.1.4.4.2 | [1D Block Scaling Factors Layout](./chs/d-block-scaling-factors-layout.md) | [1D Block Scaling Factors Layout](./eng/d-block-scaling-factors-layout.md) |
| 3.1.4.5 | [128-element 1D and 128x128 2D Block Scaling For FP8 Data Types](./chs/element-1d-and-128x128-2d-block-scaling-for-fp8-data-types.md) | [128-element 1D and 128x128 2D Block Scaling For FP8 Data Types](./eng/element-1d-and-128x128-2d-block-scaling-for-fp8-data-types.md) |
| 3.1.4.5.1 | [缩放因子布局](./chs/scaling-factors-layouts.md) | [Scaling factors layouts](./eng/scaling-factors-layouts.md) |
| 3.1.5 | [禁用 CPU 指令](./chs/disabling-cpu-instructions.md) | [Disabling CPU Instructions](./eng/disabling-cpu-instructions.md) |
| 3.3.4 | [cublasLtLoggerCallback_t](./chs/cublasltloggercallback-t.md) | [cublasLtLoggerCallback_t](./eng/cublasltloggercallback-t.md) |
| 3.4.11 | [cublasLtLoggerSetCallback()](./chs/cublasltloggersetcallback.md) | [cublasLtLoggerSetCallback()](./eng/cublasltloggersetcallback.md) |
| 4.1 | [概述](./chs/id102.md) | [General description](./eng/id102.md) |
| 4.1.1 | [瓦片化设计方案](./chs/tiling-design-approach.md) | [Tiling design approach](./eng/tiling-design-approach.md) |
| 4.1.2 | [Hybrid CPU-GPU computation](./chs/hybrid-cpu-gpu-computation.md) | [Hybrid CPU-GPU computation](./eng/hybrid-cpu-gpu-computation.md) |
| 4.1.3 | [结果可重现性](./chs/id103.md) | [Results reproducibility](./eng/id103.md) |
| 6.1 | [Error Status](./chs/id106.md) | [Error Status](./eng/id106.md) |
| 6.2 | [初始化和关闭（Initialization and Shutdown）](./chs/initialization-and-shutdown.md) | [Initialization and Shutdown](./eng/initialization-and-shutdown.md) |
| 6.3 | [线程安全](./chs/id107.md) | [Thread Safety](./eng/id107.md) |
| 6.4 | [内存管理](./chs/memory-management.md) | [Memory Management](./eng/memory-management.md) |
| 6.5 | [标量参数（Scalar Parameters）](./chs/id108.md) | [Scalar Parameters](./eng/id108.md) |
| 6.6 | [辅助函数](./chs/helper-functions.md) | [Helper Functions](./eng/helper-functions.md) |
| 6.7 | [Level-1,2,3 函数](./chs/level-1-2-3-functions.md) | [Level-1,2,3 Functions](./eng/level-1-2-3-functions.md) |
| 6.9 | [示例](./chs/examples.md) | [Examples](./eng/examples.md) |
| 7 | [cuBLAS Fortran 接口](./chs/cublas-fortran-bindings.md) | [cuBLAS Fortran Bindings](./eng/cublas-fortran-bindings.md) |
| 10.1 | [声明](./chs/notice.md) | [Notice](./eng/notice.md) |

---

## 翻译状态 / Translation Status

| 状态 Status | 数量 Count |
|-------------|------------|
| ✅ 已完成 / Completed | 184 |
| ⏳ 未转换 / Not converted | 0 |
| **总计 Total** | **184** |

---

## 版权声明 / Copyright Notice

本翻译仅供学习研究使用，原文档版权归 NVIDIA Corporation 所有。

This translation is for study and research purposes only. Original documentation copyright NVIDIA Corporation.
