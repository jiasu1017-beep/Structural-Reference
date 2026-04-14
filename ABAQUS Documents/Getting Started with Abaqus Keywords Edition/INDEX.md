# Getting Started with Abaqus Keywords Edition (6.14)

## 文档索引 / Documentation Index

本手册为 ABAQUS 6.14 Getting Started with Abaqus Keywords Edition 的中文翻译版本。

**来源 / Source:** D:\SIMULIA\Documentation\docs\v6.14\books\gsg\

---

## 双语目录对照 / Bilingual Table of Contents

### AP01
*A.1 悬挂起重机架*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| A.1 悬挂起重机架 | A.4 Cargo crane | [AP01s01-Conventions.md](./chs/AP01s01-Conventions.md) | [AP01s01-Conventions.md](./eng/AP01s01-Conventions.md) |
| A.2 连接吊环 | A.2 Connecting lug | [AP01s02-General.md](./chs/AP01s02-General.md) | [AP01s02-General.md](./eng/AP01s02-General.md) |
| A.3 斜面板 | A.3 Skew plate | [AP01s03-Geometry.md](./chs/AP01s03-Geometry.md) | [AP01s03-Geometry.md](./eng/AP01s03-Geometry.md) |
| A.4 货物起重机 | A.1 Overhead hoist frame | [AP01s04-Materials.md](./chs/AP01s04-Materials.md) | [AP01s04-Materials.md](./eng/AP01s04-Materials.md) |
| A.5 货物起重机——动态加载 | A.5 Cargo crane – dynamic loading | [AP01s05-Analysis.md](./chs/AP01s05-Analysis.md) | [AP01s05-Analysis.md](./eng/AP01s05-Analysis.md) |
|  | A.6 Nonlinear skew plate | [AP01s06-Results.md](./chs/AP01s06-Results.md) | [AP01s06-Results.md](./eng/AP01s06-Results.md) |
| A.7 应力波在杆中的传播 | A.7 Stress wave propagation in a bar | [AP01s07-Summary.md](./chs/AP01s07-Summary.md) | [AP01s07-Summary.md](./eng/AP01s07-Summary.md) |
| A.8 带塑性功能的连接耳环 | A.8 Connecting lug with plasticity | [AP01s08-Tabulated.md](./chs/AP01s08-Tabulated.md) | [AP01s08-Tabulated.md](./eng/AP01s08-Tabulated.md) |

