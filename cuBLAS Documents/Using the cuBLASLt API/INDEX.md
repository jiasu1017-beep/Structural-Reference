# Using the cuBLASLt API

## 使用 cuBLASLt API

**来源 / Source:** NVIDIA cuBLAS Library Documentation - Using the cuBLASLt API

---

## 双语目录对照 / Bilingual Table of Contents

| 章节号 | 中文 Chinese | 英文 English |
|--------|--------------|--------------|
| 2.1.4 | [结果可重现性](./chs/results-reproducibility.md) | [Results Reproducibility](./eng/results-reproducibility.md) |
| 3 | [Using the cuBLASLt API](./chs/using-the-cublaslt-api.md) | [Using the cuBLASLt API](./eng/using-the-cublaslt-api.md) |
| 3.1 | [General Description](./chs/using-the-cublaslt-api.md) | [General Description](./eng/using-the-cublaslt-api.md) |
| 3.1.1 | [Problem Size Limitations](./chs/using-the-cublaslt-api.md) | [Problem Size Limitations](./eng/using-the-cublaslt-api.md) |
| 3.1.2 | [Heuristics Cache](./chs/using-the-cublaslt-api.md) | [Heuristics Cache](./eng/using-the-cublaslt-api.md) |
| 3.1.3 | [cuBLASLt 日志记录](./chs/cublaslt-logging.md) | [cuBLASLt Logging](./eng/cublaslt-logging.md) |
| 3.1.4 | [Narrow Precision Data Types Usage](./chs/using-the-cublaslt-api.md) | [Narrow Precision Data Types Usage](./eng/using-the-cublaslt-api.md) |
| 3.1.4.1 | [Tensorwide Scaling For FP8 Data Types](./chs/using-the-cublaslt-api.md) | [Tensorwide Scaling For FP8 Data Types](./eng/using-the-cublaslt-api.md) |
| 3.1.4.2 | [Experimental: Per-batch Tensorwide Scaling For FP8 Data Types](./chs/using-the-cublaslt-api.md) | [Experimental: Per-batch Tensorwide Scaling For FP8 Data Types](./eng/using-the-cublaslt-api.md) |
| 3.1.4.3 | [Outer Vector Scaling for FP8 Data Types](./chs/using-the-cublaslt-api.md) | [Outer Vector Scaling for FP8 Data Types](./eng/using-the-cublaslt-api.md) |
| 3.1.4.4 | [16/32-Element 1D Block Scaling for FP8 and FP4 Data Types](./chs/using-the-cublaslt-api.md) | [16/32-Element 1D Block Scaling for FP8 and FP4 Data Types](./eng/using-the-cublaslt-api.md) |
| 3.1.4.5 | [128-element 1D and 128x128 2D Block Scaling For FP8 Data Types](./chs/using-the-cublaslt-api.md) | [128-element 1D and 128x128 2D Block Scaling For FP8 Data Types](./eng/using-the-cublaslt-api.md) |
| 3.1.5 | [Disabling CPU Instructions](./chs/using-the-cublaslt-api.md) | [Disabling CPU Instructions](./eng/using-the-cublaslt-api.md) |
| 3.2 | [cuBLASLt 代码示例](./chs/cublaslt-code-examples.md) | [cuBLASLt Code Examples](./eng/cublaslt-code-examples.md) |
| 3.3 | [cuBLASLt Datatypes Reference](./chs/cublaslt-datatypes-reference.md) | [cuBLASLt Datatypes Reference](./eng/cublaslt-datatypes-reference.md) |
| 3.3.1 | [cublasLtClusterShape_t](./chs/cublaslt-datatypes-reference.md) | [cublasLtClusterShape_t](./eng/cublaslt-datatypes-reference.md) |
| 3.3.2 | [cublasLtEpilogue_t](./chs/cublaslt-datatypes-reference.md) | [cublasLtEpilogue_t](./eng/cublaslt-datatypes-reference.md) |
| 3.3.3 | [cublasLtHandle_t](./chs/cublaslt-datatypes-reference.md) | [cublasLtHandle_t](./eng/cublaslt-datatypes-reference.md) |
| 3.3.4 | [cublasLtLoggerCallback_t](./chs/cublaslt-datatypes-reference.md) | [cublasLtLoggerCallback_t](./eng/cublaslt-datatypes-reference.md) |
| 3.3.5 | [cublasLtMatmulAlgo_t](./chs/cublaslt-datatypes-reference.md) | [cublasLtMatmulAlgo_t](./eng/cublaslt-datatypes-reference.md) |
| 3.3.6 | [cublasLtMatmulAlgoCapAttributes_t](./chs/cublaslt-datatypes-reference.md) | [cublasLtMatmulAlgoCapAttributes_t](./eng/cublaslt-datatypes-reference.md) |
| 3.3.7 | [cublasLtMatmulAlgoConfigAttributes_t](./chs/cublaslt-datatypes-reference.md) | [cublasLtMatmulAlgoConfigAttributes_t](./eng/cublaslt-datatypes-reference.md) |
| 3.3.8 | [cublasLtMatmulDesc_t](./chs/cublaslt-datatypes-reference.md) | [cublasLtMatmulDesc_t](./eng/cublaslt-datatypes-reference.md) |
| 3.3.9 | [cublasLtMatmulDescAttributes_t](./chs/cublaslt-datatypes-reference.md) | [cublasLtMatmulDescAttributes_t](./eng/cublaslt-datatypes-reference.md) |
| 3.3.10 | [cublasLtMatmulHeuristicResult_t](./chs/cublaslt-datatypes-reference.md) | [cublasLtMatmulHeuristicResult_t](./eng/cublaslt-datatypes-reference.md) |
| 3.3.11 | [cublasLtMatmulInnerShape_t](./chs/cublaslt-datatypes-reference.md) | [cublasLtMatmulInnerShape_t](./eng/cublaslt-datatypes-reference.md) |
| 3.3.12 | [cublasLtMatmulPreference_t](./chs/cublaslt-datatypes-reference.md) | [cublasLtMatmulPreference_t](./eng/cublaslt-datatypes-reference.md) |
| 3.3.13 | [cublasLtMatmulPreferenceAttributes_t](./chs/cublaslt-datatypes-reference.md) | [cublasLtMatmulPreferenceAttributes_t](./eng/cublaslt-datatypes-reference.md) |
| 3.3.14 | [cublasLtMatmulSearch_t](./chs/cublaslt-datatypes-reference.md) | [cublasLtMatmulSearch_t](./eng/cublaslt-datatypes-reference.md) |
| 3.3.15 | [cublasLtMatmulTile_t](./chs/cublaslt-datatypes-reference.md) | [cublasLtMatmulTile_t](./eng/cublaslt-datatypes-reference.md) |
| 3.3.16 | [cublasLtMatmulStages_t](./chs/cublaslt-datatypes-reference.md) | [cublasLtMatmulStages_t](./eng/cublaslt-datatypes-reference.md) |
| 3.3.17 | [cublasLtNumericalImplFlags_t](./chs/cublaslt-datatypes-reference.md) | [cublasLtNumericalImplFlags_t](./eng/cublaslt-datatypes-reference.md) |
| 3.3.18 | [cublasLtMatrixLayout_t](./chs/cublaslt-datatypes-reference.md) | [cublasLtMatrixLayout_t](./eng/cublaslt-datatypes-reference.md) |
| 3.3.19 | [cublasLtMatrixLayoutAttribute_t](./chs/cublaslt-datatypes-reference.md) | [cublasLtMatrixLayoutAttribute_t](./eng/cublaslt-datatypes-reference.md) |
| 3.3.20 | [cublasLtIntegerWidth_t](./chs/cublaslt-datatypes-reference.md) | [cublasLtIntegerWidth_t](./eng/cublaslt-datatypes-reference.md) |
| 3.3.21 | [cublasLtMatrixTransformDesc_t](./chs/cublaslt-datatypes-reference.md) | [cublasLtMatrixTransformDesc_t](./eng/cublaslt-datatypes-reference.md) |
| 3.3.22 | [cublasLtMatrixTransformDescAttributes_t](./chs/cublaslt-datatypes-reference.md) | [cublasLtMatrixTransformDescAttributes_t](./eng/cublaslt-datatypes-reference.md) |
| 3.3.23 | [cublasLtOrder_t](./chs/cublaslt-datatypes-reference.md) | [cublasLtOrder_t](./eng/cublaslt-datatypes-reference.md) |
| 3.3.24 | [cublasLtPointerMode_t](./chs/cublaslt-datatypes-reference.md) | [cublasLtPointerMode_t](./eng/cublaslt-datatypes-reference.md) |
| 3.3.25 | [cublasLtPointerModeMask_t](./chs/cublaslt-datatypes-reference.md) | [cublasLtPointerModeMask_t](./eng/cublaslt-datatypes-reference.md) |
| 3.3.26 | [cublasLtReductionScheme_t](./chs/cublaslt-datatypes-reference.md) | [cublasLtReductionScheme_t](./eng/cublaslt-datatypes-reference.md) |
| 3.3.27 | [cublasLtMatmulMatrixScale_t](./chs/cublaslt-datatypes-reference.md) | [cublasLtMatmulMatrixScale_t](./eng/cublaslt-datatypes-reference.md) |
| 3.3.28 | [cublasLtBatchMode_t](./chs/cublaslt-datatypes-reference.md) | [cublasLtBatchMode_t](./eng/cublaslt-datatypes-reference.md) |
| 3.3.29 | [cublasLtEmulationDesc_t](./chs/cublaslt-datatypes-reference.md) | [cublasLtEmulationDesc_t](./eng/cublaslt-datatypes-reference.md) |
| 3.3.30 | [cublasLtEmulationDescAttributes_t](./chs/cublaslt-datatypes-reference.md) | [cublasLtEmulationDescAttributes_t](./eng/cublaslt-datatypes-reference.md) |
| 3.4 | [cuBLASLt API 参考文档](./chs/cublaslt-api-reference.md) | [cuBLASLt API Reference](./eng/cublaslt-api-reference.md) |
| 3.4.1 | [cublasLtCreate()](./chs/cublasltcreate.md) | [cublasLtCreate()](./eng/cublasltcreate.md) |
| 3.4.2 | [cublasLtDestroy()](./chs/cublasltdestroy.md) | [cublasLtDestroy()](./eng/cublasltdestroy.md) |
| 3.4.3 | [cublasLtDisableCpuInstructionsSetMask()](./chs/cublasltdisablecpuinstructionssetmask.md) | [cublasLtDisableCpuInstructionsSetMask()](./eng/cublasltdisablecpuinstructionssetmask.md) |
| 3.4.4 | [cublasLtGetCudartVersion()](./chs/cublasltgetcudartversion.md) | [cublasLtGetCudartVersion()](./eng/cublasltgetcudartversion.md) |
| 3.4.5 | [cublasLtGetProperty()](./chs/cublasltgetproperty.md) | [cublasLtGetProperty()](./eng/cublasltgetproperty.md) |
| 3.4.6 | [cublasLtGetStatusName()](./chs/cublasltgetstatusname.md) | [cublasLtGetStatusName()](./eng/cublasltgetstatusname.md) |
| 3.4.7 | [cublasLtGetStatusString()](./chs/cublasltgetstatusstring.md) | [cublasLtGetStatusString()](./eng/cublasltgetstatusstring.md) |
| 3.4.8 | [cublasLtHeuristicsCacheGetCapacity()](./chs/cublasltheuristicscachegetcapacity.md) | [cublasLtHeuristicsCacheGetCapacity()](./eng/cublasltheuristicscachegetcapacity.md) |
| 3.4.9 | [cublasLtHeuristicsCacheSetCapacity()](./chs/cublasltheuristicscachesetcapacity.md) | [cublasLtHeuristicsCacheSetCapacity()](./eng/cublasltheuristicscachesetcapacity.md) |
| 3.4.10 | [cublasLtGetVersion()](./chs/cublasltgetversion.md) | [cublasLtGetVersion()](./eng/cublasltgetversion.md) |
| 3.4.11 | [cublasLtLoggerSetCallback()](./chs/cublaslt-api-reference.md) | [cublasLtLoggerSetCallback()](./eng/cublaslt-api-reference.md) |
| 3.4.12 | [cublasLtLoggerSetFile()](./chs/cublasltloggersetfile.md) | [cublasLtLoggerSetFile()](./eng/cublasltloggersetfile.md) |
| 3.4.13 | [cublasLtLoggerOpenFile()](./chs/cublasltloggeropenfile.md) | [cublasLtLoggerOpenFile()](./eng/cublasltloggeropenfile.md) |
| 3.4.14 | [cublasLtLoggerSetLevel()](./chs/cublasltloggersetlevel.md) | [cublasLtLoggerSetLevel()](./eng/cublasltloggersetlevel.md) |
| 3.4.15 | [cublasLtLoggerSetMask()](./chs/cublasltloggersetmask.md) | [cublasLtLoggerSetMask()](./eng/cublasltloggersetmask.md) |
| 3.4.16 | [cublasLtLoggerForceDisable()](./chs/cublasltloggerforcedisable.md) | [cublasLtLoggerForceDisable()](./eng/cublasltloggerforcedisable.md) |
| 3.4.17 | [cublasLtMatmul()](./chs/cublasltmatmul.md) | [cublasLtMatmul()](./eng/cublasltmatmul.md) |
| 3.4.18 | [cublasLtMatmulAlgoCapGetAttribute()](./chs/cublasltmatmulalgocapgetattribute.md) | [cublasLtMatmulAlgoCapGetAttribute()](./eng/cublasltmatmulalgocapgetattribute.md) |
| 3.4.19 | [cublasLtMatmulAlgoCheck()](./chs/cublasltmatmulalgocheck.md) | [cublasLtMatmulAlgoCheck()](./eng/cublasltmatmulalgocheck.md) |
| 3.4.20 | [cublasLtMatmulAlgoConfigGetAttribute()](./chs/cublasltmatmulalgoconfiggetattribute.md) | [cublasLtMatmulAlgoConfigGetAttribute()](./eng/cublasltmatmulalgoconfiggetattribute.md) |
| 3.4.21 | [cublasLtMatmulAlgoConfigSetAttribute()](./chs/cublasltmatmulalgoconfigsetattribute.md) | [cublasLtMatmulAlgoConfigSetAttribute()](./eng/cublasltmatmulalgoconfigsetattribute.md) |
| 3.4.22 | [cublasLtMatmulAlgoGetHeuristic()](./chs/cublasltmatmulalgogetheuristic.md) | [cublasLtMatmulAlgoGetHeuristic()](./eng/cublasltmatmulalgogetheuristic.md) |
| 3.4.23 | [cublasLtMatmulAlgoGetIds()](./chs/cublasltmatmulalgogetids.md) | [cublasLtMatmulAlgoGetIds()](./eng/cublasltmatmulalgogetids.md) |
| 3.4.24 | [cublasLtMatmulAlgoInit()](./chs/cublasltmatmulalgoinit.md) | [cublasLtMatmulAlgoInit()](./eng/cublasltmatmulalgoinit.md) |
| 3.4.25 | [cublasLtMatmulDescCreate()](./chs/cublasltmatmuldesccreate.md) | [cublasLtMatmulDescCreate()](./eng/cublasltmatmuldesccreate.md) |
| 3.4.26 | [cublasLtMatmulDescInit()](./chs/cublasltmatmuldescinit.md) | [cublasLtMatmulDescInit()](./eng/cublasltmatmuldescinit.md) |
| 3.4.27 | [cublasLtMatmulDescDestroy()](./chs/cublasltmatmuldescdestroy.md) | [cublasLtMatmulDescDestroy()](./eng/cublasltmatmuldescdestroy.md) |
| 3.4.28 | [cublasLtMatmulDescGetAttribute()](./chs/cublasltmatmuldescgetattribute.md) | [cublasLtMatmulDescGetAttribute()](./eng/cublasltmatmuldescgetattribute.md) |
| 3.4.29 | [cublasLtMatmulDescSetAttribute()](./chs/cublasltmatmuldescsetattribute.md) | [cublasLtMatmulDescSetAttribute()](./eng/cublasltmatmuldescsetattribute.md) |
| 3.4.30 | [cublasLtMatmulPreferenceCreate()](./chs/cublasltmatmulpreferencecreate.md) | [cublasLtMatmulPreferenceCreate()](./eng/cublasltmatmulpreferencecreate.md) |
| 3.4.31 | [cublasLtMatmulPreferenceInit()](./chs/cublasltmatmulpreferenceinit.md) | [cublasLtMatmulPreferenceInit()](./eng/cublasltmatmulpreferenceinit.md) |
| 3.4.32 | [cublasLtMatmulPreferenceDestroy()](./chs/cublasltmatmulpreferencedestroy.md) | [cublasLtMatmulPreferenceDestroy()](./eng/cublasltmatmulpreferencedestroy.md) |
| 3.4.33 | [cublasLtMatmulPreferenceGetAttribute()](./chs/cublasltmatmulpreferencegetattribute.md) | [cublasLtMatmulPreferenceGetAttribute()](./eng/cublasltmatmulpreferencegetattribute.md) |
| 3.4.34 | [cublasLtMatmulPreferenceSetAttribute()](./chs/cublasltmatmulpreferencesetattribute.md) | [cublasLtMatmulPreferenceSetAttribute()](./eng/cublasltmatmulpreferencesetattribute.md) |
| 3.4.35 | [cublasLtMatrixLayoutCreate()](./chs/cublasltmatrixlayoutcreate.md) | [cublasLtMatrixLayoutCreate()](./eng/cublasltmatrixlayoutcreate.md) |
| 3.4.36 | [cublasLtMatrixLayoutInit()](./chs/cublasltmatrixlayoutinit.md) | [cublasLtMatrixLayoutInit()](./eng/cublasltmatrixlayoutinit.md) |
| 3.4.37 | [cublasLtGroupedMatrixLayoutCreate()](./chs/cublasltgroupedmatrixlayoutcreate.md) | [cublasLtGroupedMatrixLayoutCreate()](./eng/cublasltgroupedmatrixlayoutcreate.md) |
| 3.4.38 | [cublasLtGroupedMatrixLayoutInit()](./chs/cublasltgroupedmatrixlayoutinit.md) | [cublasLtGroupedMatrixLayoutInit()](./eng/cublasltgroupedmatrixlayoutinit.md) |
| 3.4.39 | [cublasLtMatrixLayoutDestroy()](./chs/cublasltmatrixlayoutdestroy.md) | [cublasLtMatrixLayoutDestroy()](./eng/cublasltmatrixlayoutdestroy.md) |
| 3.4.40 | [cublasLtMatrixLayoutGetAttribute()](./chs/cublasltmatrixlayoutgetattribute.md) | [cublasLtMatrixLayoutGetAttribute()](./eng/cublasltmatrixlayoutgetattribute.md) |
| 3.4.41 | [cublasLtMatrixLayoutSetAttribute()](./chs/cublasltmatrixlayoutsetattribute.md) | [cublasLtMatrixLayoutSetAttribute()](./eng/cublasltmatrixlayoutsetattribute.md) |
| 3.4.42 | [cublasLtMatrixTransform()](./chs/cublasltmatrixtransform.md) | [cublasLtMatrixTransform()](./eng/cublasltmatrixtransform.md) |
| 3.4.43 | [cublasLtMatrixTransformDescCreate()](./chs/cublasltmatrixtransformdesccreate.md) | [cublasLtMatrixTransformDescCreate()](./eng/cublasltmatrixtransformdesccreate.md) |
| 3.4.44 | [cublasLtMatrixTransformDescInit()](./chs/cublasltmatrixtransformdescinit.md) | [cublasLtMatrixTransformDescInit()](./eng/cublasltmatrixtransformdescinit.md) |
| 3.4.45 | [cublasLtMatrixTransformDescDestroy()](./chs/cublasltmatrixtransformdescdestroy.md) | [cublasLtMatrixTransformDescDestroy()](./eng/cublasltmatrixtransformdescdestroy.md) |
| 3.4.46 | [cublasLtMatrixTransformDescGetAttribute()](./chs/cublasltmatrixtransformdescgetattribute.md) | [cublasLtMatrixTransformDescGetAttribute()](./eng/cublasltmatrixtransformdescgetattribute.md) |
| 3.4.47 | [cublasLtMatrixTransformDescSetAttribute()](./chs/cublasltmatrixtransformdescsetattribute.md) | [cublasLtMatrixTransformDescSetAttribute()](./eng/cublasltmatrixtransformdescsetattribute.md) |
| 3.4.48 | [cublasLtEmulationDescInit()](./chs/cublasltemulationdescinit.md) | [cublasLtEmulationDescInit()](./eng/cublasltemulationdescinit.md) |
| 3.4.49 | [cublasLtEmulationDescCreate()](./chs/cublasltemulationdesccreate.md) | [cublasLtEmulationDescCreate()](./eng/cublasltemulationdesccreate.md) |
| 3.4.50 | [cublasLtEmulationDescDestroy()](./chs/cublasltemulationdescdestroy.md) | [cublasLtEmulationDescDestroy()](./eng/cublasltemulationdescdestroy.md) |
| 3.4.51 | [cublasLtEmulationDescSetAttribute()](./chs/cublasltemulationdescsetattribute.md) | [cublasLtEmulationDescSetAttribute()](./eng/cublasltemulationdescsetattribute.md) |
| 3.4.52 | [cublasLtEmulationDescGetAttribute()](./chs/cublasltemulationdescgetattribute.md) | [cublasLtEmulationDescGetAttribute()](./eng/cublasltemulationdescgetattribute.md) |

---

## 翻译状态 / Translation Status

| 状态 Status | 数量 Count |
|-------------|------------|
| ✅ 已完成 / Completed | 98 |
| ⏳ 未转换 / Not converted | 0 |
| **总计 Total** | **98** |

---

## 版权声明 / Copyright Notice

本翻译仅供学习研究使用，原文档版权归 NVIDIA Corporation 所有。

This translation is for study and research purposes only. Original documentation copyright NVIDIA Corporation.
