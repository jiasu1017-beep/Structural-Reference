# Using the cuBLASXt API

## 使用 cuBLASXt API

**来源 / Source:** NVIDIA cuBLAS Library Documentation - Using the cuBLASXt API

---

## 双语目录对照 / Bilingual Table of Contents

| 章节号 | 中文 Chinese | 英文 English |
|--------|--------------|--------------|
| 2.1.2 | [cuBLAS 上下文](./chs/cublas-context.md) | [cuBLAS Context](./eng/cublas-context.md) |
| 2.8 | [类BLAS扩展](./chs/blas-like-extension.md) | [BLAS-like Extension](./eng/blas-like-extension.md) |
| 2.8.1 | [cublas<t>geam()](./chs/blas-like-extension.md) | [cublas<t>geam()](./eng/blas-like-extension.md) |
| 2.8.2 | [cublas<t>dgmm()](./chs/blas-like-extension.md) | [cublas<t>dgmm()](./eng/blas-like-extension.md) |
| 2.8.3 | [cublas<t>getrfBatched()](./chs/blas-like-extension.md) | [cublas<t>getrfBatched()](./eng/blas-like-extension.md) |
| 2.8.4 | [cublas<t>getrsBatched()](./chs/blas-like-extension.md) | [cublas<t>getrsBatched()](./eng/blas-like-extension.md) |
| 2.8.5 | [cublas<t>getriBatched()](./chs/blas-like-extension.md) | [cublas<t>getriBatched()](./eng/blas-like-extension.md) |
| 2.8.6 | [cublas<t>matinvBatched()](./chs/blas-like-extension.md) | [cublas<t>matinvBatched()](./eng/blas-like-extension.md) |
| 2.8.7 | [cublas<t>geqrfBatched()](./chs/blas-like-extension.md) | [cublas<t>geqrfBatched()](./eng/blas-like-extension.md) |
| 4 | [Using the cuBLASXt API](./chs/using-the-cublasxt-api.md) | [Using the cuBLASXt API](./eng/using-the-cublasxt-api.md) |
| 4.1 | [General description](./chs/using-the-cublasxt-api.md) | [General description](./eng/using-the-cublasxt-api.md) |
| 4.1.1 | [Tiling design approach](./chs/using-the-cublasxt-api.md) | [Tiling design approach](./eng/using-the-cublasxt-api.md) |
| 4.1.2 | [Hybrid CPU-GPU computation](./chs/using-the-cublasxt-api.md) | [Hybrid CPU-GPU computation](./eng/using-the-cublasxt-api.md) |
| 4.1.3 | [Results reproducibility](./chs/using-the-cublasxt-api.md) | [Results reproducibility](./eng/using-the-cublasxt-api.md) |
| 4.2 | [cuBLASXt API 数据类型参考](./chs/cublasxt-api-datatypes-reference.md) | [cuBLASXt API Datatypes Reference](./eng/cublasxt-api-datatypes-reference.md) |
| 4.2.1 | [cublasXtHandle_t](./chs/cublasxt-api-datatypes-reference.md) | [cublasXtHandle_t](./eng/cublasxt-api-datatypes-reference.md) |
| 4.2.2 | [cublasXtOpType_t](./chs/cublasxt-api-datatypes-reference.md) | [cublasXtOpType_t](./eng/cublasxt-api-datatypes-reference.md) |
| 4.2.3 | [cublasXtBlasOp_t](./chs/cublasxt-api-datatypes-reference.md) | [cublasXtBlasOp_t](./eng/cublasxt-api-datatypes-reference.md) |
| 4.2.4 | [cublasXtPinningMemMode_t](./chs/cublasxt-api-datatypes-reference.md) | [cublasXtPinningMemMode_t](./eng/cublasxt-api-datatypes-reference.md) |
| 4.3 | [cuBLASXt API 辅助函数参考](./chs/cublasxt-api-helper-function-reference.md) | [cuBLASXt API Helper Function Reference](./eng/cublasxt-api-helper-function-reference.md) |
| 4.3.1 | [cublasXtCreate()](./chs/cublasxtcreate.md) | [cublasXtCreate()](./eng/cublasxtcreate.md) |
| 4.3.2 | [cublasXtDestroy()](./chs/cublasxtdestroy.md) | [cublasXtDestroy()](./eng/cublasxtdestroy.md) |
| 4.3.3 | [cublasXtDeviceSelect()](./chs/cublasxtdeviceselect.md) | [cublasXtDeviceSelect()](./eng/cublasxtdeviceselect.md) |
| 4.3.4 | [cublasXtSetBlockDim()](./chs/cublasxtsetblockdim.md) | [cublasXtSetBlockDim()](./eng/cublasxtsetblockdim.md) |
| 4.3.5 | [cublasXtGetBlockDim()](./chs/cublasxtgetblockdim.md) | [cublasXtGetBlockDim()](./eng/cublasxtgetblockdim.md) |
| 4.3.6 | [cublasXtSetCpuRoutine()](./chs/cublasxtsetcpuroutine.md) | [cublasXtSetCpuRoutine()](./eng/cublasxtsetcpuroutine.md) |
| 4.3.7 | [cublasXtSetCpuRatio()](./chs/cublasxtsetcpuratio.md) | [cublasXtSetCpuRatio()](./eng/cublasxtsetcpuratio.md) |
| 4.3.8 | [cublasXtSetPinningMemMode()](./chs/cublasxtsetpinningmemmode.md) | [cublasXtSetPinningMemMode()](./eng/cublasxtsetpinningmemmode.md) |
| 4.3.9 | [cublasXtGetPinningMemMode()](./chs/cublasxtgetpinningmemmode.md) | [cublasXtGetPinningMemMode()](./eng/cublasxtgetpinningmemmode.md) |
| 4.4 | [cuBLASXt API 数学函数参考](./chs/cublasxt-api-math-functions-reference.md) | [cuBLASXt API Math Functions Reference](./eng/cublasxt-api-math-functions-reference.md) |
| 4.4.1 | [cublasXt<t>gemm()](./chs/cublasxt-api-math-functions-reference.md) | [cublasXt<t>gemm()](./eng/cublasxt-api-math-functions-reference.md) |
| 4.4.2 | [cublasXt<t>hemm()](./chs/cublasxt-api-math-functions-reference.md) | [cublasXt<t>hemm()](./eng/cublasxt-api-math-functions-reference.md) |
| 4.4.3 | [cublasXt<t>symm()](./chs/cublasxt-api-math-functions-reference.md) | [cublasXt<t>symm()](./eng/cublasxt-api-math-functions-reference.md) |
| 4.4.4 | [cublasXt<t>syrk()](./chs/cublasxt-api-math-functions-reference.md) | [cublasXt<t>syrk()](./eng/cublasxt-api-math-functions-reference.md) |
| 4.4.5 | [cublasXt<t>syr2k()](./chs/cublasxt-api-math-functions-reference.md) | [cublasXt<t>syr2k()](./eng/cublasxt-api-math-functions-reference.md) |
| 4.4.6 | [cublasXt<t>syrkx()](./chs/cublasxt-api-math-functions-reference.md) | [cublasXt<t>syrkx()](./eng/cublasxt-api-math-functions-reference.md) |
| 4.4.7 | [cublasXt<t>herk()](./chs/cublasxt-api-math-functions-reference.md) | [cublasXt<t>herk()](./eng/cublasxt-api-math-functions-reference.md) |
| 4.4.8 | [cublasXt<t>her2k()](./chs/cublasxt-api-math-functions-reference.md) | [cublasXt<t>her2k()](./eng/cublasxt-api-math-functions-reference.md) |
| 4.4.9 | [cublasXt<t>herkx()](./chs/cublasxt-t-herkx.md) | [cublasXt<t>herkx()](./eng/cublasxt-t-herkx.md) |
| 4.4.10 | [cublasXt<t>trsm()](./chs/cublasxt-t-trsm.md) | [cublasXt<t>trsm()](./eng/cublasxt-t-trsm.md) |
| 4.4.11 | [cublasXt<t>trmm()](./chs/cublasxt-t-trmm.md) | [cublasXt<t>trmm()](./eng/cublasxt-t-trmm.md) |
| 4.4.12 | [cublasXt<t>spmm()](./chs/cublasxt-t-spmm.md) | [cublasXt<t>spmm()](./eng/cublasxt-t-spmm.md) |

---

## 翻译状态 / Translation Status

| 状态 Status | 数量 Count |
|-------------|------------|
| ✅ 已完成 / Completed | 42 |
| ⏳ 未转换 / Not converted | 0 |
| **总计 Total** | **42** |

---

## 版权声明 / Copyright Notice

本翻译仅供学习研究使用，原文档版权归 NVIDIA Corporation 所有。

This translation is for study and research purposes only. Original documentation copyright NVIDIA Corporation.
