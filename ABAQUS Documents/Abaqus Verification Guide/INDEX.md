# Abaqus Verification Guide (6.14)

## 文档索引 / Documentation Index

本手册为 ABAQUS 6.14 Verification Guide 的中文翻译版本。
This is the Chinese translation of the Abaqus 6.14 Verification Guide documentation.

**来源 / Source:** D:/SIMULIA/Documentation/docs/v6.14/books/ver

---

## 双语目录对照 / Bilingual Table of Contents

### Chapter 01: # 1 Element Verification

| Section | Title | English | Chinese |
|---------|-------|---------|---------|
| 01s01 | # 1.1 Overview | [eng/ch01s01.md](./eng/ch01s01.md) | [chs/ch01s01.md](./chs/ch01s01.md) |
| 01s02 | # 1.2 Eigenvalue tests | [eng/ch01s02.md](./eng/ch01s02.md) | [chs/ch01s02.md](./chs/ch01s02.md) |
| 01s03 | # 1.3 Simple load tests | [eng/ch01s03.md](./eng/ch01s03.md) | [chs/ch01s03.md](./chs/ch01s03.md) |
| 01s04 | # 1.4 Element loading options | [eng/ch01s04.md](./eng/ch01s04.md) | [chs/ch01s04.md](./chs/ch01s04.md) |
| 01s05 | # 1.5 Patch tests | [eng/ch01s05.md](./eng/ch01s05.md) | [chs/ch01s05.md](./chs/ch01s05.md) |
| 01s06 | # 1.6 Contact tests | [eng/ch01s06.md](./eng/ch01s06.md) | [chs/ch01s06.md](./chs/ch01s06.md) |
| 01s07 | # 1.7 Interface tests | [eng/ch01s07.md](./eng/ch01s07.md) | [chs/ch01s07.md](./chs/ch01s07.md) |
| 01s08 | # 1.8 Rigid body verification | [eng/ch01s08.md](./eng/ch01s08.md) | [chs/ch01s08.md](./chs/ch01s08.md) |
| 01s09 | # 1.9 Connector element verification | [eng/ch01s09.md](./eng/ch01s09.md) | [chs/ch01s09.md](./chs/ch01s09.md) |
| 01s10 | # 1.10 Special-purpose stress/displacement elements | [eng/ch01s10.md](./eng/ch01s10.md) | [chs/ch01s10.md](./chs/ch01s10.md) |
| 01s11 | # 1.11 Miscellaneous tests | [eng/ch01s11.md](./eng/ch01s11.md) | [chs/ch01s11.md](./chs/ch01s11.md) |

### Chapter 02: # 2 Material Verification

| Section | Title | English | Chinese |
|---------|-------|---------|---------|
| 02s01 | # 2.1 Overview | [eng/ch02s01.md](./eng/ch02s01.md) | [chs/ch02s01.md](./chs/ch02s01.md) |
| 02s02 | # 2.2 Mechanical properties | [eng/ch02s02.md](./eng/ch02s02.md) | [chs/ch02s02.md](./chs/ch02s02.md) |
| 02s03 | # 2.3 Thermal properties | [eng/ch02s03.md](./eng/ch02s03.md) | [chs/ch02s03.md](./chs/ch02s03.md) |

### Chapter 03: # 3 Analysis Procedures and Techniques

