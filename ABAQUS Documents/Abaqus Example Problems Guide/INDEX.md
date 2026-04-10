# Abaqus Example Problems Guide (6.14)

## 文档索引 / Documentation Index

本手册为 ABAQUS 6.14 Example Problems Guide 的中文翻译版本。
This is the Chinese translation of the Abaqus 6.14 Example Problems Guide documentation.

**来源 / Source:** D:/SIMULIA/Documentation/docs/v6.14/books/exa

---

## 双语目录对照 / Bilingual Table of Contents

### 第01章：静力与准静力应力分析 / Static Stress/Displacement Analyses

| 章节 Section | 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|--------------|----------------|-----------------|-----------------|-----------------|
| 1.1 | 静力与准静力应力分析 | Static and quasi-static stress analyses | [chs/ch01s01.md](./chs/ch01s01.md) | [eng/ch01s01.md](./eng/ch01s01.md) |
| 1.2 | 屈曲与坍塌分析 | Buckling and collapse analyses | [chs/ch01s02.md](./chs/ch01s02.md) | [eng/ch01s02.md](./eng/ch01s02.md) |
| 1.3 | 成形分析 | Forming analyses | [chs/ch01s03.md](./chs/ch01s03.md) | [eng/ch01s03.md](./eng/ch01s03.md) |
| 1.4 | 断裂与损伤 | Fracture and damage | [chs/ch01s04.md](./chs/ch01s04.md) | [eng/ch01s04.md](./eng/ch01s04.md) |
| 1.5 | 导入分析 | Import analyses | [chs/ch01s05.md](./chs/ch01s05.md) | [eng/ch01s05.md](./eng/ch01s05.md) |

### 第02章：动力应力/位移分析 / Dynamic Stress/Displacement Analyses

| 章节 Section | 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|--------------|----------------|-----------------|-----------------|-----------------|
| 2.1 | 动力应力分析 | Dynamic stress analyses | [chs/ch02s01.md](./chs/ch02s01.md) | [eng/ch02s01.md](./eng/ch02s01.md) |
| 2.2 | 基于模态的动力分析 | Mode-based dynamic analyses | [chs/ch02s02.md](./chs/ch02s02.md) | [eng/ch02s02.md](./eng/ch02s02.md) |
| 2.3 | 欧拉分析 | Eulerian analyses | [chs/ch02s03.md](./chs/ch02s03.md) | [eng/ch02s03.md](./eng/ch02s03.md) |
| 2.4 | 协同仿真分析 | Co-simulation analyses | [chs/ch02s04.md](./chs/ch02s04.md) | [eng/ch02s04.md](./eng/ch02s04.md) |

### 第03章：轮胎与车辆分析 / Tire and Vehicle Analyses

| 章节 Section | 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|--------------|----------------|-----------------|-----------------|-----------------|
| 3.1 | 轮胎分析 | Tire analyses | [chs/ch03s01.md](./chs/ch03s01.md) | [eng/ch03s01.md](./eng/ch03s01.md) |
| 3.2 | 车辆分析 | Vehicle analyses | [chs/ch03s02.md](./chs/ch03s02.md) | [eng/ch03s02.md](./eng/ch03s02.md) |
| 3.3 | 乘员安全分析 | Occupant safety analyses | [chs/ch03s03.md](./chs/ch03s03.md) | [eng/ch03s03.md](./eng/ch03s03.md) |

### 第04章：机构分析 / Mechanism Analyses

| 章节 Section | 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|--------------|----------------|-----------------|-----------------|-----------------|
| 4.1 | 机构分析 | Mechanism analyses | [chs/ch04s01.md](./chs/ch04s01.md) | [eng/ch04s01.md](./eng/ch04s01.md) |

### 第05章：传热与热应力分析 / Heat Transfer and Thermal-Stress Analyses

| 章节 Section | 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|--------------|----------------|-----------------|-----------------|-----------------|
| 5.1 | 传热与热应力分析 | Heat transfer and thermal-stress analyses | [chs/ch05s01.md](./chs/ch05s01.md) | [eng/ch05s01.md](./eng/ch05s01.md) |

### 第06章：流体动力学与流固耦合 / Fluid Dynamics and Fluid-Structure Interaction

| 章节 Section | 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|--------------|----------------|-----------------|-----------------|-----------------|
| 6.1 | 流体动力学与流固耦合 | Fluid dynamics and fluid-structure interaction | [chs/ch06s01.md](./chs/ch06s01.md) | [eng/ch06s01.md](./eng/ch06s01.md) |

### 第07章：电磁分析 / Electromagnetic Analyses

