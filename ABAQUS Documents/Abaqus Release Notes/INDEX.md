# Abaqus Release Notes (6.14)

## 文档索引 / Documentation Index

本手册为 ABAQUS 6.14 Abaqus Release Notes 的中文翻译版本。

**来源 / Source:** D:\SIMULIA\Documentation\docs\v6.14\books\rnb\

---

## 双语目录对照 / Bilingual Table of Contents

### OTHER
*1.4 Abaqus/CAE 输入数据解释的变更*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 1.4 Abaqus/CAE 输入数据解释的变更 | 1 Introduction to Abaqus 6.14 | [abc01.md](./chs/abc01.md) | [abc01.md](./eng/abc01.md) |
| 1.2 Abaqus 产品 | 1.1 Key features of Abaqus 6.14 | [abc01sct01.md](./chs/abc01sct01.md) | [abc01sct01.md](./eng/abc01sct01.md) |
| 1.3 输入数据解释的变更 | 1.2 Abaqus products | [abc01sct02.md](./chs/abc01sct02.md) | [abc01sct02.md](./eng/abc01sct02.md) |
| 1.1 Abaqus 6.14 的主要功能 | 1.3 Changes in interpretation of input data | [abc01sct03.md](./chs/abc01sct03.md) | [abc01sct03.md](./eng/abc01sct03.md) |
| 2 总体增强 | 1.4 Changes in interpretation of input data for Abaqus/CAE | [abc01sct04.md](./chs/abc01sct04.md) | [abc01sct04.md](./eng/abc01sct04.md) |
| 1 Abaqus 6.14 简介 | 2 General enhancements | [abc02.md](./chs/abc02.md) | [abc02.md](./eng/abc02.md) |
| 2.1 从 Abaqus/CAE 访问 Learning Community | 2.1 Accessing the Learning Community from Abaqus/CAE | [abc02aqs01.md](./chs/abc02aqs01.md) | [abc02aqs01.md](./eng/abc02aqs01.md) |
| 3 建模 | 3 Modeling | [abc03.md](./chs/abc03.md) | [abc03.md](./eng/abc03.md) |
| 3.1 尺寸优化 | 3.1 Sizing optimization | [abc03aqs01.md](./chs/abc03aqs01.md) | [abc03aqs01.md](./eng/abc03aqs01.md) |
| 3.2 跨多个模型的优化 | 3.2 Optimization across multiple models | [abc03aqs02.md](./chs/abc03aqs02.md) | [abc03aqs02.md](./eng/abc03aqs02.md) |
| 3.3 通过合并输出数据库文件查看优化进程 | 3.3 Viewing the progression of an optimization by combining output database files | [abc03aqs03.md](./chs/abc03aqs03.md) | [abc03aqs03.md](./eng/abc03aqs03.md) |
| 3.4 监控优化过程 | 3.4 Monitoring an optimization process | [abc03aqs04.md](./chs/abc03aqs04.md) | [abc03aqs04.md](./eng/abc03aqs04.md) |
| 3.5 创建软单元的其他标准 | 3.5 Additional criteria for creating soft elements | [abc03aqs05.md](./chs/abc03aqs05.md) | [abc03aqs05.md](./eng/abc03aqs05.md) |
| 3.6 新的设计响应 | 3.6 New design responses | [abc03aqs06.md](./chs/abc03aqs06.md) | [abc03aqs06.md](./eng/abc03aqs06.md) |
| 3.7 指定优化数据保存的速率 | 3.7 Specifying the rate at which optimization data are saved | [abc03aqs07.md](./chs/abc03aqs07.md) | [abc03aqs07.md](./eng/abc03aqs07.md) |
| 3.8 写入优化文件 | 3.8 Writing optimization files | [abc03aqs08.md](./chs/abc03aqs08.md) | [abc03aqs08.md](./eng/abc03aqs08.md) |
| 3.9 在 Abaqus/CAE 中切换模型实例的上下文 | 3.9 Switching the context for model instances in Abaqus/CAE | [abc03aqs09.md](./chs/abc03aqs09.md) | [abc03aqs09.md](./eng/abc03aqs09.md) |
| 3.10 将与孤立网格创建的几何面与网格关联 | 3.10 Associating geometric faces created from an orphan mesh with the mesh | [abc03aqs10.md](./chs/abc03aqs10.md) | [abc03aqs10.md](./eng/abc03aqs10.md) |
| 3.11 使用 CATIA V6 Associative Interface 进行参数的双向导入 | 3.11 Bidirectional import of parameters using the CATIA V6 Associative Interface | [abc03aqs11.md](./chs/abc03aqs11.md) | [abc03aqs11.md](./eng/abc03aqs11.md) |
| 4 分析过程 | 4 Analysis procedures | [abc04.md](./chs/abc04.md) | [abc04.md](./eng/abc04.md) |
| 4.1 AMS 特征值求解器可以提取耦合结构-声学特征模式 | 4.1 The AMS eigensolver can extract coupled structural-acoustic eigenmodes | [abc04aqs01.md](./chs/abc04aqs01.md) | [abc04aqs01.md](./eng/abc04aqs01.md) |
| 4.2 AMS 特征值求解器性能改进 | 4.2 AMS eigensolver performance improvements | [abc04aqs02.md](./chs/abc04aqs02.md) | [abc04aqs02.md](./eng/abc04aqs02.md) |
| 4.3 在流体腔中指定附加体积 | 4.3 Specifying additional volume in a fluid cavity | [abc04aqs03.md](./chs/abc04aqs03.md) | [abc04aqs03.md](./eng/abc04aqs03.md) |
| 4.4 Abaqus/CFD 中的 k-epsilon 可实现湍流模型 | 4.4 K–epsilon realizable turbulence model in Abaqus/CFD | [abc04aqs04.md](./chs/abc04aqs04.md) | [abc04aqs04.md](./eng/abc04aqs04.md) |
| 4.5 矩阵质量检查 | 4.5 Matrix quality check | [abc04aqs05.md](./chs/abc04aqs05.md) | [abc04aqs05.md](./eng/abc04aqs05.md) |
| 4.6 柔性体生成 | 4.6 Flexible body generation | [abc04aqs06.md](./chs/abc04aqs06.md) | [abc04aqs06.md](./eng/abc04aqs06.md) |
| 5 分析技术 | 5 Analysis techniques | [abc05.md](./chs/abc05.md) | [abc05.md](./eng/abc05.md) |
| 5.1 欧拉单元中材料的局部坐标系定义 | 5.1 Defining a local coordinate system for materials in Eulerian elements | [abc05aqs01.md](./chs/abc05aqs01.md) | [abc05aqs01.md](./eng/abc05aqs01.md) |
| 5.2 基于 XFEM 的裂纹扩展功能增强 | 5.2 Enhancements to the XFEM-based crack propagation capability | [abc05aqs02.md](./chs/abc05aqs02.md) | [abc05aqs02.md](./eng/abc05aqs02.md) |
| 5.3 SIMULIA Co-Simulation Engine API 可用性 | 5.3 SIMULIA Co-Simulation Engine API availability | [abc05aqs03.md](./chs/abc05aqs03.md) | [abc05aqs03.md](./eng/abc05aqs03.md) |
| 5.4 自适应网格细化增强 | 5.4 Enhancement to adaptive mesh refinement | [abc05aqs04.md](./chs/abc05aqs04.md) | [abc05aqs04.md](./eng/abc05aqs04.md) |
| 5.5 Abaqus/CAE 中基于 XFEM 的裂纹扩展功能增强 | 5.5 Enhancements to the XFEM-based crack propagation capability in Abaqus/CAE | [abc05aqs05.md](./chs/abc05aqs05.md) | [abc05aqs05.md](./eng/abc05aqs05.md) |
| 5.6 DEM 分析的并行增强 | 5.6 Parallel enhancement for DEM analysis | [abc05aqs06.md](./chs/abc05aqs06.md) | [abc05aqs06.md](./eng/abc05aqs06.md) |
| 5.7 Abaqus 复合材料压溃模拟的 CZone 增强 | 5.7 Enhancements to CZone for Abaqus for composite crush simulation | [abc05aqs07.md](./chs/abc05aqs07.md) | [abc05aqs07.md](./eng/abc05aqs07.md) |
| 5.8 车辆行驶舒适性和耐久性协同仿真 | 5.8 Vehicle ride comfort and durability co-simulation | [abc05aqs08.md](./chs/abc05aqs08.md) | [abc05aqs08.md](./eng/abc05aqs08.md) |
| 5.9 使用 Abaqus 和 Dymola 进行逻辑-物理协同仿真 | 5.9 Logical-Physical co-simulation using Abaqus and Dymola | [abc05aqs09.md](./chs/abc05aqs09.md) | [abc05aqs09.md](./eng/abc05aqs09.md) |
| 5.10 SIMULIA Co-Simulation Engine 增强 | 5.10 Enhancements to the SIMULIA Co-Simulation Engine | [abc05aqs10.md](./chs/abc05aqs10.md) | [abc05aqs10.md](./eng/abc05aqs10.md) |
| 5.11 协同仿真增强 | 5.11 Enhancements for co-simulation | [abc05aqs11.md](./chs/abc05aqs11.md) | [abc05aqs11.md](./eng/abc05aqs11.md) |
| 5.12 MpCCI 与 SIMULIA Co-Simulation Engine 的连接器 | 5.12 MpCCI connector to the SIMULIA Co-Simulation Engine | [abc05aqs12.md](./chs/abc05aqs12.md) | [abc05aqs12.md](./eng/abc05aqs12.md) |
| 6 材料 | 6 Materials | [abc06.md](./chs/abc06.md) | [abc06.md](./eng/abc06.md) |
| 6.1 并联流变框架增强 | 6.1 Enhancements to parallel rheological framework | [abc06aqs01.md](./chs/abc06aqs01.md) | [abc06aqs01.md](./eng/abc06aqs01.md) |
| 6.2 具有各向异性材料的欧拉单元 | 6.2 Eulerian elements with anisotropic materials | [abc06aqs02.md](./chs/abc06aqs02.md) | [abc06aqs02.md](./eng/abc06aqs02.md) |
| 6.3 蠕变模型增强 | 6.3 Enhancements to creep models | [abc06aqs03.md](./chs/abc06aqs03.md) | [abc06aqs03.md](./eng/abc06aqs03.md) |
| 6.4 用户定义的频域粘弹性行为 | 6.4 User-defined frequency domain viscoelastic behavior | [abc06aqs04.md](./chs/abc06aqs04.md) | [abc06aqs04.md](./eng/abc06aqs04.md) |
| 6.5 用户定义材料行为的新型混合公式 | 6.5 New hybrid formulations for user-defined material behavior | [abc06aqs05.md](./chs/abc06aqs05.md) | [abc06aqs05.md](./eng/abc06aqs05.md) |
| 6.6 牵引-分离弹性的拉压不同刚度 | 6.6 Different stiffness in tension versus compression for traction-separation elasticity | [abc06aqs06.md](./chs/abc06aqs06.md) | [abc06aqs06.md](./eng/abc06aqs06.md) |
| 6.7 由状态变量控制的单元删除 | 6.7 Element deletion controlled by state variables | [abc06aqs07.md](./chs/abc06aqs07.md) | [abc06aqs07.md](./eng/abc06aqs07.md) |
| 7 单元 | 7 Elements | [abc07.md](./chs/abc07.md) | [abc07.md](./eng/abc07.md) |
| 7.1 Abaqus/CAE 中耦合温度-孔隙压力单元的支持 | 7.1 Support for coupled temperature–pore pressure elements in Abaqus/CAE | [abc07aqs01.md](./chs/abc07aqs01.md) | [abc07aqs01.md](./eng/abc07aqs01.md) |
| 7.2 线性棱锥声学单元 | 7.2 Linear pyramid acoustic element | [abc07aqs02.md](./chs/abc07aqs02.md) | [abc07aqs02.md](./eng/abc07aqs02.md) |
| 8 预设条件 | 8 Prescribed conditions | [abc08.md](./chs/abc08.md) | [abc08.md](./eng/abc08.md) |
| 8.1 损伤起始的初始条件 | 8.1 Initial conditions on damage initiation | [abc08aqs01.md](./chs/abc08aqs01.md) | [abc08aqs01.md](./eng/abc08aqs01.md) |
| 9.2 增强型热绑定连接的区域分解 | 8.2 Enhancements for prescribed conditions in Abaqus/CFD | [abc08aqs02.md](./chs/abc08aqs02.md) | [abc08aqs02.md](./eng/abc08aqs02.md) |
| 8.2 Abaqus/CFD  prescribed条件的增强 | 8.3 Acoustic base motion for SIM-based procedures | [abc08aqs03.md](./chs/abc08aqs03.md) | [abc08aqs03.md](./eng/abc08aqs03.md) |
| 9 约束 | 9 Constraints | [abc09.md](./chs/abc09.md) | [abc09.md](./eng/abc09.md) |
| 9.1 网格无关紧固件的新附着方法 | 9.1 New attachment method for mesh-independent fasteners | [abc09aqs01.md](./chs/abc09aqs01.md) | [abc09aqs01.md](./eng/abc09aqs01.md) |
| 8.3 基于SIM的分析过程的声学基础运动 | 9.2 Enhanced domain decomposition of thermal ties | [abc09aqs02.md](./chs/abc09aqs02.md) | [abc09aqs02.md](./eng/abc09aqs02.md) |
| 10 相互作用 | 10 Interactions | [abc10.md](./chs/abc10.md) | [abc10.md](./eng/abc10.md) |
| 10.1 Abaqus/Standard 中通用接触的边对边接触 | 10.1 Edge-to-edge contact for general contact in Abaqus/Standard | [abc10aqs01.md](./chs/abc10aqs01.md) | [abc10aqs01.md](./eng/abc10aqs01.md) |
| 10.2 Abaqus/Explicit 中复杂交叉处的接触改进 | 10.2 Improved contact at complex intersections in Abaqus/Explicit | [abc10aqs02.md](./chs/abc10aqs02.md) | [abc10aqs02.md](./eng/abc10aqs02.md) |
| 10.3 Abaqus/CAE 中接触检测工具的增强 | 10.3 Enhancement to the contact detection tool in Abaqus/CAE | [abc10aqs03.md](./chs/abc10aqs03.md) | [abc10aqs03.md](./eng/abc10aqs03.md) |
| 11 执行 | 11 Execution | [abc11.md](./chs/abc11.md) | [abc11.md](./eng/abc11.md) |
| 11.1 AMS 特征值求解器的 GPGPU 加速 | 11.1 GPGPU acceleration of the AMS eigensolver | [abc11aqs01.md](./chs/abc11aqs01.md) | [abc11aqs01.md](./eng/abc11aqs01.md) |
| 11.2 GPGPU 加速的直接方程求解器 | 11.2 GPGPU accelerated direct equation solver | [abc11aqs02.md](./chs/abc11aqs02.md) | [abc11aqs02.md](./eng/abc11aqs02.md) |
| 11.3 用户控制的区域分解 | 11.3 User control of domain decomposition | [abc11aqs03.md](./chs/abc11aqs03.md) | [abc11aqs03.md](./eng/abc11aqs03.md) |
| 11.4 作业执行控制增强 | 11.4 Job execution control enhancements | [abc11aqs04.md](./chs/abc11aqs04.md) | [abc11aqs04.md](./eng/abc11aqs04.md) |
| 11.5 SIM 数据库实用程序 | 11.5 SIM database utilities | [abc11aqs05.md](./chs/abc11aqs05.md) | [abc11aqs05.md](./eng/abc11aqs05.md) |
| 11.6 将 Abaqus 数据转换到模态中性文件的增强 | 11.6 Enhancements for translating Abaqus data to modal neutral files | [abc11aqs06.md](./chs/abc11aqs06.md) | [abc11aqs06.md](./eng/abc11aqs06.md) |
| 12 输出和可视化 | 12 Output and visualization | [abc12.md](./chs/abc12.md) | [abc12.md](./eng/abc12.md) |
| 12.1 将 Abaqus 分析结果写入 SIM 数据库 | 12.1 Writing results from an Abaqus analysis to a SIM database | [abc12aqs01.md](./chs/abc12aqs01.md) | [abc12aqs01.md](./eng/abc12aqs01.md) |
| 12.2 混合模式分层过程中的模式混合比输出 | 12.2 Output of mode mix ratios during mixed mode delamination | [abc12aqs02.md](./chs/abc12aqs02.md) | [abc12aqs02.md](./eng/abc12aqs02.md) |
| 12.3 最后收敛增量的输出 | 12.3 Output of last converged increment | [abc12aqs03.md](./chs/abc12aqs03.md) | [abc12aqs03.md](./eng/abc12aqs03.md) |
| 12.4 接触相关能量的输出 | 12.4 Output of contact-related energies | [abc12aqs04.md](./chs/abc12aqs04.md) | [abc12aqs04.md](./eng/abc12aqs04.md) |
| 12.5 矢量节点变量的幅值输出 | 12.5 Magnitude output of vector nodal variables | [abc12aqs05.md](./chs/abc12aqs05.md) | [abc12aqs05.md](./eng/abc12aqs05.md) |
| 12.6 等效塑性应变率 | 12.6 Equivalent plastic strain rate | [abc12aqs06.md](./chs/abc12aqs06.md) | [abc12aqs06.md](./eng/abc12aqs06.md) |
| 12.7 用于输出场过滤的有界值主应力 | 12.7 Principal stresses with bounding values for output field filtering | [abc12aqs07.md](./chs/abc12aqs07.md) | [abc12aqs07.md](./eng/abc12aqs07.md) |
| 12.8 在 Abaqus/CAE 中请求参考汇温度和膜系数场输出 | 12.8 Requesting reference sink temperature and film coefficient field output in Abaqus/CAE | [abc12aqs08.md](./chs/abc12aqs08.md) | [abc12aqs08.md](./eng/abc12aqs08.md) |
| 12.9 从多个帧生成自由体切割的表格报告 | 12.9 Generating tabular reports for free body cuts from multiple frames | [abc12aqs09.md](./chs/abc12aqs09.md) | [abc12aqs09.md](./eng/abc12aqs09.md) |
| 12.11 从视图切割定义的自由体读取X–Y数据 | 12.10 Selecting the area centroid as the summation point for free body cuts | [abc12aqs10.md](./chs/abc12aqs10.md) | [abc12aqs10.md](./eng/abc12aqs10.md) |
| 12.12 在链接视口上执行显示组布尔运算 | 12.11 Reading X–Y data from free bodies defined on view cuts | [abc12aqs11.md](./chs/abc12aqs11.md) | [abc12aqs11.md](./eng/abc12aqs11.md) |
| 12.10 选择面积质心作为自由体切割的求和点 | 12.12 Performing display group Boolean operations on linked viewports | [abc12aqs12.md](./chs/abc12aqs12.md) | [abc12aqs12.md](./eng/abc12aqs12.md) |
| 13 用户子程序、实用程序和插件 | 13 User subroutines, utilities, and plug-ins | [abc13.md](./chs/abc13.md) | [abc13.md](./eng/abc13.md) |
| 13.1 VEXTERNALDB：在分析关键时刻将控制权交给用户的用户子程序 | 13.1 VEXTERNALDB: User subroutine that gives control to the user at key moments of the analysis | [abc13aqs01.md](./chs/abc13aqs01.md) | [abc13aqs01.md](./eng/abc13aqs01.md) |
| 13.2 VUCHARLENGTH：在材料点定义特征单元长度的用户子程序 | 13.2 VUCHARLENGTH: User subroutine to define the characteristic element length at a material point | [abc13aqs02.md](./chs/abc13aqs02.md) | [abc13aqs02.md](./eng/abc13aqs02.md) |
| 13.3 用户子程序UMAT的增强 | 13.3 Enhancements to user subroutine UMAT | [abc13aqs03.md](./chs/abc13aqs03.md) | [abc13aqs03.md](./eng/abc13aqs03.md) |
| 13.4 可分配数组 | 13.4 Allocatable arrays | [abc13aqs04.md](./chs/abc13aqs04.md) | [abc13aqs04.md](./eng/abc13aqs04.md) |
| 13.5 并行用户子程序 | 13.5 Parallel user subroutines | [abc13aqs05.md](./chs/abc13aqs05.md) | [abc13aqs05.md](./eng/abc13aqs05.md) |
| 14 Abaqus Scripting Interface | 14 Abaqus Scripting Interface | [abc14.md](./chs/abc14.md) | [abc14.md](./eng/abc14.md) |
| 14.1 addData方法的增强 | 14.1 Enhancements to the addData method | [abc14aqs01.md](./chs/abc14aqs01.md) | [abc14aqs01.md](./eng/abc14aqs01.md) |
| 14.2 OdbSet对象的nodes成员的增强 | 14.2 Enhancement to the nodes member of the OdbSet object | [abc14aqs02.md](./chs/abc14aqs02.md) | [abc14aqs02.md](./eng/abc14aqs02.md) |
| 15 变更摘要 | 15 Summary of changes | [abs01.md](./chs/abs01.md) | [abs01.md](./eng/abs01.md) |
| 15.1 Abaqus单元的变更 | 15.1 Changes in Abaqus elements | [abs01acs01.md](./chs/abs01acs01.md) | [abs01acs01.md](./eng/abs01acs01.md) |
| 15.2 Abaqus选项的变更 | 15.2 Changes in Abaqus options | [abs01acs02.md](./chs/abs01acs02.md) | [abs01acs02.md](./eng/abs01acs02.md) |
| 15.3 Abaqus用户子程序的变更 | 15.3 Changes in Abaqus user subroutines | [abs01acs03.md](./chs/abs01acs03.md) | [abs01acs03.md](./eng/abs01acs03.md) |
| 15.4 Abaqus输出变量标识符的变更 | 15.4 Changes in Abaqus output variable identifiers | [abs01acs04.md](./chs/abs01acs04.md) | [abs01acs04.md](./eng/abs01acs04.md) |
| 产品索引 | Product Index | [pdx01.md](./chs/pdx01.md) | [pdx01.md](./eng/pdx01.md) |
| Abaqus/CFD | Abaqus/Standard | [pdx01pdd01.md](./chs/pdx01pdd01.md) | [pdx01pdd01.md](./eng/pdx01pdd01.md) |
| Abaqus/Explicit | Abaqus/Explicit | [pdx01pdd02.md](./chs/pdx01pdd02.md) | [pdx01pdd02.md](./eng/pdx01pdd02.md) |
| Abaqus/Standard | Abaqus/CFD | [pdx01pdd03.md](./chs/pdx01pdd03.md) | [pdx01pdd03.md](./eng/pdx01pdd03.md) |
| Abaqus/AMS | Abaqus/CAE | [pdx01pdd04.md](./chs/pdx01pdd04.md) | [pdx01pdd04.md](./eng/pdx01pdd04.md) |
| Abaqus/CAE | Abaqus/AMS | [pdx01pdd05.md](./chs/pdx01pdd05.md) | [pdx01pdd05.md](./eng/pdx01pdd05.md) |

---

## 资源文件 / Resource Files

图片资源位于 `graphics/` 目录。

---

## 版权声明 / Copyright Notice

本翻译仅供学习研究使用，原文档版权归 Dassault Systèmes Simulia Corp. 所有。
This translation is for study and research purposes only. Original documentation copyright Dassault Systèmes Simulia Corp.