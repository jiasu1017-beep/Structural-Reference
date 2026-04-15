# Using the cuBLAS API

## 使用 cuBLAS API

**来源 / Source:** NVIDIA cuBLAS Library Documentation - Using the cuBLAS API

---

## 双语目录对照 / Bilingual Table of Contents

| 章节号 | 中文 Chinese | 英文 English |
|--------|--------------|--------------|
| 2 | [ch02.md](./chs/ch02.md) | [ch02.md](./eng/ch02.md) |
| 2 | [using-the-cublas-api.md](./chs/using-the-cublas-api.md) | [using-the-cublas-api.md](./eng/using-the-cublas-api.md) |
| 2.1 | [general-description.md](./chs/general-description.md) | [general-description.md](./eng/general-description.md) |
| 2.1.1 | [error-status.md](./chs/error-status.md) | [error-status.md](./eng/error-status.md) |
| 2.1.3 | [thread-safety.md](./chs/thread-safety.md) | [thread-safety.md](./eng/thread-safety.md) |
| 2.1.5 | [scalar-parameters.md](./chs/scalar-parameters.md) | [scalar-parameters.md](./eng/scalar-parameters.md) |
| 2.1.6 | [parallelism-with-streams.md](./chs/parallelism-with-streams.md) | [parallelism-with-streams.md](./eng/parallelism-with-streams.md) |
| 2.1.7 | [batching-kernels.md](./chs/batching-kernels.md) | [batching-kernels.md](./eng/batching-kernels.md) |
| 2.1.8 | [cache-configuration.md](./chs/cache-configuration.md) | [cache-configuration.md](./eng/cache-configuration.md) |
| 2.1.9 | [static-library-support.md](./chs/static-library-support.md) | [static-library-support.md](./eng/static-library-support.md) |
| 2.1.10 | [gemm-algorithms-numerical-behavior.md](./chs/gemm-algorithms-numerical-behavior.md) | [gemm-algorithms-numerical-behavior.md](./eng/gemm-algorithms-numerical-behavior.md) |
| 2.1.11 | [tensor-core-usage.md](./chs/tensor-core-usage.md) | [tensor-core-usage.md](./eng/tensor-core-usage.md) |
| 2.1.12 | [cuda-graphs-support.md](./chs/cuda-graphs-support.md) | [cuda-graphs-support.md](./eng/cuda-graphs-support.md) |
| 2.1.13 | [bit-integer-interface.md](./chs/bit-integer-interface.md) | [bit-integer-interface.md](./eng/bit-integer-interface.md) |
| 2.2 | [cublas-datatypes-reference.md](./chs/cublas-datatypes-reference.md) | [cublas-datatypes-reference.md](./eng/cublas-datatypes-reference.md) |
| 2.2.1 | [cublashandle-t.md](./chs/cublashandle-t.md) | [cublashandle-t.md](./eng/cublashandle-t.md) |
| 2.2.2 | [cublasstatus-t.md](./chs/cublasstatus-t.md) | [cublasstatus-t.md](./eng/cublasstatus-t.md) |
| 2.2.3 | [cublasoperation-t.md](./chs/cublasoperation-t.md) | [cublasoperation-t.md](./eng/cublasoperation-t.md) |
| 2.2.4 | [cublasfillmode-t.md](./chs/cublasfillmode-t.md) | [cublasfillmode-t.md](./eng/cublasfillmode-t.md) |
| 2.2.5 | [cublasdiagtype-t.md](./chs/cublasdiagtype-t.md) | [cublasdiagtype-t.md](./eng/cublasdiagtype-t.md) |
| 2.2.6 | [cublassidemode-t.md](./chs/cublassidemode-t.md) | [cublassidemode-t.md](./eng/cublassidemode-t.md) |
| 2.2.7 | [cublaspointermode-t.md](./chs/cublaspointermode-t.md) | [cublaspointermode-t.md](./eng/cublaspointermode-t.md) |
| 2.2.8 | [cublasatomicsmode-t.md](./chs/cublasatomicsmode-t.md) | [cublasatomicsmode-t.md](./eng/cublasatomicsmode-t.md) |
| 2.2.9 | [cublasgemmalgo-t.md](./chs/cublasgemmalgo-t.md) | [cublasgemmalgo-t.md](./eng/cublasgemmalgo-t.md) |
| 2.2.10 | [cublasmath-t.md](./chs/cublasmath-t.md) | [cublasmath-t.md](./eng/cublasmath-t.md) |
| 2.2.11 | [cublascomputetype-t.md](./chs/cublascomputetype-t.md) | [cublascomputetype-t.md](./eng/cublascomputetype-t.md) |
| 2.2.12 | [cublasemulationstrategy-t.md](./chs/cublasemulationstrategy-t.md) | [cublasemulationstrategy-t.md](./eng/cublasemulationstrategy-t.md) |
| 2.3 | [cuda-datatypes-reference.md](./chs/cuda-datatypes-reference.md) | [cuda-datatypes-reference.md](./eng/cuda-datatypes-reference.md) |
| 2.3.1 | [cudadatatype-t.md](./chs/cudadatatype-t.md) | [cudadatatype-t.md](./eng/cudadatatype-t.md) |
| 2.3.2 | [cudaemulationstrategy-t.md](./chs/cudaemulationstrategy-t.md) | [cudaemulationstrategy-t.md](./eng/cudaemulationstrategy-t.md) |
| 2.3.3 | [cudaemulationmantissacontrol-t.md](./chs/cudaemulationmantissacontrol-t.md) | [cudaemulationmantissacontrol-t.md](./eng/cudaemulationmantissacontrol-t.md) |
| 2.3.4 | [cudaemulationspecialvaluessupport-t.md](./chs/cudaemulationspecialvaluessupport-t.md) | [cudaemulationspecialvaluessupport-t.md](./eng/cudaemulationspecialvaluessupport-t.md) |
| 2.3.5 | [librarypropertytype-t.md](./chs/librarypropertytype-t.md) | [librarypropertytype-t.md](./eng/librarypropertytype-t.md) |
| 2.4 | [cublas-helper-function-reference.md](./chs/cublas-helper-function-reference.md) | [cublas-helper-function-reference.md](./eng/cublas-helper-function-reference.md) |
| 2.4.1 | [cublascreate.md](./chs/cublascreate.md) | [cublascreate.md](./eng/cublascreate.md) |
| 2.4.2 | [cublasdestroy.md](./chs/cublasdestroy.md) | [cublasdestroy.md](./eng/cublasdestroy.md) |
| 2.4.3 | [cublasgetversion.md](./chs/cublasgetversion.md) | [cublasgetversion.md](./eng/cublasgetversion.md) |
| 2.4.4 | [cublasgetproperty.md](./chs/cublasgetproperty.md) | [cublasgetproperty.md](./eng/cublasgetproperty.md) |
| 2.4.5 | [cublasgetstatusname.md](./chs/cublasgetstatusname.md) | [cublasgetstatusname.md](./eng/cublasgetstatusname.md) |
| 2.4.6 | [cublasgetstatusstring.md](./chs/cublasgetstatusstring.md) | [cublasgetstatusstring.md](./eng/cublasgetstatusstring.md) |
| 2.4.7 | [cublassetstream.md](./chs/cublassetstream.md) | [cublassetstream.md](./eng/cublassetstream.md) |
| 2.4.8 | [cublassetworkspace.md](./chs/cublassetworkspace.md) | [cublassetworkspace.md](./eng/cublassetworkspace.md) |
| 2.4.9 | [cublasgetstream.md](./chs/cublasgetstream.md) | [cublasgetstream.md](./eng/cublasgetstream.md) |
| 2.4.10 | [cublasgetpointermode.md](./chs/cublasgetpointermode.md) | [cublasgetpointermode.md](./eng/cublasgetpointermode.md) |
| 2.4.11 | [cublassetpointermode.md](./chs/cublassetpointermode.md) | [cublassetpointermode.md](./eng/cublassetpointermode.md) |
| 2.4.12 | [cublassetvector.md](./chs/cublassetvector.md) | [cublassetvector.md](./eng/cublassetvector.md) |
| 2.4.13 | [cublasgetvector.md](./chs/cublasgetvector.md) | [cublasgetvector.md](./eng/cublasgetvector.md) |
| 2.4.14 | [cublassetmatrix.md](./chs/cublassetmatrix.md) | [cublassetmatrix.md](./eng/cublassetmatrix.md) |
| 2.4.15 | [cublasgetmatrix.md](./chs/cublasgetmatrix.md) | [cublasgetmatrix.md](./eng/cublasgetmatrix.md) |
| 2.4.16 | [cublassetvectorasync.md](./chs/cublassetvectorasync.md) | [cublassetvectorasync.md](./eng/cublassetvectorasync.md) |
| 2.4.17 | [cublasgetvectorasync.md](./chs/cublasgetvectorasync.md) | [cublasgetvectorasync.md](./eng/cublasgetvectorasync.md) |
| 2.4.18 | [cublassetmatrixasync.md](./chs/cublassetmatrixasync.md) | [cublassetmatrixasync.md](./eng/cublassetmatrixasync.md) |
| 2.4.19 | [cublasgetmatrixasync.md](./chs/cublasgetmatrixasync.md) | [cublasgetmatrixasync.md](./eng/cublasgetmatrixasync.md) |
| 2.4.20 | [cublassetatomicsmode.md](./chs/cublassetatomicsmode.md) | [cublassetatomicsmode.md](./eng/cublassetatomicsmode.md) |
| 2.4.21 | [cublasgetatomicsmode.md](./chs/cublasgetatomicsmode.md) | [cublasgetatomicsmode.md](./eng/cublasgetatomicsmode.md) |
| 2.4.22 | [cublassetmathmode.md](./chs/cublassetmathmode.md) | [cublassetmathmode.md](./eng/cublassetmathmode.md) |
| 2.4.23 | [cublasgetmathmode.md](./chs/cublasgetmathmode.md) | [cublasgetmathmode.md](./eng/cublasgetmathmode.md) |
| 2.4.24 | [cublassetsmcounttarget.md](./chs/cublassetsmcounttarget.md) | [cublassetsmcounttarget.md](./eng/cublassetsmcounttarget.md) |
| 2.4.25 | [cublasgetsmcounttarget.md](./chs/cublasgetsmcounttarget.md) | [cublasgetsmcounttarget.md](./eng/cublasgetsmcounttarget.md) |
| 2.4.26 | [cublassetemulationstrategy.md](./chs/cublassetemulationstrategy.md) | [cublassetemulationstrategy.md](./eng/cublassetemulationstrategy.md) |
| 2.4.27 | [cublasgetemulationstrategy.md](./chs/cublasgetemulationstrategy.md) | [cublasgetemulationstrategy.md](./eng/cublasgetemulationstrategy.md) |
| 2.4.28 | [cublasgetemulationspecialvaluessupport.md](./chs/cublasgetemulationspecialvaluessupport.md) | [cublasgetemulationspecialvaluessupport.md](./eng/cublasgetemulationspecialvaluessupport.md) |
| 2.4.29 | [cublassetemulationspecialvaluessupport.md](./chs/cublassetemulationspecialvaluessupport.md) | [cublassetemulationspecialvaluessupport.md](./eng/cublassetemulationspecialvaluessupport.md) |
| 2.4.30 | [cublasgetfixedpointemulationmantissacontrol.md](./chs/cublasgetfixedpointemulationmantissacontrol.md) | [cublasgetfixedpointemulationmantissacontrol.md](./eng/cublasgetfixedpointemulationmantissacontrol.md) |
| 2.4.31 | [cublassetfixedpointemulationmantissacontrol.md](./chs/cublassetfixedpointemulationmantissacontrol.md) | [cublassetfixedpointemulationmantissacontrol.md](./eng/cublassetfixedpointemulationmantissacontrol.md) |
| 2.4.32 | [cublasgetfixedpointemulationmaxmantissabitcount.md](./chs/cublasgetfixedpointemulationmaxmantissabitcount.md) | [cublasgetfixedpointemulationmaxmantissabitcount.md](./eng/cublasgetfixedpointemulationmaxmantissabitcount.md) |
| 2.4.33 | [cublassetfixedpointemulationmaxmantissabitcount.md](./chs/cublassetfixedpointemulationmaxmantissabitcount.md) | [cublassetfixedpointemulationmaxmantissabitcount.md](./eng/cublassetfixedpointemulationmaxmantissabitcount.md) |
| 2.4.34 | [cublasgetfixedpointemulationmantissabitoffset.md](./chs/cublasgetfixedpointemulationmantissabitoffset.md) | [cublasgetfixedpointemulationmantissabitoffset.md](./eng/cublasgetfixedpointemulationmantissabitoffset.md) |
| 2.4.35 | [cublassetfixedpointemulationmantissabitoffset.md](./chs/cublassetfixedpointemulationmantissabitoffset.md) | [cublassetfixedpointemulationmantissabitoffset.md](./eng/cublassetfixedpointemulationmantissabitoffset.md) |
| 2.4.36 | [cublasgetfixedpointemulationmantissabitcountpointer.md](./chs/cublasgetfixedpointemulationmantissabitcountpointer.md) | [cublasgetfixedpointemulationmantissabitcountpointer.md](./eng/cublasgetfixedpointemulationmantissabitcountpointer.md) |
| 2.4.37 | [cublassetfixedpointemulationmantissabitcountpointer.md](./chs/cublassetfixedpointemulationmantissabitcountpointer.md) | [cublassetfixedpointemulationmantissabitcountpointer.md](./eng/cublassetfixedpointemulationmantissabitcountpointer.md) |
| 2.4.38 | [cublasloggerconfigure.md](./chs/cublasloggerconfigure.md) | [cublasloggerconfigure.md](./eng/cublasloggerconfigure.md) |
| 2.4.39 | [cublasgetloggercallback.md](./chs/cublasgetloggercallback.md) | [cublasgetloggercallback.md](./eng/cublasgetloggercallback.md) |
| 2.4.40 | [cublassetloggercallback.md](./chs/cublassetloggercallback.md) | [cublassetloggercallback.md](./eng/cublassetloggercallback.md) |
| 2.5 | [cublas-level-1-function-reference.md](./chs/cublas-level-1-function-reference.md) | [cublas-level-1-function-reference.md](./eng/cublas-level-1-function-reference.md) |
| 2.5.1 | [cublasi-t-amax.md](./chs/cublasi-t-amax.md) | [cublasi-t-amax.md](./eng/cublasi-t-amax.md) |
| 2.5.2 | [cublasi-t-amin.md](./chs/cublasi-t-amin.md) | [cublasi-t-amin.md](./eng/cublasi-t-amin.md) |
| 2.5.3 | [cublas-t-asum.md](./chs/cublas-t-asum.md) | [cublas-t-asum.md](./eng/cublas-t-asum.md) |
| 2.5.4 | [cublas-t-axpy.md](./chs/cublas-t-axpy.md) | [cublas-t-axpy.md](./eng/cublas-t-axpy.md) |
| 2.5.5 | [cublas-t-copy.md](./chs/cublas-t-copy.md) | [cublas-t-copy.md](./eng/cublas-t-copy.md) |
| 2.5.6 | [cublas-t-dot.md](./chs/cublas-t-dot.md) | [cublas-t-dot.md](./eng/cublas-t-dot.md) |
| 2.5.7 | [cublas-t-nrm2.md](./chs/cublas-t-nrm2.md) | [cublas-t-nrm2.md](./eng/cublas-t-nrm2.md) |
| 2.5.8 | [cublas-t-rot.md](./chs/cublas-t-rot.md) | [cublas-t-rot.md](./eng/cublas-t-rot.md) |
| 2.5.9 | [cublas-t-rotg.md](./chs/cublas-t-rotg.md) | [cublas-t-rotg.md](./eng/cublas-t-rotg.md) |
| 2.5.10 | [cublas-t-rotm.md](./chs/cublas-t-rotm.md) | [cublas-t-rotm.md](./eng/cublas-t-rotm.md) |
| 2.5.11 | [cublas-t-rotmg.md](./chs/cublas-t-rotmg.md) | [cublas-t-rotmg.md](./eng/cublas-t-rotmg.md) |
| 2.5.12 | [cublas-t-scal.md](./chs/cublas-t-scal.md) | [cublas-t-scal.md](./eng/cublas-t-scal.md) |
| 2.5.13 | [cublas-t-swap.md](./chs/cublas-t-swap.md) | [cublas-t-swap.md](./eng/cublas-t-swap.md) |
| 2.6 | [cublas-level-2-function-reference.md](./chs/cublas-level-2-function-reference.md) | [cublas-level-2-function-reference.md](./eng/cublas-level-2-function-reference.md) |
| 2.6.1 | [cublas-t-gbmv.md](./chs/cublas-t-gbmv.md) | [cublas-t-gbmv.md](./eng/cublas-t-gbmv.md) |
| 2.6.2 | [cublas-t-gemv.md](./chs/cublas-t-gemv.md) | [cublas-t-gemv.md](./eng/cublas-t-gemv.md) |
| 2.6.3 | [cublas-t-ger.md](./chs/cublas-t-ger.md) | [cublas-t-ger.md](./eng/cublas-t-ger.md) |
| 2.6.4 | [cublas-t-sbmv.md](./chs/cublas-t-sbmv.md) | [cublas-t-sbmv.md](./eng/cublas-t-sbmv.md) |
| 2.6.5 | [cublas-t-spmv.md](./chs/cublas-t-spmv.md) | [cublas-t-spmv.md](./eng/cublas-t-spmv.md) |
| 2.6.6 | [cublas-t-spr.md](./chs/cublas-t-spr.md) | [cublas-t-spr.md](./eng/cublas-t-spr.md) |
| 2.6.7 | [cublas-t-spr2.md](./chs/cublas-t-spr2.md) | [cublas-t-spr2.md](./eng/cublas-t-spr2.md) |
| 2.6.8 | [cublas-t-symv.md](./chs/cublas-t-symv.md) | [cublas-t-symv.md](./eng/cublas-t-symv.md) |
| 2.6.9 | [cublas-t-syr.md](./chs/cublas-t-syr.md) | [cublas-t-syr.md](./eng/cublas-t-syr.md) |
| 2.6.10 | [cublas-t-syr2.md](./chs/cublas-t-syr2.md) | [cublas-t-syr2.md](./eng/cublas-t-syr2.md) |
| 2.6.11 | [cublas-t-tbmv.md](./chs/cublas-t-tbmv.md) | [cublas-t-tbmv.md](./eng/cublas-t-tbmv.md) |
| 2.6.12 | [cublas-t-tbsv.md](./chs/cublas-t-tbsv.md) | [cublas-t-tbsv.md](./eng/cublas-t-tbsv.md) |
| 2.6.13 | [cublas-t-tpmv.md](./chs/cublas-t-tpmv.md) | [cublas-t-tpmv.md](./eng/cublas-t-tpmv.md) |
| 2.6.14 | [cublas-t-tpsv.md](./chs/cublas-t-tpsv.md) | [cublas-t-tpsv.md](./eng/cublas-t-tpsv.md) |
| 2.6.15 | [cublas-t-trmv.md](./chs/cublas-t-trmv.md) | [cublas-t-trmv.md](./eng/cublas-t-trmv.md) |
| 2.6.16 | [cublas-t-trsv.md](./chs/cublas-t-trsv.md) | [cublas-t-trsv.md](./eng/cublas-t-trsv.md) |
| 2.6.17 | [cublas-t-hemv.md](./chs/cublas-t-hemv.md) | [cublas-t-hemv.md](./eng/cublas-t-hemv.md) |
| 2.6.18 | [cublas-t-hbmv.md](./chs/cublas-t-hbmv.md) | [cublas-t-hbmv.md](./eng/cublas-t-hbmv.md) |
| 2.6.19 | [cublas-t-hpmv.md](./chs/cublas-t-hpmv.md) | [cublas-t-hpmv.md](./eng/cublas-t-hpmv.md) |
| 2.6.20 | [cublas-t-her.md](./chs/cublas-t-her.md) | [cublas-t-her.md](./eng/cublas-t-her.md) |
| 2.6.21 | [cublas-t-her2.md](./chs/cublas-t-her2.md) | [cublas-t-her2.md](./eng/cublas-t-her2.md) |
| 2.6.22 | [cublas-t-hpr.md](./chs/cublas-t-hpr.md) | [cublas-t-hpr.md](./eng/cublas-t-hpr.md) |
| 2.6.23 | [cublas-t-hpr2.md](./chs/cublas-t-hpr2.md) | [cublas-t-hpr2.md](./eng/cublas-t-hpr2.md) |
| 2.6.24 | [cublas-t-gemvbatched.md](./chs/cublas-t-gemvbatched.md) | [cublas-t-gemvbatched.md](./eng/cublas-t-gemvbatched.md) |
| 2.6.25 | [cublas-t-gemvstridedbatched.md](./chs/cublas-t-gemvstridedbatched.md) | [cublas-t-gemvstridedbatched.md](./eng/cublas-t-gemvstridedbatched.md) |
| 2.7 | [cublas-level-3-function-reference.md](./chs/cublas-level-3-function-reference.md) | [cublas-level-3-function-reference.md](./eng/cublas-level-3-function-reference.md) |
| 2.7.1 | [cublas-t-gemm.md](./chs/cublas-t-gemm.md) | [cublas-t-gemm.md](./eng/cublas-t-gemm.md) |
| 2.7.2 | [cublas-t-gemm3m.md](./chs/cublas-t-gemm3m.md) | [cublas-t-gemm3m.md](./eng/cublas-t-gemm3m.md) |
| 2.7.3 | [cublas-t-gemmbatched.md](./chs/cublas-t-gemmbatched.md) | [cublas-t-gemmbatched.md](./eng/cublas-t-gemmbatched.md) |
| 2.7.4 | [cublas-t-gemmstridedbatched.md](./chs/cublas-t-gemmstridedbatched.md) | [cublas-t-gemmstridedbatched.md](./eng/cublas-t-gemmstridedbatched.md) |
| 2.7.5 | [cublas-t-gemmgroupedbatched.md](./chs/cublas-t-gemmgroupedbatched.md) | [cublas-t-gemmgroupedbatched.md](./eng/cublas-t-gemmgroupedbatched.md) |
| 2.7.6 | [cublas-t-symm.md](./chs/cublas-t-symm.md) | [cublas-t-symm.md](./eng/cublas-t-symm.md) |
| 2.7.7 | [cublas-t-syrk.md](./chs/cublas-t-syrk.md) | [cublas-t-syrk.md](./eng/cublas-t-syrk.md) |
| 2.7.8 | [cublas-t-syr2k.md](./chs/cublas-t-syr2k.md) | [cublas-t-syr2k.md](./eng/cublas-t-syr2k.md) |
| 2.7.9 | [cublas-t-syrkx.md](./chs/cublas-t-syrkx.md) | [cublas-t-syrkx.md](./eng/cublas-t-syrkx.md) |
| 2.7.10 | [cublas-t-trmm.md](./chs/cublas-t-trmm.md) | [cublas-t-trmm.md](./eng/cublas-t-trmm.md) |
| 2.7.11 | [cublas-t-trsm.md](./chs/cublas-t-trsm.md) | [cublas-t-trsm.md](./eng/cublas-t-trsm.md) |
| 2.7.12 | [cublas-t-trsmbatched.md](./chs/cublas-t-trsmbatched.md) | [cublas-t-trsmbatched.md](./eng/cublas-t-trsmbatched.md) |
| 2.7.13 | [cublas-t-hemm.md](./chs/cublas-t-hemm.md) | [cublas-t-hemm.md](./eng/cublas-t-hemm.md) |
| 2.7.14 | [cublas-t-herk.md](./chs/cublas-t-herk.md) | [cublas-t-herk.md](./eng/cublas-t-herk.md) |
| 2.7.15 | [cublas-t-her2k.md](./chs/cublas-t-her2k.md) | [cublas-t-her2k.md](./eng/cublas-t-her2k.md) |
| 2.7.16 | [cublas-t-herkx.md](./chs/cublas-t-herkx.md) | [cublas-t-herkx.md](./eng/cublas-t-herkx.md) |
| 2.8.1 | [cublas-t-geam.md](./chs/cublas-t-geam.md) | [cublas-t-geam.md](./eng/cublas-t-geam.md) |
| 2.8.2 | [cublas-t-dgmm.md](./chs/cublas-t-dgmm.md) | [cublas-t-dgmm.md](./eng/cublas-t-dgmm.md) |
| 2.8.3 | [cublas-t-getrfbatched.md](./chs/cublas-t-getrfbatched.md) | [cublas-t-getrfbatched.md](./eng/cublas-t-getrfbatched.md) |
| 2.8.4 | [cublas-t-getrsbatched.md](./chs/cublas-t-getrsbatched.md) | [cublas-t-getrsbatched.md](./eng/cublas-t-getrsbatched.md) |
| 2.8.5 | [cublas-t-getribatched.md](./chs/cublas-t-getribatched.md) | [cublas-t-getribatched.md](./eng/cublas-t-getribatched.md) |
| 2.8.6 | [cublas-t-matinvbatched.md](./chs/cublas-t-matinvbatched.md) | [cublas-t-matinvbatched.md](./eng/cublas-t-matinvbatched.md) |
| 2.8.7 | [cublas-t-geqrfbatched.md](./chs/cublas-t-geqrfbatched.md) | [cublas-t-geqrfbatched.md](./eng/cublas-t-geqrfbatched.md) |
| 2.8.8 | [cublas-t-gelsbatched.md](./chs/cublas-t-gelsbatched.md) | [cublas-t-gelsbatched.md](./eng/cublas-t-gelsbatched.md) |
| 2.8.9 | [cublas-t-tpttr.md](./chs/cublas-t-tpttr.md) | [cublas-t-tpttr.md](./eng/cublas-t-tpttr.md) |
| 2.8.10 | [cublas-t-trttp.md](./chs/cublas-t-trttp.md) | [cublas-t-trttp.md](./eng/cublas-t-trttp.md) |
| 2.8.11 | [cublas-t-gemmex.md](./chs/cublas-t-gemmex.md) | [cublas-t-gemmex.md](./eng/cublas-t-gemmex.md) |
| 2.8.12 | [cublasgemmex.md](./chs/cublasgemmex.md) | [cublasgemmex.md](./eng/cublasgemmex.md) |
| 2.8.13 | [cublasgemmbatchedex.md](./chs/cublasgemmbatchedex.md) | [cublasgemmbatchedex.md](./eng/cublasgemmbatchedex.md) |
| 2.8.14 | [cublasgemmstridedbatchedex.md](./chs/cublasgemmstridedbatchedex.md) | [cublasgemmstridedbatchedex.md](./eng/cublasgemmstridedbatchedex.md) |
| 2.8.15 | [cublasgemmgroupedbatchedex.md](./chs/cublasgemmgroupedbatchedex.md) | [cublasgemmgroupedbatchedex.md](./eng/cublasgemmgroupedbatchedex.md) |
| 2.8.16 | [cublascsyrkex.md](./chs/cublascsyrkex.md) | [cublascsyrkex.md](./eng/cublascsyrkex.md) |
| 2.8.17 | [cublascsyrk3mex.md](./chs/cublascsyrk3mex.md) | [cublascsyrk3mex.md](./eng/cublascsyrk3mex.md) |
| 2.8.18 | [cublascherkex.md](./chs/cublascherkex.md) | [cublascherkex.md](./eng/cublascherkex.md) |
| 2.8.19 | [cublascherk3mex.md](./chs/cublascherk3mex.md) | [cublascherk3mex.md](./eng/cublascherk3mex.md) |
| 2.8.20 | [cublasnrm2ex.md](./chs/cublasnrm2ex.md) | [cublasnrm2ex.md](./eng/cublasnrm2ex.md) |
| 2.8.21 | [cublasaxpyex.md](./chs/cublasaxpyex.md) | [cublasaxpyex.md](./eng/cublasaxpyex.md) |
| 2.8.22 | [cublasdotex.md](./chs/cublasdotex.md) | [cublasdotex.md](./eng/cublasdotex.md) |
| 2.8.23 | [cublasrotex.md](./chs/cublasrotex.md) | [cublasrotex.md](./eng/cublasrotex.md) |
| 2.8.24 | [cublasscalex.md](./chs/cublasscalex.md) | [cublasscalex.md](./eng/cublasscalex.md) |
| 3.1 | [id16.md](./chs/id16.md) | [id16.md](./eng/id16.md) |
| 3.1.1 | [problem-size-limitations.md](./chs/problem-size-limitations.md) | [problem-size-limitations.md](./eng/problem-size-limitations.md) |
| 3.1.2 | [heuristics-cache.md](./chs/heuristics-cache.md) | [heuristics-cache.md](./eng/heuristics-cache.md) |
| 3.1.4 | [narrow-precision-data-types-usage.md](./chs/narrow-precision-data-types-usage.md) | [narrow-precision-data-types-usage.md](./eng/narrow-precision-data-types-usage.md) |
| 3.1.4.1 | [tensorwide-scaling-for-fp8-data-types.md](./chs/tensorwide-scaling-for-fp8-data-types.md) | [tensorwide-scaling-for-fp8-data-types.md](./eng/tensorwide-scaling-for-fp8-data-types.md) |
| 3.1.4.2 | [experimental-per-batch-tensorwide-scaling-for-fp8-data-types.md](./chs/experimental-per-batch-tensorwide-scaling-for-fp8-data-types.md) | [experimental-per-batch-tensorwide-scaling-for-fp8-data-types.md](./eng/experimental-per-batch-tensorwide-scaling-for-fp8-data-types.md) |
| 3.1.4.3 | [outer-vector-scaling-for-fp8-data-types.md](./chs/outer-vector-scaling-for-fp8-data-types.md) | [outer-vector-scaling-for-fp8-data-types.md](./eng/outer-vector-scaling-for-fp8-data-types.md) |
| 3.1.4.4 | [element-1d-block-scaling-for-fp8-and-fp4-data-types.md](./chs/element-1d-block-scaling-for-fp8-and-fp4-data-types.md) | [element-1d-block-scaling-for-fp8-and-fp4-data-types.md](./eng/element-1d-block-scaling-for-fp8-and-fp4-data-types.md) |
| 3.1.4.4.1 | [d-block-quantization.md](./chs/d-block-quantization.md) | [d-block-quantization.md](./eng/d-block-quantization.md) |
| 3.1.4.4.2 | [d-block-scaling-factors-layout.md](./chs/d-block-scaling-factors-layout.md) | [d-block-scaling-factors-layout.md](./eng/d-block-scaling-factors-layout.md) |
| 3.1.4.5 | [element-1d-and-128x128-2d-block-scaling-for-fp8-data-types.md](./chs/element-1d-and-128x128-2d-block-scaling-for-fp8-data-types.md) | [element-1d-and-128x128-2d-block-scaling-for-fp8-data-types.md](./eng/element-1d-and-128x128-2d-block-scaling-for-fp8-data-types.md) |
| 3.1.4.5.1 | [scaling-factors-layouts.md](./chs/scaling-factors-layouts.md) | [scaling-factors-layouts.md](./eng/scaling-factors-layouts.md) |
| 3.1.5 | [disabling-cpu-instructions.md](./chs/disabling-cpu-instructions.md) | [disabling-cpu-instructions.md](./eng/disabling-cpu-instructions.md) |
| 3.3.4 | [cublasltloggercallback-t.md](./chs/cublasltloggercallback-t.md) | [cublasltloggercallback-t.md](./eng/cublasltloggercallback-t.md) |
| 3.4.11 | [cublasltloggersetcallback.md](./chs/cublasltloggersetcallback.md) | [cublasltloggersetcallback.md](./eng/cublasltloggersetcallback.md) |
| 4.1 | [id102.md](./chs/id102.md) | [id102.md](./eng/id102.md) |
| 4.1.1 | [tiling-design-approach.md](./chs/tiling-design-approach.md) | [tiling-design-approach.md](./eng/tiling-design-approach.md) |
| 4.1.2 | [hybrid-cpu-gpu-computation.md](./chs/hybrid-cpu-gpu-computation.md) | [hybrid-cpu-gpu-computation.md](./eng/hybrid-cpu-gpu-computation.md) |
| 4.1.3 | [id103.md](./chs/id103.md) | [id103.md](./eng/id103.md) |
| 6.1 | [id106.md](./chs/id106.md) | [id106.md](./eng/id106.md) |
| 6.2 | [initialization-and-shutdown.md](./chs/initialization-and-shutdown.md) | [initialization-and-shutdown.md](./eng/initialization-and-shutdown.md) |
| 6.3 | [id107.md](./chs/id107.md) | [id107.md](./eng/id107.md) |
| 6.4 | [memory-management.md](./chs/memory-management.md) | [memory-management.md](./eng/memory-management.md) |
| 6.5 | [id108.md](./chs/id108.md) | [id108.md](./eng/id108.md) |
| 6.6 | [helper-functions.md](./chs/helper-functions.md) | [helper-functions.md](./eng/helper-functions.md) |
| 6.7 | [level-1-2-3-functions.md](./chs/level-1-2-3-functions.md) | [level-1-2-3-functions.md](./eng/level-1-2-3-functions.md) |
| 6.9 | [examples.md](./chs/examples.md) | [examples.md](./eng/examples.md) |
| 7 | [cublas-fortran-bindings.md](./chs/cublas-fortran-bindings.md) | [cublas-fortran-bindings.md](./eng/cublas-fortran-bindings.md) |
| 10.1 | [notice.md](./chs/notice.md) | [notice.md](./eng/notice.md) |

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
