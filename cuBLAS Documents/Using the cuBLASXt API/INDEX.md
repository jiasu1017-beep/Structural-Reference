# Using the cuBLASXt API

## 使用 cuBLASXt API

**来源 / Source:** NVIDIA cuBLAS Library Documentation - Using the cuBLASXt API

---

## 双语目录对照 / Bilingual Table of Contents

| 章节号 | 中文 Chinese | 英文 English |
|--------|--------------|--------------|
| 4 | [Using the cuBLASXt API](./chs/using-the-cublasxt-api.md) | [Using the cuBLASXt API](./eng/using-the-cublasxt-api.md) |
| 4.1 | [General description](./chs/using-the-cublasxt-api.md) | [General description](./eng/using-the-cublasxt-api.md) |
| 4.1.1 | [Tiling design approach](./chs/using-the-cublasxt-api.md) | [Tiling design approach](./eng/using-the-cublasxt-api.md) |
| 4.1.2 | [Hybrid CPU-GPU computation](./chs/using-the-cublasxt-api.md) | [Hybrid CPU-GPU computation](./eng/using-the-cublasxt-api.md) |
| 4.1.3 | [Results reproducibility](./chs/using-the-cublasxt-api.md) | [Results reproducibility](./eng/using-the-cublasxt-api.md) |
| 4.2 | [cuBLASXt API Datatypes Reference](./chs/using-the-cublasxt-api.md) | [cuBLASXt API Datatypes Reference](./eng/using-the-cublasxt-api.md) |
| 4.2.1 | [cublasXtHandle_t](./chs/using-the-cublasxt-api.md) | [cublasXtHandle_t](./eng/using-the-cublasxt-api.md) |
| 4.2.2 | [cublasXtOpType_t](./chs/using-the-cublasxt-api.md) | [cublasXtOpType_t](./eng/using-the-cublasxt-api.md) |
| 4.2.3 | [cublasXtBlasOp_t](./chs/using-the-cublasxt-api.md) | [cublasXtBlasOp_t](./eng/using-the-cublasxt-api.md) |
| 4.2.4 | [cublasXtPinningMemMode_t](./chs/using-the-cublasxt-api.md) | [cublasXtPinningMemMode_t](./eng/using-the-cublasxt-api.md) |
| 4.3 | [cuBLASXt API Helper Function Reference](./chs/using-the-cublasxt-api.md) | [cuBLASXt API Helper Function Reference](./eng/using-the-cublasxt-api.md) |
| 4.3.1 | [cublasXtCreate()](./chs/using-the-cublasxt-api.md) | [cublasXtCreate()](./eng/using-the-cublasxt-api.md) |
| 4.3.2 | [cublasXtDestroy()](./chs/using-the-cublasxt-api.md) | [cublasXtDestroy()](./eng/using-the-cublasxt-api.md) |
| 4.3.3 | [cublasXtDeviceSelect()](./chs/using-the-cublasxt-api.md) | [cublasXtDeviceSelect()](./eng/using-the-cublasxt-api.md) |
| 4.3.4 | [cublasXtSetBlockDim()](./chs/using-the-cublasxt-api.md) | [cublasXtSetBlockDim()](./eng/using-the-cublasxt-api.md) |
| 4.3.5 | [cublasXtGetBlockDim()](./chs/using-the-cublasxt-api.md) | [cublasXtGetBlockDim()](./eng/using-the-cublasxt-api.md) |
| 4.3.6 | [cublasXtSetCpuRoutine()](./chs/using-the-cublasxt-api.md) | [cublasXtSetCpuRoutine()](./eng/using-the-cublasxt-api.md) |
| 4.3.7 | [cublasXtSetCpuRatio()](./chs/using-the-cublasxt-api.md) | [cublasXtSetCpuRatio()](./eng/using-the-cublasxt-api.md) |
| 4.3.8 | [cublasXtSetPinningMemMode()](./chs/using-the-cublasxt-api.md) | [cublasXtSetPinningMemMode()](./eng/using-the-cublasxt-api.md) |
| 4.3.9 | [cublasXtGetPinningMemMode()](./chs/using-the-cublasxt-api.md) | [cublasXtGetPinningMemMode()](./eng/using-the-cublasxt-api.md) |
| 4.4 | [cuBLASXt API Math Functions Reference](./chs/using-the-cublasxt-api.md) | [cuBLASXt API Math Functions Reference](./eng/using-the-cublasxt-api.md) |
| 4.4.1 | [cublasXt<t>gemm()](./chs/using-the-cublasxt-api.md) | [cublasXt<t>gemm()](./eng/using-the-cublasxt-api.md) |
| 4.4.2 | [cublasXt<t>hemm()](./chs/using-the-cublasxt-api.md) | [cublasXt<t>hemm()](./eng/using-the-cublasxt-api.md) |
| 4.4.3 | [cublasXt<t>symm()](./chs/using-the-cublasxt-api.md) | [cublasXt<t>symm()](./eng/using-the-cublasxt-api.md) |
| 4.4.4 | [cublasXt<t>syrk()](./chs/using-the-cublasxt-api.md) | [cublasXt<t>syrk()](./eng/using-the-cublasxt-api.md) |
| 4.4.5 | [cublasXt<t>syr2k()](./chs/using-the-cublasxt-api.md) | [cublasXt<t>syr2k()](./eng/using-the-cublasxt-api.md) |
| 4.4.6 | [cublasXt<t>syrkx()](./chs/using-the-cublasxt-api.md) | [cublasXt<t>syrkx()](./eng/using-the-cublasxt-api.md) |
| 4.4.7 | [cublasXt<t>herk()](./chs/using-the-cublasxt-api.md) | [cublasXt<t>herk()](./eng/using-the-cublasxt-api.md) |
| 4.4.8 | [cublasXt<t>her2k()](./chs/using-the-cublasxt-api.md) | [cublasXt<t>her2k()](./eng/using-the-cublasxt-api.md) |
| 4.4.9 | [cublasXt<t>herkx()](./chs/using-the-cublasxt-api.md) | [cublasXt<t>herkx()](./eng/using-the-cublasxt-api.md) |
| 4.4.10 | [cublasXt<t>trsm()](./chs/using-the-cublasxt-api.md) | [cublasXt<t>trsm()](./eng/using-the-cublasxt-api.md) |
| 4.4.11 | [cublasXt<t>trmm()](./chs/using-the-cublasxt-api.md) | [cublasXt<t>trmm()](./eng/using-the-cublasxt-api.md) |
| 4.4.12 | [cublasXt<t>spmm()](./chs/using-the-cublasxt-api.md) | [cublasXt<t>spmm()](./eng/using-the-cublasxt-api.md) |

---

## 翻译状态 / Translation Status

| 状态 Status | 数量 Count |
|-------------|------------|
| ✅ 已完成 / Completed | 33 |
| ⏳ 未转换 / Not converted | 0 |
| **总计 Total** | **33** |

---

## 版权声明 / Copyright Notice

本翻译仅供学习研究使用，原文档版权归 NVIDIA Corporation 所有。

This translation is for study and research purposes only. Original documentation copyright NVIDIA Corporation.
