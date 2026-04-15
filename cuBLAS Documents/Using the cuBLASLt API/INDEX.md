# Using the cuBLASLt API (3.)

## 文档索引 / Documentation Index

本手册为 NVIDIA cuBLAS 13.2 Using the cuBLASLt API 的中文翻译版本。

**来源 / Source:** NVIDIA cuBLAS Library Documentation - Section 3

---

## 双语目录对照 / Bilingual Table of Contents

### 03
*第三章 使用 cuBLASLt API*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 3 使用 cuBLASLt API | 3. Using the cuBLASLt API | [ch03.md](./chs/ch03.md) | [ch03.md](./eng/ch03.md) |
| 3.1 一般描述 | 3.1. General Description | [ch03s01.md](./chs/ch03s01.md) | [ch03s01.md](./eng/ch03s01.md) |
| 3.1.1 问题大小限制 | 3.1.1. Problem Size Limitations | [ch03s01s01.md](./chs/ch03s01s01.md) | [ch03s01s01.md](./eng/ch03s01s01.md) |
| 3.1.2 启发式缓存 | 3.1.2. Heuristics Cache | [ch03s01s02.md](./chs/ch03s01s02.md) | [ch03s01s02.md](./eng/ch03s01s02.md) |
| 3.1.3 cuBLASLt 日志记录 | 3.1.3. cuBLASLt Logging | [ch03s01s03.md](./chs/ch03s01s03.md) | [ch03s01s03.md](./eng/ch03s01s03.md) |
| 3.1.4 窄精度数据类型使用 | 3.1.4. Narrow Precision Data Types Usage | [ch03s01s04.md](./chs/ch03s01s04.md) | [ch03s01s04.md](./eng/ch03s01s04.md) |
| 3.1.5 禁用 CPU 指令 | 3.1.5. Disabling CPU Instructions | [ch03s01s05.md](./chs/ch03s01s05.md) | [ch03s01s05.md](./eng/ch03s01s05.md) |
| 3.2 cuBLASLt 代码示例 | 3.2. cuBLASLt Code Examples | [ch03s02.md](./chs/ch03s02.md) | [ch03s02.md](./eng/ch03s02.md) |
| 3.3 cuBLASLt 数据类型参考 | 3.3. cuBLASLt Datatypes Reference | [ch03s03.md](./chs/ch03s03.md) | [ch03s03.md](./eng/ch03s03.md) |
| 3.3.1 cublasLtClusterShape_t | 3.3.1. cublasLtClusterShape_t | [ch03s03s01.md](./chs/ch03s03s01.md) | [ch03s03s01.md](./eng/ch03s03s01.md) |
| 3.3.2 cublasLtEpilogue_t | 3.3.2. cublasLtEpilogue_t | [ch03s03s02.md](./chs/ch03s03s02.md) | [ch03s03s02.md](./eng/ch03s03s02.md) |
| 3.3.3 cublasLtHandle_t | 3.3.3. cublasLtHandle_t | [ch03s03s03.md](./chs/ch03s03s03.md) | [ch03s03s03.md](./eng/ch03s03s03.md) |
| 3.3.4 cublasLtLoggerCallback_t | 3.3.4. cublasLtLoggerCallback_t | [ch03s03s04.md](./chs/ch03s03s04.md) | [ch03s03s04.md](./eng/ch03s03s04.md) |
| 3.3.5 cublasLtMatmulAlgo_t | 3.3.5. cublasLtMatmulAlgo_t | [ch03s03s05.md](./chs/ch03s03s05.md) | [ch03s03s05.md](./eng/ch03s03s05.md) |
| 3.3.6 cublasLtMatmulAlgoCapAttributes_t | 3.3.6. cublasLtMatmulAlgoCapAttributes_t | [ch03s03s06.md](./chs/ch03s03s06.md) | [ch03s03s06.md](./eng/ch03s03s06.md) |
| 3.3.7 cublasLtMatmulAlgoConfigAttributes_t | 3.3.7. cublasLtMatmulAlgoConfigAttributes_t | [ch03s03s07.md](./chs/ch03s03s07.md) | [ch03s03s07.md](./eng/ch03s03s07.md) |
| 3.3.8 cublasLtMatmulDesc_t | 3.3.8. cublasLtMatmulDesc_t | [ch03s03s08.md](./chs/ch03s03s08.md) | [ch03s03s08.md](./eng/ch03s03s08.md) |
| 3.3.9 cublasLtMatmulDescAttributes_t | 3.3.9. cublasLtMatmulDescAttributes_t | [ch03s03s09.md](./chs/ch03s03s09.md) | [ch03s03s09.md](./eng/ch03s03s09.md) |
| 3.3.10 cublasLtMatmulHeuristicResult_t | 3.3.10. cublasLtMatmulHeuristicResult_t | [ch03s03s10.md](./chs/ch03s03s10.md) | [ch03s03s10.md](./eng/ch03s03s10.md) |
| 3.3.11 cublasLtMatmulInnerShape_t | 3.3.11. cublasLtMatmulInnerShape_t | [ch03s03s11.md](./chs/ch03s03s11.md) | [ch03s03s11.md](./eng/ch03s03s11.md) |
| 3.3.12 cublasLtMatmulPreference_t | 3.3.12. cublasLtMatmulPreference_t | [ch03s03s12.md](./chs/ch03s03s12.md) | [ch03s03s12.md](./eng/ch03s03s12.md) |
| 3.3.13 cublasLtMatmulPreferenceAttributes_t | 3.3.13. cublasLtMatmulPreferenceAttributes_t | [ch03s03s13.md](./chs/ch03s03s13.md) | [ch03s03s13.md](./eng/ch03s03s13.md) |
| 3.3.14 cublasLtMatmulSearch_t | 3.3.14. cublasLtMatmulSearch_t | [ch03s03s14.md](./chs/ch03s03s14.md) | [ch03s03s14.md](./eng/ch03s03s14.md) |
| 3.3.15 cublasLtMatmulTile_t | 3.3.15. cublasLtMatmulTile_t | [ch03s03s15.md](./chs/ch03s03s15.md) | [ch03s03s15.md](./eng/ch03s03s15.md) |
| 3.3.16 cublasLtMatmulStages_t | 3.3.16. cublasLtMatmulStages_t | [ch03s03s16.md](./chs/ch03s03s16.md) | [ch03s03s16.md](./eng/ch03s03s16.md) |
| 3.3.17 cublasLtNumericalImplFlags_t | 3.3.17. cublasLtNumericalImplFlags_t | [ch03s03s17.md](./chs/ch03s03s17.md) | [ch03s03s17.md](./eng/ch03s03s17.md) |
| 3.3.18 cublasLtMatrixLayout_t | 3.3.18. cublasLtMatrixLayout_t | [ch03s03s18.md](./chs/ch03s03s18.md) | [ch03s03s18.md](./eng/ch03s03s18.md) |
| 3.3.19 cublasLtMatrixLayoutAttribute_t | 3.3.19. cublasLtMatrixLayoutAttribute_t | [ch03s03s19.md](./chs/ch03s03s19.md) | [ch03s03s19.md](./eng/ch03s03s19.md) |
| 3.3.20 cublasLtIntegerWidth_t | 3.3.20. cublasLtIntegerWidth_t | [ch03s03s20.md](./chs/ch03s03s20.md) | [ch03s03s20.md](./eng/ch03s03s20.md) |
| 3.3.21 cublasLtMatrixTransformDesc_t | 3.3.21. cublasLtMatrixTransformDesc_t | [ch03s03s21.md](./chs/ch03s03s21.md) | [ch03s03s21.md](./eng/ch03s03s21.md) |
| 3.3.22 cublasLtMatrixTransformDescAttributes_t | 3.3.22. cublasLtMatrixTransformDescAttributes_t | [ch03s03s22.md](./chs/ch03s03s22.md) | [ch03s03s22.md](./eng/ch03s03s22.md) |
| 3.3.23 cublasLtOrder_t | 3.3.23. cublasLtOrder_t | [ch03s03s23.md](./chs/ch03s03s23.md) | [ch03s03s23.md](./eng/ch03s03s23.md) |
| 3.3.24 cublasLtPointerMode_t | 3.3.24. cublasLtPointerMode_t | [ch03s03s24.md](./chs/ch03s03s24.md) | [ch03s03s24.md](./eng/ch03s03s24.md) |
| 3.3.25 cublasLtPointerModeMask_t | 3.3.25. cublasLtPointerModeMask_t | [ch03s03s25.md](./chs/ch03s03s25.md) | [ch03s03s25.md](./eng/ch03s03s25.md) |
| 3.4 cuBLASLt API 辅助函数参考 | 3.4. cuBLASLt API Helper Function Reference | [ch03s04.md](./chs/ch03s04.md) | [ch03s04.md](./eng/ch03s04.md) |
| 3.5 cuBLASLt Matmul 函数参考 | 3.5. cuBLASLt Matmul Function Reference | [ch03s05.md](./chs/ch03s05.md) | [ch03s05.md](./eng/ch03s05.md) |
| 3.6 cuBLASLt 矩阵转换函数参考 | 3.6. cuBLASLt Matrix Transformation Function Reference | [ch03s06.md](./chs/ch03s06.md) | [ch03s06.md](./eng/ch03s06.md) |

---

## 转换状态统计 / Conversion Status Summary

| 状态 Status | 数量 Count |
|-------------|------------|
| ✅ 已完成 / Completed | 0 |
| ⏳ 翻译中 / Translating | 0 |
| ⏳ 未转换 / Not converted | 40 |
| **总计 Total** | **40** |

---

## 版权声明 / Copyright Notice

本翻译仅供学习研究使用，原文档版权归 NVIDIA Corporation 所有。

This translation is for study and research purposes only. Original documentation copyright NVIDIA Corporation.