| 章节 Section | 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|--------------|----------------|-----------------|-----------------|-----------------|
| 7.1 | 压电分析 | Piezoelectric analyses | [chs/ch07s01.md](./chs/ch07s01.md) | [eng/ch07s01.md](./eng/ch07s01.md) |
| 7.2 | 焦耳加热分析 | Joule heating analyses | [chs/ch07s02.md](./chs/ch07s02.md) | [eng/ch07s02.md](./eng/ch07s02.md) |

### 第08章：质量扩散分析 / Mass Diffusion Analyses

| 章节 Section | 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|--------------|----------------|-----------------|-----------------|-----------------|
| 8.1 | 质量扩散分析 | Mass diffusion analyses | [chs/ch08s01.md](./chs/ch08s01.md) | [eng/ch08s01.md](./eng/ch08s01.md) |

### 第09章：声学与冲击分析 / Acoustic and Shock Analyses

| 章节 Section | 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|--------------|----------------|-----------------|-----------------|-----------------|
| 9.1 | 声学与冲击分析 | Acoustic and shock analyses | [chs/ch09s01.md](./chs/ch09s01.md) | [eng/ch09s01.md](./eng/ch09s01.md) |

### 第10章：土体分析 / Soils Analyses

| 章节 Section | 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|--------------|----------------|-----------------|-----------------|-----------------|
| 10.1 | 土体分析 | Soils analyses | [chs/ch10s01.md](./chs/ch10s01.md) | [eng/ch10s01.md](./eng/ch10s01.md) |

### 第11章：结构优化分析 / Structural Optimization Analyses

| 章节 Section | 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|--------------|----------------|-----------------|-----------------|-----------------|
| 11.1 | 拓扑优化分析 | Topology optimization analyses | [chs/ch11s01.md](./chs/ch11s01.md) | [eng/ch11s01.md](./eng/ch11s01.md) |
| 11.2 | 形状优化分析 | Shape optimization analyses | [chs/ch11s02.md](./chs/ch11s02.md) | [eng/ch11s02.md](./eng/ch11s02.md) |
| 11.3 | 尺寸优化分析 | Sizing optimization analyses | [chs/ch11s03.md](./chs/ch11s03.md) | [eng/ch11s03.md](./eng/ch11s03.md) |

### 第12章：Abaqus/Aqua 分析 / Abaqus/Aqua Analyses

| 章节 Section | 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|--------------|----------------|-----------------|-----------------|-----------------|
| 12.1 | Abaqus/Aqua 分析 | Abaqus/Aqua analyses | [chs/ch12s01.md](./chs/ch12s01.md) | [eng/ch12s01.md](./eng/ch12s01.md) |

### 第13章：颗粒方法分析 / Particle Methods Analyses

| 章节 Section | 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|--------------|----------------|-----------------|-----------------|-----------------|
| 13.1 | 离散单元方法分析 | Discrete element method analyses | [chs/ch13s01.md](./chs/ch13s01.md) | [eng/ch13s01.md](./eng/ch13s01.md) |

### 第14章：设计敏感性分析 / Design Sensitivity Analyses

| 章节 Section | 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|--------------|----------------|-----------------|-----------------|-----------------|
| 14.1 | 概述 | Overview | [chs/ch14s01.md](./chs/ch14s01.md) | [eng/ch14s01.md](./eng/ch14s01.md) |
| 14.2 | 示例 | Examples | [chs/ch14s02.md](./chs/ch14s02.md) | [eng/ch14s02.md](./eng/ch14s02.md) |

### 第15章：Abaqus 结果后处理 / Postprocessing of Abaqus Results

| 章节 Section | 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|--------------|----------------|-----------------|-----------------|-----------------|
| 15.1 | 后处理示例 | Postprocessing examples | [chs/ch15s01.md](./chs/ch15s01.md) | [eng/ch15s01.md](./eng/ch15s01.md) |

---

## 资源文件 / Resource Files

| 目录 Directory | 说明 Description |
|---------------|-----------------|
| eng/ | 英文原文件 English source files |
| chs/ | 中文翻译文件 Chinese translated files |
| graphics/ | 图片资源 Image resources |
| eif/ | Abaqus输入文件 Abaqus input files |

**获取输入文件:**
```bash
abaqus fetch job=<input_file>
```

---

## 统计信息 / Statistics

| 项目 Item | 数量 Count |
|---------|-----------|
| 章节 Chapters | 15 |
| HTML源文件 Source files | 217 |
| 英文文件 English files | 217 (eng/) |
| 中文文件 Chinese files | 217 (chs/) |

---

## 版权声明 / Copyright Notice

本翻译仅供学习研究使用，原文档版权归 Dassault Systèmes Simulia Corp. 所有。
This translation is for study and research purposes only. Original documentation copyright Dassault Systèmes Simulia Corp.