| Section | Title | English | Chinese |
|---------|-------|---------|---------|
| 03s01 | # 3.1 Overview | [eng/ch03s01.md](./eng/ch03s01.md) | [chs/ch03s01.md](./chs/ch03s01.md) |
| 03s02 | # 3.2 Dynamic analysis | [eng/ch03s02.md](./eng/ch03s02.md) | [chs/ch03s02.md](./chs/ch03s02.md) |
| 03s03 | # 3.3 Fluid dynamic analysis | [eng/ch03s03.md](./eng/ch03s03.md) | [chs/ch03s03.md](./chs/ch03s03.md) |
| 03s04 | # 3.4 Crack propagation | [eng/ch03s04.md](./eng/ch03s04.md) | [chs/ch03s04.md](./chs/ch03s04.md) |
| 03s05 | # 3.5 Substructuring | [eng/ch03s05.md](./eng/ch03s05.md) | [chs/ch03s05.md](./chs/ch03s05.md) |
| 03s06 | # 3.6 Electromagnetic analysis | [eng/ch03s06.md](./eng/ch03s06.md) | [chs/ch03s06.md](./chs/ch03s06.md) |
| 03s07 | # 3.7 Piezoelectric analysis | [eng/ch03s07.md](./eng/ch03s07.md) | [chs/ch03s07.md](./chs/ch03s07.md) |
| 03s08 | # 3.8 Submodeling | [eng/ch03s08.md](./eng/ch03s08.md) | [chs/ch03s08.md](./chs/ch03s08.md) |
| 03s09 | # 3.9 Acoustic and shock analyses | [eng/ch03s09.md](./eng/ch03s09.md) | [chs/ch03s09.md](./chs/ch03s09.md) |
| 03s10 | # 3.10 Model change | [eng/ch03s10.md](./eng/ch03s10.md) | [chs/ch03s10.md](./chs/ch03s10.md) |
| 03s11 | # 3.11 Symmetric model generation and analysis of cyclic symmetry models | [eng/ch03s11.md](./eng/ch03s11.md) | [chs/ch03s11.md](./chs/ch03s11.md) |
| 03s12 | # 3.12 Abaqus/Aqua analysis | [eng/ch03s12.md](./eng/ch03s12.md) | [chs/ch03s12.md](./chs/ch03s12.md) |
| 03s13 | # 3.13 Design sensitivity analysis | [eng/ch03s13.md](./eng/ch03s13.md) | [chs/ch03s13.md](./chs/ch03s13.md) |
| 03s14 | # 3.14 Transferring results between Abaqus/Standard and Abaqus/Explicit | [eng/ch03s14.md](./eng/ch03s14.md) | [chs/ch03s14.md](./chs/ch03s14.md) |
| 03s15 | # 3.15 Transferring results between dissimilar meshes | [eng/ch03s15.md](./eng/ch03s15.md) | [chs/ch03s15.md](./chs/ch03s15.md) |
| 03s16 | # 3.16 Direct cyclic analysis | [eng/ch03s16.md](./eng/ch03s16.md) | [chs/ch03s16.md](./chs/ch03s16.md) |
| 03s17 | # 3.17 Meshed beam cross-sections | [eng/ch03s17.md](./eng/ch03s17.md) | [chs/ch03s17.md](./chs/ch03s17.md) |
| 03s18 | # 3.18 Complex eigenvalue extraction | [eng/ch03s18.md](./eng/ch03s18.md) | [chs/ch03s18.md](./chs/ch03s18.md) |
| 03s19 | # 3.19 Eulerian analysis | [eng/ch03s19.md](./eng/ch03s19.md) | [chs/ch03s19.md](./chs/ch03s19.md) |
| 03s20 | # 3.20 Smoothed particle hydrodynamic analysis | [eng/ch03s20.md](./eng/ch03s20.md) | [chs/ch03s20.md](./chs/ch03s20.md) |
| 03s21 | # 3.21 Co-simulation | [eng/ch03s21.md](./eng/ch03s21.md) | [chs/ch03s21.md](./chs/ch03s21.md) |
| 03s22 | # 3.22 Adaptive remeshing | [eng/ch03s22.md](./eng/ch03s22.md) | [chs/ch03s22.md](./chs/ch03s22.md) |
| 03s23 | # 3.23 Frequency extraction using the AMS eigensolver | [eng/ch03s23.md](./eng/ch03s23.md) | [chs/ch03s23.md](./chs/ch03s23.md) |
| 03s24 | # 3.24 Steady-state dynamics with nondiagonal damping using the AMS eigensolver | [eng/ch03s24.md](./eng/ch03s24.md) | [chs/ch03s24.md](./chs/ch03s24.md) |
| 03s25 | # 3.25 Periodic media analysis | [eng/ch03s25.md](./eng/ch03s25.md) | [chs/ch03s25.md](./chs/ch03s25.md) |
| 03s26 | # 3.26 Discrete element method analysis | [eng/ch03s26.md](./eng/ch03s26.md) | [chs/ch03s26.md](./chs/ch03s26.md) |

### Chapter 04: # 4 User Subroutines

| Section | Title | English | Chinese |
|---------|-------|---------|---------|
| 04s01 | # 4.1 User subroutines | [eng/ch04s01.md](./eng/ch04s01.md) | [chs/ch04s01.md](./chs/ch04s01.md) |

### Chapter 05: # 5 Miscellaneous Options

| Section | Title | English | Chinese |
|---------|-------|---------|---------|
| 05s01 | # 5.1 Miscellaneous modeling options | [eng/ch05s01.md](./eng/ch05s01.md) | [chs/ch05s01.md](./chs/ch05s01.md) |
| 05s02 | # 5.2 Miscellaneous output options | [eng/ch05s02.md](./eng/ch05s02.md) | [chs/ch05s02.md](./chs/ch05s02.md) |

---

## 资源文件 / Resource Files

| 目录 Directory | 说明 Description |
|---------------|-----------------|
| eng/ | 英文原文件 English source files |
| chs/ | 中文翻译文件 Chinese translated files |
| graphics/ | 图片资源 Image resources |

---

## 统计信息 / Statistics

| 项目 Item | 数量 Count |
|---------|-----------|
| HTML源文件 | 414 |
| 英文文件 | 414 (eng/) |
| 中文文件 | 414 (chs/) |

---

## 版权声明 / Copyright Notice

本翻译仅供学习研究使用，原文档版权归 Dassault Systèmes Simulia Corp. 所有。
This translation is for study and research purposes only. Original documentation copyright Dassault Systèmes Simulia Corp.
