# Using the cuBLASXt API (4.)

## 文档索引 / Documentation Index

本手册为 NVIDIA cuBLAS 13.2 Using the cuBLASXt API 的中文翻译版本。

**来源 / Source:** NVIDIA cuBLAS Library Documentation - Section 4

---

## 双语目录对照 / Bilingual Table of Contents

### 04
*第四章 使用 cuBLASXt API*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 4 使用 cuBLASXt API | 4. Using the cuBLASXt API | [ch04.md](./chs/ch04.md) | [ch04.md](./eng/ch04.md) |
| 4.1 一般描述 | 4.1. General description | [ch04s01.md](./chs/ch04s01.md) | [ch04s01.md](./eng/ch04s01.md) |
| 4.1.1 平铺设计方法 | 4.1.1. Tiling design approach | [ch04s01s01.md](./chs/ch04s01s01.md) | [ch04s01s01.md](./eng/ch04s01s01.md) |
| 4.1.2 混合 CPU-GPU 计算 | 4.1.2. Hybrid CPU-GPU computation | [ch04s01s02.md](./chs/ch04s01s02.md) | [ch04s01s02.md](./eng/ch04s01s02.md) |
| 4.1.3 结果可重现性 | 4.1.3. Results reproducibility | [ch04s01s03.md](./chs/ch04s01s03.md) | [ch04s01s03.md](./eng/ch04s01s03.md) |
| 4.2 cuBLASXt API 数据类型参考 | 4.2. cuBLASXt API Datatypes Reference | [ch04s02.md](./chs/ch04s02.md) | [ch04s02.md](./eng/ch04s02.md) |
| 4.2.1 cublasXtHandle_t | 4.2.1. cublasXtHandle_t | [ch04s02s01.md](./chs/ch04s02s01.md) | [ch04s02s01.md](./eng/ch04s02s01.md) |
| 4.2.2 cublasXtOpType_t | 4.2.2. cublasXtOpType_t | [ch04s02s02.md](./chs/ch04s02s02.md) | [ch04s02s02.md](./eng/ch04s02s02.md) |
| 4.2.3 cublasXtBlasOp_t | 4.2.3. cublasXtBlasOp_t | [ch04s02s03.md](./chs/ch04s02s03.md) | [ch04s02s03.md](./eng/ch04s02s03.md) |
| 4.2.4 cublasXtPinningMemMode_t | 4.2.4. cublasXtPinningMemMode_t | [ch04s02s04.md](./chs/ch04s02s04.md) | [ch04s02s04.md](./eng/ch04s02s04.md) |
| 4.3 cuBLASXt API 辅助函数参考 | 4.3. cuBLASXt API Helper Function Reference | [ch04s03.md](./chs/ch04s03.md) | [ch04s03.md](./eng/ch04s03.md) |
| 4.3.1 cublasXtCreate() | 4.3.1. cublasXtCreate() | [ch04s03s01.md](./chs/ch04s03s01.md) | [ch04s03s01.md](./eng/ch04s03s01.md) |
| 4.3.2 cublasXtDestroy() | 4.3.2. cublasXtDestroy() | [ch04s03s02.md](./chs/ch04s03s02.md) | [ch04s03s02.md](./eng/ch04s03s02.md) |
| 4.3.3 cublasXtDeviceSelect() | 4.3.3. cublasXtDeviceSelect() | [ch04s03s03.md](./chs/ch04s03s03.md) | [ch04s03s03.md](./eng/ch04s03s03.md) |
| 4.3.4 cublasXtSetBlockDim() | 4.3.4. cublasXtSetBlockDim() | [ch04s03s04.md](./chs/ch04s03s04.md) | [ch04s03s04.md](./eng/ch04s03s04.md) |
| 4.3.5 cublasXtGetBlockDim() | 4.3.5. cublasXtGetBlockDim() | [ch04s03s05.md](./chs/ch04s03s05.md) | [ch04s03s05.md](./eng/ch04s03s05.md) |
| 4.3.6 cublasXtSetCpuRoutine() | 4.3.6. cublasXtSetCpuRoutine() | [ch04s03s06.md](./chs/ch04s03s06.md) | [ch04s03s06.md](./eng/ch04s03s06.md) |
| 4.3.7 cublasXtSetCpuRatio() | 4.3.7. cublasXtSetCpuRatio() | [ch04s03s07.md](./chs/ch04s03s07.md) | [ch04s03s07.md](./eng/ch04s03s07.md) |
| 4.3.8 cublasXtSetPinningMemMode() | 4.3.8. cublasXtSetPinningMemMode() | [ch04s03s08.md](./chs/ch04s03s08.md) | [ch04s03s08.md](./eng/ch04s03s08.md) |
| 4.3.9 cublasXtGetPinningMemMode() | 4.3.9. cublasXtGetPinningMemMode() | [ch04s03s09.md](./chs/ch04s03s09.md) | [ch04s03s09.md](./eng/ch04s03s09.md) |
| 4.4 cuBLASXt API 数学函数参考 | 4.4. cuBLASXt API Math Functions Reference | [ch04s04.md](./chs/ch04s04.md) | [ch04s04.md](./eng/ch04s04.md) |
| 4.4.1 cublasXt<t>gemm() | 4.4.1. cublasXt<t>gemm() | [ch04s04s01.md](./chs/ch04s04s01.md) | [ch04s04s01.md](./eng/ch04s04s01.md) |
| 4.4.2 cublasXt<t>hemm() | 4.4.2. cublasXt<t>hemm() | [ch04s04s02.md](./chs/ch04s04s02.md) | [ch04s04s02.md](./eng/ch04s04s02.md) |
| 4.4.3 cublasXt<t>symm() | 4.4.3. cublasXt<t>symm() | [ch04s04s03.md](./chs/ch04s04s03.md) | [ch04s04s03.md](./eng/ch04s04s03.md) |
| 4.4.4 cublasXt<t>syrk() | 4.4.4. cublasXt<t>syrk() | [ch04s04s04.md](./chs/ch04s04s04.md) | [ch04s04s04.md](./eng/ch04s04s04.md) |
| 4.4.5 cublasXt<t>syr2k() | 4.4.5. cublasXt<t>syr2k() | [ch04s04s05.md](./chs/ch04s04s05.md) | [ch04s04s05.md](./eng/ch04s04s05.md) |
| 4.4.6 cublasXt<t>syrkx() | 4.4.6. cublasXt<t>syrkx() | [ch04s04s06.md](./chs/ch04s04s06.md) | [ch04s04s06.md](./eng/ch04s04s06.md) |
| 4.4.7 cublasXt<t>herk() | 4.4.7. cublasXt<t>herk() | [ch04s04s07.md](./chs/ch04s04s07.md) | [ch04s04s07.md](./eng/ch04s04s07.md) |
| 4.4.8 cublasXt<t>her2k() | 4.4.8. cublasXt<t>her2k() | [ch04s04s08.md](./chs/ch04s04s08.md) | [ch04s04s08.md](./eng/ch04s04s08.md) |
| 4.4.9 cublasXt<t>herkx() | 4.4.9. cublasXt<t>herkx() | [ch04s04s09.md](./chs/ch04s04s09.md) | [ch04s04s09.md](./eng/ch04s04s09.md) |
| 4.4.10 cublasXt<t>trsm() | 4.4.10. cublasXt<t>trsm() | [ch04s04s10.md](./chs/ch04s04s10.md) | [ch04s04s10.md](./eng/ch04s04s10.md) |
| 4.4.11 cublasXt<t>trmm() | 4.4.11. cublasXt<t>trmm() | [ch04s04s11.md](./chs/ch04s04s11.md) | [ch04s04s11.md](./eng/ch04s04s11.md) |
| 4.4.12 cublasXt<t>spmm() | 4.4.12. cublasXt<t>spmm() | [ch04s04s12.md](./chs/ch04s04s12.md) | [ch04s04s12.md](./eng/ch04s04s12.md) |

---

## 转换状态统计 / Conversion Status Summary

| 状态 Status | 数量 Count |
|-------------|------------|
| ✅ 已完成 / Completed | 0 |
| ⏳ 翻译中 / Translating | 0 |
| ⏳ 未转换 / Not converted | 27 |
| **总计 Total** | **27** |

---

## 版权声明 / Copyright Notice

本翻译仅供学习研究使用，原文档版权归 NVIDIA Corporation 所有。

This translation is for study and research purposes only. Original documentation copyright NVIDIA Corporation.