### OTHER
*1.1 Abaqus产品*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 1.1 Abaqus产品 | 1.1 The Abaqus products | [01s01-Abaqus-Products.md](./chs/01s01-Abaqus-Products.md) | [01s01-Abaqus-Products.md](./eng/01s01-Abaqus-Products.md) |
| 1.2 Abaqus 入门 | 1.2 Getting started with Abaqus | [01s02-Getting-Started.md](./chs/01s02-Getting-Started.md) | [01s02-Getting-Started.md](./eng/01s02-Getting-Started.md) |
| 1.3 Abaqus 文档 | 1.3 Abaqus documentation | [01s03-Concepts.md](./chs/01s03-Concepts.md) | [01s03-Concepts.md](./eng/01s03-Concepts.md) |
| 1.4 获取帮助 | 1.4 Getting help | [01s04-Verification.md](./chs/01s04-Verification.md) | [01s04-Verification.md](./eng/01s04-Verification.md) |
| 1.5 技术支持 | 1.5 Support | [01s05-Files.md](./chs/01s05-Files.md) | [01s05-Files.md](./eng/01s05-Files.md) |
| 1.6 有限元方法快速回顾 | 1.6 A quick review of the finite element method | [01s06-Support.md](./chs/01s06-Support.md) | [01s06-Support.md](./eng/01s06-Support.md) |
| 2.1 Abaqus分析模型的组成部分 | 2.1 Components of an Abaqus analysis model | [02s01-Simple-Model.md](./chs/02s01-Simple-Model.md) | [02s01-Simple-Model.md](./eng/02s01-Simple-Model.md) |
| 2.2 输入文件的格式 | 2.2 Format of the input file | [02s02-Boost-Analysis.md](./chs/02s02-Boost-Analysis.md) | [02s02-Boost-Analysis.md](./eng/02s02-Boost-Analysis.md) |
| 2.3 示例：创建架空起重机的模型 | 2.3 Example: creating a model of an overhead hoist | [02s03-Keyword.md](./chs/02s03-Keyword.md) | [02s03-Keyword.md](./eng/02s03-Keyword.md) |
| 2.4 隐式与显式程序的比较 | 2.4 Comparison of implicit and explicit procedures | [02s04-Execution.md](./chs/02s04-Execution.md) | [02s04-Execution.md](./eng/02s04-Execution.md) |
| 2.5 小结 | 2.5 Summary | [02s05-Working-Directories.md](./chs/02s05-Working-Directories.md) | [02s05-Working-Directories.md](./eng/02s05-Working-Directories.md) |
| 3.1 有限元 | 3.1 Finite elements | [03s01-Modeling-Techniques.md](./chs/03s01-Modeling-Techniques.md) | [03s01-Modeling-Techniques.md](./eng/03s01-Modeling-Techniques.md) |
| 3.2 刚性体 | 3.2 Rigid bodies | [03s02-Element-Technology.md](./chs/03s02-Element-Technology.md) | [03s02-Element-Technology.md](./eng/03s02-Element-Technology.md) |
| 3.3 小结 | 3.3 Summary | [03s03-Selection.md](./chs/03s03-Selection.md) | [03s03-Selection.md](./eng/03s03-Selection.md) |
| 4.1 单元公式与积分 | 4.1 Element formulation and integration | [04s01-Static-Stress-Analysis.md](./chs/04s01-Static-Stress-Analysis.md) | [04s01-Static-Stress-Analysis.md](./eng/04s01-Static-Stress-Analysis.md) |
| 4.2 选择连续体单元 | 4.2 Selecting continuum elements | [04s02-Quasi-Static-Analysis.md](./chs/04s02-Quasi-Static-Analysis.md) | [04s02-Quasi-Static-Analysis.md](./eng/04s02-Quasi-Static-Analysis.md) |
| 4.3 示例：连接销 | 4.3 Example: connecting lug | [04s03-Element-Selection.md](./chs/04s03-Element-Selection.md) | [04s03-Element-Selection.md](./eng/04s03-Element-Selection.md) |
| 4.4 网格收敛 | 04s04-Enhanced-Strain | [04s04-Enhanced-Strain.md](./chs/04s04-Enhanced-Strain.md) | [04s04-Enhanced-Strain.md](./eng/04s04-Enhanced-Strain.md) |
| 4.5 相关 Abaqus 示例 | 4.5 Related Abaqus examples | [04s05-Hybrid-Elements.md](./chs/04s05-Hybrid-Elements.md) | [04s05-Hybrid-Elements.md](./eng/04s05-Hybrid-Elements.md) |
| 4.6 推荐阅读 | 4.6 Suggested reading | [04s06-Prescribed-States.md](./chs/04s06-Prescribed-States.md) | [04s06-Prescribed-States.md](./eng/04s06-Prescribed-States.md) |
| 4.7 总结 | 4.7 Summary | [04s07-Summary.md](./chs/04s07-Summary.md) | [04s07-Summary.md](./eng/04s07-Summary.md) |
| 5.1 单元几何 | 5.1 Element geometry | [05s01-Static-Analysis.md](./chs/05s01-Static-Analysis.md) | [05s01-Static-Analysis.md](./eng/05s01-Static-Analysis.md) |
| 5.3 壳体材料方向 | 5.3 Shell material directions | [05s03-Modeling.md](./chs/05s03-Modeling.md) | [05s03-Modeling.md](./eng/05s03-Modeling.md) |
| 5.4 选择壳单元 | 5.4 Selecting shell elements | [05s04-Transverse-Shear.md](./chs/05s04-Transverse-Shear.md) | [05s04-Transverse-Shear.md](./eng/05s04-Transverse-Shear.md) |
| 5.5 示例：斜板 | 5.5 Example: skew plate | [05s05-Constrained-Layouts.md](./chs/05s05-Constrained-Layouts.md) | [05s05-Constrained-Layouts.md](./eng/05s05-Constrained-Layouts.md) |
| 5.6 相关 Abaqus 实例 | 5.6 Related Abaqus examples | [05s06-Compression.md](./chs/05s06-Compression.md) | [05s06-Compression.md](./eng/05s06-Compression.md) |
| 5.7 推荐阅读 | 5.7 Suggested reading | [05s07-Membrane-Elements.md](./chs/05s07-Membrane-Elements.md) | [05s07-Membrane-Elements.md](./eng/05s07-Membrane-Elements.md) |
| 5.8 小结 | 5.8 Summary | [05s08-Summary.md](./chs/05s08-Summary.md) | [05s08-Summary.md](./eng/05s08-Summary.md) |
| 6.1 梁截面几何 | 6.1 Beam cross-section geometry | [06s01-Beam-Analysis.md](./chs/06s01-Beam-Analysis.md) | [06s01-Beam-Analysis.md](./eng/06s01-Beam-Analysis.md) |
| 6.2 公式与积分 | 6.2 Formulation and integration | [06s02-Beam-Sections.md](./chs/06s02-Beam-Sections.md) | [06s02-Beam-Sections.md](./eng/06s02-Beam-Sections.md) |
| 6.3 选择梁单元 | 6.3 Selecting beam elements | [06s03-Beam-Modeling.md](./chs/06s03-Beam-Modeling.md) | [06s03-Beam-Modeling.md](./eng/06s03-Beam-Modeling.md) |
| 6.4 示例：货运吊车 | 6.4 Example: cargo crane | [06s04-Lug-Analysis.md](./chs/06s04-Lug-Analysis.md) | [06s04-Lug-Analysis.md](./eng/06s04-Lug-Analysis.md) |
| 6.5 相关 Abaqus 示例 | 06s05-Element-Technology | [06s05-Element-Technology.md](./chs/06s05-Element-Technology.md) | [06s05-Element-Technology.md](./eng/06s05-Element-Technology.md) |
| 6.6 推荐阅读 | 6.6 Suggested reading | [06s06-Selection.md](./chs/06s06-Selection.md) | [06s06-Selection.md](./eng/06s06-Selection.md) |
| 6.7 总结 | 6.7 Summary | [06s07-Summary.md](./chs/06s07-Summary.md) | [06s07-Summary.md](./eng/06s07-Summary.md) |
| 7.1 简介 | 7.1 Introduction | [07s01-Dynamic-Analysis.md](./chs/07s01-Dynamic-Analysis.md) | [07s01-Dynamic-Analysis.md](./eng/07s01-Dynamic-Analysis.md) |
| 7.2 阻尼 | 7.2 Damping | [07s02-Resonant.md](./chs/07s02-Resonant.md) | [07s02-Resonant.md](./eng/07s02-Resonant.md) |
| 7.3 单元选择 | 7.3 Element selection | [07s03-Modal-Dynamic.md](./chs/07s03-Modal-Dynamic.md) | [07s03-Modal-Dynamic.md](./eng/07s03-Modal-Dynamic.md) |
| 7.4 动力学网格设计 | 7.4 Mesh design for dynamics | [07s04-Sinspace.md](./chs/07s04-Sinspace.md) | [07s04-Sinspace.md](./eng/07s04-Sinspace.md) |
| 7.5 示例：动态载荷作用下的货物起重机 | 7.5 Example: cargo crane under dynamic loading | [07s05-Impact-Analysis.md](./chs/07s05-Impact-Analysis.md) | [07s05-Impact-Analysis.md](./eng/07s05-Impact-Analysis.md) |
| 7.6 模态数量的影响 | 7.6 Effect of the number of modes | [07s06-Explicit-Method.md](./chs/07s06-Explicit-Method.md) | [07s06-Explicit-Method.md](./eng/07s06-Explicit-Method.md) |
| 7.7 阻尼效应 | 7.7 Effect of damping | [07s07-Surface-Contact.md](./chs/07s07-Surface-Contact.md) | [07s07-Surface-Contact.md](./eng/07s07-Surface-Contact.md) |
| 7.8 与直接时间积分的比较 | 7.8 Comparison with direct time integration | [07s08-Mass-Scaling.md](./chs/07s08-Mass-Scaling.md) | [07s08-Mass-Scaling.md](./eng/07s08-Mass-Scaling.md) |
| 7.9 其他动力分析过程 | 7.9 Other dynamic procedures | [07s09-Selection.md](./chs/07s09-Selection.md) | [07s09-Selection.md](./eng/07s09-Selection.md) |
|  | 07s10-Explicit-Examples | [07s10-Explicit-Examples.md](./chs/07s10-Explicit-Examples.md) | [07s10-Explicit-Examples.md](./eng/07s10-Explicit-Examples.md) |
| 7.11 建议阅读 | 7.11 Suggested reading | [07s11-Summary.md](./chs/07s11-Summary.md) | [07s11-Summary.md](./eng/07s11-Summary.md) |
| 7.12 小结 | 7.12 Summary | [07s12-Examples.md](./chs/07s12-Examples.md) | [07s12-Examples.md](./eng/07s12-Examples.md) |
| 8.1 非线性的来源 | 8.1 Sources of nonlinearity | [08s01-Heat-Transfer.md](./chs/08s01-Heat-Transfer.md) | [08s01-Heat-Transfer.md](./eng/08s01-Heat-Transfer.md) |
| 8.2 非线性问题的求解 | 8.2 The solution of nonlinear problems | [08s02-Thermal-Analysis.md](./chs/08s02-Thermal-Analysis.md) | [08s02-Thermal-Analysis.md](./eng/08s02-Thermal-Analysis.md) |
| 8.3 在Abaqus分析中考虑非线性 | 8.3 Including nonlinearity in an Abaqus analysis | [08s03-Mesh-Design.md](./chs/08s03-Mesh-Design.md) | [08s03-Mesh-Design.md](./eng/08s03-Mesh-Design.md) |
| 8.4 示例：非线性斜板 | 8.4 Example: nonlinear skew plate | [08s04-Quasi-Static.md](./chs/08s04-Quasi-Static.md) | [08s04-Quasi-Static.md](./eng/08s04-Quasi-Static.md) |
| 8.5 相关 Abaqus 示例 | 8.5 Related Abaqus examples | [08s05-Convergence.md](./chs/08s05-Convergence.md) | [08s05-Convergence.md](./eng/08s05-Convergence.md) |
| 8.6 推荐阅读 | 8.6 Suggested reading | [08s06-Summary.md](./chs/08s06-Summary.md) | [08s06-Summary.md](./eng/08s06-Summary.md) |
| 8.7 小结 | 8.7 Summary | [08s07-Examples.md](./chs/08s07-Examples.md) | [08s07-Examples.md](./eng/08s07-Examples.md) |
| 9.2 显式动态有限元方法 | 9.2 Explicit dynamic finite element methods | [09s02-Surface-Contact.md](./chs/09s02-Surface-Contact.md) | [09s02-Surface-Contact.md](./eng/09s02-Surface-Contact.md) |
| 9.3 自动时间步长与稳定性 | 9.3 Automatic time incrementation and stability | [09s03-Modeling-Techniques.md](./chs/09s03-Modeling-Techniques.md) | [09s03-Modeling-Techniques.md](./eng/09s03-Modeling-Techniques.md) |
| 9.4 示例：杆中的应力波传播 | 9.4 Example: stress wave propagation in a bar | [09s04-Brake-Analysis.md](./chs/09s04-Brake-Analysis.md) | [09s04-Brake-Analysis.md](./eng/09s04-Brake-Analysis.md) |
| 9.5 动力振荡的阻尼 | 9.5 Damping of dynamic oscillations | [09s05-Selection.md](./chs/09s05-Selection.md) | [09s05-Selection.md](./eng/09s05-Selection.md) |
| 9.6 能量平衡 | 9.6 Energy balance | [09s06-Mass-Scaling.md](./chs/09s06-Mass-Scaling.md) | [09s06-Mass-Scaling.md](./eng/09s06-Mass-Scaling.md) |
| 9.7 总结 | 9.7 Summary | [09s07-Summary.md](./chs/09s07-Summary.md) | [09s07-Summary.md](./eng/09s07-Summary.md) |
| 10.1 在 Abaqus 中定义材料 | 10.1 Defining materials in Abaqus | [10s01-Materials.md](./chs/10s01-Materials.md) | [10s01-Materials.md](./eng/10s01-Materials.md) |
| 10.2 延性金属的塑性 | 10.2 Plasticity in ductile metals | [10s02-Elastoplasticity.md](./chs/10s02-Elastoplasticity.md) | [10s02-Elastoplasticity.md](./eng/10s02-Elastoplasticity.md) |
| 10.3 为弹塑性问题选择单元 | 10.3 Selecting elements for elastic-plastic problems | [10s03-Hyperelasticity.md](./chs/10s03-Hyperelasticity.md) | [10s03-Hyperelasticity.md](./eng/10s03-Hyperelasticity.md) |
| 10.4 示例：带塑性的连接耳片 | 10.4 Example: connecting lug with plasticity | [10s04-Hyperelasticity-Test.md](./chs/10s04-Hyperelasticity-Test.md) | [10s04-Hyperelasticity-Test.md](./eng/10s04-Hyperelasticity-Test.md) |
| 10.5 示例：加筋板上的爆炸载荷 | 10.5 Example: blast loading on a stiffened plate | [10s05-Mooney-Rivlin.md](./chs/10s05-Mooney-Rivlin.md) | [10s05-Mooney-Rivlin.md](./eng/10s05-Mooney-Rivlin.md) |
| 10.6 超弹性 | 10.6 Hyperelasticity | [10s06-Rate-Dependency.md](./chs/10s06-Rate-Dependency.md) | [10s06-Rate-Dependency.md](./eng/10s06-Rate-Dependency.md) |
| 10.7 示例：轴对称支架 | 10.7 Example: axisymmetric mount | [10s07-Time-Based.md](./chs/10s07-Time-Based.md) | [10s07-Time-Based.md](./eng/10s07-Time-Based.md) |
| 10.8 大变形网格设计 | 10.8 Mesh design for large distortions | [10s08-Temperature-Dependency.md](./chs/10s08-Temperature-Dependency.md) | [10s08-Temperature-Dependency.md](./eng/10s08-Temperature-Dependency.md) |
| 10.9 减少体积锁定的技术 | 10.9 Techniques for reducing volumetric locking | [10s09-Examples.md](./chs/10s09-Examples.md) | [10s09-Examples.md](./eng/10s09-Examples.md) |
|  | 10s10-Reading | ⏳ 翻译中 | [10s10-Reading.md](./eng/10s10-Reading.md) |
| 10.11 推荐阅读 | 10.11 Suggested reading | [10s11-Viscoelasticity.md](./chs/10s11-Viscoelasticity.md) | [10s11-Viscoelasticity.md](./eng/10s11-Viscoelasticity.md) |
|  | 10s12-Summary | ⏳ 翻译中 | [10s12-Summary.md](./eng/10s12-Summary.md) |
| 11.1 常规分析流程 | 11.1 General analysis procedures | [11s01-Modeling-Techniques.md](./chs/11s01-Modeling-Techniques.md) | [11s01-Modeling-Techniques.md](./eng/11s01-Modeling-Techniques.md) |
| 11.2 线性扰动分析 | 11.2 Linear perturbation analysis | [11s02-Adaptive-Mesh.md](./chs/11s02-Adaptive-Mesh.md) | [11s02-Adaptive-Mesh.md](./eng/11s02-Adaptive-Mesh.md) |
| 11.3 示例：管道系统的振动 | 11.3 Example: vibration of a piping system | [11s03-Pipe-Example.md](./chs/11s03-Pipe-Example.md) | [11s03-Pipe-Example.md](./eng/11s03-Pipe-Example.md) |
| 11.4 重启动分析 | 11.4 Restart analysis | [11s04-Restart-Analysis.md](./chs/11s04-Restart-Analysis.md) | [11s04-Restart-Analysis.md](./eng/11s04-Restart-Analysis.md) |
| 11.5 示例：管道振动分析的重新启动 | 11.5 Example: restarting the pipe vibration analysis | [11s05-Restart-Pipe.md](./chs/11s05-Restart-Pipe.md) | [11s05-Restart-Pipe.md](./eng/11s05-Restart-Pipe.md) |
| 11.6 相关 Abaqus 示例 | 11.6 Related Abaqus examples | [11s06-Summary.md](./chs/11s06-Summary.md) | [11s06-Summary.md](./eng/11s06-Summary.md) |
|  | 12.1 Overview of contact capabilities in Abaqus | ⏳ 翻译中 | [12s01-Contact-Analysis.md](./eng/12s01-Contact-Analysis.md) |
| 12.2 定义表面 | 12.2 Defining surfaces | [12s02-Surface-Interaction.md](./chs/12s02-Surface-Interaction.md) | [12s02-Surface-Interaction.md](./eng/12s02-Surface-Interaction.md) |
| 12.3 表面之间的相互作用 | 12.3 Interaction between surfaces | [12s03-Master-Slave.md](./chs/12s03-Master-Slave.md) | [12s03-Master-Slave.md](./eng/12s03-Master-Slave.md) |
| 12.4 在 Abaqus/Standard 中定义接触 | 12.4 Defining contact in Abaqus/Standard | [12s04-Constraints.md](./chs/12s04-Constraints.md) | [12s04-Constraints.md](./eng/12s04-Constraints.md) |
| 12.5 Abaqus/Standard中刚性曲面建模问题 | 12s05-Sliding | [12s05-Sliding.md](./chs/12s05-Sliding.md) | [12s05-Sliding.md](./eng/12s05-Sliding.md) |
| 12.6 Abaqus/Standard 二维示例：成形通道 | 12.6 Abaqus/Standard 2D example: forming a channel | [12s06-Modeling-Techniques.md](./chs/12s06-Modeling-Techniques.md) | [12s06-Modeling-Techniques.md](./eng/12s06-Modeling-Techniques.md) |
| 12.7 Abaqus/Standard中的通用接触 | 12.7 General contact in Abaqus/Standard | [12s07-Examples.md](./chs/12s07-Examples.md) | [12s07-Examples.md](./eng/12s07-Examples.md) |
| 12.8 Abaqus/Standard 三维实例：搭接接头的剪切 | 12.8 Abaqus/Standard 3D example: shearing of a lap joint | [12s08-Explicit-Contact.md](./chs/12s08-Explicit-Contact.md) | [12s08-Explicit-Contact.md](./eng/12s08-Explicit-Contact.md) |
| 12.9 在Abaqus/Explicit中定义接触 | 12.9 Defining contact in Abaqus/Explicit | [12s09-General-Contact.md](./chs/12s09-General-Contact.md) | [12s09-General-Contact.md](./eng/12s09-General-Contact.md) |
| 12.10 Abaqus/Explicit 中的建模注意事项 | 12.10 Modeling considerations in Abaqus/Explicit | [12s10-Contact-Controls.md](./chs/12s10-Contact-Controls.md) | [12s10-Contact-Controls.md](./eng/12s10-Contact-Controls.md) |
| 12.11 Abaqus/Explicit实例：电路板跌落试验 | 12s11-3D-Example | [12s11-3D-Example.md](./chs/12s11-3D-Example.md) | [12s11-3D-Example.md](./eng/12s11-3D-Example.md) |
| 12.12 Abaqus/Standard与Abaqus/Explicit的兼容性 | 12.12 Compatibility between Abaqus/Standard and Abaqus/Explicit | [12s12-Selection.md](./chs/12s12-Selection.md) | [12s12-Selection.md](./eng/12s12-Selection.md) |
|  | 12.13 Related Abaqus examples | ⏳ 翻译中 | [12s13-Nonlinear.md](./eng/12s13-Nonlinear.md) |
|  | 12.14 Suggested reading | ⏳ 翻译中 | [12s14-Contact.md](./eng/12s14-Contact.md) |
|  | 12.15 Summary | [12s15-Summary.md](./chs/12s15-Summary.md) | [12s15-Summary.md](./eng/12s15-Summary.md) |
|  | Getting Started with Abaqus: Keywords Edition (English) | ⏳ 翻译中 | [README.md](./eng/README.md) |

### 01
*第1章 引言*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 第1章 引言 | 1. Introduction | [01-Introduction.md](./chs/01-Introduction.md) | [01-Introduction.md](./eng/01-Introduction.md) |

---

## 资源文件 / Resource Files

图片资源位于 `graphics/` 目录。

---

## 版权声明 / Copyright Notice

本翻译仅供学习研究使用，原文档版权归 Dassault Systèmes Simulia Corp. 所有。
This translation is for study and research purposes only. Original documentation copyright Dassault Systèmes Simulia Corp.