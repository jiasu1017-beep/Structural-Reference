# Using the cuBLASLt API

## 使用 cuBLASLt API

**来源 / Source:** NVIDIA cuBLAS Library Documentation - Using the cuBLASLt API

---

## 双语目录对照 / Bilingual Table of Contents

| 章节号 | 中文 Chinese | 英文 English |
|--------|--------------|--------------|
| 2.1.4 | [结果可重现性](./chs/results-reproducibility.md) | [Results Reproducibility](./eng/results-reproducibility.md) |
| 3 | [Using the cuBLASLt API](./chs/using-the-cublaslt-api.md) | [Using the cuBLASLt API](./eng/using-the-cublaslt-api.md) |
| 3.1.3 | [cuBLASLt 日志记录](./chs/cublaslt-logging.md) | [cuBLASLt Logging](./eng/cublaslt-logging.md) |
| 3.2 | [cuBLASLt 代码示例](./chs/cublaslt-code-examples.md) | [cuBLASLt Code Examples](./eng/cublaslt-code-examples.md) |
| 3.3 | [cuBLASLt Datatypes Reference](./chs/cublaslt-datatypes-reference.md) | [cuBLASLt Datatypes Reference](./eng/cublaslt-datatypes-reference.md) |
| 3.3.1 | [cublasLtClusterShape_t](./chs/cublasltclustershape-t.md) | [cublasLtClusterShape_t](./eng/cublasltclustershape-t.md) |
| 3.3.2 | [cublasLtEpilogue_t](./chs/cublasltepilogue-t.md) | [cublasLtEpilogue_t](./eng/cublasltepilogue-t.md) |
| 3.3.3 | [cublasLtHandle_t](./chs/cublaslthandle-t.md) | [cublasLtHandle_t](./eng/cublaslthandle-t.md) |
| 3.3.5 | [cublasLtMatmulAlgo_t](./chs/cublasltmatmulalgo-t.md) | [cublasLtMatmulAlgo_t](./eng/cublasltmatmulalgo-t.md) |
| 3.3.6 | [cublasLtMatmulAlgoCapAttributes_t](./chs/cublasltmatmulalgocapattributes-t.md) | [cublasLtMatmulAlgoCapAttributes_t](./eng/cublasltmatmulalgocapattributes-t.md) |
| 3.3.7 | [cublasLtMatmulAlgoConfigAttributes_t](./chs/cublasltmatmulalgoconfigattributes-t.md) | [cublasLtMatmulAlgoConfigAttributes_t](./eng/cublasltmatmulalgoconfigattributes-t.md) |
| 3.3.8 | [cublasLtMatmulDesc_t](./chs/cublasltmatmuldesc-t.md) | [cublasLtMatmulDesc_t](./eng/cublasltmatmuldesc-t.md) |
| 3.3.9 | [cublasLtMatmulDescAttributes_t](./chs/cublasltmatmuldescattributes-t.md) | [cublasLtMatmulDescAttributes_t](./eng/cublasltmatmuldescattributes-t.md) |
| 3.3.10 | [cublasLtMatmulHeuristicResult_t](./chs/cublasltmatmulheuristicresult-t.md) | [cublasLtMatmulHeuristicResult_t](./eng/cublasltmatmulheuristicresult-t.md) |
| 3.3.11 | [cublasLtMatmulInnerShape_t](./chs/cublasltmatmulinnershape-t.md) | [cublasLtMatmulInnerShape_t](./eng/cublasltmatmulinnershape-t.md) |
| 3.3.12 | [cublasLtMatmulPreference_t](./chs/cublasltmatmulpreference-t.md) | [cublasLtMatmulPreference_t](./eng/cublasltmatmulpreference-t.md) |
| 3.3.13 | [cublasLtMatmulPreferenceAttributes_t](./chs/cublasltmatmulpreferenceattributes-t.md) | [cublasLtMatmulPreferenceAttributes_t](./eng/cublasltmatmulpreferenceattributes-t.md) |
| 3.3.14 | [cublasLtMatmulSearch_t](./chs/cublasltmatmulsearch-t.md) | [cublasLtMatmulSearch_t](./eng/cublasltmatmulsearch-t.md) |
| 3.3.15 | [cublasLtMatmulTile_t](./chs/cublasltmatmultile-t.md) | [cublasLtMatmulTile_t](./eng/cublasltmatmultile-t.md) |
| 3.3.16 | [cublasLtMatmulStages_t](./chs/cublasltmatmulstages-t.md) | [cublasLtMatmulStages_t](./eng/cublasltmatmulstages-t.md) |
| 3.3.17 | [cublasLtNumericalImplFlags_t](./chs/cublasltnumericalimplflags-t.md) | [cublasLtNumericalImplFlags_t](./eng/cublasltnumericalimplflags-t.md) |
| 3.3.18 | [cublasLtMatrixLayout_t](./chs/cublasltmatrixlayout-t.md) | [cublasLtMatrixLayout_t](./eng/cublasltmatrixlayout-t.md) |
| 3.3.19 | [cublasLtMatrixLayoutAttribute_t](./chs/cublasltmatrixlayoutattribute-t.md) | [cublasLtMatrixLayoutAttribute_t](./eng/cublasltmatrixlayoutattribute-t.md) |
| 3.3.20 | [cublasLtIntegerWidth_t](./chs/cublasltintegerwidth-t.md) | [cublasLtIntegerWidth_t](./eng/cublasltintegerwidth-t.md) |
| 3.3.21 | [cublasLtMatrixTransformDesc_t¶](./chs/cublasltmatrixtransformdesc-t.md) | [cublasLtMatrixTransformDesc_t](./eng/cublasltmatrixtransformdesc-t.md) |
| 3.3.22 | [cublasLtMatrixTransformDescAttributes_t](./chs/cublasltmatrixtransformdescattributes-t.md) | [cublasLtMatrixTransformDescAttributes_t](./eng/cublasltmatrixtransformdescattributes-t.md) |
| 3.3.23 | [cublasLtOrder_t](./chs/cublasltorder-t.md) | [cublasLtOrder_t](./eng/cublasltorder-t.md) |
| 3.3.24 | [cublasLtPointerMode_t](./chs/cublasltpointermode-t.md) | [cublasLtPointerMode_t](./eng/cublasltpointermode-t.md) |
| 3.3.25 | [cublasLtPointerModeMask_t](./chs/cublasltpointermodemask-t.md) | [cublasLtPointerModeMask_t](./eng/cublasltpointermodemask-t.md) |
| 3.3.26 | [cublasLtReductionScheme_t](./chs/cublasltreductionscheme-t.md) | [cublasLtReductionScheme_t](./eng/cublasltreductionscheme-t.md) |
| 3.3.27 | [cublasLtMatmulMatrixScale_t](./chs/cublasltmatmulmatrixscale-t.md) | [cublasLtMatmulMatrixScale_t](./eng/cublasltmatmulmatrixscale-t.md) |
| 3.3.28 | [cublasLtBatchMode_t](./chs/cublasltbatchmode-t.md) | [cublasLtBatchMode_t](./eng/cublasltbatchmode-t.md) |
| 3.3.29 | [cublasLtEmulationDesc_t](./chs/cublasltemulationdesc-t.md) | [cublasLtEmulationDesc_t](./eng/cublasltemulationdesc-t.md) |
| 3.3.30 | [cublasLtEmulationDescAttributes_t](./chs/cublasltemulationdescattributes-t.md) | [cublasLtEmulationDescAttributes_t](./eng/cublasltemulationdescattributes-t.md) |
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
| ✅ 已完成 / Completed | 86 |
| ⏳ 未转换 / Not converted | 0 |
| **总计 Total** | **86** |

---

## 版权声明 / Copyright Notice

本翻译仅供学习研究使用，原文档版权归 NVIDIA Corporation 所有。

This translation is for study and research purposes only. Original documentation copyright NVIDIA Corporation.
