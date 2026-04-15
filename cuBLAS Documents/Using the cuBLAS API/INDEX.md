# Using the cuBLAS API

## 使用 cuBLAS API

**来源 / Source:** NVIDIA cuBLAS Library Documentation - Using the cuBLAS API

---

## 双语目录对照 / Bilingual Table of Contents

| 序号 | 文件 File | 中文 Chinese | 英文 English |
|------|-----------|--------------|--------------|
| 1 | batching-kernels.md | [batching-kernels.md](./chs/batching-kernels.md) | [batching-kernels.md](./eng/batching-kernels.md) |
| 2 | bit-integer-interface.md | [bit-integer-interface.md](./chs/bit-integer-interface.md) | [bit-integer-interface.md](./eng/bit-integer-interface.md) |
| 3 | cache-configuration.md | [cache-configuration.md](./chs/cache-configuration.md) | [cache-configuration.md](./eng/cache-configuration.md) |
| 4 | ch02.md | [ch02.md](./chs/ch02.md) | [ch02.md](./eng/ch02.md) |
| 5 | cublas-datatypes-reference.md | [cublas-datatypes-reference.md](./chs/cublas-datatypes-reference.md) | [cublas-datatypes-reference.md](./eng/cublas-datatypes-reference.md) |
| 6 | cublas-fortran-bindings.md | [cublas-fortran-bindings.md](./chs/cublas-fortran-bindings.md) | [cublas-fortran-bindings.md](./eng/cublas-fortran-bindings.md) |
| 7 | cublas-helper-function-reference.md | [cublas-helper-function-reference.md](./chs/cublas-helper-function-reference.md) | [cublas-helper-function-reference.md](./eng/cublas-helper-function-reference.md) |
| 8 | cublas-level-1-function-reference.md | [cublas-level-1-function-reference.md](./chs/cublas-level-1-function-reference.md) | [cublas-level-1-function-reference.md](./eng/cublas-level-1-function-reference.md) |
| 9 | cublas-level-2-function-reference.md | [cublas-level-2-function-reference.md](./chs/cublas-level-2-function-reference.md) | [cublas-level-2-function-reference.md](./eng/cublas-level-2-function-reference.md) |
| 10 | cublas-level-3-function-reference.md | [cublas-level-3-function-reference.md](./chs/cublas-level-3-function-reference.md) | [cublas-level-3-function-reference.md](./eng/cublas-level-3-function-reference.md) |
| 11 | cublas-t-asum.md | [cublas-t-asum.md](./chs/cublas-t-asum.md) | [cublas-t-asum.md](./eng/cublas-t-asum.md) |
| 12 | cublas-t-axpy.md | [cublas-t-axpy.md](./chs/cublas-t-axpy.md) | [cublas-t-axpy.md](./eng/cublas-t-axpy.md) |
| 13 | cublas-t-copy.md | [cublas-t-copy.md](./chs/cublas-t-copy.md) | [cublas-t-copy.md](./eng/cublas-t-copy.md) |
| 14 | cublas-t-dgmm.md | [cublas-t-dgmm.md](./chs/cublas-t-dgmm.md) | [cublas-t-dgmm.md](./eng/cublas-t-dgmm.md) |
| 15 | cublas-t-dot.md | [cublas-t-dot.md](./chs/cublas-t-dot.md) | [cublas-t-dot.md](./eng/cublas-t-dot.md) |
| 16 | cublas-t-gbmv.md | [cublas-t-gbmv.md](./chs/cublas-t-gbmv.md) | [cublas-t-gbmv.md](./eng/cublas-t-gbmv.md) |
| 17 | cublas-t-geam.md | [cublas-t-geam.md](./chs/cublas-t-geam.md) | [cublas-t-geam.md](./eng/cublas-t-geam.md) |
| 18 | cublas-t-gelsbatched.md | [cublas-t-gelsbatched.md](./chs/cublas-t-gelsbatched.md) | [cublas-t-gelsbatched.md](./eng/cublas-t-gelsbatched.md) |
| 19 | cublas-t-gemm3m.md | [cublas-t-gemm3m.md](./chs/cublas-t-gemm3m.md) | [cublas-t-gemm3m.md](./eng/cublas-t-gemm3m.md) |
| 20 | cublas-t-gemm.md | [cublas-t-gemm.md](./chs/cublas-t-gemm.md) | [cublas-t-gemm.md](./eng/cublas-t-gemm.md) |
| 21 | cublas-t-gemmbatched.md | [cublas-t-gemmbatched.md](./chs/cublas-t-gemmbatched.md) | [cublas-t-gemmbatched.md](./eng/cublas-t-gemmbatched.md) |
| 22 | cublas-t-gemmex.md | [cublas-t-gemmex.md](./chs/cublas-t-gemmex.md) | [cublas-t-gemmex.md](./eng/cublas-t-gemmex.md) |
| 23 | cublas-t-gemmgroupedbatched.md | [cublas-t-gemmgroupedbatched.md](./chs/cublas-t-gemmgroupedbatched.md) | [cublas-t-gemmgroupedbatched.md](./eng/cublas-t-gemmgroupedbatched.md) |
| 24 | cublas-t-gemmstridedbatched.md | [cublas-t-gemmstridedbatched.md](./chs/cublas-t-gemmstridedbatched.md) | [cublas-t-gemmstridedbatched.md](./eng/cublas-t-gemmstridedbatched.md) |
| 25 | cublas-t-gemv.md | [cublas-t-gemv.md](./chs/cublas-t-gemv.md) | [cublas-t-gemv.md](./eng/cublas-t-gemv.md) |
| 26 | cublas-t-gemvbatched.md | [cublas-t-gemvbatched.md](./chs/cublas-t-gemvbatched.md) | [cublas-t-gemvbatched.md](./eng/cublas-t-gemvbatched.md) |
| 27 | cublas-t-gemvstridedbatched.md | [cublas-t-gemvstridedbatched.md](./chs/cublas-t-gemvstridedbatched.md) | [cublas-t-gemvstridedbatched.md](./eng/cublas-t-gemvstridedbatched.md) |
| 28 | cublas-t-geqrfbatched.md | [cublas-t-geqrfbatched.md](./chs/cublas-t-geqrfbatched.md) | [cublas-t-geqrfbatched.md](./eng/cublas-t-geqrfbatched.md) |
| 29 | cublas-t-ger.md | [cublas-t-ger.md](./chs/cublas-t-ger.md) | [cublas-t-ger.md](./eng/cublas-t-ger.md) |
| 30 | cublas-t-getrfbatched.md | [cublas-t-getrfbatched.md](./chs/cublas-t-getrfbatched.md) | [cublas-t-getrfbatched.md](./eng/cublas-t-getrfbatched.md) |
| 31 | cublas-t-getribatched.md | [cublas-t-getribatched.md](./chs/cublas-t-getribatched.md) | [cublas-t-getribatched.md](./eng/cublas-t-getribatched.md) |
| 32 | cublas-t-getrsbatched.md | [cublas-t-getrsbatched.md](./chs/cublas-t-getrsbatched.md) | [cublas-t-getrsbatched.md](./eng/cublas-t-getrsbatched.md) |
| 33 | cublas-t-hbmv.md | [cublas-t-hbmv.md](./chs/cublas-t-hbmv.md) | [cublas-t-hbmv.md](./eng/cublas-t-hbmv.md) |
| 34 | cublas-t-hemm.md | [cublas-t-hemm.md](./chs/cublas-t-hemm.md) | [cublas-t-hemm.md](./eng/cublas-t-hemm.md) |
| 35 | cublas-t-hemv.md | [cublas-t-hemv.md](./chs/cublas-t-hemv.md) | [cublas-t-hemv.md](./eng/cublas-t-hemv.md) |
| 36 | cublas-t-her2.md | [cublas-t-her2.md](./chs/cublas-t-her2.md) | [cublas-t-her2.md](./eng/cublas-t-her2.md) |
| 37 | cublas-t-her2k.md | [cublas-t-her2k.md](./chs/cublas-t-her2k.md) | [cublas-t-her2k.md](./eng/cublas-t-her2k.md) |
| 38 | cublas-t-her.md | [cublas-t-her.md](./chs/cublas-t-her.md) | [cublas-t-her.md](./eng/cublas-t-her.md) |
| 39 | cublas-t-herk.md | [cublas-t-herk.md](./chs/cublas-t-herk.md) | [cublas-t-herk.md](./eng/cublas-t-herk.md) |
| 40 | cublas-t-herkx.md | [cublas-t-herkx.md](./chs/cublas-t-herkx.md) | [cublas-t-herkx.md](./eng/cublas-t-herkx.md) |
| 41 | cublas-t-hpmv.md | [cublas-t-hpmv.md](./chs/cublas-t-hpmv.md) | [cublas-t-hpmv.md](./eng/cublas-t-hpmv.md) |
| 42 | cublas-t-hpr2.md | [cublas-t-hpr2.md](./chs/cublas-t-hpr2.md) | [cublas-t-hpr2.md](./eng/cublas-t-hpr2.md) |
| 43 | cublas-t-hpr.md | [cublas-t-hpr.md](./chs/cublas-t-hpr.md) | [cublas-t-hpr.md](./eng/cublas-t-hpr.md) |
| 44 | cublas-t-matinvbatched.md | [cublas-t-matinvbatched.md](./chs/cublas-t-matinvbatched.md) | [cublas-t-matinvbatched.md](./eng/cublas-t-matinvbatched.md) |
| 45 | cublas-t-nrm2.md | [cublas-t-nrm2.md](./chs/cublas-t-nrm2.md) | [cublas-t-nrm2.md](./eng/cublas-t-nrm2.md) |
| 46 | cublas-t-rot.md | [cublas-t-rot.md](./chs/cublas-t-rot.md) | [cublas-t-rot.md](./eng/cublas-t-rot.md) |
| 47 | cublas-t-rotg.md | [cublas-t-rotg.md](./chs/cublas-t-rotg.md) | [cublas-t-rotg.md](./eng/cublas-t-rotg.md) |
| 48 | cublas-t-rotm.md | [cublas-t-rotm.md](./chs/cublas-t-rotm.md) | [cublas-t-rotm.md](./eng/cublas-t-rotm.md) |
| 49 | cublas-t-rotmg.md | [cublas-t-rotmg.md](./chs/cublas-t-rotmg.md) | [cublas-t-rotmg.md](./eng/cublas-t-rotmg.md) |
| 50 | cublas-t-sbmv.md | [cublas-t-sbmv.md](./chs/cublas-t-sbmv.md) | [cublas-t-sbmv.md](./eng/cublas-t-sbmv.md) |
| 51 | cublas-t-scal.md | [cublas-t-scal.md](./chs/cublas-t-scal.md) | [cublas-t-scal.md](./eng/cublas-t-scal.md) |
| 52 | cublas-t-spmv.md | [cublas-t-spmv.md](./chs/cublas-t-spmv.md) | [cublas-t-spmv.md](./eng/cublas-t-spmv.md) |
| 53 | cublas-t-spr2.md | [cublas-t-spr2.md](./chs/cublas-t-spr2.md) | [cublas-t-spr2.md](./eng/cublas-t-spr2.md) |
| 54 | cublas-t-spr.md | [cublas-t-spr.md](./chs/cublas-t-spr.md) | [cublas-t-spr.md](./eng/cublas-t-spr.md) |
| 55 | cublas-t-swap.md | [cublas-t-swap.md](./chs/cublas-t-swap.md) | [cublas-t-swap.md](./eng/cublas-t-swap.md) |
| 56 | cublas-t-symm.md | [cublas-t-symm.md](./chs/cublas-t-symm.md) | [cublas-t-symm.md](./eng/cublas-t-symm.md) |
| 57 | cublas-t-symv.md | [cublas-t-symv.md](./chs/cublas-t-symv.md) | [cublas-t-symv.md](./eng/cublas-t-symv.md) |
| 58 | cublas-t-syr2.md | [cublas-t-syr2.md](./chs/cublas-t-syr2.md) | [cublas-t-syr2.md](./eng/cublas-t-syr2.md) |
| 59 | cublas-t-syr2k.md | [cublas-t-syr2k.md](./chs/cublas-t-syr2k.md) | [cublas-t-syr2k.md](./eng/cublas-t-syr2k.md) |
| 60 | cublas-t-syr.md | [cublas-t-syr.md](./chs/cublas-t-syr.md) | [cublas-t-syr.md](./eng/cublas-t-syr.md) |
| 61 | cublas-t-syrk.md | [cublas-t-syrk.md](./chs/cublas-t-syrk.md) | [cublas-t-syrk.md](./eng/cublas-t-syrk.md) |
| 62 | cublas-t-syrkx.md | [cublas-t-syrkx.md](./chs/cublas-t-syrkx.md) | [cublas-t-syrkx.md](./eng/cublas-t-syrkx.md) |
| 63 | cublas-t-tbmv.md | [cublas-t-tbmv.md](./chs/cublas-t-tbmv.md) | [cublas-t-tbmv.md](./eng/cublas-t-tbmv.md) |
| 64 | cublas-t-tbsv.md | [cublas-t-tbsv.md](./chs/cublas-t-tbsv.md) | [cublas-t-tbsv.md](./eng/cublas-t-tbsv.md) |
| 65 | cublas-t-tpmv.md | [cublas-t-tpmv.md](./chs/cublas-t-tpmv.md) | [cublas-t-tpmv.md](./eng/cublas-t-tpmv.md) |
| 66 | cublas-t-tpsv.md | [cublas-t-tpsv.md](./chs/cublas-t-tpsv.md) | [cublas-t-tpsv.md](./eng/cublas-t-tpsv.md) |
| 67 | cublas-t-tpttr.md | [cublas-t-tpttr.md](./chs/cublas-t-tpttr.md) | [cublas-t-tpttr.md](./eng/cublas-t-tpttr.md) |
| 68 | cublas-t-trmm.md | [cublas-t-trmm.md](./chs/cublas-t-trmm.md) | [cublas-t-trmm.md](./eng/cublas-t-trmm.md) |
| 69 | cublas-t-trmv.md | [cublas-t-trmv.md](./chs/cublas-t-trmv.md) | [cublas-t-trmv.md](./eng/cublas-t-trmv.md) |
| 70 | cublas-t-trsm.md | [cublas-t-trsm.md](./chs/cublas-t-trsm.md) | [cublas-t-trsm.md](./eng/cublas-t-trsm.md) |
| 71 | cublas-t-trsmbatched.md | [cublas-t-trsmbatched.md](./chs/cublas-t-trsmbatched.md) | [cublas-t-trsmbatched.md](./eng/cublas-t-trsmbatched.md) |
| 72 | cublas-t-trsv.md | [cublas-t-trsv.md](./chs/cublas-t-trsv.md) | [cublas-t-trsv.md](./eng/cublas-t-trsv.md) |
| 73 | cublas-t-trttp.md | [cublas-t-trttp.md](./chs/cublas-t-trttp.md) | [cublas-t-trttp.md](./eng/cublas-t-trttp.md) |
| 74 | cublasatomicsmode-t.md | [cublasatomicsmode-t.md](./chs/cublasatomicsmode-t.md) | [cublasatomicsmode-t.md](./eng/cublasatomicsmode-t.md) |
| 75 | cublasaxpyex.md | [cublasaxpyex.md](./chs/cublasaxpyex.md) | [cublasaxpyex.md](./eng/cublasaxpyex.md) |
| 76 | cublascherk3mex.md | [cublascherk3mex.md](./chs/cublascherk3mex.md) | [cublascherk3mex.md](./eng/cublascherk3mex.md) |
| 77 | cublascherkex.md | [cublascherkex.md](./chs/cublascherkex.md) | [cublascherkex.md](./eng/cublascherkex.md) |
| 78 | cublascomputetype-t.md | [cublascomputetype-t.md](./chs/cublascomputetype-t.md) | [cublascomputetype-t.md](./eng/cublascomputetype-t.md) |
| 79 | cublascreate.md | [cublascreate.md](./chs/cublascreate.md) | [cublascreate.md](./eng/cublascreate.md) |
| 80 | cublascsyrk3mex.md | [cublascsyrk3mex.md](./chs/cublascsyrk3mex.md) | [cublascsyrk3mex.md](./eng/cublascsyrk3mex.md) |
| 81 | cublascsyrkex.md | [cublascsyrkex.md](./chs/cublascsyrkex.md) | [cublascsyrkex.md](./eng/cublascsyrkex.md) |
| 82 | cublasdestroy.md | [cublasdestroy.md](./chs/cublasdestroy.md) | [cublasdestroy.md](./eng/cublasdestroy.md) |
| 83 | cublasdiagtype-t.md | [cublasdiagtype-t.md](./chs/cublasdiagtype-t.md) | [cublasdiagtype-t.md](./eng/cublasdiagtype-t.md) |
| 84 | cublasdotex.md | [cublasdotex.md](./chs/cublasdotex.md) | [cublasdotex.md](./eng/cublasdotex.md) |
| 85 | cublasemulationstrategy-t.md | [cublasemulationstrategy-t.md](./chs/cublasemulationstrategy-t.md) | [cublasemulationstrategy-t.md](./eng/cublasemulationstrategy-t.md) |
| 86 | cublasfillmode-t.md | [cublasfillmode-t.md](./chs/cublasfillmode-t.md) | [cublasfillmode-t.md](./eng/cublasfillmode-t.md) |
| 87 | cublasgemmalgo-t.md | [cublasgemmalgo-t.md](./chs/cublasgemmalgo-t.md) | [cublasgemmalgo-t.md](./eng/cublasgemmalgo-t.md) |
| 88 | cublasgemmbatchedex.md | [cublasgemmbatchedex.md](./chs/cublasgemmbatchedex.md) | [cublasgemmbatchedex.md](./eng/cublasgemmbatchedex.md) |
| 89 | cublasgemmex.md | [cublasgemmex.md](./chs/cublasgemmex.md) | [cublasgemmex.md](./eng/cublasgemmex.md) |
| 90 | cublasgemmgroupedbatchedex.md | [cublasgemmgroupedbatchedex.md](./chs/cublasgemmgroupedbatchedex.md) | [cublasgemmgroupedbatchedex.md](./eng/cublasgemmgroupedbatchedex.md) |
| 91 | cublasgemmstridedbatchedex.md | [cublasgemmstridedbatchedex.md](./chs/cublasgemmstridedbatchedex.md) | [cublasgemmstridedbatchedex.md](./eng/cublasgemmstridedbatchedex.md) |
| 92 | cublasgetatomicsmode.md | [cublasgetatomicsmode.md](./chs/cublasgetatomicsmode.md) | [cublasgetatomicsmode.md](./eng/cublasgetatomicsmode.md) |
| 93 | cublasgetemulationspecialvaluessupport.md | [cublasgetemulationspecialvaluessupport.md](./chs/cublasgetemulationspecialvaluessupport.md) | [cublasgetemulationspecialvaluessupport.md](./eng/cublasgetemulationspecialvaluessupport.md) |
| 94 | cublasgetemulationstrategy.md | [cublasgetemulationstrategy.md](./chs/cublasgetemulationstrategy.md) | [cublasgetemulationstrategy.md](./eng/cublasgetemulationstrategy.md) |
| 95 | cublasgetfixedpointemulationmantissabitcountpointer.md | [cublasgetfixedpointemulationmantissabitcountpointer.md](./chs/cublasgetfixedpointemulationmantissabitcountpointer.md) | [cublasgetfixedpointemulationmantissabitcountpointer.md](./eng/cublasgetfixedpointemulationmantissabitcountpointer.md) |
| 96 | cublasgetfixedpointemulationmantissabitoffset.md | [cublasgetfixedpointemulationmantissabitoffset.md](./chs/cublasgetfixedpointemulationmantissabitoffset.md) | [cublasgetfixedpointemulationmantissabitoffset.md](./eng/cublasgetfixedpointemulationmantissabitoffset.md) |
| 97 | cublasgetfixedpointemulationmantissacontrol.md | [cublasgetfixedpointemulationmantissacontrol.md](./chs/cublasgetfixedpointemulationmantissacontrol.md) | [cublasgetfixedpointemulationmantissacontrol.md](./eng/cublasgetfixedpointemulationmantissacontrol.md) |
| 98 | cublasgetfixedpointemulationmaxmantissabitcount.md | [cublasgetfixedpointemulationmaxmantissabitcount.md](./chs/cublasgetfixedpointemulationmaxmantissabitcount.md) | [cublasgetfixedpointemulationmaxmantissabitcount.md](./eng/cublasgetfixedpointemulationmaxmantissabitcount.md) |
| 99 | cublasgetloggercallback.md | [cublasgetloggercallback.md](./chs/cublasgetloggercallback.md) | [cublasgetloggercallback.md](./eng/cublasgetloggercallback.md) |
| 100 | cublasgetmathmode.md | [cublasgetmathmode.md](./chs/cublasgetmathmode.md) | [cublasgetmathmode.md](./eng/cublasgetmathmode.md) |
| 101 | cublasgetmatrix.md | [cublasgetmatrix.md](./chs/cublasgetmatrix.md) | [cublasgetmatrix.md](./eng/cublasgetmatrix.md) |
| 102 | cublasgetmatrixasync.md | [cublasgetmatrixasync.md](./chs/cublasgetmatrixasync.md) | [cublasgetmatrixasync.md](./eng/cublasgetmatrixasync.md) |
| 103 | cublasgetpointermode.md | [cublasgetpointermode.md](./chs/cublasgetpointermode.md) | [cublasgetpointermode.md](./eng/cublasgetpointermode.md) |
| 104 | cublasgetproperty.md | [cublasgetproperty.md](./chs/cublasgetproperty.md) | [cublasgetproperty.md](./eng/cublasgetproperty.md) |
| 105 | cublasgetsmcounttarget.md | [cublasgetsmcounttarget.md](./chs/cublasgetsmcounttarget.md) | [cublasgetsmcounttarget.md](./eng/cublasgetsmcounttarget.md) |
| 106 | cublasgetstatusname.md | [cublasgetstatusname.md](./chs/cublasgetstatusname.md) | [cublasgetstatusname.md](./eng/cublasgetstatusname.md) |
| 107 | cublasgetstatusstring.md | [cublasgetstatusstring.md](./chs/cublasgetstatusstring.md) | [cublasgetstatusstring.md](./eng/cublasgetstatusstring.md) |
| 108 | cublasgetstream.md | [cublasgetstream.md](./chs/cublasgetstream.md) | [cublasgetstream.md](./eng/cublasgetstream.md) |
| 109 | cublasgetvector.md | [cublasgetvector.md](./chs/cublasgetvector.md) | [cublasgetvector.md](./eng/cublasgetvector.md) |
| 110 | cublasgetvectorasync.md | [cublasgetvectorasync.md](./chs/cublasgetvectorasync.md) | [cublasgetvectorasync.md](./eng/cublasgetvectorasync.md) |
| 111 | cublasgetversion.md | [cublasgetversion.md](./chs/cublasgetversion.md) | [cublasgetversion.md](./eng/cublasgetversion.md) |
| 112 | cublashandle-t.md | [cublashandle-t.md](./chs/cublashandle-t.md) | [cublashandle-t.md](./eng/cublashandle-t.md) |
| 113 | cublasi-t-amax.md | [cublasi-t-amax.md](./chs/cublasi-t-amax.md) | [cublasi-t-amax.md](./eng/cublasi-t-amax.md) |
| 114 | cublasi-t-amin.md | [cublasi-t-amin.md](./chs/cublasi-t-amin.md) | [cublasi-t-amin.md](./eng/cublasi-t-amin.md) |
| 115 | cublasloggerconfigure.md | [cublasloggerconfigure.md](./chs/cublasloggerconfigure.md) | [cublasloggerconfigure.md](./eng/cublasloggerconfigure.md) |
| 116 | cublasltloggercallback-t.md | [cublasltloggercallback-t.md](./chs/cublasltloggercallback-t.md) | [cublasltloggercallback-t.md](./eng/cublasltloggercallback-t.md) |
| 117 | cublasltloggersetcallback.md | [cublasltloggersetcallback.md](./chs/cublasltloggersetcallback.md) | [cublasltloggersetcallback.md](./eng/cublasltloggersetcallback.md) |
| 118 | cublasmath-t.md | [cublasmath-t.md](./chs/cublasmath-t.md) | [cublasmath-t.md](./eng/cublasmath-t.md) |
| 119 | cublasnrm2ex.md | [cublasnrm2ex.md](./chs/cublasnrm2ex.md) | [cublasnrm2ex.md](./eng/cublasnrm2ex.md) |
| 120 | cublasoperation-t.md | [cublasoperation-t.md](./chs/cublasoperation-t.md) | [cublasoperation-t.md](./eng/cublasoperation-t.md) |
| 121 | cublaspointermode-t.md | [cublaspointermode-t.md](./chs/cublaspointermode-t.md) | [cublaspointermode-t.md](./eng/cublaspointermode-t.md) |
| 122 | cublasrotex.md | [cublasrotex.md](./chs/cublasrotex.md) | [cublasrotex.md](./eng/cublasrotex.md) |
| 123 | cublasscalex.md | [cublasscalex.md](./chs/cublasscalex.md) | [cublasscalex.md](./eng/cublasscalex.md) |
| 124 | cublassetatomicsmode.md | [cublassetatomicsmode.md](./chs/cublassetatomicsmode.md) | [cublassetatomicsmode.md](./eng/cublassetatomicsmode.md) |
| 125 | cublassetemulationspecialvaluessupport.md | [cublassetemulationspecialvaluessupport.md](./chs/cublassetemulationspecialvaluessupport.md) | [cublassetemulationspecialvaluessupport.md](./eng/cublassetemulationspecialvaluessupport.md) |
| 126 | cublassetemulationstrategy.md | [cublassetemulationstrategy.md](./chs/cublassetemulationstrategy.md) | [cublassetemulationstrategy.md](./eng/cublassetemulationstrategy.md) |
| 127 | cublassetfixedpointemulationmantissabitcountpointer.md | [cublassetfixedpointemulationmantissabitcountpointer.md](./chs/cublassetfixedpointemulationmantissabitcountpointer.md) | [cublassetfixedpointemulationmantissabitcountpointer.md](./eng/cublassetfixedpointemulationmantissabitcountpointer.md) |
| 128 | cublassetfixedpointemulationmantissabitoffset.md | [cublassetfixedpointemulationmantissabitoffset.md](./chs/cublassetfixedpointemulationmantissabitoffset.md) | [cublassetfixedpointemulationmantissabitoffset.md](./eng/cublassetfixedpointemulationmantissabitoffset.md) |
| 129 | cublassetfixedpointemulationmantissacontrol.md | [cublassetfixedpointemulationmantissacontrol.md](./chs/cublassetfixedpointemulationmantissacontrol.md) | [cublassetfixedpointemulationmantissacontrol.md](./eng/cublassetfixedpointemulationmantissacontrol.md) |
| 130 | cublassetfixedpointemulationmaxmantissabitcount.md | [cublassetfixedpointemulationmaxmantissabitcount.md](./chs/cublassetfixedpointemulationmaxmantissabitcount.md) | [cublassetfixedpointemulationmaxmantissabitcount.md](./eng/cublassetfixedpointemulationmaxmantissabitcount.md) |
| 131 | cublassetloggercallback.md | [cublassetloggercallback.md](./chs/cublassetloggercallback.md) | [cublassetloggercallback.md](./eng/cublassetloggercallback.md) |
| 132 | cublassetmathmode.md | [cublassetmathmode.md](./chs/cublassetmathmode.md) | [cublassetmathmode.md](./eng/cublassetmathmode.md) |
| 133 | cublassetmatrix.md | [cublassetmatrix.md](./chs/cublassetmatrix.md) | [cublassetmatrix.md](./eng/cublassetmatrix.md) |
| 134 | cublassetmatrixasync.md | [cublassetmatrixasync.md](./chs/cublassetmatrixasync.md) | [cublassetmatrixasync.md](./eng/cublassetmatrixasync.md) |
| 135 | cublassetpointermode.md | [cublassetpointermode.md](./chs/cublassetpointermode.md) | [cublassetpointermode.md](./eng/cublassetpointermode.md) |
| 136 | cublassetsmcounttarget.md | [cublassetsmcounttarget.md](./chs/cublassetsmcounttarget.md) | [cublassetsmcounttarget.md](./eng/cublassetsmcounttarget.md) |
| 137 | cublassetstream.md | [cublassetstream.md](./chs/cublassetstream.md) | [cublassetstream.md](./eng/cublassetstream.md) |
| 138 | cublassetvector.md | [cublassetvector.md](./chs/cublassetvector.md) | [cublassetvector.md](./eng/cublassetvector.md) |
| 139 | cublassetvectorasync.md | [cublassetvectorasync.md](./chs/cublassetvectorasync.md) | [cublassetvectorasync.md](./eng/cublassetvectorasync.md) |
| 140 | cublassetworkspace.md | [cublassetworkspace.md](./chs/cublassetworkspace.md) | [cublassetworkspace.md](./eng/cublassetworkspace.md) |
| 141 | cublassidemode-t.md | [cublassidemode-t.md](./chs/cublassidemode-t.md) | [cublassidemode-t.md](./eng/cublassidemode-t.md) |
| 142 | cublasstatus-t.md | [cublasstatus-t.md](./chs/cublasstatus-t.md) | [cublasstatus-t.md](./eng/cublasstatus-t.md) |
| 143 | cuda-datatypes-reference.md | [cuda-datatypes-reference.md](./chs/cuda-datatypes-reference.md) | [cuda-datatypes-reference.md](./eng/cuda-datatypes-reference.md) |
| 144 | cuda-graphs-support.md | [cuda-graphs-support.md](./chs/cuda-graphs-support.md) | [cuda-graphs-support.md](./eng/cuda-graphs-support.md) |
| 145 | cudadatatype-t.md | [cudadatatype-t.md](./chs/cudadatatype-t.md) | [cudadatatype-t.md](./eng/cudadatatype-t.md) |
| 146 | cudaemulationmantissacontrol-t.md | [cudaemulationmantissacontrol-t.md](./chs/cudaemulationmantissacontrol-t.md) | [cudaemulationmantissacontrol-t.md](./eng/cudaemulationmantissacontrol-t.md) |
| 147 | cudaemulationspecialvaluessupport-t.md | [cudaemulationspecialvaluessupport-t.md](./chs/cudaemulationspecialvaluessupport-t.md) | [cudaemulationspecialvaluessupport-t.md](./eng/cudaemulationspecialvaluessupport-t.md) |
| 148 | cudaemulationstrategy-t.md | [cudaemulationstrategy-t.md](./chs/cudaemulationstrategy-t.md) | [cudaemulationstrategy-t.md](./eng/cudaemulationstrategy-t.md) |
| 149 | d-block-quantization.md | [d-block-quantization.md](./chs/d-block-quantization.md) | [d-block-quantization.md](./eng/d-block-quantization.md) |
| 150 | d-block-scaling-factors-layout.md | [d-block-scaling-factors-layout.md](./chs/d-block-scaling-factors-layout.md) | [d-block-scaling-factors-layout.md](./eng/d-block-scaling-factors-layout.md) |
| 151 | disabling-cpu-instructions.md | [disabling-cpu-instructions.md](./chs/disabling-cpu-instructions.md) | [disabling-cpu-instructions.md](./eng/disabling-cpu-instructions.md) |
| 152 | element-1d-and-128x128-2d-block-scaling-for-fp8-data-types.md | [element-1d-and-128x128-2d-block-scaling-for-fp8-data-types.md](./chs/element-1d-and-128x128-2d-block-scaling-for-fp8-data-types.md) | [element-1d-and-128x128-2d-block-scaling-for-fp8-data-types.md](./eng/element-1d-and-128x128-2d-block-scaling-for-fp8-data-types.md) |
| 153 | element-1d-block-scaling-for-fp8-and-fp4-data-types.md | [element-1d-block-scaling-for-fp8-and-fp4-data-types.md](./chs/element-1d-block-scaling-for-fp8-and-fp4-data-types.md) | [element-1d-block-scaling-for-fp8-and-fp4-data-types.md](./eng/element-1d-block-scaling-for-fp8-and-fp4-data-types.md) |
| 154 | error-status.md | [error-status.md](./chs/error-status.md) | [error-status.md](./eng/error-status.md) |
| 155 | examples.md | [examples.md](./chs/examples.md) | [examples.md](./eng/examples.md) |
| 156 | experimental-per-batch-tensorwide-scaling-for-fp8-data-types.md | [experimental-per-batch-tensorwide-scaling-for-fp8-data-types.md](./chs/experimental-per-batch-tensorwide-scaling-for-fp8-data-types.md) | [experimental-per-batch-tensorwide-scaling-for-fp8-data-types.md](./eng/experimental-per-batch-tensorwide-scaling-for-fp8-data-types.md) |
| 157 | gemm-algorithms-numerical-behavior.md | [gemm-algorithms-numerical-behavior.md](./chs/gemm-algorithms-numerical-behavior.md) | [gemm-algorithms-numerical-behavior.md](./eng/gemm-algorithms-numerical-behavior.md) |
| 158 | general-description.md | [general-description.md](./chs/general-description.md) | [general-description.md](./eng/general-description.md) |
| 159 | helper-functions.md | [helper-functions.md](./chs/helper-functions.md) | [helper-functions.md](./eng/helper-functions.md) |
| 160 | heuristics-cache.md | [heuristics-cache.md](./chs/heuristics-cache.md) | [heuristics-cache.md](./eng/heuristics-cache.md) |
| 161 | hybrid-cpu-gpu-computation.md | [hybrid-cpu-gpu-computation.md](./chs/hybrid-cpu-gpu-computation.md) | [hybrid-cpu-gpu-computation.md](./eng/hybrid-cpu-gpu-computation.md) |
| 162 | id16.md | [id16.md](./chs/id16.md) | [id16.md](./eng/id16.md) |
| 163 | id102.md | [id102.md](./chs/id102.md) | [id102.md](./eng/id102.md) |
| 164 | id103.md | [id103.md](./chs/id103.md) | [id103.md](./eng/id103.md) |
| 165 | id106.md | [id106.md](./chs/id106.md) | [id106.md](./eng/id106.md) |
| 166 | id107.md | [id107.md](./chs/id107.md) | [id107.md](./eng/id107.md) |
| 167 | id108.md | [id108.md](./chs/id108.md) | [id108.md](./eng/id108.md) |
| 168 | initialization-and-shutdown.md | [initialization-and-shutdown.md](./chs/initialization-and-shutdown.md) | [initialization-and-shutdown.md](./eng/initialization-and-shutdown.md) |
| 169 | level-1-2-3-functions.md | [level-1-2-3-functions.md](./chs/level-1-2-3-functions.md) | [level-1-2-3-functions.md](./eng/level-1-2-3-functions.md) |
| 170 | librarypropertytype-t.md | [librarypropertytype-t.md](./chs/librarypropertytype-t.md) | [librarypropertytype-t.md](./eng/librarypropertytype-t.md) |
| 171 | memory-management.md | [memory-management.md](./chs/memory-management.md) | [memory-management.md](./eng/memory-management.md) |
| 172 | narrow-precision-data-types-usage.md | [narrow-precision-data-types-usage.md](./chs/narrow-precision-data-types-usage.md) | [narrow-precision-data-types-usage.md](./eng/narrow-precision-data-types-usage.md) |
| 173 | notice.md | [notice.md](./chs/notice.md) | [notice.md](./eng/notice.md) |
| 174 | outer-vector-scaling-for-fp8-data-types.md | [outer-vector-scaling-for-fp8-data-types.md](./chs/outer-vector-scaling-for-fp8-data-types.md) | [outer-vector-scaling-for-fp8-data-types.md](./eng/outer-vector-scaling-for-fp8-data-types.md) |
| 175 | parallelism-with-streams.md | [parallelism-with-streams.md](./chs/parallelism-with-streams.md) | [parallelism-with-streams.md](./eng/parallelism-with-streams.md) |
| 176 | problem-size-limitations.md | [problem-size-limitations.md](./chs/problem-size-limitations.md) | [problem-size-limitations.md](./eng/problem-size-limitations.md) |
| 177 | scalar-parameters.md | [scalar-parameters.md](./chs/scalar-parameters.md) | [scalar-parameters.md](./eng/scalar-parameters.md) |
| 178 | scaling-factors-layouts.md | [scaling-factors-layouts.md](./chs/scaling-factors-layouts.md) | [scaling-factors-layouts.md](./eng/scaling-factors-layouts.md) |
| 179 | static-library-support.md | [static-library-support.md](./chs/static-library-support.md) | [static-library-support.md](./eng/static-library-support.md) |
| 180 | tensor-core-usage.md | [tensor-core-usage.md](./chs/tensor-core-usage.md) | [tensor-core-usage.md](./eng/tensor-core-usage.md) |
| 181 | tensorwide-scaling-for-fp8-data-types.md | [tensorwide-scaling-for-fp8-data-types.md](./chs/tensorwide-scaling-for-fp8-data-types.md) | [tensorwide-scaling-for-fp8-data-types.md](./eng/tensorwide-scaling-for-fp8-data-types.md) |
| 182 | thread-safety.md | [thread-safety.md](./chs/thread-safety.md) | [thread-safety.md](./eng/thread-safety.md) |
| 183 | tiling-design-approach.md | [tiling-design-approach.md](./chs/tiling-design-approach.md) | [tiling-design-approach.md](./eng/tiling-design-approach.md) |
| 184 | using-the-cublas-api.md | [using-the-cublas-api.md](./chs/using-the-cublas-api.md) | [using-the-cublas-api.md](./eng/using-the-cublas-api.md) |

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
