# Using the cuBLASLt API

## 使用 cuBLASLt API

**来源 / Source:** NVIDIA cuBLAS Library Documentation - Using the cuBLASLt API

---

## 双语目录对照 / Bilingual Table of Contents

| 章节号 | 中文 Chinese | 英文 English |
|--------|--------------|--------------|
| 3 | [Using the cuBLASLt API](./chs/using-the-cublaslt-api.md) | [Using the cuBLASLt API](./eng/using-the-cublaslt-api.md) |
| 3.1 | [General Description](./chs/using-the-cublaslt-api.md) | [General Description](./eng/using-the-cublaslt-api.md) |
| 3.1.1 | [Problem Size Limitations](./chs/using-the-cublaslt-api.md) | [Problem Size Limitations](./eng/using-the-cublaslt-api.md) |
| 3.1.2 | [Heuristics Cache](./chs/using-the-cublaslt-api.md) | [Heuristics Cache](./eng/using-the-cublaslt-api.md) |
| 3.1.3 | [cuBLASLt Logging](./chs/using-the-cublaslt-api.md) | [cuBLASLt Logging](./eng/using-the-cublaslt-api.md) |
| 3.1.4 | [Narrow Precision Data Types Usage](./chs/using-the-cublaslt-api.md) | [Narrow Precision Data Types Usage](./eng/using-the-cublaslt-api.md) |
| 3.1.4.1 | [Tensorwide Scaling For FP8 Data Types](./chs/using-the-cublaslt-api.md) | [Tensorwide Scaling For FP8 Data Types](./eng/using-the-cublaslt-api.md) |
| 3.1.4.2 | [Experimental: Per-batch Tensorwide Scaling For FP8 Data Types](./chs/using-the-cublaslt-api.md) | [Experimental: Per-batch Tensorwide Scaling For FP8 Data Types](./eng/using-the-cublaslt-api.md) |
| 3.1.4.3 | [Outer Vector Scaling for FP8 Data Types](./chs/using-the-cublaslt-api.md) | [Outer Vector Scaling for FP8 Data Types](./eng/using-the-cublaslt-api.md) |
| 3.1.4.4 | [16/32-Element 1D Block Scaling for FP8 and FP4 Data Types](./chs/using-the-cublaslt-api.md) | [16/32-Element 1D Block Scaling for FP8 and FP4 Data Types](./eng/using-the-cublaslt-api.md) |
| 3.1.4.5 | [128-element 1D and 128x128 2D Block Scaling For FP8 Data Types](./chs/using-the-cublaslt-api.md) | [128-element 1D and 128x128 2D Block Scaling For FP8 Data Types](./eng/using-the-cublaslt-api.md) |
| 3.1.5 | [Disabling CPU Instructions](./chs/using-the-cublaslt-api.md) | [Disabling CPU Instructions](./eng/using-the-cublaslt-api.md) |
| 3.2 | [cuBLASLt Code Examples](./chs/using-the-cublaslt-api.md) | [cuBLASLt Code Examples](./eng/using-the-cublaslt-api.md) |
| 3.3 | [cuBLASLt Datatypes Reference](./chs/using-the-cublaslt-api.md) | [cuBLASLt Datatypes Reference](./eng/using-the-cublaslt-api.md) |
| 3.3.1 | [cublasLtClusterShape_t](./chs/using-the-cublaslt-api.md) | [cublasLtClusterShape_t](./eng/using-the-cublaslt-api.md) |
| 3.3.2 | [cublasLtEpilogue_t](./chs/using-the-cublaslt-api.md) | [cublasLtEpilogue_t](./eng/using-the-cublaslt-api.md) |
| 3.3.3 | [cublasLtHandle_t](./chs/using-the-cublaslt-api.md) | [cublasLtHandle_t](./eng/using-the-cublaslt-api.md) |
| 3.3.4 | [cublasLtLoggerCallback_t](./chs/using-the-cublaslt-api.md) | [cublasLtLoggerCallback_t](./eng/using-the-cublaslt-api.md) |
| 3.3.5 | [cublasLtMatmulAlgo_t](./chs/using-the-cublaslt-api.md) | [cublasLtMatmulAlgo_t](./eng/using-the-cublaslt-api.md) |
| 3.3.6 | [cublasLtMatmulAlgoCapAttributes_t](./chs/using-the-cublaslt-api.md) | [cublasLtMatmulAlgoCapAttributes_t](./eng/using-the-cublaslt-api.md) |
| 3.3.7 | [cublasLtMatmulAlgoConfigAttributes_t](./chs/using-the-cublaslt-api.md) | [cublasLtMatmulAlgoConfigAttributes_t](./eng/using-the-cublaslt-api.md) |
| 3.3.8 | [cublasLtMatmulDesc_t](./chs/using-the-cublaslt-api.md) | [cublasLtMatmulDesc_t](./eng/using-the-cublaslt-api.md) |
| 3.3.9 | [cublasLtMatmulDescAttributes_t](./chs/using-the-cublaslt-api.md) | [cublasLtMatmulDescAttributes_t](./eng/using-the-cublaslt-api.md) |
| 3.3.10 | [cublasLtMatmulHeuristicResult_t](./chs/using-the-cublaslt-api.md) | [cublasLtMatmulHeuristicResult_t](./eng/using-the-cublaslt-api.md) |
| 3.3.11 | [cublasLtMatmulInnerShape_t](./chs/using-the-cublaslt-api.md) | [cublasLtMatmulInnerShape_t](./eng/using-the-cublaslt-api.md) |
| 3.3.12 | [cublasLtMatmulPreference_t](./chs/using-the-cublaslt-api.md) | [cublasLtMatmulPreference_t](./eng/using-the-cublaslt-api.md) |
| 3.3.13 | [cublasLtMatmulPreferenceAttributes_t](./chs/using-the-cublaslt-api.md) | [cublasLtMatmulPreferenceAttributes_t](./eng/using-the-cublaslt-api.md) |
| 3.3.14 | [cublasLtMatmulSearch_t](./chs/using-the-cublaslt-api.md) | [cublasLtMatmulSearch_t](./eng/using-the-cublaslt-api.md) |
| 3.3.15 | [cublasLtMatmulTile_t](./chs/using-the-cublaslt-api.md) | [cublasLtMatmulTile_t](./eng/using-the-cublaslt-api.md) |
| 3.3.16 | [cublasLtMatmulStages_t](./chs/using-the-cublaslt-api.md) | [cublasLtMatmulStages_t](./eng/using-the-cublaslt-api.md) |
| 3.3.17 | [cublasLtNumericalImplFlags_t](./chs/using-the-cublaslt-api.md) | [cublasLtNumericalImplFlags_t](./eng/using-the-cublaslt-api.md) |
| 3.3.18 | [cublasLtMatrixLayout_t](./chs/using-the-cublaslt-api.md) | [cublasLtMatrixLayout_t](./eng/using-the-cublaslt-api.md) |
| 3.3.19 | [cublasLtMatrixLayoutAttribute_t](./chs/using-the-cublaslt-api.md) | [cublasLtMatrixLayoutAttribute_t](./eng/using-the-cublaslt-api.md) |
| 3.3.20 | [cublasLtIntegerWidth_t](./chs/using-the-cublaslt-api.md) | [cublasLtIntegerWidth_t](./eng/using-the-cublaslt-api.md) |
| 3.3.21 | [cublasLtMatrixTransformDesc_t](./chs/using-the-cublaslt-api.md) | [cublasLtMatrixTransformDesc_t](./eng/using-the-cublaslt-api.md) |
| 3.3.22 | [cublasLtMatrixTransformDescAttributes_t](./chs/using-the-cublaslt-api.md) | [cublasLtMatrixTransformDescAttributes_t](./eng/using-the-cublaslt-api.md) |
| 3.3.23 | [cublasLtOrder_t](./chs/using-the-cublaslt-api.md) | [cublasLtOrder_t](./eng/using-the-cublaslt-api.md) |
| 3.3.24 | [cublasLtPointerMode_t](./chs/using-the-cublaslt-api.md) | [cublasLtPointerMode_t](./eng/using-the-cublaslt-api.md) |
| 3.3.25 | [cublasLtPointerModeMask_t](./chs/using-the-cublaslt-api.md) | [cublasLtPointerModeMask_t](./eng/using-the-cublaslt-api.md) |
| 3.3.26 | [cublasLtReductionScheme_t](./chs/using-the-cublaslt-api.md) | [cublasLtReductionScheme_t](./eng/using-the-cublaslt-api.md) |
| 3.3.27 | [cublasLtMatmulMatrixScale_t](./chs/using-the-cublaslt-api.md) | [cublasLtMatmulMatrixScale_t](./eng/using-the-cublaslt-api.md) |
| 3.3.28 | [cublasLtBatchMode_t](./chs/using-the-cublaslt-api.md) | [cublasLtBatchMode_t](./eng/using-the-cublaslt-api.md) |
| 3.3.29 | [cublasLtEmulationDesc_t](./chs/using-the-cublaslt-api.md) | [cublasLtEmulationDesc_t](./eng/using-the-cublaslt-api.md) |
| 3.3.30 | [cublasLtEmulationDescAttributes_t](./chs/using-the-cublaslt-api.md) | [cublasLtEmulationDescAttributes_t](./eng/using-the-cublaslt-api.md) |
| 3.4 | [cuBLASLt API Reference](./chs/using-the-cublaslt-api.md) | [cuBLASLt API Reference](./eng/using-the-cublaslt-api.md) |
| 3.4.1 | [cublasLtCreate()](./chs/using-the-cublaslt-api.md) | [cublasLtCreate()](./eng/using-the-cublaslt-api.md) |
| 3.4.2 | [cublasLtDestroy()](./chs/using-the-cublaslt-api.md) | [cublasLtDestroy()](./eng/using-the-cublaslt-api.md) |
| 3.4.3 | [cublasLtDisableCpuInstructionsSetMask()](./chs/using-the-cublaslt-api.md) | [cublasLtDisableCpuInstructionsSetMask()](./eng/using-the-cublaslt-api.md) |
| 3.4.4 | [cublasLtGetCudartVersion()](./chs/using-the-cublaslt-api.md) | [cublasLtGetCudartVersion()](./eng/using-the-cublaslt-api.md) |
| 3.4.5 | [cublasLtGetProperty()](./chs/using-the-cublaslt-api.md) | [cublasLtGetProperty()](./eng/using-the-cublaslt-api.md) |
| 3.4.6 | [cublasLtGetStatusName()](./chs/using-the-cublaslt-api.md) | [cublasLtGetStatusName()](./eng/using-the-cublaslt-api.md) |
| 3.4.7 | [cublasLtGetStatusString()](./chs/using-the-cublaslt-api.md) | [cublasLtGetStatusString()](./eng/using-the-cublaslt-api.md) |
| 3.4.8 | [cublasLtHeuristicsCacheGetCapacity()](./chs/using-the-cublaslt-api.md) | [cublasLtHeuristicsCacheGetCapacity()](./eng/using-the-cublaslt-api.md) |
| 3.4.9 | [cublasLtHeuristicsCacheSetCapacity()](./chs/using-the-cublaslt-api.md) | [cublasLtHeuristicsCacheSetCapacity()](./eng/using-the-cublaslt-api.md) |
| 3.4.10 | [cublasLtGetVersion()](./chs/using-the-cublaslt-api.md) | [cublasLtGetVersion()](./eng/using-the-cublaslt-api.md) |
| 3.4.11 | [cublasLtLoggerSetCallback()](./chs/using-the-cublaslt-api.md) | [cublasLtLoggerSetCallback()](./eng/using-the-cublaslt-api.md) |
| 3.4.12 | [cublasLtLoggerSetFile()](./chs/using-the-cublaslt-api.md) | [cublasLtLoggerSetFile()](./eng/using-the-cublaslt-api.md) |
| 3.4.13 | [cublasLtLoggerOpenFile()](./chs/using-the-cublaslt-api.md) | [cublasLtLoggerOpenFile()](./eng/using-the-cublaslt-api.md) |
| 3.4.14 | [cublasLtLoggerSetLevel()](./chs/using-the-cublaslt-api.md) | [cublasLtLoggerSetLevel()](./eng/using-the-cublaslt-api.md) |
| 3.4.15 | [cublasLtLoggerSetMask()](./chs/using-the-cublaslt-api.md) | [cublasLtLoggerSetMask()](./eng/using-the-cublaslt-api.md) |
| 3.4.16 | [cublasLtLoggerForceDisable()](./chs/using-the-cublaslt-api.md) | [cublasLtLoggerForceDisable()](./eng/using-the-cublaslt-api.md) |
| 3.4.17 | [cublasLtMatmul()](./chs/using-the-cublaslt-api.md) | [cublasLtMatmul()](./eng/using-the-cublaslt-api.md) |
| 3.4.18 | [cublasLtMatmulAlgoCapGetAttribute()](./chs/using-the-cublaslt-api.md) | [cublasLtMatmulAlgoCapGetAttribute()](./eng/using-the-cublaslt-api.md) |
| 3.4.19 | [cublasLtMatmulAlgoCheck()](./chs/using-the-cublaslt-api.md) | [cublasLtMatmulAlgoCheck()](./eng/using-the-cublaslt-api.md) |
| 3.4.20 | [cublasLtMatmulAlgoConfigGetAttribute()](./chs/using-the-cublaslt-api.md) | [cublasLtMatmulAlgoConfigGetAttribute()](./eng/using-the-cublaslt-api.md) |
| 3.4.21 | [cublasLtMatmulAlgoConfigSetAttribute()](./chs/using-the-cublaslt-api.md) | [cublasLtMatmulAlgoConfigSetAttribute()](./eng/using-the-cublaslt-api.md) |
| 3.4.22 | [cublasLtMatmulAlgoGetHeuristic()](./chs/using-the-cublaslt-api.md) | [cublasLtMatmulAlgoGetHeuristic()](./eng/using-the-cublaslt-api.md) |
| 3.4.23 | [cublasLtMatmulAlgoGetIds()](./chs/using-the-cublaslt-api.md) | [cublasLtMatmulAlgoGetIds()](./eng/using-the-cublaslt-api.md) |
| 3.4.24 | [cublasLtMatmulAlgoInit()](./chs/using-the-cublaslt-api.md) | [cublasLtMatmulAlgoInit()](./eng/using-the-cublaslt-api.md) |
| 3.4.25 | [cublasLtMatmulDescCreate()](./chs/using-the-cublaslt-api.md) | [cublasLtMatmulDescCreate()](./eng/using-the-cublaslt-api.md) |
| 3.4.26 | [cublasLtMatmulDescInit()](./chs/using-the-cublaslt-api.md) | [cublasLtMatmulDescInit()](./eng/using-the-cublaslt-api.md) |
| 3.4.27 | [cublasLtMatmulDescDestroy()](./chs/using-the-cublaslt-api.md) | [cublasLtMatmulDescDestroy()](./eng/using-the-cublaslt-api.md) |
| 3.4.28 | [cublasLtMatmulDescGetAttribute()](./chs/using-the-cublaslt-api.md) | [cublasLtMatmulDescGetAttribute()](./eng/using-the-cublaslt-api.md) |
| 3.4.29 | [cublasLtMatmulDescSetAttribute()](./chs/using-the-cublaslt-api.md) | [cublasLtMatmulDescSetAttribute()](./eng/using-the-cublaslt-api.md) |
| 3.4.30 | [cublasLtMatmulPreferenceCreate()](./chs/using-the-cublaslt-api.md) | [cublasLtMatmulPreferenceCreate()](./eng/using-the-cublaslt-api.md) |
| 3.4.31 | [cublasLtMatmulPreferenceInit()](./chs/using-the-cublaslt-api.md) | [cublasLtMatmulPreferenceInit()](./eng/using-the-cublaslt-api.md) |
| 3.4.32 | [cublasLtMatmulPreferenceDestroy()](./chs/using-the-cublaslt-api.md) | [cublasLtMatmulPreferenceDestroy()](./eng/using-the-cublaslt-api.md) |
| 3.4.33 | [cublasLtMatmulPreferenceGetAttribute()](./chs/using-the-cublaslt-api.md) | [cublasLtMatmulPreferenceGetAttribute()](./eng/using-the-cublaslt-api.md) |
| 3.4.34 | [cublasLtMatmulPreferenceSetAttribute()](./chs/using-the-cublaslt-api.md) | [cublasLtMatmulPreferenceSetAttribute()](./eng/using-the-cublaslt-api.md) |
| 3.4.35 | [cublasLtMatrixLayoutCreate()](./chs/using-the-cublaslt-api.md) | [cublasLtMatrixLayoutCreate()](./eng/using-the-cublaslt-api.md) |
| 3.4.36 | [cublasLtMatrixLayoutInit()](./chs/using-the-cublaslt-api.md) | [cublasLtMatrixLayoutInit()](./eng/using-the-cublaslt-api.md) |
| 3.4.37 | [cublasLtGroupedMatrixLayoutCreate()](./chs/using-the-cublaslt-api.md) | [cublasLtGroupedMatrixLayoutCreate()](./eng/using-the-cublaslt-api.md) |
| 3.4.38 | [cublasLtGroupedMatrixLayoutInit()](./chs/using-the-cublaslt-api.md) | [cublasLtGroupedMatrixLayoutInit()](./eng/using-the-cublaslt-api.md) |
| 3.4.39 | [cublasLtMatrixLayoutDestroy()](./chs/using-the-cublaslt-api.md) | [cublasLtMatrixLayoutDestroy()](./eng/using-the-cublaslt-api.md) |
| 3.4.40 | [cublasLtMatrixLayoutGetAttribute()](./chs/using-the-cublaslt-api.md) | [cublasLtMatrixLayoutGetAttribute()](./eng/using-the-cublaslt-api.md) |
| 3.4.41 | [cublasLtMatrixLayoutSetAttribute()](./chs/using-the-cublaslt-api.md) | [cublasLtMatrixLayoutSetAttribute()](./eng/using-the-cublaslt-api.md) |
| 3.4.42 | [cublasLtMatrixTransform()](./chs/using-the-cublaslt-api.md) | [cublasLtMatrixTransform()](./eng/using-the-cublaslt-api.md) |
| 3.4.43 | [cublasLtMatrixTransformDescCreate()](./chs/using-the-cublaslt-api.md) | [cublasLtMatrixTransformDescCreate()](./eng/using-the-cublaslt-api.md) |
| 3.4.44 | [cublasLtMatrixTransformDescInit()](./chs/using-the-cublaslt-api.md) | [cublasLtMatrixTransformDescInit()](./eng/using-the-cublaslt-api.md) |
| 3.4.45 | [cublasLtMatrixTransformDescDestroy()](./chs/using-the-cublaslt-api.md) | [cublasLtMatrixTransformDescDestroy()](./eng/using-the-cublaslt-api.md) |
| 3.4.46 | [cublasLtMatrixTransformDescGetAttribute()](./chs/using-the-cublaslt-api.md) | [cublasLtMatrixTransformDescGetAttribute()](./eng/using-the-cublaslt-api.md) |
| 3.4.47 | [cublasLtMatrixTransformDescSetAttribute()](./chs/using-the-cublaslt-api.md) | [cublasLtMatrixTransformDescSetAttribute()](./eng/using-the-cublaslt-api.md) |
| 3.4.48 | [cublasLtEmulationDescInit()](./chs/using-the-cublaslt-api.md) | [cublasLtEmulationDescInit()](./eng/using-the-cublaslt-api.md) |
| 3.4.49 | [cublasLtEmulationDescCreate()](./chs/using-the-cublaslt-api.md) | [cublasLtEmulationDescCreate()](./eng/using-the-cublaslt-api.md) |
| 3.4.50 | [cublasLtEmulationDescDestroy()](./chs/using-the-cublaslt-api.md) | [cublasLtEmulationDescDestroy()](./eng/using-the-cublaslt-api.md) |
| 3.4.51 | [cublasLtEmulationDescSetAttribute()](./chs/using-the-cublaslt-api.md) | [cublasLtEmulationDescSetAttribute()](./eng/using-the-cublaslt-api.md) |
| 3.4.52 | [cublasLtEmulationDescGetAttribute()](./chs/using-the-cublaslt-api.md) | [cublasLtEmulationDescGetAttribute()](./eng/using-the-cublaslt-api.md) |

---

## 翻译状态 / Translation Status

| 状态 Status | 数量 Count |
|-------------|------------|
| ✅ 已完成 / Completed | 97 |
| ⏳ 未转换 / Not converted | 0 |
| **总计 Total** | **97** |

---

## 版权声明 / Copyright Notice

本翻译仅供学习研究使用，原文档版权归 NVIDIA Corporation 所有。

This translation is for study and research purposes only. Original documentation copyright NVIDIA Corporation.
