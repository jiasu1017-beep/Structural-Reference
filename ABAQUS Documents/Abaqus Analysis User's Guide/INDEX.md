# Abaqus Analysis User's Guide (6.14)

## 文档索引 / Documentation Index

本手册为 ABAQUS 6.14 Abaqus Analysis User's Guide 的中文翻译版本。

**来源 / Source:** D:\SIMULIA\Documentation\docs\v6.14\books\usb\

---

## 双语目录对照 / Bilingual Table of Contents

### PT01
*1 简介*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 1 简介 | Introduction, Spatial Modeling, and Execution | [pt01.md](./chs/pt01.md) | [pt01.md](./eng/pt01.md) |
| 1.1 简介 | 1 Introduction | [pt01ch01.md](./chs/pt01ch01.md) | [pt01ch01.md](./eng/pt01ch01.md) |
| Abaqus Analysis User's Guide | 1.1 Introduction | [pt01ch01s01.md](./chs/pt01ch01s01.md) | [pt01ch01s01.md](./eng/pt01ch01s01.md) |
| 1.2 Abaqus 语法与约定 | 1.1.1 Introduction: general | [pt01ch01s01abo01.md](./chs/pt01ch01s01abo01.md) | [pt01ch01s01abo01.md](./eng/pt01ch01s01abo01.md) |
| 1.1.1 简介：概述 | 1.2 Abaqus syntax and conventions | [pt01ch01s02.md](./chs/pt01ch01s02.md) | [pt01ch01s02.md](./eng/pt01ch01s02.md) |
| 1.2.1 输入语法规则 | 1.2.1 Input syntax rules | [pt01ch01s02aus01.md](./chs/pt01ch01s02aus01.md) | [pt01ch01s02aus01.md](./eng/pt01ch01s02aus01.md) |
| 1.2.2 约定 | 1.2.2 Conventions | [pt01ch01s02aus02.md](./chs/pt01ch01s02aus02.md) | [pt01ch01s02aus02.md](./eng/pt01ch01s02aus02.md) |
| 1.3 Abaqus 模型定义 | 1.3 Abaqus model definition | [pt01ch01s03.md](./chs/pt01ch01s03.md) | [pt01ch01s03.md](./eng/pt01ch01s03.md) |
| 1.3.1 在 Abaqus 中定义模型 | 1.3.1 Defining a model in Abaqus | [pt01ch01s03aus03.md](./chs/pt01ch01s03aus03.md) | [pt01ch01s03aus03.md](./eng/pt01ch01s03aus03.md) |
| 1.4 参数化建模 | 1.4 Parametric modeling | [pt01ch01s04.md](./chs/pt01ch01s04.md) | [pt01ch01s04.md](./eng/pt01ch01s04.md) |
| 1.4.1 参数化输入 | 1.4.1 Parametric input | [pt01ch01s04aus04.md](./chs/pt01ch01s04aus04.md) | [pt01ch01s04aus04.md](./eng/pt01ch01s04aus04.md) |
| 2 空间建模 | 2 Spatial Modeling | [pt01ch02.md](./chs/pt01ch02.md) | [pt01ch02.md](./eng/pt01ch02.md) |
| 3.1 执行过程：概述 | 2.1 Node definition | [pt01ch02s01.md](./chs/pt01ch02s01.md) | [pt01ch02s01.md](./eng/pt01ch02s01.md) |
| 2.1.2 参数化形状变化 | 2.1.1 Node definition | [pt01ch02s01aus05.md](./chs/pt01ch02s01aus05.md) | [pt01ch02s01aus05.md](./eng/pt01ch02s01aus05.md) |
| 2.1.3 节点厚度 | 2.1.2 Parametric shape variation | [pt01ch02s01aus06.md](./chs/pt01ch02s01aus06.md) | [pt01ch02s01aus06.md](./eng/pt01ch02s01aus06.md) |
| 2.1.4 节点处的法线定义 | 2.1.3 Nodal thicknesses | [pt01ch02s01aus07.md](./chs/pt01ch02s01aus07.md) | [pt01ch02s01aus07.md](./eng/pt01ch02s01aus07.md) |
| 2.1.5 变换坐标系 | 2.1.4 Normal definitions at nodes | [pt01ch02s01aus08.md](./chs/pt01ch02s01aus08.md) | [pt01ch02s01aus08.md](./eng/pt01ch02s01aus08.md) |
| 2.1.1 节点定义 | 2.1.5 Transformed coordinate systems | [pt01ch02s01aus09.md](./chs/pt01ch02s01aus09.md) | [pt01ch02s01aus09.md](./eng/pt01ch02s01aus09.md) |
| 2.1.6 调整节点坐标 | 2.1.6 Adjusting nodal coordinates | [pt01ch02s01aus10.md](./chs/pt01ch02s01aus10.md) | [pt01ch02s01aus10.md](./eng/pt01ch02s01aus10.md) |
| 2.2 单元定义 | 2.2 Element definition | [pt01ch02s02.md](./chs/pt01ch02s02.md) | [pt01ch02s02.md](./eng/pt01ch02s02.md) |
| 2.2.1 单元定义 | 2.2.1 Element definition | [pt01ch02s02aus11.md](./chs/pt01ch02s02aus11.md) | [pt01ch02s02aus11.md](./eng/pt01ch02s02aus11.md) |
| 2.2.2 单元基础 | 2.2.2 Element foundations | [pt01ch02s02aus12.md](./chs/pt01ch02s02aus12.md) | [pt01ch02s02aus12.md](./eng/pt01ch02s02aus12.md) |
| 2.2.4 将钢筋定义为单元属性 | 2.2.3 Defining reinforcement | [pt01ch02s02aus13.md](./chs/pt01ch02s02aus13.md) | [pt01ch02s02aus13.md](./eng/pt01ch02s02aus13.md) |
| 2.2.3 定义钢筋 | 2.2.4 Defining rebar as an element property | [pt01ch02s02aus14.md](./chs/pt01ch02s02aus14.md) | [pt01ch02s02aus14.md](./eng/pt01ch02s02aus14.md) |
| 2.2.5 方向 | 2.2.5 Orientations | [pt01ch02s02aus15.md](./chs/pt01ch02s02aus15.md) | [pt01ch02s02aus15.md](./eng/pt01ch02s02aus15.md) |
| 2.3 表面定义 | 2.3 Surface definition | [pt01ch02s03.md](./chs/pt01ch02s03.md) | [pt01ch02s03.md](./eng/pt01ch02s03.md) |
| 2.3.1 表面：概述 | 2.3.1 Surfaces: overview | [pt01ch02s03aus16.md](./chs/pt01ch02s03aus16.md) | [pt01ch02s03aus16.md](./eng/pt01ch02s03aus16.md) |
| 2.3.2 基于单元的表面定义 | 2.3.2 Element-based surface definition | [pt01ch02s03aus17.md](./chs/pt01ch02s03aus17.md) | [pt01ch02s03aus17.md](./eng/pt01ch02s03aus17.md) |
| 2.3.3 基于节点的表面定义 | 2.3.3 Node-based surface definition | [pt01ch02s03aus18.md](./chs/pt01ch02s03aus18.md) | [pt01ch02s03aus18.md](./eng/pt01ch02s03aus18.md) |
| 2.3.4 解析刚体表面定义 | 2.3.4 Analytical rigid surface definition | [pt01ch02s03aus19.md](./chs/pt01ch02s03aus19.md) | [pt01ch02s03aus19.md](./eng/pt01ch02s03aus19.md) |
| 2.3.5 欧拉曲面定义 | 2.3.5 Eulerian surface definition | [pt01ch02s03aus20.md](./chs/pt01ch02s03aus20.md) | [pt01ch02s03aus20.md](./eng/pt01ch02s03aus20.md) |
| 2.3.6 曲面操作 | 2.3.6 Operating on surfaces | [pt01ch02s03aus21.md](./chs/pt01ch02s03aus21.md) | [pt01ch02s03aus21.md](./eng/pt01ch02s03aus21.md) |
| 2.4 分布定义 | 2.4 Rigid body definition | [pt01ch02s04.md](./chs/pt01ch02s04.md) | [pt01ch02s04.md](./eng/pt01ch02s04.md) |
| 2.4.1 刚体定义 | 2.4.1 Rigid body definition | [pt01ch02s04aus22.md](./chs/pt01ch02s04aus22.md) | [pt01ch02s04aus22.md](./eng/pt01ch02s04aus22.md) |
| 2.5 积分输出截面定义 | 2.5 Integrated output section definition | [pt01ch02s05.md](./chs/pt01ch02s05.md) | [pt01ch02s05.md](./eng/pt01ch02s05.md) |
| 2.5.1 积分输出截面定义 | 2.5.1 Integrated output section definition | [pt01ch02s05aus23.md](./chs/pt01ch02s05aus23.md) | [pt01ch02s05aus23.md](./eng/pt01ch02s05aus23.md) |
| 2.6 质量调整 | 2.6 Mass adjustment | [pt01ch02s06.md](./chs/pt01ch02s06.md) | [pt01ch02s06.md](./eng/pt01ch02s06.md) |
| 2.6.1 调整和/或重新分配单元集的质量 | 2.6.1 Adjust and/or redistribute mass of an element set | [pt01ch02s06aus24.md](./chs/pt01ch02s06aus24.md) | [pt01ch02s06aus24.md](./eng/pt01ch02s06aus24.md) |
| 2.7 非结构质量定义 | 2.7 Nonstructural mass definition | [pt01ch02s07.md](./chs/pt01ch02s07.md) | [pt01ch02s07.md](./eng/pt01ch02s07.md) |
| 2.7.1 非结构质量定义 | 2.7.1 Nonstructural mass definition | [pt01ch02s07aus25.md](./chs/pt01ch02s07aus25.md) | [pt01ch02s07aus25.md](./eng/pt01ch02s07aus25.md) |
| 2.8 分布定义 | 2.8 Distribution definition | [pt01ch02s08.md](./chs/pt01ch02s08.md) | [pt01ch02s08.md](./eng/pt01ch02s08.md) |
| 2.8.1 分布定义 | 2.8.1 Distribution definition | [pt01ch02s08aus26.md](./chs/pt01ch02s08aus26.md) | [pt01ch02s08aus26.md](./eng/pt01ch02s08aus26.md) |
| 2.9 显示体定义 | 2.9 Display body definition | [pt01ch02s09.md](./chs/pt01ch02s09.md) | [pt01ch02s09.md](./eng/pt01ch02s09.md) |
| 2.9.1 显示体定义 | 2.9.1 Display body definition | [pt01ch02s09aus27.md](./chs/pt01ch02s09aus27.md) | [pt01ch02s09aus27.md](./eng/pt01ch02s09aus27.md) |
| 2.10 装配定义 | 2.10 Assembly definition | [pt01ch02s10.md](./chs/pt01ch02s10.md) | [pt01ch02s10.md](./eng/pt01ch02s10.md) |
| 2.10.1 定义装配 | 2.10.1 Defining an assembly | [pt01ch02s10aus28.md](./chs/pt01ch02s10aus28.md) | [pt01ch02s10aus28.md](./eng/pt01ch02s10aus28.md) |
| 2.11 矩阵定义 | 2.11 Matrix definition | [pt01ch02s11.md](./chs/pt01ch02s11.md) | [pt01ch02s11.md](./eng/pt01ch02s11.md) |
| 2.11.1 定义矩阵 | 2.11.1 Defining matrices | [pt01ch02s11aus29.md](./chs/pt01ch02s11aus29.md) | [pt01ch02s11aus29.md](./eng/pt01ch02s11aus29.md) |
| 3 执行 | 3 Job Execution | [pt01ch03.md](./chs/pt01ch03.md) | [pt01ch03.md](./eng/pt01ch03.md) |
| 2.1 节点定义 | 3.1 Execution procedures: overview | [pt01ch03s01.md](./chs/pt01ch03s01.md) | [pt01ch03s01.md](./eng/pt01ch03s01.md) |
| 3.2 执行过程 | 3.1.1 Execution procedure for Abaqus: overview | [pt01ch03s01abo02.md](./chs/pt01ch03s01abo02.md) | [pt01ch03s01abo02.md](./eng/pt01ch03s01abo02.md) |
| 3.2.1 获取信息 | 3.2 Execution procedures | [pt01ch03s02.md](./chs/pt01ch03s02.md) | [pt01ch03s02.md](./eng/pt01ch03s02.md) |
| 3.1.1 Abaqus执行过程概述 | 3.2.1 Obtaining information | [pt01ch03s02abx01.md](./chs/pt01ch03s02abx01.md) | [pt01ch03s02abx01.md](./eng/pt01ch03s02abx01.md) |
| 3.2.2 Abaqus/Standard、Abaqus/Explicit和Abaqus/CFD执行 | 3.2.2 Abaqus/Standard, Abaqus/Explicit, and Abaqus/CFD execution | [pt01ch03s02abx02.md](./chs/pt01ch03s02abx02.md) | [pt01ch03s02abx02.md](./eng/pt01ch03s02abx02.md) |
| 3.2.3 SIMULIA协同仿真引擎director执行 | 3.2.3 SIMULIA Co-Simulation Engine director execution | [pt01ch03s02abx03.md](./chs/pt01ch03s02abx03.md) | [pt01ch03s02abx03.md](./eng/pt01ch03s02abx03.md) |
| 3.2.4 Abaqus/Standard、Abaqus/Explicit和Abaqus/CFD协同仿真执行 | 3.2.4 Abaqus/Standard, Abaqus/Explicit, and Abaqus/CFD co-simulation execution | [pt01ch03s02abx04.md](./chs/pt01ch03s02abx04.md) | [pt01ch03s02abx04.md](./eng/pt01ch03s02abx04.md) |
| 3.2.5 Dymola模型执行 | 3.2.5 Dymola model execution | [pt01ch03s02abx05.md](./chs/pt01ch03s02abx05.md) | [pt01ch03s02abx05.md](./eng/pt01ch03s02abx05.md) |
| 3.2.6 Abaqus/CAE执行 | 3.2.6 Abaqus/CAE execution | [pt01ch03s02abx06.md](./chs/pt01ch03s02abx06.md) | [pt01ch03s02abx06.md](./eng/pt01ch03s02abx06.md) |
| 3.2.7 Abaqus/Viewer执行 | 3.2.7 Abaqus/Viewer execution | [pt01ch03s02abx07.md](./chs/pt01ch03s02abx07.md) | [pt01ch03s02abx07.md](./eng/pt01ch03s02abx07.md) |
| 3.2.8 拓扑优化执行 | 3.2.8 Topology optimization execution | [pt01ch03s02abx08.md](./chs/pt01ch03s02abx08.md) | [pt01ch03s02abx08.md](./eng/pt01ch03s02abx08.md) |
| 3.2.9 Python 执行 | 3.2.9 Python execution | [pt01ch03s02abx09.md](./chs/pt01ch03s02abx09.md) | [pt01ch03s02abx09.md](./eng/pt01ch03s02abx09.md) |
| 3.2.10 参数化研究 | 3.2.10 Parametric studies | [pt01ch03s02abx10.md](./chs/pt01ch03s02abx10.md) | [pt01ch03s02abx10.md](./eng/pt01ch03s02abx10.md) |
| 3.2.11 Abaqus文档 | 3.2.11 Abaqus documentation | [pt01ch03s02abx11.md](./chs/pt01ch03s02abx11.md) | [pt01ch03s02abx11.md](./eng/pt01ch03s02abx11.md) |
| 3.2.12 许可工具 | 3.2.12 Licensing utilities | [pt01ch03s02abx12.md](./chs/pt01ch03s02abx12.md) | [pt01ch03s02abx12.md](./eng/pt01ch03s02abx12.md) |
| 3.2.13 结果(.fil)文件的ASCII转换 | 3.2.13 ASCII translation of results (.fil) files | [pt01ch03s02abx13.md](./chs/pt01ch03s02abx13.md) | [pt01ch03s02abx13.md](./eng/pt01ch03s02abx13.md) |
| 3.2.14 连接结果(.fil)文件 | 3.2.14 Joining results (.fil) files | [pt01ch03s02abx14.md](./chs/pt01ch03s02abx14.md) | [pt01ch03s02abx14.md](./eng/pt01ch03s02abx14.md) |
| 3.2.15 查询关键字/问题数据库 | 3.2.15 Querying the keyword/problem database | [pt01ch03s02abx15.md](./chs/pt01ch03s02abx15.md) | [pt01ch03s02abx15.md](./eng/pt01ch03s02abx15.md) |
| 3.2.16 获取示例输入文件 | 3.2.16 Fetching sample input files | [pt01ch03s02abx16.md](./chs/pt01ch03s02abx16.md) | [pt01ch03s02abx16.md](./eng/pt01ch03s02abx16.md) |
| 3.2.17 创建用户定义的可执行文件和子程序 | 3.2.17 Making user-defined executables and subroutines | [pt01ch03s02abx17.md](./chs/pt01ch03s02abx17.md) | [pt01ch03s02abx17.md](./eng/pt01ch03s02abx17.md) |
| 3.2.18 输出数据库升级工具 | 3.2.18 Output database upgrade utility | [pt01ch03s02abx18.md](./chs/pt01ch03s02abx18.md) | [pt01ch03s02abx18.md](./eng/pt01ch03s02abx18.md) |
| 3.2.19 SIM数据库工具 | 3.2.19 SIM database utilities | [pt01ch03s02abx19.md](./chs/pt01ch03s02abx19.md) | [pt01ch03s02abx19.md](./eng/pt01ch03s02abx19.md) |
| 3.2.20 生成输出数据库报告 | 3.2.20 Generating output database reports | [pt01ch03s02abx20.md](./chs/pt01ch03s02abx20.md) | [pt01ch03s02abx20.md](./eng/pt01ch03s02abx20.md) |
| 3.2.21 连接重启分析的输出数据库(.odb)文件 | 3.2.21 Joining output database (.odb) files from restarted analyses | [pt01ch03s02abx21.md](./chs/pt01ch03s02abx21.md) | [pt01ch03s02abx21.md](./eng/pt01ch03s02abx21.md) |
| 3.2.22 组合子结构输出 | 3.2.22 Combining output from substructures | [pt01ch03s02abx22.md](./chs/pt01ch03s02abx22.md) | [pt01ch03s02abx22.md](./eng/pt01ch03s02abx22.md) |
| 3.2.23 组合多个输出数据库的数据 | 3.2.23 Combining data from multiple output databases | [pt01ch03s02abx23.md](./chs/pt01ch03s02abx23.md) | [pt01ch03s02abx23.md](./eng/pt01ch03s02abx23.md) |
| 3.2.24 网络输出数据库文件连接器 | 3.2.24 Network output database file connector | [pt01ch03s02abx24.md](./chs/pt01ch03s02abx24.md) | [pt01ch03s02abx24.md](./eng/pt01ch03s02abx24.md) |
| 3.2.25 映射热载荷和磁载荷 | 3.2.25 Mapping thermal and magnetic loads | [pt01ch03s02abx25.md](./chs/pt01ch03s02abx25.md) | [pt01ch03s02abx25.md](./eng/pt01ch03s02abx25.md) |
| 3.2.26 元素矩阵装配工具 | 3.2.26 Element matrix assembly utility | [pt01ch03s02abx26.md](./chs/pt01ch03s02abx26.md) | [pt01ch03s02abx26.md](./eng/pt01ch03s02abx26.md) |
| 3.2.27 固定格式转换工具 | 3.2.27 Fixed format conversion utility | [pt01ch03s02abx27.md](./chs/pt01ch03s02abx27.md) | [pt01ch03s02abx27.md](./eng/pt01ch03s02abx27.md) |
| 3.2.28 将Nastran bulk数据文件转换为Abaqus输入文件 | 3.2.28 Translating Nastran bulk data files to Abaqus input files | [pt01ch03s02abx28.md](./chs/pt01ch03s02abx28.md) | [pt01ch03s02abx28.md](./eng/pt01ch03s02abx28.md) |
| 3.2.29 将Abaqus文件转换为Nastran bulk数据文件 | 3.2.29 Translating Abaqus files to Nastran bulk data files | [pt01ch03s02abx29.md](./chs/pt01ch03s02abx29.md) | [pt01ch03s02abx29.md](./eng/pt01ch03s02abx29.md) |
| 3.2.30 将ANSYS输入文件转换为部分Abaqus输入文件 | 3.2.30 Translating ANSYS input files to partial Abaqus input files | [pt01ch03s02abx30.md](./chs/pt01ch03s02abx30.md) | [pt01ch03s02abx30.md](./eng/pt01ch03s02abx30.md) |
| 3.2.31 将 PAM-CRASH 输入文件转换为部分 Abaqus 输入文件 | 3.2.31 Translating PAM-CRASH input files to partial Abaqus input files | [pt01ch03s02abx31.md](./chs/pt01ch03s02abx31.md) | [pt01ch03s02abx31.md](./eng/pt01ch03s02abx31.md) |
| 3.2.32 将 RADIOSS 输入文件转换为部分 Abaqus 输入文件 | 3.2.32 Translating RADIOSS input files to partial Abaqus input files | [pt01ch03s02abx32.md](./chs/pt01ch03s02abx32.md) | [pt01ch03s02abx32.md](./eng/pt01ch03s02abx32.md) |
| 3.2.33 将 Abaqus 输出数据库文件转换为 Nastran Output2 结果文件 | 3.2.33 Translating Abaqus output database files to Nastran Output2 results files | [pt01ch03s02abx33.md](./chs/pt01ch03s02abx33.md) | [pt01ch03s02abx33.md](./eng/pt01ch03s02abx33.md) |
| 3.2.34 将 LS-DYNA 数据文件转换为 Abaqus 输入文件 | 3.2.34 Translating LS-DYNA data files to Abaqus input files | [pt01ch03s02abx34.md](./chs/pt01ch03s02abx34.md) | [pt01ch03s02abx34.md](./eng/pt01ch03s02abx34.md) |
| 3.2.35 与 ZAERO 交换 Abaqus 数据 | 3.2.35 Exchanging Abaqus data with ZAERO | [pt01ch03s02abx35.md](./chs/pt01ch03s02abx35.md) | [pt01ch03s02abx35.md](./eng/pt01ch03s02abx35.md) |
| 3.2.36 将 Abaqus 数据转换为 MSC.ADAMS 模态中性文件 | 3.2.36 Translating Abaqus data to MSC.ADAMS modal neutral files | [pt01ch03s02abx36.md](./chs/pt01ch03s02abx36.md) | [pt01ch03s02abx36.md](./eng/pt01ch03s02abx36.md) |
| 3.2.37 将 Moldflow 数据转换为 Abaqus 输入文件 | 3.2.37 Translating Moldflow data to Abaqus input files | [pt01ch03s02abx37.md](./chs/pt01ch03s02abx37.md) | [pt01ch03s02abx37.md](./eng/pt01ch03s02abx37.md) |
| 3.2.38 加密和解密 Abaqus 输入数据 | 3.2.38 Encrypting and decrypting Abaqus input data | [pt01ch03s02abx38.md](./chs/pt01ch03s02abx38.md) | [pt01ch03s02abx38.md](./eng/pt01ch03s02abx38.md) |
| 3.2.39 作业执行控制 | 3.2.39 Job execution control | [pt01ch03s02abx39.md](./chs/pt01ch03s02abx39.md) | [pt01ch03s02abx39.md](./eng/pt01ch03s02abx39.md) |
| 3.3 环境文件设置 | 3.3 Environment file settings | [pt01ch03s03.md](./chs/pt01ch03s03.md) | [pt01ch03s03.md](./eng/pt01ch03s03.md) |
| 3.3.1 使用Abaqus环境设置 | 3.3.1 Using the Abaqus environment settings | [pt01ch03s03aus30.md](./chs/pt01ch03s03aus30.md) | [pt01ch03s03aus30.md](./eng/pt01ch03s03aus30.md) |
| 3.4 管理内存和磁盘资源 | 3.4 Managing memory and disk resources | [pt01ch03s04.md](./chs/pt01ch03s04.md) | [pt01ch03s04.md](./eng/pt01ch03s04.md) |
| 3.4.1 管理Abaqus中的内存和磁盘使用 | 3.4.1 Managing memory and disk use in Abaqus | [pt01ch03s04aus31.md](./chs/pt01ch03s04aus31.md) | [pt01ch03s04aus31.md](./eng/pt01ch03s04aus31.md) |
| 3.5 并行执行 | 3.5 Parallel execution | [pt01ch03s05.md](./chs/pt01ch03s05.md) | [pt01ch03s05.md](./eng/pt01ch03s05.md) |
| 3.5.1 并行执行：概述 | 3.5.1 Parallel execution: overview | [pt01ch03s05aus32.md](./chs/pt01ch03s05aus32.md) | [pt01ch03s05aus32.md](./eng/pt01ch03s05aus32.md) |
| 3.5.2 Abaqus/Standard中的并行执行 | 3.5.2 Parallel execution in Abaqus/Standard | [pt01ch03s05aus33.md](./chs/pt01ch03s05aus33.md) | [pt01ch03s05aus33.md](./eng/pt01ch03s05aus33.md) |
| 3.5.3 Abaqus/Explicit中的并行执行 | 3.5.3 Parallel execution in Abaqus/Explicit | [pt01ch03s05aus34.md](./chs/pt01ch03s05aus34.md) | [pt01ch03s05aus34.md](./eng/pt01ch03s05aus34.md) |
| 3.5.4 Abaqus/CFD中的并行执行 | 3.5.4 Parallel execution in Abaqus/CFD | [pt01ch03s05aus35.md](./chs/pt01ch03s05aus35.md) | [pt01ch03s05aus35.md](./eng/pt01ch03s05aus35.md) |
| 3.6 文件扩展名定义 | 3.6 File extension definitions | [pt01ch03s06.md](./chs/pt01ch03s06.md) | [pt01ch03s06.md](./eng/pt01ch03s06.md) |
| 3.6.1 Abaqus使用的文件扩展名 | 3.6.1 File extensions used by Abaqus | [pt01ch03s06aus36.md](./chs/pt01ch03s06aus36.md) | [pt01ch03s06aus36.md](./eng/pt01ch03s06aus36.md) |
| 3.7 FORTRAN单元号 | 3.7 FORTRAN unit numbers | [pt01ch03s07.md](./chs/pt01ch03s07.md) | [pt01ch03s07.md](./eng/pt01ch03s07.md) |
| 3.7.1 Abaqus使用的FORTRAN单元号 | 3.7.1 FORTRAN unit numbers used by Abaqus | [pt01ch03s07aus37.md](./chs/pt01ch03s07aus37.md) | [pt01ch03s07aus37.md](./eng/pt01ch03s07aus37.md) |

### PT02
*输出*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 输出 | Output | [pt02.md](./chs/pt02.md) | [pt02.md](./eng/pt02.md) |
| 4 输出 | 4 Output | [pt02ch04.md](./chs/pt02ch04.md) | [pt02ch04.md](./eng/pt02ch04.md) |
| 4.1 输出 | 4.1 Output | [pt02ch04s01.md](./chs/pt02ch04s01.md) | [pt02ch04s01.md](./eng/pt02ch04s01.md) |
| 4.1.1 输出 | 4.1.1 Output | [pt02ch04s01aus38.md](./chs/pt02ch04s01aus38.md) | [pt02ch04s01aus38.md](./eng/pt02ch04s01aus38.md) |
| 4.1.2 输出到数据和结果文件 | 4.1.2 Output to the data and results files | [pt02ch04s01aus39.md](./chs/pt02ch04s01aus39.md) | [pt02ch04s01aus39.md](./eng/pt02ch04s01aus39.md) |
| 4.1.3 输出到输出数据库 | 4.1.3 Output to the output database | [pt02ch04s01aus40.md](./chs/pt02ch04s01aus40.md) | [pt02ch04s01aus40.md](./eng/pt02ch04s01aus40.md) |
| 4.1.4 误差指示器输出 | 4.1.4 Error indicator output | [pt02ch04s01aus41.md](./chs/pt02ch04s01aus41.md) | [pt02ch04s01aus41.md](./eng/pt02ch04s01aus41.md) |
| 4.2 输出变量 | 4.2 Output variables | [pt02ch04s02.md](./chs/pt02ch04s02.md) | [pt02ch04s02.md](./eng/pt02ch04s02.md) |
| 4.2.3 Abaqus/CFD 输出变量标识符 | 4.2.1 Abaqus/Standard output variable identifiers | [pt02ch04s02abv01.md](./chs/pt02ch04s02abv01.md) | [pt02ch04s02abv01.md](./eng/pt02ch04s02abv01.md) |
| 4.2.3 Abaqus/CFD输出变量标识符 | 4.2.3 Abaqus/CFD output variable identifiers | [pt02ch04s02cbv01.md](./chs/pt02ch04s02cbv01.md) | [pt02ch04s02cbv01.md](./eng/pt02ch04s02cbv01.md) |
| 4.2.2 Abaqus/Explicit输出变量标识符 | 4.2.2 Abaqus/Explicit output variable identifiers | [pt02ch04s02xbv01.md](./chs/pt02ch04s02xbv01.md) | [pt02ch04s02xbv01.md](./eng/pt02ch04s02xbv01.md) |
| 4.3 后处理计算器 | 4.3 The postprocessing calculator | [pt02ch04s03.md](./chs/pt02ch04s03.md) | [pt02ch04s03.md](./eng/pt02ch04s03.md) |
| 4.3.1 后处理计算器 | 4.3.1 The postprocessing calculator | [pt02ch04s03aus42.md](./chs/pt02ch04s03aus42.md) | [pt02ch04s03aus42.md](./eng/pt02ch04s03aus42.md) |
| 5 文件输出格式 | 5 File Output Format | [pt02ch05.md](./chs/pt02ch05.md) | [pt02ch05.md](./eng/pt02ch05.md) |
| 5.1 访问结果文件 | 5.1 Accessing the results file | [pt02ch05s01.md](./chs/pt02ch05s01.md) | [pt02ch05s01.md](./eng/pt02ch05s01.md) |
| 5.1.1 Accessing the results file: overview | 5.1.1 Accessing the results file: overview | [pt02ch05s01abo03.md](./chs/pt02ch05s01abo03.md) | [pt02ch05s01abo03.md](./eng/pt02ch05s01abo03.md) |
| 5.1.4 访问结果文件的实用程序 | 5.1.4 Utility routines for accessing the results file | [pt02ch05s01abu01.md](./chs/pt02ch05s01abu01.md) | [pt02ch05s01abu01.md](./eng/pt02ch05s01abu01.md) |
| 5.1.2 结果文件输出格式 | 5.1.2 Results file output format | [pt02ch05s01afi01.md](./chs/pt02ch05s01afi01.md) | [pt02ch05s01afi01.md](./eng/pt02ch05s01afi01.md) |
| 5.1.3 访问结果文件信息 | 5.1.3 Accessing the results file information | [pt02ch05s01aus43.md](./chs/pt02ch05s01aus43.md) | [pt02ch05s01aus43.md](./eng/pt02ch05s01aus43.md) |

### PT03
*6 分析过程*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 6 分析过程 | Analysis Procedures, Solution, and Control | [pt03.md](./chs/pt03.md) | [pt03.md](./eng/pt03.md) |
| 6.1 简介 | 6 Analysis Procedures | [pt03ch06.md](./chs/pt03ch06.md) | [pt03ch06.md](./eng/pt03ch06.md) |
| 分析过程、解和控制的说明 | 6.1 Introduction | [pt03ch06s01.md](./chs/pt03ch06s01.md) | [pt03ch06s01.md](./eng/pt03ch06s01.md) |
| 6.1.1 求解分析问题：概述 | 6.1.1 Solving analysis problems: overview | [pt03ch06s01abo04.md](./chs/pt03ch06s01abo04.md) | [pt03ch06s01abo04.md](./eng/pt03ch06s01abo04.md) |
| 6.1.2 定义分析 | 6.1.2 Defining an analysis | [pt03ch06s01abo05.md](./chs/pt03ch06s01abo05.md) | [pt03ch06s01abo05.md](./eng/pt03ch06s01abo05.md) |
| 6.1.3 常规与线性扰动分析步骤 | 6.1.3 General and linear perturbation procedures | [pt03ch06s01aus44.md](./chs/pt03ch06s01aus44.md) | [pt03ch06s01aus44.md](./eng/pt03ch06s01aus44.md) |
| 6.1.4 多载荷工况分析 | 6.1.4 Multiple load case analysis | [pt03ch06s01aus45.md](./chs/pt03ch06s01aus45.md) | [pt03ch06s01aus45.md](./eng/pt03ch06s01aus45.md) |
| 6.1.5 直接线性方程求解器 | 6.1.5 Direct linear equation solver | [pt03ch06s01aus46.md](./chs/pt03ch06s01aus46.md) | [pt03ch06s01aus46.md](./eng/pt03ch06s01aus46.md) |
| 6.1.6 迭代线性方程求解器 | 6.1.6 Iterative linear equation solver | [pt03ch06s01aus47.md](./chs/pt03ch06s01aus47.md) | [pt03ch06s01aus47.md](./eng/pt03ch06s01aus47.md) |
| 6.2 Static stress/displacement analysis | 6.2 Static stress/displacement analysis | [pt03ch06s02.md](./chs/pt03ch06s02.md) | [pt03ch06s02.md](./eng/pt03ch06s02.md) |
| 6.2.1 Static stress analysis procedures: overview | 6.2.1 Static stress analysis procedures: overview | [pt03ch06s02abo06.md](./chs/pt03ch06s02abo06.md) | [pt03ch06s02abo06.md](./eng/pt03ch06s02abo06.md) |
| 6.2.2 静态应力分析 | 6.2.2 Static stress analysis | [pt03ch06s02at01.md](./chs/pt03ch06s02at01.md) | [pt03ch06s02at01.md](./eng/pt03ch06s02at01.md) |
| 6.2.3 特征值屈曲预测 | 6.2.3 Eigenvalue buckling prediction | [pt03ch06s02at02.md](./chs/pt03ch06s02at02.md) | [pt03ch06s02at02.md](./eng/pt03ch06s02at02.md) |
| 6.2.4 不稳定坍塌与后屈曲分析 | 6.2.4 Unstable collapse and postbuckling analysis | [pt03ch06s02at03.md](./chs/pt03ch06s02at03.md) | [pt03ch06s02at03.md](./eng/pt03ch06s02at03.md) |
| 6.2.5 准静态分析 | 6.2.5 Quasi-static analysis | [pt03ch06s02at04.md](./chs/pt03ch06s02at04.md) | [pt03ch06s02at04.md](./eng/pt03ch06s02at04.md) |
| 6.2.6 直接循环分析 | 6.2.6 Direct cyclic analysis | [pt03ch06s02at05.md](./chs/pt03ch06s02at05.md) | [pt03ch06s02at05.md](./eng/pt03ch06s02at05.md) |
| 6.2.7 使用直接循环方法的低周疲劳分析 | 6.2.7 Low-cycle fatigue analysis using the direct cyclic approach | [pt03ch06s02at06.md](./chs/pt03ch06s02at06.md) | [pt03ch06s02at06.md](./eng/pt03ch06s02at06.md) |
| 6.3 Dynamic stress/displacement analysis | 6.3 Dynamic stress/displacement analysis | [pt03ch06s03.md](./chs/pt03ch06s03.md) | [pt03ch06s03.md](./eng/pt03ch06s03.md) |
| 6.3.1 动态分析过程：概述 | 6.3.1 Dynamic analysis procedures: overview | [pt03ch06s03abo07.md](./chs/pt03ch06s03abo07.md) | [pt03ch06s03abo07.md](./eng/pt03ch06s03abo07.md) |
| 6.3.2 使用直接积分的隐式动态分析 | 6.3.2 Implicit dynamic analysis using direct integration | [pt03ch06s03at07.md](./chs/pt03ch06s03at07.md) | [pt03ch06s03at07.md](./eng/pt03ch06s03at07.md) |
| 6.3.6 复特征值提取 | 6.3.3 Explicit dynamic analysis | [pt03ch06s03at08.md](./chs/pt03ch06s03at08.md) | [pt03ch06s03at08.md](./eng/pt03ch06s03at08.md) |
| 6.3.4 直接求解稳态动态分析 | 6.3.4 Direct-solution steady-state dynamic analysis | [pt03ch06s03at09.md](./chs/pt03ch06s03at09.md) | [pt03ch06s03at09.md](./eng/pt03ch06s03at09.md) |
| 6.3.3 显式动态分析 | 6.3.5 Natural frequency extraction | [pt03ch06s03at10.md](./chs/pt03ch06s03at10.md) | [pt03ch06s03at10.md](./eng/pt03ch06s03at10.md) |
| 6.3.6 复特征值提取 | 6.3.6 Complex eigenvalue extraction | [pt03ch06s03at11.md](./chs/pt03ch06s03at11.md) | [pt03ch06s03at11.md](./eng/pt03ch06s03at11.md) |
| 6.3.7 瞬态模态动态分析 | 6.3.7 Transient modal dynamic analysis | [pt03ch06s03at12.md](./chs/pt03ch06s03at12.md) | [pt03ch06s03at12.md](./eng/pt03ch06s03at12.md) |
| 6.3.8 基于模态的稳态动力学分析 | 6.3.8 Mode-based steady-state dynamic analysis | [pt03ch06s03at13.md](./chs/pt03ch06s03at13.md) | [pt03ch06s03at13.md](./eng/pt03ch06s03at13.md) |
| 6.3.9 基于子空间的稳态动力学分析 | 6.3.9 Subspace-based steady-state dynamic analysis | [pt03ch06s03at14.md](./chs/pt03ch06s03at14.md) | [pt03ch06s03at14.md](./eng/pt03ch06s03at14.md) |
| 6.3.10 响应谱分析 | 6.3.10 Response spectrum analysis | [pt03ch06s03at15.md](./chs/pt03ch06s03at15.md) | [pt03ch06s03at15.md](./eng/pt03ch06s03at15.md) |
| 6.3.11 随机响应分析 | 6.3.11 Random response analysis | [pt03ch06s03at16.md](./chs/pt03ch06s03at16.md) | [pt03ch06s03at16.md](./eng/pt03ch06s03at16.md) |
| 6.4 Steady-state transport analysis | 6.4 Steady-state transport analysis | [pt03ch06s04.md](./chs/pt03ch06s04.md) | [pt03ch06s04.md](./eng/pt03ch06s04.md) |
| 6.4.1 稳态传输分析 | 6.4.1 Steady-state transport analysis | [pt03ch06s04at17.md](./chs/pt03ch06s04at17.md) | [pt03ch06s04at17.md](./eng/pt03ch06s04at17.md) |
| 6.5 Heat transfer and thermal-stress analysis | 6.5 Heat transfer and thermal-stress analysis | [pt03ch06s05.md](./chs/pt03ch06s05.md) | [pt03ch06s05.md](./eng/pt03ch06s05.md) |
| 6.5.1 Heat transfer analysis procedures: overview | 6.5.1 Heat transfer analysis procedures: overview | [pt03ch06s05abo08.md](./chs/pt03ch06s05abo08.md) | [pt03ch06s05abo08.md](./eng/pt03ch06s05abo08.md) |
| 6.5.2 非耦合热传递分析 | 6.5.2 Uncoupled heat transfer analysis | [pt03ch06s05at18.md](./chs/pt03ch06s05at18.md) | [pt03ch06s05at18.md](./eng/pt03ch06s05at18.md) |
| 6.5.3 全耦合热应力分析 | 6.5.3 Fully coupled thermal-stress analysis | [pt03ch06s05at19.md](./chs/pt03ch06s05at19.md) | [pt03ch06s05at19.md](./eng/pt03ch06s05at19.md) |
| 6.5.4 绝热分析 | 6.5.4 Adiabatic analysis | [pt03ch06s05at20.md](./chs/pt03ch06s05at20.md) | [pt03ch06s05at20.md](./eng/pt03ch06s05at20.md) |
| 6.6 Fluid dynamic analysis | 6.6 Fluid dynamic analysis | [pt03ch06s06.md](./chs/pt03ch06s06.md) | [pt03ch06s06.md](./eng/pt03ch06s06.md) |
| 6.6.1 流体动力学分析过程：概述 | 6.6.1 Fluid dynamic analysis procedures: overview | [pt03ch06s06abo09.md](./chs/pt03ch06s06abo09.md) | [pt03ch06s06abo09.md](./eng/pt03ch06s06abo09.md) |
| 6.6.2 不可压缩流体动力学分析 | 6.6.2 Incompressible fluid dynamic analysis | [pt03ch06s06aus48.md](./chs/pt03ch06s06aus48.md) | [pt03ch06s06aus48.md](./eng/pt03ch06s06aus48.md) |
| 6.7 Electromagnetic analysis | 6.7 Electromagnetic analysis | [pt03ch06s07.md](./chs/pt03ch06s07.md) | [pt03ch06s07.md](./eng/pt03ch06s07.md) |
| 6.7.1 电磁分析步概述 | 6.7.1 Electromagnetic analysis procedures | [pt03ch06s07abo10.md](./chs/pt03ch06s07abo10.md) | [pt03ch06s07abo10.md](./eng/pt03ch06s07abo10.md) |
| 6.7.2 压电分析 | 6.7.2 Piezoelectric analysis | [pt03ch06s07at21.md](./chs/pt03ch06s07at21.md) | [pt03ch06s07at21.md](./eng/pt03ch06s07at21.md) |
| 6.7.3 耦合热-电分析 | 6.7.3 Coupled thermal-electrical analysis | [pt03ch06s07at22.md](./chs/pt03ch06s07at22.md) | [pt03ch06s07at22.md](./eng/pt03ch06s07at22.md) |
| 6.7.4 全耦合热-电-结构分析 | 6.7.4 Fully coupled thermal-electrical-structural analysis | [pt03ch06s07at23.md](./chs/pt03ch06s07at23.md) | [pt03ch06s07at23.md](./eng/pt03ch06s07at23.md) |
| 6.7.5 涡流分析 | 6.7.5 Eddy current analysis | [pt03ch06s07at24.md](./chs/pt03ch06s07at24.md) | [pt03ch06s07at24.md](./eng/pt03ch06s07at24.md) |
| 6.7.6 磁静态分析 | 6.7.6 Magnetostatic analysis | [pt03ch06s07at25.md](./chs/pt03ch06s07at25.md) | [pt03ch06s07at25.md](./eng/pt03ch06s07at25.md) |
| 6.8 Coupled pore fluid flow and stress analysis | 6.8 Coupled pore fluid flow and stress analysis | [pt03ch06s08.md](./chs/pt03ch06s08.md) | [pt03ch06s08.md](./eng/pt03ch06s08.md) |
| 6.8.1 耦合孔隙流体扩散与应力分析 | 6.8.1 Coupled pore fluid diffusion and stress analysis | [pt03ch06s08at26.md](./chs/pt03ch06s08at26.md) | [pt03ch06s08at26.md](./eng/pt03ch06s08at26.md) |
| 6.8.2 地静力应力状态 | 6.8.2 Geostatic stress state | [pt03ch06s08at27.md](./chs/pt03ch06s08at27.md) | [pt03ch06s08at27.md](./eng/pt03ch06s08at27.md) |
| 6.9 Mass diffusion analysis | 6.9 Mass diffusion analysis | [pt03ch06s09.md](./chs/pt03ch06s09.md) | [pt03ch06s09.md](./eng/pt03ch06s09.md) |
| 6.9.1 质量扩散分析 | 6.9.1 Mass diffusion analysis | [pt03ch06s09at28.md](./chs/pt03ch06s09at28.md) | [pt03ch06s09at28.md](./eng/pt03ch06s09at28.md) |
| 6.10 Acoustic and shock analysis | 6.10 Acoustic and shock analysis | [pt03ch06s10.md](./chs/pt03ch06s10.md) | [pt03ch06s10.md](./eng/pt03ch06s10.md) |
| 10.3.1 在 Abaqus/Explicit 中使用退火程序 | 6.10.1 Acoustic, shock, and coupled acoustic-structural analysis | [pt03ch06s10at29.md](./chs/pt03ch06s10at29.md) | [pt03ch06s10at29.md](./eng/pt03ch06s10at29.md) |
| 6.11 Abaqus/Aqua analysis | 6.11 Abaqus/Aqua analysis | [pt03ch06s11.md](./chs/pt03ch06s11.md) | [pt03ch06s11.md](./eng/pt03ch06s11.md) |
| 10.3.2 Abaqus/Aqua 分析 | 6.11.1 Abaqus/Aqua analysis | [pt03ch06s11at30.md](./chs/pt03ch06s11at30.md) | [pt03ch06s11at30.md](./eng/pt03ch06s11at30.md) |
| 6.12 Annealing | 6.12 Annealing | [pt03ch06s12.md](./chs/pt03ch06s12.md) | [pt03ch06s12.md](./eng/pt03ch06s12.md) |
| 10.3.3 声学、冲击和耦合声学-结构分析 | 6.12.1 Annealing procedure | [pt03ch06s12at31.md](./chs/pt03ch06s12at31.md) | [pt03ch06s12at31.md](./eng/pt03ch06s12at31.md) |
| 7 Analysis Solution and Control | 7 Analysis Solution and Control | [pt03ch07.md](./chs/pt03ch07.md) | [pt03ch07.md](./eng/pt03ch07.md) |
| 7.1 Solving nonlinear problems | 7.1 Solving nonlinear problems | [pt03ch07s01.md](./chs/pt03ch07s01.md) | [pt03ch07s01.md](./eng/pt03ch07s01.md) |
| 11.1.1 使用牛顿法求解非线性问题 | 7.1.1 Solving nonlinear problems | [pt03ch07s01aus49.md](./chs/pt03ch07s01aus49.md) | [pt03ch07s01aus49.md](./eng/pt03ch07s01aus49.md) |
| 7.2 Analysis convergence controls | 7.2 Analysis convergence controls | [pt03ch07s02.md](./chs/pt03ch07s02.md) | [pt03ch07s02.md](./eng/pt03ch07s02.md) |
| 7.2.1 Convergence and time integration criteria: overview | 7.2.1 Convergence and time integration criteria: overview | [pt03ch07s02abo11.md](./chs/pt03ch07s02abo11.md) | [pt03ch07s02abo11.md](./eng/pt03ch07s02abo11.md) |
| 11.1.2 常用求解控制参数 | 7.2.2 Commonly used control parameters | [pt03ch07s02aus50.md](./chs/pt03ch07s02aus50.md) | [pt03ch07s02aus50.md](./eng/pt03ch07s02aus50.md) |
| 11.1.3 非线性问题的收敛准则 | 7.2.3 Convergence criteria for nonlinear problems | [pt03ch07s02aus51.md](./chs/pt03ch07s02aus51.md) | [pt03ch07s02aus51.md](./eng/pt03ch07s02aus51.md) |
| 11.1.4 瞬态问题的时间积分精度 | 7.2.4 Time integration accuracy in transient problems | [pt03ch07s02aus52.md](./chs/pt03ch07s02aus52.md) | [pt03ch07s02aus52.md](./eng/pt03ch07s02aus52.md) |

### PT04
*Analysis Techniques*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| Analysis Techniques | Analysis Techniques | [pt04.md](./chs/pt04.md) | [pt04.md](./eng/pt04.md) |
| 8 Analysis Techniques: Introduction | 8 Analysis Techniques: Introduction | [pt04ch08.md](./chs/pt04ch08.md) | [pt04ch08.md](./eng/pt04ch08.md) |
| 8.1 Introduction | 8.1 Introduction | [pt04ch08s01.md](./chs/pt04ch08s01.md) | [pt04ch08s01.md](./eng/pt04ch08s01.md) |
| 8.1.1 Analysis techniques: overview | 8.1.1 Analysis techniques: overview | [pt04ch08s01abo12.md](./chs/pt04ch08s01abo12.md) | [pt04ch08s01abo12.md](./eng/pt04ch08s01abo12.md) |
| 9 Analysis Continuation Techniques | 9 Analysis Continuation Techniques | [pt04ch09.md](./chs/pt04ch09.md) | [pt04ch09.md](./eng/pt04ch09.md) |
| 9.1 Restarting an analysis | 9.1 Restarting an analysis | [pt04ch09s01.md](./chs/pt04ch09s01.md) | [pt04ch09s01.md](./eng/pt04ch09s01.md) |
| 12.1.1 重启动分析概述 | 9.1.1 Restarting an analysis | [pt04ch09s01aus53.md](./chs/pt04ch09s01aus53.md) | [pt04ch09s01aus53.md](./eng/pt04ch09s01aus53.md) |
| 9.2 Importing and transferring results | 9.2 Importing and transferring results | [pt04ch09s02.md](./chs/pt04ch09s02.md) | [pt04ch09s02.md](./eng/pt04ch09s02.md) |
| 12.2.1 结果传递概述 | 9.2.1 Transferring results between Abaqus analyses: overview | [pt04ch09s02aus54.md](./chs/pt04ch09s02aus54.md) | [pt04ch09s02aus54.md](./eng/pt04ch09s02aus54.md) |
| 12.2.2 Abaqus/Explicit 与 Abaqus/Standard 之间的结果传递 | 9.2.2 Transferring results between Abaqus/Explicit and Abaqus/Standard | [pt04ch09s02aus55.md](./chs/pt04ch09s02aus55.md) | [pt04ch09s02aus55.md](./eng/pt04ch09s02aus55.md) |
| 12.2.3 在 Abaqus/Standard 之间传递结果 | 9.2.3 Transferring results from one Abaqus/Standard analysis to another | [pt04ch09s02aus56.md](./chs/pt04ch09s02aus56.md) | [pt04ch09s02aus56.md](./eng/pt04ch09s02aus56.md) |
| 12.2.4 在 Abaqus/Explicit 之间传递结果 | 9.2.4 Transferring results from one Abaqus/Explicit analysis to another | [pt04ch09s02aus57.md](./chs/pt04ch09s02aus57.md) | [pt04ch09s02aus57.md](./eng/pt04ch09s02aus57.md) |
| 10 Modeling Abstractions | 10 Modeling Abstractions | [pt04ch10.md](./chs/pt04ch10.md) | [pt04ch10.md](./eng/pt04ch10.md) |
| 10.1 Substructuring | 10.1 Substructuring | [pt04ch10s01.md](./chs/pt04ch10s01.md) | [pt04ch10s01.md](./eng/pt04ch10s01.md) |
| 12.3.1 使用子结构概述 | 10.1.1 Using substructures | [pt04ch10s01aus58.md](./chs/pt04ch10s01aus58.md) | [pt04ch10s01aus58.md](./eng/pt04ch10s01aus58.md) |
| 12.3.2 定义子结构 | 10.1.2 Defining substructures | [pt04ch10s01aus59.md](./chs/pt04ch10s01aus59.md) | [pt04ch10s01aus59.md](./eng/pt04ch10s01aus59.md) |
| 10.2 Submodeling | 10.2 Submodeling | [pt04ch10s02.md](./chs/pt04ch10s02.md) | [pt04ch10s02.md](./eng/pt04ch10s02.md) |
| 12.4.1 子模型技术概述 | 10.2.1 Submodeling: overview | [pt04ch10s02aus60.md](./chs/pt04ch10s02aus60.md) | [pt04ch10s02aus60.md](./eng/pt04ch10s02aus60.md) |
| 12.4.2 节点-based 子模型 | 10.2.2 Node-based submodeling | [pt04ch10s02aus61.md](./chs/pt04ch10s02aus61.md) | [pt04ch10s02aus61.md](./eng/pt04ch10s02aus61.md) |
| 12.4.3 Surface-based 子模型 | 10.2.3 Surface-based submodeling | [pt04ch10s02aus62.md](./chs/pt04ch10s02aus62.md) | [pt04ch10s02aus62.md](./eng/pt04ch10s02aus62.md) |
| 10.3 Generating matrices | 10.3 Generating matrices | [pt04ch10s03.md](./chs/pt04ch10s03.md) | [pt04ch10s03.md](./eng/pt04ch10s03.md) |
| 12.5.1 生成矩阵 | 10.3.1 Generating matrices | [pt04ch10s03at32.md](./chs/pt04ch10s03at32.md) | [pt04ch10s03at32.md](./eng/pt04ch10s03at32.md) |
| 12.5.2 生成热矩阵 | 10.3.2 Generating thermal matrices | [pt04ch10s03at33.md](./chs/pt04ch10s03at33.md) | [pt04ch10s03at33.md](./eng/pt04ch10s03at33.md) |
| 10.4 Symmetric model generation, results transfer, and analysis of cyclic symmetry models | 10.4 Symmetric model generation, results transfer, and analysis of cyclic symmetry models | [pt04ch10s04.md](./chs/pt04ch10s04.md) | [pt04ch10s04.md](./eng/pt04ch10s04.md) |
| 12.5.3 模型的循环对称分析 | 10.4.3 Analysis of models that exhibit cyclic symmetry | [pt04ch10s04at34.md](./chs/pt04ch10s04at34.md) | [pt04ch10s04at34.md](./eng/pt04ch10s04at34.md) |
| 10.4.1 对称模型生成 | 10.4.1 Symmetric model generation | [pt04ch10s04aus63.md](./chs/pt04ch10s04aus63.md) | [pt04ch10s04aus63.md](./eng/pt04ch10s04aus63.md) |
| 10.4.2 将结果从对称网格或部分三维网格转换到完整三维网格 | 10.4.2 Transferring results from a symmetric mesh or a partial three-dimensional mesh to a full three-dimensional mesh | [pt04ch10s04aus64.md](./chs/pt04ch10s04aus64.md) | [pt04ch10s04aus64.md](./eng/pt04ch10s04aus64.md) |
| 10.5 Periodic media analysis | 10.5 Periodic media analysis | [pt04ch10s05.md](./chs/pt04ch10s05.md) | [pt04ch10s05.md](./eng/pt04ch10s05.md) |
| 10.5.1 周期介质分析 | 10.5.1 Periodic media analysis | [pt04ch10s05aus65.md](./chs/pt04ch10s05aus65.md) | [pt04ch10s05aus65.md](./eng/pt04ch10s05aus65.md) |
| 10.6 Meshed beam cross-sections | 10.6 Meshed beam cross-sections | [pt04ch10s06.md](./chs/pt04ch10s06.md) | [pt04ch10s06.md](./eng/pt04ch10s06.md) |
| 10.6.1 网格化梁横截面 | 10.6.1 Meshed beam cross-sections | [pt04ch10s06at35.md](./chs/pt04ch10s06at35.md) | [pt04ch10s06at35.md](./eng/pt04ch10s06at35.md) |
| 10.7 Modeling discontinuities as an enriched feature using the extended finite element method | 10.7 Modeling discontinuities as an enriched feature using the extended finite element method | [pt04ch10s07.md](./chs/pt04ch10s07.md) | [pt04ch10s07.md](./eng/pt04ch10s07.md) |
| 10.7.1 使用扩展有限元方法将不连续性建模为富集特征 | 10.7.1 Modeling discontinuities as an enriched feature using the extended finite element method | [pt04ch10s07at36.md](./chs/pt04ch10s07at36.md) | [pt04ch10s07at36.md](./eng/pt04ch10s07at36.md) |
| 11 Special-Purpose Techniques | 11 Special-Purpose Techniques | [pt04ch11.md](./chs/pt04ch11.md) | [pt04ch11.md](./eng/pt04ch11.md) |
| 11.1 Inertia relief | 11.1 Inertia relief | [pt04ch11s01.md](./chs/pt04ch11s01.md) | [pt04ch11s01.md](./eng/pt04ch11s01.md) |
| 11.1.1 几何缺陷 | 11.1.1 Inertia relief | [pt04ch11s01at37.md](./chs/pt04ch11s01at37.md) | [pt04ch11s01at37.md](./eng/pt04ch11s01at37.md) |
| 11.2 Mesh modification or replacement | 11.2 Mesh modification or replacement | [pt04ch11s02.md](./chs/pt04ch11s02.md) | [pt04ch11s02.md](./eng/pt04ch11s02.md) |
| 11.2 单元与接触对的移除与重新激活 | 11.2.1 Element and contact pair removal and reactivation | [pt04ch11s02aus66.md](./chs/pt04ch11s02aus66.md) | [pt04ch11s02aus66.md](./eng/pt04ch11s02aus66.md) |
| 11.3 Geometric imperfections | 11.3 Geometric imperfections | [pt04ch11s03.md](./chs/pt04ch11s03.md) | [pt04ch11s03.md](./eng/pt04ch11s03.md) |
| 11.3 惯性relief | 11.3.1 Introducing a geometric imperfection into a model | [pt04ch11s03aus67.md](./chs/pt04ch11s03aus67.md) | [pt04ch11s03aus67.md](./eng/pt04ch11s03aus67.md) |
| 11.4 Fracture mechanics | 11.4 Fracture mechanics | [pt04ch11s04.md](./chs/pt04ch11s04.md) | [pt04ch11s04.md](./eng/pt04ch11s04.md) |
| 11.4.1 Fracture mechanics: overview | 11.4.1 Fracture mechanics: overview | [pt04ch11s04abo13.md](./chs/pt04ch11s04abo13.md) | [pt04ch11s04abo13.md](./eng/pt04ch11s04abo13.md) |
| 11.4.1 轮廓积分评估 | 11.4.2 Contour integral evaluation | [pt04ch11s04aus68.md](./chs/pt04ch11s04aus68.md) | [pt04ch11s04aus68.md](./eng/pt04ch11s04aus68.md) |
| 11.4.2 裂纹扩展分析 | 11.4.3 Crack propagation analysis | [pt04ch11s04aus69.md](./chs/pt04ch11s04aus69.md) | [pt04ch11s04aus69.md](./eng/pt04ch11s04aus69.md) |
| 11.5 Surface-based fluid modeling | 11.5 Surface-based fluid modeling | [pt04ch11s05.md](./chs/pt04ch11s05.md) | [pt04ch11s05.md](./eng/pt04ch11s05.md) |
| 11.5.1 流体腔体概述 | 11.5.1 Surface-based fluid cavities: overview | [pt04ch11s05aus70.md](./chs/pt04ch11s05aus70.md) | [pt04ch11s05aus70.md](./eng/pt04ch11s05aus70.md) |
| 11.5.2 流体腔体定义 | 11.5.2 Fluid cavity definition | [pt04ch11s05aus71.md](./chs/pt04ch11s05aus71.md) | [pt04ch11s05aus71.md](./eng/pt04ch11s05aus71.md) |
| 11.5.3 流体交换定义 | 11.5.3 Fluid exchange definition | [pt04ch11s05aus72.md](./chs/pt04ch11s05aus72.md) | [pt04ch11s05aus72.md](./eng/pt04ch11s05aus72.md) |
| 11.5.4 充气器定义 | 11.5.4 Inflator definition | [pt04ch11s05aus73.md](./chs/pt04ch11s05aus73.md) | [pt04ch11s05aus73.md](./eng/pt04ch11s05aus73.md) |
| 11.6 Mass scaling | 11.6 Mass scaling | [pt04ch11s06.md](./chs/pt04ch11s06.md) | [pt04ch11s06.md](./eng/pt04ch11s06.md) |
| 11.6 质量缩放 | 11.6.1 Mass scaling | [pt04ch11s06aus74.md](./chs/pt04ch11s06aus74.md) | [pt04ch11s06aus74.md](./eng/pt04ch11s06aus74.md) |
| 11.7 Selective subcycling | 11.7 Selective subcycling | [pt04ch11s07.md](./chs/pt04ch11s07.md) | [pt04ch11s07.md](./eng/pt04ch11s07.md) |
| 11.7 选择性子循环 | 11.7.1 Selective subcycling | [pt04ch11s07aus75.md](./chs/pt04ch11s07aus75.md) | [pt04ch11s07aus75.md](./eng/pt04ch11s07aus75.md) |
| 11.8 Steady-state detection | 11.8 Steady-state detection | [pt04ch11s08.md](./chs/pt04ch11s08.md) | [pt04ch11s08.md](./eng/pt04ch11s08.md) |
| 11.8 稳态检测 | 11.8.1 Steady-state detection | [pt04ch11s08aus76.md](./chs/pt04ch11s08aus76.md) | [pt04ch11s08aus76.md](./eng/pt04ch11s08aus76.md) |
| 12 Adaptivity Techniques | 12 Adaptivity Techniques | [pt04ch12.md](./chs/pt04ch12.md) | [pt04ch12.md](./eng/pt04ch12.md) |
| 12.1 Adaptivity techniques: overview | 12.1 Adaptivity techniques: overview | [pt04ch12s01.md](./chs/pt04ch12s01.md) | [pt04ch12s01.md](./eng/pt04ch12s01.md) |
| 12.1.1 自适应技术 | 12.1.1 Adaptivity techniques | [pt04ch12s01aus77.md](./chs/pt04ch12s01aus77.md) | [pt04ch12s01aus77.md](./eng/pt04ch12s01aus77.md) |
| 12.2 ALE adaptive meshing | 12.2 ALE adaptive meshing | [pt04ch12s02.md](./chs/pt04ch12s02.md) | [pt04ch12s02.md](./eng/pt04ch12s02.md) |
| 12.2.1 ALE adaptive meshing: overview | 12.2.1 ALE adaptive meshing: overview | [pt04ch12s02abo14.md](./chs/pt04ch12s02abo14.md) | [pt04ch12s02abo14.md](./eng/pt04ch12s02abo14.md) |
| 12.2.2 在Abaqus/Explicit中定义ALE自适应网格域 | 12.2.2 Defining ALE adaptive mesh domains in Abaqus/Explicit | [pt04ch12s02aus78.md](./chs/pt04ch12s02aus78.md) | [pt04ch12s02aus78.md](./eng/pt04ch12s02aus78.md) |
| 12.2.3 Abaqus/Explicit中ALE自适应网格划分与重映射 | 12.2.3 ALE adaptive meshing and remapping in Abaqus/Explicit | [pt04ch12s02aus79.md](./chs/pt04ch12s02aus79.md) | [pt04ch12s02aus79.md](./eng/pt04ch12s02aus79.md) |
| 12.2.4 Abaqus/Explicit中欧拉自适应网格域的建模技术 | 12.2.4 Modeling techniques for Eulerian adaptive mesh domains in Abaqus/Explicit | [pt04ch12s02aus80.md](./chs/pt04ch12s02aus80.md) | [pt04ch12s02aus80.md](./eng/pt04ch12s02aus80.md) |
| 12.2.5 Abaqus/Explicit中ALE自适应网格划分的输出和诊断 | 12.2.5 Output and diagnostics for ALE adaptive meshing in Abaqus/Explicit | [pt04ch12s02aus81.md](./chs/pt04ch12s02aus81.md) | [pt04ch12s02aus81.md](./eng/pt04ch12s02aus81.md) |
| 12.2.6 在 Abaqus/Standard 中定义 ALE 自适应网格域 | 12.2.6 Defining ALE adaptive mesh domains in Abaqus/Standard | [pt04ch12s02aus82.md](./chs/pt04ch12s02aus82.md) | [pt04ch12s02aus82.md](./eng/pt04ch12s02aus82.md) |
| 12.2.7 Abaqus/Standard 中的 ALE 自适应网格划分和重映射 | 12.2.7 ALE adaptive meshing and remapping in Abaqus/Standard | [pt04ch12s02aus83.md](./chs/pt04ch12s02aus83.md) | [pt04ch12s02aus83.md](./eng/pt04ch12s02aus83.md) |
| 12.3 Adaptive remeshing | 12.3 Adaptive remeshing | [pt04ch12s03.md](./chs/pt04ch12s03.md) | [pt04ch12s03.md](./eng/pt04ch12s03.md) |
| 12.3.1 自适应重网格划分：概述 | 12.3.1 Adaptive remeshing: overview | [pt04ch12s03abo15.md](./chs/pt04ch12s03abo15.md) | [pt04ch12s03abo15.md](./eng/pt04ch12s03abo15.md) |
| 12.3.2 选择影响自适应重网格划分的误差指标 | 12.3.2 Selection of error indicators influencing adaptive remeshing | [pt04ch12s03aus84.md](./chs/pt04ch12s03aus84.md) | [pt04ch12s03aus84.md](./eng/pt04ch12s03aus84.md) |
| 12.3.3 基于解的网格划分 | 12.3.3 Solution-based mesh sizing | [pt04ch12s03aus85.md](./chs/pt04ch12s03aus85.md) | [pt04ch12s03aus85.md](./eng/pt04ch12s03aus85.md) |
| 12.4 Analysis continuation after mesh replacement | 12.4 Analysis continuation after mesh replacement | [pt04ch12s04.md](./chs/pt04ch12s04.md) | [pt04ch12s04.md](./eng/pt04ch12s04.md) |
| 12.4.1 网格到网格解映射 | 12.4.1 Mesh-to-mesh solution mapping | [pt04ch12s04aus86.md](./chs/pt04ch12s04aus86.md) | [pt04ch12s04aus86.md](./eng/pt04ch12s04aus86.md) |
| 13 Optimization Techniques | 13 Optimization Techniques | [pt04ch13.md](./chs/pt04ch13.md) | [pt04ch13.md](./eng/pt04ch13.md) |
| 13.1 Structural optimization: overview | 13.1 Structural optimization: overview | [pt04ch13s01.md](./chs/pt04ch13s01.md) | [pt04ch13s01.md](./eng/pt04ch13s01.md) |
| 13.1.1 Structural optimization: overview | 13.1.1 Structural optimization: overview | [pt04ch13s01abo16.md](./chs/pt04ch13s01abo16.md) | [pt04ch13s01abo16.md](./eng/pt04ch13s01abo16.md) |
| 13.2 Optimization models | 13.2 Optimization models | [pt04ch13s02.md](./chs/pt04ch13s02.md) | [pt04ch13s02.md](./eng/pt04ch13s02.md) |
| 13.2.1 设计响应 | 13.2.1 Design responses | [pt04ch13s02aus87.md](./chs/pt04ch13s02aus87.md) | [pt04ch13s02aus87.md](./eng/pt04ch13s02aus87.md) |
| 13.2.2 目标函数和约束 | 13.2.2 Objectives and constraints | [pt04ch13s02aus88.md](./chs/pt04ch13s02aus88.md) | [pt04ch13s02aus88.md](./eng/pt04ch13s02aus88.md) |
| 13.2.3 创建 Abaqus 优化模型 | 13.2.3 Creating Abaqus optimization models | [pt04ch13s02aus89.md](./chs/pt04ch13s02aus89.md) | [pt04ch13s02aus89.md](./eng/pt04ch13s02aus89.md) |
| 14 Eulerian Analysis | 14 Eulerian Analysis | [pt04ch14.md](./chs/pt04ch14.md) | [pt04ch14.md](./eng/pt04ch14.md) |
| 14.1 Eulerian analysis | 14.1 Eulerian analysis | [pt04ch14s01.md](./chs/pt04ch14s01.md) | [pt04ch14s01.md](./eng/pt04ch14s01.md) |
| 14.1.1 欧拉分析 | 14.1.1 Eulerian analysis | [pt04ch14s01aus90.md](./chs/pt04ch14s01aus90.md) | [pt04ch14s01aus90.md](./eng/pt04ch14s01aus90.md) |
| 14.1.2 定义欧拉边界 | 14.1.2 Defining Eulerian boundaries | [pt04ch14s01aus91.md](./chs/pt04ch14s01aus91.md) | [pt04ch14s01aus91.md](./eng/pt04ch14s01aus91.md) |
| 14.1.3 欧拉网格运动 | 14.1.3 Eulerian mesh motion | [pt04ch14s01aus92.md](./chs/pt04ch14s01aus92.md) | [pt04ch14s01aus92.md](./eng/pt04ch14s01aus92.md) |
| 14.1.4 在欧拉域中定义自适应网格细化 | 14.1.4 Defining adaptive mesh refinement in the Eulerian domain | [pt04ch14s01aus93.md](./chs/pt04ch14s01aus93.md) | [pt04ch14s01aus93.md](./eng/pt04ch14s01aus93.md) |
| 15 Particle Methods | 15 Particle Methods | [pt04ch15.md](./chs/pt04ch15.md) | [pt04ch15.md](./eng/pt04ch15.md) |
| 15.1 Discrete element method | 15.1 Discrete element method | [pt04ch15s01.md](./chs/pt04ch15s01.md) | [pt04ch15s01.md](./eng/pt04ch15s01.md) |
| 15.1.1 离散单元方法 | 15.1.1 Discrete element method | [pt04ch15s01aus94.md](./chs/pt04ch15s01aus94.md) | [pt04ch15s01aus94.md](./eng/pt04ch15s01aus94.md) |
| 15.2 Continuum particle analyses | 15.2 Continuum particle analyses | [pt04ch15s02.md](./chs/pt04ch15s02.md) | [pt04ch15s02.md](./eng/pt04ch15s02.md) |
| 15.2.1 光滑粒子流体力学 | 15.2.1 Smoothed particle hydrodynamics | [pt04ch15s02aus95.md](./chs/pt04ch15s02aus95.md) | [pt04ch15s02aus95.md](./eng/pt04ch15s02aus95.md) |
| 15.2.2 有限元转换为 SPH 粒子 | 15.2.2 Finite element conversion to SPH particles | [pt04ch15s02aus96.md](./chs/pt04ch15s02aus96.md) | [pt04ch15s02aus96.md](./eng/pt04ch15s02aus96.md) |
| 16 Sequentially Coupled Multiphysics Analyses | 16 Sequentially Coupled Multiphysics Analyses | [pt04ch16.md](./chs/pt04ch16.md) | [pt04ch16.md](./eng/pt04ch16.md) |
| 16.1 Sequentially coupled multiphysics analyses | 16.1 Sequentially coupled multiphysics analyses | [pt04ch16s01.md](./chs/pt04ch16s01.md) | [pt04ch16s01.md](./eng/pt04ch16s01.md) |
| 16.1.1 序贯耦合的预定义场 | 16.1.1 Predefined fields for sequential coupling | [pt04ch16s01at38.md](./chs/pt04ch16s01at38.md) | [pt04ch16s01at38.md](./eng/pt04ch16s01at38.md) |
| 16.1.2 序贯耦合热应力分析 | 16.1.2 Sequentially coupled thermal-stress analysis | [pt04ch16s01at39.md](./chs/pt04ch16s01at39.md) | [pt04ch16s01at39.md](./eng/pt04ch16s01at39.md) |
| 16.1.3 序贯耦合的预定义载荷 | 16.1.3 Predefined loads for sequential coupling | [pt04ch16s01aus97.md](./chs/pt04ch16s01aus97.md) | [pt04ch16s01aus97.md](./eng/pt04ch16s01aus97.md) |
| 17 Co-simulation | 17 Co-simulation | [pt04ch17.md](./chs/pt04ch17.md) | [pt04ch17.md](./eng/pt04ch17.md) |
| 17.1 Co-simulation | 17.1 Co-simulation | [pt04ch17s01.md](./chs/pt04ch17s01.md) | [pt04ch17s01.md](./eng/pt04ch17s01.md) |
| 17.1.1 Co-simulation: overview | 17.1.1 Co-simulation: overview | [pt04ch17s01abo17.md](./chs/pt04ch17s01abo17.md) | [pt04ch17s01abo17.md](./eng/pt04ch17s01abo17.md) |
| 17.2 Preparing an Abaqus analysis for co-simulation | 17.2 Preparing an Abaqus analysis for co-simulation | [pt04ch17s02.md](./chs/pt04ch17s02.md) | [pt04ch17s02.md](./eng/pt04ch17s02.md) |
| 17.2.1 准备协同仿真的 Abaqus 分析 | 17.2.1 Preparing an Abaqus analysis for co-simulation | [pt04ch17s02aus98.md](./chs/pt04ch17s02aus98.md) | [pt04ch17s02aus98.md](./eng/pt04ch17s02aus98.md) |
| 17.3 Co-simulation between Abaqus solvers | 17.3 Co-simulation between Abaqus solvers | [pt04ch17s03.md](./chs/pt04ch17s03.md) | [pt04ch17s03.md](./eng/pt04ch17s03.md) |
| 17.3.2 流固耦合和共轭热传递协同仿真 | 17.3.2 Fluid-to-structural and conjugate heat transfer co-simulation | [pt04ch17s03aus100.md](./chs/pt04ch17s03aus100.md) | [pt04ch17s03aus100.md](./eng/pt04ch17s03aus100.md) |
| 17.3.3 电磁到结构以及电磁到热协同仿真 | 17.3.3 Electromagnetic-to-structural and electromagnetic-to-thermal co-simulation | [pt04ch17s03aus101.md](./chs/pt04ch17s03aus101.md) | [pt04ch17s03aus101.md](./eng/pt04ch17s03aus101.md) |
| 17.3.4 执行协同仿真 | 17.3.4 Executing a co-simulation | [pt04ch17s03aus102.md](./chs/pt04ch17s03aus102.md) | [pt04ch17s03aus102.md](./eng/pt04ch17s03aus102.md) |
| 17.3.1 结构对结构协同仿真 | 17.3.1 Structural-to-structural co-simulation | [pt04ch17s03aus99.md](./chs/pt04ch17s03aus99.md) | [pt04ch17s03aus99.md](./eng/pt04ch17s03aus99.md) |
| 17.4 Co-simulation using Abaqus and discrete models | 17.4 Co-simulation using Abaqus and discrete models | [pt04ch17s04.md](./chs/pt04ch17s04.md) | [pt04ch17s04.md](./eng/pt04ch17s04.md) |
| 17.4.1 结构对逻辑协同仿真 | 17.4.1 Structural-to-logical co-simulation | [pt04ch17s04aus103.md](./chs/pt04ch17s04aus103.md) | [pt04ch17s04aus103.md](./eng/pt04ch17s04aus103.md) |
| 18 Extending Abaqus Analysis Functionality | 18 Extending Abaqus Analysis Functionality | [pt04ch18.md](./chs/pt04ch18.md) | [pt04ch18.md](./eng/pt04ch18.md) |
| 18.1 User subroutines and utilities | 18.1 User subroutines and utilities | [pt04ch18s01.md](./chs/pt04ch18s01.md) | [pt04ch18s01.md](./eng/pt04ch18s01.md) |
| 18.1.1 用户子程序：概述 | 18.1.1 User subroutines: overview | [pt04ch18s01aus104.md](./chs/pt04ch18s01aus104.md) | [pt04ch18s01aus104.md](./eng/pt04ch18s01aus104.md) |
| 18.1.2 可用的用户子程序 | 18.1.2 Available user subroutines | [pt04ch18s01aus105.md](./chs/pt04ch18s01aus105.md) | [pt04ch18s01aus105.md](./eng/pt04ch18s01aus105.md) |
| 18.1.3 可用的实用程序 | 18.1.3 Available utility routines | [pt04ch18s01aus106.md](./chs/pt04ch18s01aus106.md) | [pt04ch18s01aus106.md](./eng/pt04ch18s01aus106.md) |
| 19 Design Sensitivity Analysis | 19 Design Sensitivity Analysis | [pt04ch19.md](./chs/pt04ch19.md) | [pt04ch19.md](./eng/pt04ch19.md) |
| 19.1 Design sensitivity analysis | 19.1 Design sensitivity analysis | [pt04ch19s01.md](./chs/pt04ch19s01.md) | [pt04ch19s01.md](./eng/pt04ch19s01.md) |
| 19.1.1 设计灵敏度分析 | 19.1.1 Design sensitivity analysis | [pt04ch19s01aus107.md](./chs/pt04ch19s01aus107.md) | [pt04ch19s01aus107.md](./eng/pt04ch19s01aus107.md) |
| 20 Parametric Studies | 20 Parametric Studies | [pt04ch20.md](./chs/pt04ch20.md) | [pt04ch20.md](./eng/pt04ch20.md) |
| 20.1 Scripting parametric studies | 20.1 Scripting parametric studies | [pt04ch20s01.md](./chs/pt04ch20s01.md) | [pt04ch20s01.md](./eng/pt04ch20s01.md) |
| 20.1.1 参数化研究脚本 | 20.1.1 Scripting parametric studies | [pt04ch20s01aus108.md](./chs/pt04ch20s01aus108.md) | [pt04ch20s01aus108.md](./eng/pt04ch20s01aus108.md) |
| 20.2 Parametric studies: commands | 20.2 Parametric studies: commands | [pt04ch20s02.md](./chs/pt04ch20s02.md) | [pt04ch20s02.md](./eng/pt04ch20s02.md) |
| 20.2.1 aStudy.combine() | 20.2.1 aStudy.combine() | [pt04ch20s02asr01.md](./chs/pt04ch20s02asr01.md) | [pt04ch20s02asr01.md](./eng/pt04ch20s02asr01.md) |
| 20.2.2 aStudy.constrain() | 20.2.2 aStudy.constrain() | [pt04ch20s02asr02.md](./chs/pt04ch20s02asr02.md) | [pt04ch20s02asr02.md](./eng/pt04ch20s02asr02.md) |
| 20.2.3 aStudy.define() | 20.2.3 aStudy.define() | [pt04ch20s02asr03.md](./chs/pt04ch20s02asr03.md) | [pt04ch20s02asr03.md](./eng/pt04ch20s02asr03.md) |
| 20.2.4 aStudy.execute() | 20.2.4 aStudy.execute() | [pt04ch20s02asr04.md](./chs/pt04ch20s02asr04.md) | [pt04ch20s02asr04.md](./eng/pt04ch20s02asr04.md) |
| 20.2.5 aStudy.gather() | 20.2.5 aStudy.gather() | [pt04ch20s02asr05.md](./chs/pt04ch20s02asr05.md) | [pt04ch20s02asr05.md](./eng/pt04ch20s02asr05.md) |
| 20.2.6 aStudy.generate() | 20.2.6 aStudy.generate() | [pt04ch20s02asr06.md](./chs/pt04ch20s02asr06.md) | [pt04ch20s02asr06.md](./eng/pt04ch20s02asr06.md) |
| 20.2.7 aStudy.output() | 20.2.7 aStudy.output() | [pt04ch20s02asr07.md](./chs/pt04ch20s02asr07.md) | [pt04ch20s02asr07.md](./eng/pt04ch20s02asr07.md) |
| 20.2.8 aStudy=ParStudy() | 20.2.8 aStudy=ParStudy() | [pt04ch20s02asr08.md](./chs/pt04ch20s02asr08.md) | [pt04ch20s02asr08.md](./eng/pt04ch20s02asr08.md) |
| 20.2.9 aStudy.report() | 20.2.9 aStudy.report() | [pt04ch20s02asr09.md](./chs/pt04ch20s02asr09.md) | [pt04ch20s02asr09.md](./eng/pt04ch20s02asr09.md) |
| 20.2.10 aStudy.sample() | 20.2.10 aStudy.sample() | [pt04ch20s02asr10.md](./chs/pt04ch20s02asr10.md) | [pt04ch20s02asr10.md](./eng/pt04ch20s02asr10.md) |

### PT05
*Materials*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| Materials | Materials | [pt05.md](./chs/pt05.md) | [pt05.md](./eng/pt05.md) |
| 21 Materials: Introduction | 21 Materials: Introduction | [pt05ch21.md](./chs/pt05ch21.md) | [pt05ch21.md](./eng/pt05ch21.md) |
| 21.1 Introduction | 21.1 Introduction | [pt05ch21s01.md](./chs/pt05ch21s01.md) | [pt05ch21s01.md](./eng/pt05ch21s01.md) |
| 21.1.1 Material library: overview | 21.1.1 Material library: overview | [pt05ch21s01abo18.md](./chs/pt05ch21s01abo18.md) | [pt05ch21s01abo18.md](./eng/pt05ch21s01abo18.md) |
| 21.1.2 材料数据定义 | 21.1.2 Material data definition | [pt05ch21s01aus109.md](./chs/pt05ch21s01aus109.md) | [pt05ch21s01aus109.md](./eng/pt05ch21s01aus109.md) |
| 21.1.3 组合材料行为 | 21.1.3 Combining material behaviors | [pt05ch21s01aus110.md](./chs/pt05ch21s01aus110.md) | [pt05ch21s01aus110.md](./eng/pt05ch21s01aus110.md) |
| 21.2 General properties | 21.2 General properties | [pt05ch21s02.md](./chs/pt05ch21s02.md) | [pt05ch21s02.md](./eng/pt05ch21s02.md) |
| 21.2.1 密度 | 21.2.1 Density | [pt05ch21s02abm01.md](./chs/pt05ch21s02abm01.md) | [pt05ch21s02abm01.md](./eng/pt05ch21s02abm01.md) |
| 22 Elastic Mechanical Properties | 22 Elastic Mechanical Properties | [pt05ch22.md](./chs/pt05ch22.md) | [pt05ch22.md](./eng/pt05ch22.md) |
| 22.1 Overview | 22.1 Overview | [pt05ch22s01.md](./chs/pt05ch22s01.md) | [pt05ch22s01.md](./eng/pt05ch22s01.md) |
| 22.1.1 Elastic behavior: overview | 22.1.1 Elastic behavior: overview | [pt05ch22s01abo19.md](./chs/pt05ch22s01abo19.md) | [pt05ch22s01abo19.md](./eng/pt05ch22s01abo19.md) |
| 22.2 Linear elasticity | 22.2 Linear elasticity | [pt05ch22s02.md](./chs/pt05ch22s02.md) | [pt05ch22s02.md](./eng/pt05ch22s02.md) |
| 22.2.1 线弹性行为 | 22.2.1 Linear elastic behavior | [pt05ch22s02abm02.md](./chs/pt05ch22s02abm02.md) | [pt05ch22s02abm02.md](./eng/pt05ch22s02abm02.md) |
| 22.3.1 多孔材料的弹性行为 | 22.2.2 No compression or no tension | [pt05ch22s02abm03.md](./chs/pt05ch22s02abm03.md) | [pt05ch22s02abm03.md](./eng/pt05ch22s02abm03.md) |
| 22.2.2 无压缩或无拉伸 | 22.2.3 Plane stress orthotropic failure measures | [pt05ch22s02abm04.md](./chs/pt05ch22s02abm04.md) | [pt05ch22s02abm04.md](./eng/pt05ch22s02abm04.md) |
| 22.3 Porous elasticity | 22.3 Porous elasticity | [pt05ch22s03.md](./chs/pt05ch22s03.md) | [pt05ch22s03.md](./eng/pt05ch22s03.md) |
| 22.3.1 多孔材料的弹性行为 | 22.3.1 Elastic behavior of porous materials | [pt05ch22s03abm05.md](./chs/pt05ch22s03abm05.md) | [pt05ch22s03abm05.md](./eng/pt05ch22s03abm05.md) |
| 22.4 Hypoelasticity | 22.4 Hypoelasticity | [pt05ch22s04.md](./chs/pt05ch22s04.md) | [pt05ch22s04.md](./eng/pt05ch22s04.md) |
| 22.4.1 亚弹性行为 | 22.4.1 Hypoelastic behavior | [pt05ch22s04abm06.md](./chs/pt05ch22s04abm06.md) | [pt05ch22s04abm06.md](./eng/pt05ch22s04abm06.md) |
| 22.5 Hyperelasticity | 22.5 Hyperelasticity | [pt05ch22s05.md](./chs/pt05ch22s05.md) | [pt05ch22s05.md](./eng/pt05ch22s05.md) |
| 22.5.1 橡胶类材料的超弹性行为 | 22.5.1 Hyperelastic behavior of rubberlike materials | [pt05ch22s05abm07.md](./chs/pt05ch22s05abm07.md) | [pt05ch22s05abm07.md](./eng/pt05ch22s05abm07.md) |
| 22.5.2 弹性泡沫中的超弹性行为 | 22.5.2 Hyperelastic behavior in elastomeric foams | [pt05ch22s05abm08.md](./chs/pt05ch22s05abm08.md) | [pt05ch22s05abm08.md](./eng/pt05ch22s05abm08.md) |
| 22.5.3 各向异性超弹性行为 | 22.5.3 Anisotropic hyperelastic behavior | [pt05ch22s05abm09.md](./chs/pt05ch22s05abm09.md) | [pt05ch22s05abm09.md](./eng/pt05ch22s05abm09.md) |
| 22.6 Stress softening in elastomers | 22.6 Stress softening in elastomers | [pt05ch22s06.md](./chs/pt05ch22s06.md) | [pt05ch22s06.md](./eng/pt05ch22s06.md) |
| 22.6.1 Mullins效应 | 22.6.1 Mullins effect | [pt05ch22s06abm10.md](./chs/pt05ch22s06abm10.md) | [pt05ch22s06abm10.md](./eng/pt05ch22s06abm10.md) |
| 22.6.2 弹性泡沫中的能量耗散 | 22.6.2 Energy dissipation in elastomeric foams | [pt05ch22s06abm11.md](./chs/pt05ch22s06abm11.md) | [pt05ch22s06abm11.md](./eng/pt05ch22s06abm11.md) |
| 22.7 Linear viscoelasticity | 22.7 Linear viscoelasticity | [pt05ch22s07.md](./chs/pt05ch22s07.md) | [pt05ch22s07.md](./eng/pt05ch22s07.md) |
| 22.7.1 时域粘弹性 | 22.7.1 Time domain viscoelasticity | [pt05ch22s07abm12.md](./chs/pt05ch22s07abm12.md) | [pt05ch22s07abm12.md](./eng/pt05ch22s07abm12.md) |
| 22.7.2 频域粘弹性 | 22.7.2 Frequency domain viscoelasticity | [pt05ch22s07abm13.md](./chs/pt05ch22s07abm13.md) | [pt05ch22s07abm13.md](./eng/pt05ch22s07abm13.md) |
| 22.8 Nonlinear viscoelasticity | 22.8 Nonlinear viscoelasticity | [pt05ch22s08.md](./chs/pt05ch22s08.md) | [pt05ch22s08.md](./eng/pt05ch22s08.md) |
| 22.8.1 弹性体中的滞后 | 22.8.1 Hysteresis in elastomers | [pt05ch22s08abm14.md](./chs/pt05ch22s08abm14.md) | [pt05ch22s08abm14.md](./eng/pt05ch22s08abm14.md) |
| 22.8.2 并行流变学框架 | 22.8.2 Parallel rheological framework | [pt05ch22s08abm15.md](./chs/pt05ch22s08abm15.md) | [pt05ch22s08abm15.md](./eng/pt05ch22s08abm15.md) |
| 22.9 Rate sensitive elastomeric foams | 22.9 Rate sensitive elastomeric foams | [pt05ch22s09.md](./chs/pt05ch22s09.md) | [pt05ch22s09.md](./eng/pt05ch22s09.md) |
| 22.9.1 低密度泡沫 | 22.9.1 Low-density foams | [pt05ch22s09abm16.md](./chs/pt05ch22s09abm16.md) | [pt05ch22s09abm16.md](./eng/pt05ch22s09abm16.md) |
| 23 Inelastic Mechanical Properties | 23 Inelastic Mechanical Properties | [pt05ch23.md](./chs/pt05ch23.md) | [pt05ch23.md](./eng/pt05ch23.md) |
| 23.1 Overview | 23.1 Overview | [pt05ch23s01.md](./chs/pt05ch23s01.md) | [pt05ch23s01.md](./eng/pt05ch23s01.md) |
| 23.1.1 Inelastic behavior | 23.1.1 Inelastic behavior | [pt05ch23s01abo20.md](./chs/pt05ch23s01abo20.md) | [pt05ch23s01abo20.md](./eng/pt05ch23s01abo20.md) |
| 23.2 Metal plasticity | 23.2 Metal plasticity | [pt05ch23s02.md](./chs/pt05ch23s02.md) | [pt05ch23s02.md](./eng/pt05ch23s02.md) |
| 23.2.1 经典金属塑性 | 23.2.1 Classical metal plasticity | [pt05ch23s02abm17.md](./chs/pt05ch23s02abm17.md) | [pt05ch23s02abm17.md](./eng/pt05ch23s02abm17.md) |
| 23.2.2 金属承受循环加载的模型 | 23.2.2 Models for metals subjected to cyclic loading | [pt05ch23s02abm18.md](./chs/pt05ch23s02abm18.md) | [pt05ch23s02abm18.md](./eng/pt05ch23s02abm18.md) |
| 23.2.3 率相关屈服 | 23.2.3 Rate-dependent yield | [pt05ch23s02abm19.md](./chs/pt05ch23s02abm19.md) | [pt05ch23s02abm19.md](./eng/pt05ch23s02abm19.md) |
| 23.2.4 率相关塑性：蠕变和膨胀 | 23.2.4 Rate-dependent plasticity: creep and swelling | [pt05ch23s02abm20.md](./chs/pt05ch23s02abm20.md) | [pt05ch23s02abm20.md](./eng/pt05ch23s02abm20.md) |
| 23.2.5 退火或熔化 | 23.2.5 Annealing or melting | [pt05ch23s02abm21.md](./chs/pt05ch23s02abm21.md) | [pt05ch23s02abm21.md](./eng/pt05ch23s02abm21.md) |
| 23.2.6 各向异性屈服/蠕变 | 23.2.6 Anisotropic yield/creep | [pt05ch23s02abm22.md](./chs/pt05ch23s02abm22.md) | [pt05ch23s02abm22.md](./eng/pt05ch23s02abm22.md) |
| 23.2.7 Johnson-Cook塑性 | 23.2.7 Johnson-Cook plasticity | [pt05ch23s02abm23.md](./chs/pt05ch23s02abm23.md) | [pt05ch23s02abm23.md](./eng/pt05ch23s02abm23.md) |
| 23.2.8 动态失效模型 | 23.2.8 Dynamic failure models | [pt05ch23s02abm24.md](./chs/pt05ch23s02abm24.md) | [pt05ch23s02abm24.md](./eng/pt05ch23s02abm24.md) |
| 23.2.9 多孔金属塑性 | 23.2.9 Porous metal plasticity | [pt05ch23s02abm25.md](./chs/pt05ch23s02abm25.md) | [pt05ch23s02abm25.md](./eng/pt05ch23s02abm25.md) |
| 23.2.4 铸铁塑性模型 | 23.2.10 Cast iron plasticity | [pt05ch23s02abm26.md](./chs/pt05ch23s02abm26.md) | [pt05ch23s02abm26.md](./eng/pt05ch23s02abm26.md) |
| 23.2.5 双层粘塑性 | 23.2.11 Two-layer viscoplasticity | [pt05ch23s02abm27.md](./chs/pt05ch23s02abm27.md) | [pt05ch23s02abm27.md](./eng/pt05ch23s02abm27.md) |
| 23.2.6 ORNL constitutive model | 23.2.12 ORNL – Oak Ridge National Laboratory constitutive model | [pt05ch23s02abm28.md](./chs/pt05ch23s02abm28.md) | [pt05ch23s02abm28.md](./eng/pt05ch23s02abm28.md) |
| 23.2.7 变形塑性 | 23.2.13 Deformation plasticity | [pt05ch23s02abm29.md](./chs/pt05ch23s02abm29.md) | [pt05ch23s02abm29.md](./eng/pt05ch23s02abm29.md) |
| 23.3 Other plasticity models | 23.3 Other plasticity models | [pt05ch23s03.md](./chs/pt05ch23s03.md) | [pt05ch23s03.md](./eng/pt05ch23s03.md) |
| 23.3.2 扩展德鲁克-普拉格模型 | 23.3.1 Extended Drucker-Prager models | [pt05ch23s03abm30.md](./chs/pt05ch23s03abm30.md) | [pt05ch23s03abm30.md](./eng/pt05ch23s03abm30.md) |
| 23.3.3 修正德鲁克-普拉格/盖帽模型 | 23.3.2 Modified Drucker-Prager/Cap model | [pt05ch23s03abm31.md](./chs/pt05ch23s03abm31.md) | [pt05ch23s03abm31.md](./eng/pt05ch23s03abm31.md) |
| 23.3.4 莫尔-库仑塑性 | 23.3.3 Mohr-Coulomb plasticity | [pt05ch23s03abm32.md](./chs/pt05ch23s03abm32.md) | [pt05ch23s03abm32.md](./eng/pt05ch23s03abm32.md) |
| 23.3.5 临界状态（粘土）塑性 | 23.3.4 Critical state (clay) plasticity model | [pt05ch23s03abm33.md](./chs/pt05ch23s03abm33.md) | [pt05ch23s03abm33.md](./eng/pt05ch23s03abm33.md) |
| 23.3.6 可压碎泡沫塑性 | 23.3.5 Crushable foam plasticity models | [pt05ch23s03abm34.md](./chs/pt05ch23s03abm34.md) | [pt05ch23s03abm34.md](./eng/pt05ch23s03abm34.md) |
| 23.4 Fabric materials | 23.4 Fabric materials | [pt05ch23s04.md](./chs/pt05ch23s04.md) | [pt05ch23s04.md](./eng/pt05ch23s04.md) |
| 23.4.1 织物材料行为 | 23.4.1 Fabric material behavior | [pt05ch23s04abm35.md](./chs/pt05ch23s04abm35.md) | [pt05ch23s04abm35.md](./eng/pt05ch23s04abm35.md) |
| 23.5 Jointed materials | 23.5 Jointed materials | [pt05ch23s05.md](./chs/pt05ch23s05.md) | [pt05ch23s05.md](./eng/pt05ch23s05.md) |
| 23.5.1 韧性金属的损伤起始 | 23.5.1 Jointed material model | [pt05ch23s05abm36.md](./chs/pt05ch23s05abm36.md) | [pt05ch23s05abm36.md](./eng/pt05ch23s05abm36.md) |
| 23.6 Concrete | 23.6 Concrete | [pt05ch23s06.md](./chs/pt05ch23s06.md) | [pt05ch23s06.md](./eng/pt05ch23s06.md) |
| 23.6.1 混凝土弥散裂缝模型 | 23.6.1 Concrete smeared cracking | [pt05ch23s06abm37.md](./chs/pt05ch23s06abm37.md) | [pt05ch23s06abm37.md](./eng/pt05ch23s06abm37.md) |
| 23.6.1 低循环疲劳损伤概述 | 23.6.2 Cracking model for concrete | [pt05ch23s06abm38.md](./chs/pt05ch23s06abm38.md) | [pt05ch23s06abm38.md](./eng/pt05ch23s06abm38.md) |
| 23.6.2 低循环疲劳损伤模型 | 23.6.3 Concrete damaged plasticity | [pt05ch23s06abm39.md](./chs/pt05ch23s06abm39.md) | [pt05ch23s06abm39.md](./eng/pt05ch23s06abm39.md) |
| 23.7 Permanent set in rubberlike materials | 23.7 Permanent set in rubberlike materials | [pt05ch23s07.md](./chs/pt05ch23s07.md) | [pt05ch23s07.md](./eng/pt05ch23s07.md) |
| 23.7.1 粘性行为概述 | 23.7.1 Permanent set in rubberlike materials | [pt05ch23s07abm40.md](./chs/pt05ch23s07abm40.md) | [pt05ch23s07abm40.md](./eng/pt05ch23s07abm40.md) |
| 24 Progressive Damage and Failure | 24 Progressive Damage and Failure | [pt05ch24.md](./chs/pt05ch24.md) | [pt05ch24.md](./eng/pt05ch24.md) |
| 24.1 Progressive damage and failure: overview | 24.1 Progressive damage and failure: overview | [pt05ch24s01.md](./chs/pt05ch24s01.md) | [pt05ch24s01.md](./eng/pt05ch24s01.md) |
| 24.1.1 Progressive damage and failure | 24.1.1 Progressive damage and failure | [pt05ch24s01abo21.md](./chs/pt05ch24s01abo21.md) | [pt05ch24s01abo21.md](./eng/pt05ch24s01abo21.md) |
| 24.2 Damage and failure for ductile metals | 24.2 Damage and failure for ductile metals | [pt05ch24s02.md](./chs/pt05ch24s02.md) | [pt05ch24s02.md](./eng/pt05ch24s02.md) |
| 24.2.1 韧性金属的损伤与失效概述 | 24.2.1 Damage and failure for ductile metals: overview | [pt05ch24s02abm41.md](./chs/pt05ch24s02abm41.md) | [pt05ch24s02abm41.md](./eng/pt05ch24s02abm41.md) |
| 24.2.2 韧性金属的损伤起始 | 24.2.2 Damage initiation for ductile metals | [pt05ch24s02abm42.md](./chs/pt05ch24s02abm42.md) | [pt05ch24s02abm42.md](./eng/pt05ch24s02abm42.md) |
| 24.2.3 韧性金属的损伤演化 | 24.2.3 Damage evolution and element removal for ductile metals | [pt05ch24s02abm43.md](./chs/pt05ch24s02abm43.md) | [pt05ch24s02abm43.md](./eng/pt05ch24s02abm43.md) |
| 24.3 Damage and failure for fiber-reinforced composites | 24.3 Damage and failure for fiber-reinforced composites | [pt05ch24s03.md](./chs/pt05ch24s03.md) | [pt05ch24s03.md](./eng/pt05ch24s03.md) |
| 24.3.1 纤维增强复合材料损伤概述 | 24.3.1 Damage and failure for fiber-reinforced composites: overview | [pt05ch24s03abm44.md](./chs/pt05ch24s03abm44.md) | [pt05ch24s03abm44.md](./eng/pt05ch24s03abm44.md) |
| 24.3.2 纤维增强复合材料的损伤起始 | 24.3.2 Damage initiation for fiber-reinforced composites | [pt05ch24s03abm45.md](./chs/pt05ch24s03abm45.md) | [pt05ch24s03abm45.md](./eng/pt05ch24s03abm45.md) |
| 24.3.3 纤维增强复合材料的损伤演化 | 24.3.3 Damage evolution and element removal for fiber-reinforced composites | [pt05ch24s03abm46.md](./chs/pt05ch24s03abm46.md) | [pt05ch24s03abm46.md](./eng/pt05ch24s03abm46.md) |
| 24.4 Damage and failure for ductile materials in low-cycle fatigue analysis | 24.4 Damage and failure for ductile materials in low-cycle fatigue analysis | [pt05ch24s04.md](./chs/pt05ch24s04.md) | [pt05ch24s04.md](./eng/pt05ch24s04.md) |
| 24.4.1 低循环疲劳损伤概述 | 24.4.1 Damage and failure for ductile materials in low-cycle fatigue analysis: overview | [pt05ch24s04abm47.md](./chs/pt05ch24s04abm47.md) | [pt05ch24s04abm47.md](./eng/pt05ch24s04abm47.md) |
| 24.4.2 低循环疲劳损伤模型 | 24.4.2 Damage initiation for ductile materials in low-cycle fatigue | [pt05ch24s04abm48.md](./chs/pt05ch24s04abm48.md) | [pt05ch24s04abm48.md](./eng/pt05ch24s04abm48.md) |
| 24.4.3 低循环疲劳损伤与损伤演化的结合 | 24.4.3 Damage evolution for ductile materials in low-cycle fatigue | [pt05ch24s04abm49.md](./chs/pt05ch24s04abm49.md) | [pt05ch24s04abm49.md](./eng/pt05ch24s04abm49.md) |
| 25 Hydrodynamic Properties | 25 Hydrodynamic Properties | [pt05ch25.md](./chs/pt05ch25.md) | [pt05ch25.md](./eng/pt05ch25.md) |
| 25.1 Overview | 25.1 Overview | [pt05ch25s01.md](./chs/pt05ch25s01.md) | [pt05ch25s01.md](./eng/pt05ch25s01.md) |
| 25.1.1 Hydrodynamic behavior: overview | 25.1.1 Hydrodynamic behavior: overview | [pt05ch25s01abo22.md](./chs/pt05ch25s01abo22.md) | [pt05ch25s01abo22.md](./eng/pt05ch25s01abo22.md) |
| 25.2 Equations of state | 25.2 Equations of state | [pt05ch25s02.md](./chs/pt05ch25s02.md) | [pt05ch25s02.md](./eng/pt05ch25s02.md) |
| 25.2.1 状态方程 | 25.2.1 Equation of state | [pt05ch25s02abm50.md](./chs/pt05ch25s02abm50.md) | [pt05ch25s02abm50.md](./eng/pt05ch25s02abm50.md) |
| 26 Other Material Properties | 26 Other Material Properties | [pt05ch26.md](./chs/pt05ch26.md) | [pt05ch26.md](./eng/pt05ch26.md) |
| 26.1 Mechanical properties | 26.1 Mechanical properties | [pt05ch26s01.md](./chs/pt05ch26s01.md) | [pt05ch26s01.md](./eng/pt05ch26s01.md) |
| 26.1.1 材料阻尼 | 26.1.1 Material damping | [pt05ch26s01abm51.md](./chs/pt05ch26s01abm51.md) | [pt05ch26s01abm51.md](./eng/pt05ch26s01abm51.md) |
| 26.1.2 热膨胀 | 26.1.2 Thermal expansion | [pt05ch26s01abm52.md](./chs/pt05ch26s01abm52.md) | [pt05ch26s01abm52.md](./eng/pt05ch26s01abm52.md) |
| 26.1.3 场膨胀 | 26.1.3 Field expansion | [pt05ch26s01abm53.md](./chs/pt05ch26s01abm53.md) | [pt05ch26s01abm53.md](./eng/pt05ch26s01abm53.md) |
| 26.1.4 粘度 | 26.1.4 Viscosity | [pt05ch26s01abm54.md](./chs/pt05ch26s01abm54.md) | [pt05ch26s01abm54.md](./eng/pt05ch26s01abm54.md) |
| 26.2 Heat transfer properties | 26.2 Heat transfer properties | [pt05ch26s02.md](./chs/pt05ch26s02.md) | [pt05ch26s02.md](./eng/pt05ch26s02.md) |
| 26.2.2 传导性 | 26.2.2 Conductivity | [pt05ch26s02abm55.md](./chs/pt05ch26s02abm55.md) | [pt05ch26s02abm55.md](./eng/pt05ch26s02abm55.md) |
| 26.2.3 比热容 | 26.2.3 Specific heat | [pt05ch26s02abm56.md](./chs/pt05ch26s02abm56.md) | [pt05ch26s02abm56.md](./eng/pt05ch26s02abm56.md) |
| 26.2.4 潜热 | 26.2.4 Latent heat | [pt05ch26s02abm57.md](./chs/pt05ch26s02abm57.md) | [pt05ch26s02abm57.md](./eng/pt05ch26s02abm57.md) |
| 26.2.1 Thermal properties: overview | 26.2.1 Thermal properties: overview | [pt05ch26s02abo23.md](./chs/pt05ch26s02abo23.md) | [pt05ch26s02abo23.md](./eng/pt05ch26s02abo23.md) |
| 26.3 Acoustic properties | 26.3 Acoustic properties | [pt05ch26s03.md](./chs/pt05ch26s03.md) | [pt05ch26s03.md](./eng/pt05ch26s03.md) |
| 26.3.1 声学介质 | 26.3.1 Acoustic medium | [pt05ch26s03abm58.md](./chs/pt05ch26s03abm58.md) | [pt05ch26s03abm58.md](./eng/pt05ch26s03abm58.md) |
| 26.4 Mass diffusion properties | 26.4 Mass diffusion properties | [pt05ch26s04.md](./chs/pt05ch26s04.md) | [pt05ch26s04.md](./eng/pt05ch26s04.md) |
| 26.4.1 扩散率 | 26.4.1 Diffusivity | [pt05ch26s04abm59.md](./chs/pt05ch26s04abm59.md) | [pt05ch26s04abm59.md](./eng/pt05ch26s04abm59.md) |
| 26.4.2 溶解度 | 26.4.2 Solubility | [pt05ch26s04abm60.md](./chs/pt05ch26s04abm60.md) | [pt05ch26s04abm60.md](./eng/pt05ch26s04abm60.md) |
| 26.5 Electromagnetic properties | 26.5 Electromagnetic properties | [pt05ch26s05.md](./chs/pt05ch26s05.md) | [pt05ch26s05.md](./eng/pt05ch26s05.md) |
| 26.5.1 电导率 | 26.5.1 Electrical conductivity | [pt05ch26s05abm61.md](./chs/pt05ch26s05abm61.md) | [pt05ch26s05abm61.md](./eng/pt05ch26s05abm61.md) |
| 26.5.2 压电行为 | 26.5.2 Piezoelectric behavior | [pt05ch26s05abm62.md](./chs/pt05ch26s05abm62.md) | [pt05ch26s05abm62.md](./eng/pt05ch26s05abm62.md) |
| 26.5.3 磁导率 | 26.5.3 Magnetic permeability | [pt05ch26s05abm63.md](./chs/pt05ch26s05abm63.md) | [pt05ch26s05abm63.md](./eng/pt05ch26s05abm63.md) |
| 26.6 Pore fluid flow properties | 26.6 Pore fluid flow properties | [pt05ch26s06.md](./chs/pt05ch26s06.md) | [pt05ch26s06.md](./eng/pt05ch26s06.md) |
| 26.6.2 渗透率 | 26.6.2 Permeability | [pt05ch26s06abm64.md](./chs/pt05ch26s06abm64.md) | [pt05ch26s06abm64.md](./eng/pt05ch26s06abm64.md) |
| 26.6.3 多孔体积模量 | 26.6.3 Porous bulk moduli | [pt05ch26s06abm65.md](./chs/pt05ch26s06abm65.md) | [pt05ch26s06abm65.md](./eng/pt05ch26s06abm65.md) |
| 26.6.4 吸湿性 | 26.6.4 Sorption | [pt05ch26s06abm66.md](./chs/pt05ch26s06abm66.md) | [pt05ch26s06abm66.md](./eng/pt05ch26s06abm66.md) |
| 26.6.5 溶胀凝胶 | 26.6.5 Swelling gel | [pt05ch26s06abm67.md](./chs/pt05ch26s06abm67.md) | [pt05ch26s06abm67.md](./eng/pt05ch26s06abm67.md) |
| 26.6.6 湿胀 | 26.6.6 Moisture swelling | [pt05ch26s06abm68.md](./chs/pt05ch26s06abm68.md) | [pt05ch26s06abm68.md](./eng/pt05ch26s06abm68.md) |
| 26.6.1 Pore fluid flow properties | 26.6.1 Pore fluid flow properties | [pt05ch26s06abo24.md](./chs/pt05ch26s06abo24.md) | [pt05ch26s06abo24.md](./eng/pt05ch26s06abo24.md) |
| 26.7 User materials | 26.7 User materials | [pt05ch26s07.md](./chs/pt05ch26s07.md) | [pt05ch26s07.md](./eng/pt05ch26s07.md) |
| 26.7.1 用户定义的机械材料行为 | 26.7.1 User-defined mechanical material behavior | [pt05ch26s07abm69.md](./chs/pt05ch26s07abm69.md) | [pt05ch26s07abm69.md](./eng/pt05ch26s07abm69.md) |
| 26.7.2 用户定义的热材料行为 | 26.7.2 User-defined thermal material behavior | [pt05ch26s07abm70.md](./chs/pt05ch26s07abm70.md) | [pt05ch26s07abm70.md](./eng/pt05ch26s07abm70.md) |

### PT06
*Elements*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| Elements | Elements | [pt06.md](./chs/pt06.md) | [pt06.md](./eng/pt06.md) |
| 27 Elements: Introduction | 27 Elements: Introduction | [pt06ch27.md](./chs/pt06ch27.md) | [pt06ch27.md](./eng/pt06ch27.md) |
| 27.1 Introduction | 27.1 Introduction | [pt06ch27s01.md](./chs/pt06ch27s01.md) | [pt06ch27s01.md](./eng/pt06ch27s01.md) |
| 27.1.1 Element library: overview | 27.1.1 Element library: overview | [pt06ch27s01abo25.md](./chs/pt06ch27s01abo25.md) | [pt06ch27s01abo25.md](./eng/pt06ch27s01abo25.md) |
| 27.1.2 选择单元的维度 | 27.1.2 Choosing the element's dimensionality | [pt06ch27s01aus111.md](./chs/pt06ch27s01aus111.md) | [pt06ch27s01aus111.md](./eng/pt06ch27s01aus111.md) |
| 27.1.3 为分析类型选择合适的单元 | 27.1.3 Choosing the appropriate element for an analysis type | [pt06ch27s01aus112.md](./chs/pt06ch27s01aus112.md) | [pt06ch27s01aus112.md](./eng/pt06ch27s01aus112.md) |
| 27.1.4 截面控制 | 27.1.4 Section controls | [pt06ch27s01aus113.md](./chs/pt06ch27s01aus113.md) | [pt06ch27s01aus113.md](./eng/pt06ch27s01aus113.md) |
| 28 Continuum Elements | 28 Continuum Elements | [pt06ch28.md](./chs/pt06ch28.md) | [pt06ch28.md](./eng/pt06ch28.md) |
| 28.1 General-purpose continuum elements | 28.1 General-purpose continuum elements | [pt06ch28s01.md](./chs/pt06ch28s01.md) | [pt06ch28s01.md](./eng/pt06ch28s01.md) |
| 28.1.2 一维实体（连接）单元库 | 28.1.2 One-dimensional solid (link) element library | [pt06ch28s01ael01.md](./chs/pt06ch28s01ael01.md) | [pt06ch28s01ael01.md](./eng/pt06ch28s01ael01.md) |
| 28.1.3 二维实体单元库 | 28.1.3 Two-dimensional solid element library | [pt06ch28s01ael02.md](./chs/pt06ch28s01ael02.md) | [pt06ch28s01ael02.md](./eng/pt06ch28s01ael02.md) |
| 28.1.4 三维实体单元库 | 28.1.4 Three-dimensional solid element library | [pt06ch28s01ael03.md](./chs/pt06ch28s01ael03.md) | [pt06ch28s01ael03.md](./eng/pt06ch28s01ael03.md) |
| 28.1.5 圆柱实体单元库 | 28.1.5 Cylindrical solid element library | [pt06ch28s01ael04.md](./chs/pt06ch28s01ael04.md) | [pt06ch28s01ael04.md](./eng/pt06ch28s01ael04.md) |
| 28.1.6 轴对称实体单元库 | 28.1.6 Axisymmetric solid element library | [pt06ch28s01ael05.md](./chs/pt06ch28s01ael05.md) | [pt06ch28s01ael05.md](./eng/pt06ch28s01ael05.md) |
| 28.1.7 具有非线性非对称变形的轴对称实体单元 | 28.1.7 Axisymmetric solid elements with nonlinear, asymmetric deformation | [pt06ch28s01ael06.md](./chs/pt06ch28s01ael06.md) | [pt06ch28s01ael06.md](./eng/pt06ch28s01ael06.md) |
| 28.1.1 实体（连续体）单元 | 28.1.1 Solid (continuum) elements | [pt06ch28s01alm01.md](./chs/pt06ch28s01alm01.md) | [pt06ch28s01alm01.md](./eng/pt06ch28s01alm01.md) |
| 28.2 Fluid continuum elements | 28.2 Fluid continuum elements | [pt06ch28s02.md](./chs/pt06ch28s02.md) | [pt06ch28s02.md](./eng/pt06ch28s02.md) |
| 28.2.2 流体单元库 | 28.2.2 Fluid element library | [pt06ch28s02ael07.md](./chs/pt06ch28s02ael07.md) | [pt06ch28s02ael07.md](./eng/pt06ch28s02ael07.md) |
| 28.2.1 流体（连续体）单元 | 28.2.1 Fluid (continuum) elements | [pt06ch28s02alm02.md](./chs/pt06ch28s02alm02.md) | [pt06ch28s02alm02.md](./eng/pt06ch28s02alm02.md) |
| 28.3 Infinite elements | 28.3 Infinite elements | [pt06ch28s03.md](./chs/pt06ch28s03.md) | [pt06ch28s03.md](./eng/pt06ch28s03.md) |
| 28.3.2 无限单元库 | 28.3.2 Infinite element library | [pt06ch28s03ael08.md](./chs/pt06ch28s03ael08.md) | [pt06ch28s03ael08.md](./eng/pt06ch28s03ael08.md) |
| 28.3.1 无限单元 | 28.3.1 Infinite elements | [pt06ch28s03alm03.md](./chs/pt06ch28s03alm03.md) | [pt06ch28s03alm03.md](./eng/pt06ch28s03alm03.md) |
| 28.4 Warping elements | 28.4 Warping elements | [pt06ch28s04.md](./chs/pt06ch28s04.md) | [pt06ch28s04.md](./eng/pt06ch28s04.md) |
| 28.4.2 翘曲单元库 | 28.4.2 Warping element library | [pt06ch28s04ael09.md](./chs/pt06ch28s04ael09.md) | [pt06ch28s04ael09.md](./eng/pt06ch28s04ael09.md) |
| 28.4.1 翘曲单元 | 28.4.1 Warping elements | [pt06ch28s04alm04.md](./chs/pt06ch28s04alm04.md) | [pt06ch28s04alm04.md](./eng/pt06ch28s04alm04.md) |
| 29 Structural Elements | 29 Structural Elements | [pt06ch29.md](./chs/pt06ch29.md) | [pt06ch29.md](./eng/pt06ch29.md) |
| 29.1 Membrane elements | 29.1 Membrane elements | [pt06ch29s01.md](./chs/pt06ch29s01.md) | [pt06ch29s01.md](./eng/pt06ch29s01.md) |
| 29.1.2 通用膜单元库 | 29.1.2 General membrane element library | [pt06ch29s01ael10.md](./chs/pt06ch29s01ael10.md) | [pt06ch29s01ael10.md](./eng/pt06ch29s01ael10.md) |
| 29.1.3 圆柱膜单元库 | 29.1.3 Cylindrical membrane element library | [pt06ch29s01ael11.md](./chs/pt06ch29s01ael11.md) | [pt06ch29s01ael11.md](./eng/pt06ch29s01ael11.md) |
| 29.1.4 轴对称膜单元库 | 29.1.4 Axisymmetric membrane element library | [pt06ch29s01ael12.md](./chs/pt06ch29s01ael12.md) | [pt06ch29s01ael12.md](./eng/pt06ch29s01ael12.md) |
| 29.1.1 膜单元 | 29.1.1 Membrane elements | [pt06ch29s01alm05.md](./chs/pt06ch29s01alm05.md) | [pt06ch29s01alm05.md](./eng/pt06ch29s01alm05.md) |
| 29.2 Truss elements | 29.2 Truss elements | [pt06ch29s02.md](./chs/pt06ch29s02.md) | [pt06ch29s02.md](./eng/pt06ch29s02.md) |
| 29.2.2 桁架单元库 | 29.2.2 Truss element library | [pt06ch29s02ael13.md](./chs/pt06ch29s02ael13.md) | [pt06ch29s02ael13.md](./eng/pt06ch29s02ael13.md) |
| 29.2.1 桁架单元 | 29.2.1 Truss elements | [pt06ch29s02alm06.md](./chs/pt06ch29s02alm06.md) | [pt06ch29s02alm06.md](./eng/pt06ch29s02alm06.md) |
| 29.3 Beam elements | 29.3 Beam elements | [pt06ch29s03.md](./chs/pt06ch29s03.md) | [pt06ch29s03.md](./eng/pt06ch29s03.md) |
| 29.3.9 梁截面库 | 29.3.9 Beam cross-section library | [pt06ch29s03abm01.md](./chs/pt06ch29s03abm01.md) | [pt06ch29s03abm01.md](./eng/pt06ch29s03abm01.md) |
| 29.3.1 梁建模：概述 | 29.3.1 Beam modeling: overview | [pt06ch29s03abo26.md](./chs/pt06ch29s03abo26.md) | [pt06ch29s03abo26.md](./eng/pt06ch29s03abo26.md) |
| 29.3.8 梁单元库 | 29.3.8 Beam element library | [pt06ch29s03ael14.md](./chs/pt06ch29s03ael14.md) | [pt06ch29s03ael14.md](./eng/pt06ch29s03ael14.md) |
| 29.3.2 选择梁截面 | 29.3.2 Choosing a beam cross-section | [pt06ch29s03alm07.md](./chs/pt06ch29s03alm07.md) | [pt06ch29s03alm07.md](./eng/pt06ch29s03alm07.md) |
| 29.3.4 梁单元横截面方向 | 29.3.3 Choosing a beam element | [pt06ch29s03alm08.md](./chs/pt06ch29s03alm08.md) | [pt06ch29s03alm08.md](./eng/pt06ch29s03alm08.md) |
| 29.3.3 选择梁单元 | 29.3.4 Beam element cross-section orientation | [pt06ch29s03alm09.md](./chs/pt06ch29s03alm09.md) | [pt06ch29s03alm09.md](./eng/pt06ch29s03alm09.md) |
| 29.3.5 梁截面行为 | 29.3.5 Beam section behavior | [pt06ch29s03alm10.md](./chs/pt06ch29s03alm10.md) | [pt06ch29s03alm10.md](./eng/pt06ch29s03alm10.md) |
| 29.3.6 使用分析过程中积分的梁截面定义截面行为 | 29.3.6 Using a beam section integrated during the analysis to define the section behavior | [pt06ch29s03alm11.md](./chs/pt06ch29s03alm11.md) | [pt06ch29s03alm11.md](./eng/pt06ch29s03alm11.md) |
| 29.3.7 使用通用梁截面定义截面行为 | 29.3.7 Using a general beam section to define the section behavior | [pt06ch29s03alm12.md](./chs/pt06ch29s03alm12.md) | [pt06ch29s03alm12.md](./eng/pt06ch29s03alm12.md) |
| 29.4 Frame elements | 29.4 Frame elements | [pt06ch29s04.md](./chs/pt06ch29s04.md) | [pt06ch29s04.md](./eng/pt06ch29s04.md) |
| 29.4.3 框架单元库 | 29.4.3 Frame element library | [pt06ch29s04ael15.md](./chs/pt06ch29s04ael15.md) | [pt06ch29s04ael15.md](./eng/pt06ch29s04ael15.md) |
| 29.4.1 框架单元 | 29.4.1 Frame elements | [pt06ch29s04alm13.md](./chs/pt06ch29s04alm13.md) | [pt06ch29s04alm13.md](./eng/pt06ch29s04alm13.md) |
| 29.4.2 框架截面行为 | 29.4.2 Frame section behavior | [pt06ch29s04alm14.md](./chs/pt06ch29s04alm14.md) | [pt06ch29s04alm14.md](./eng/pt06ch29s04alm14.md) |
| 29.5 Elbow elements | 29.5 Elbow elements | [pt06ch29s05.md](./chs/pt06ch29s05.md) | [pt06ch29s05.md](./eng/pt06ch29s05.md) |
| 29.5.2 弯头单元库 | 29.5.2 Elbow element library | [pt06ch29s05ael16.md](./chs/pt06ch29s05ael16.md) | [pt06ch29s05ael16.md](./eng/pt06ch29s05ael16.md) |
| 29.5.1 具有变形横截面的管道和弯头：弯头单元 | 29.5.1 Pipes and pipebends with deforming cross-sections: elbow elements | [pt06ch29s05alm15.md](./chs/pt06ch29s05alm15.md) | [pt06ch29s05alm15.md](./eng/pt06ch29s05alm15.md) |
| 29.6 Shell elements | 29.6 Shell elements | [pt06ch29s06.md](./chs/pt06ch29s06.md) | [pt06ch29s06.md](./eng/pt06ch29s06.md) |
| 29.6.1 壳单元：概述 | 29.6.1 Shell elements: overview | [pt06ch29s06abo27.md](./chs/pt06ch29s06abo27.md) | [pt06ch29s06abo27.md](./eng/pt06ch29s06abo27.md) |
| 29.6.7 三维常规壳单元库 | 29.6.7 Three-dimensional conventional shell element library | [pt06ch29s06ael17.md](./chs/pt06ch29s06ael17.md) | [pt06ch29s06ael17.md](./eng/pt06ch29s06ael17.md) |
| 29.6.8 连续体壳单元库 | 29.6.8 Continuum shell element library | [pt06ch29s06ael18.md](./chs/pt06ch29s06ael18.md) | [pt06ch29s06ael18.md](./eng/pt06ch29s06ael18.md) |
| 29.6.9 轴对称壳单元库 | 29.6.9 Axisymmetric shell element library | [pt06ch29s06ael19.md](./chs/pt06ch29s06ael19.md) | [pt06ch29s06ael19.md](./eng/pt06ch29s06ael19.md) |
| 29.6.10 具有非线性非对称变形的轴对称壳单元 | 29.6.10 Axisymmetric shell elements with nonlinear, asymmetric deformation | [pt06ch29s06ael20.md](./chs/pt06ch29s06ael20.md) | [pt06ch29s06ael20.md](./eng/pt06ch29s06ael20.md) |
| 29.6.2 选择壳单元 | 29.6.2 Choosing a shell element | [pt06ch29s06alm16.md](./chs/pt06ch29s06alm16.md) | [pt06ch29s06alm16.md](./eng/pt06ch29s06alm16.md) |
| 29.6.3 定义常规壳单元的初始几何形状 | 29.6.3 Defining the initial geometry of conventional shell elements | [pt06ch29s06alm17.md](./chs/pt06ch29s06alm17.md) | [pt06ch29s06alm17.md](./eng/pt06ch29s06alm17.md) |
| 29.6.4 壳截面行为 | 29.6.4 Shell section behavior | [pt06ch29s06alm18.md](./chs/pt06ch29s06alm18.md) | [pt06ch29s06alm18.md](./eng/pt06ch29s06alm18.md) |
| 29.6.5 使用分析过程中积分的壳截面定义截面行为 | 29.6.5 Using a shell section integrated during the analysis to define the section behavior | [pt06ch29s06alm19.md](./chs/pt06ch29s06alm19.md) | [pt06ch29s06alm19.md](./eng/pt06ch29s06alm19.md) |
| 29.6.6 使用通用壳截面定义截面行为 | 29.6.6 Using a general shell section to define the section behavior | [pt06ch29s06alm20.md](./chs/pt06ch29s06alm20.md) | [pt06ch29s06alm20.md](./eng/pt06ch29s06alm20.md) |
| 30 Inertial, Rigid, and Capacitance Elements | 30 Inertial, Rigid, and Capacitance Elements | [pt06ch30.md](./chs/pt06ch30.md) | [pt06ch30.md](./eng/pt06ch30.md) |
| 30.1 Point mass elements | 30.1 Point mass elements | [pt06ch30s01.md](./chs/pt06ch30s01.md) | [pt06ch30s01.md](./eng/pt06ch30s01.md) |
| 30.1.2 质量单元库 | 30.1.2 Mass element library | [pt06ch30s01ael21.md](./chs/pt06ch30s01ael21.md) | [pt06ch30s01ael21.md](./eng/pt06ch30s01ael21.md) |
| 30.1.1 点质量 | 30.1.1 Point masses | [pt06ch30s01alm21.md](./chs/pt06ch30s01alm21.md) | [pt06ch30s01alm21.md](./eng/pt06ch30s01alm21.md) |
| 30.2 Rotary inertia elements | 30.2 Rotary inertia elements | [pt06ch30s02.md](./chs/pt06ch30s02.md) | [pt06ch30s02.md](./eng/pt06ch30s02.md) |
| 30.2.2 转动惯量单元库 | 30.2.2 Rotary inertia element library | [pt06ch30s02ael22.md](./chs/pt06ch30s02ael22.md) | [pt06ch30s02ael22.md](./eng/pt06ch30s02ael22.md) |
| 30.2.1 转动惯量 | 30.2.1 Rotary inertia | [pt06ch30s02alm22.md](./chs/pt06ch30s02alm22.md) | [pt06ch30s02alm22.md](./eng/pt06ch30s02alm22.md) |
| 30.3 Rigid elements | 30.3 Rigid elements | [pt06ch30s03.md](./chs/pt06ch30s03.md) | [pt06ch30s03.md](./eng/pt06ch30s03.md) |
| 30.3.1 刚性单元 | 30.3.2 Rigid element library | [pt06ch30s03ael23.md](./chs/pt06ch30s03ael23.md) | [pt06ch30s03ael23.md](./eng/pt06ch30s03ael23.md) |
| 30.3.2 刚性单元库 | 30.3.1 Rigid elements | [pt06ch30s03alm23.md](./chs/pt06ch30s03alm23.md) | [pt06ch30s03alm23.md](./eng/pt06ch30s03alm23.md) |
| 30.4 Capacitance elements | 30.4 Capacitance elements | [pt06ch30s04.md](./chs/pt06ch30s04.md) | [pt06ch30s04.md](./eng/pt06ch30s04.md) |
| 30.4.1 点电容 | 30.4.2 Capacitance element library | [pt06ch30s04ael24.md](./chs/pt06ch30s04ael24.md) | [pt06ch30s04ael24.md](./eng/pt06ch30s04ael24.md) |
| 30.4.2 电容单元库 | 30.4.1 Point capacitance | [pt06ch30s04alm24.md](./chs/pt06ch30s04alm24.md) | [pt06ch30s04alm24.md](./eng/pt06ch30s04alm24.md) |
| 31 Connector Elements | 31 Connector Elements | [pt06ch31.md](./chs/pt06ch31.md) | [pt06ch31.md](./eng/pt06ch31.md) |
| 31.1 Connector elements | 31.1 Connector elements | [pt06ch31s01.md](./chs/pt06ch31s01.md) | [pt06ch31s01.md](./eng/pt06ch31s01.md) |
| 31.1.1 连接器：概述 | 31.1.1 Connectors: overview | [pt06ch31s01abo28.md](./chs/pt06ch31s01abo28.md) | [pt06ch31s01abo28.md](./eng/pt06ch31s01abo28.md) |
| 31.1.4 连接器单元库 | 31.1.4 Connector element library | [pt06ch31s01ael25.md](./chs/pt06ch31s01ael25.md) | [pt06ch31s01ael25.md](./eng/pt06ch31s01ael25.md) |
| 31.1.2 连接器单元 | 31.1.2 Connector elements | [pt06ch31s01alm25.md](./chs/pt06ch31s01alm25.md) | [pt06ch31s01alm25.md](./eng/pt06ch31s01alm25.md) |
| 31.1.3 连接器驱动 | 31.1.3 Connector actuation | [pt06ch31s01alm26.md](./chs/pt06ch31s01alm26.md) | [pt06ch31s01alm26.md](./eng/pt06ch31s01alm26.md) |
| 31.1.5 连接类型库 | 31.1.5 Connection-type library | [pt06ch31s01aus114.md](./chs/pt06ch31s01aus114.md) | [pt06ch31s01aus114.md](./eng/pt06ch31s01aus114.md) |
| 31.2 Connector element behavior | 31.2 Connector element behavior | [pt06ch31s02.md](./chs/pt06ch31s02.md) | [pt06ch31s02.md](./eng/pt06ch31s02.md) |
| 31.2.1 连接器行为 | 31.2.1 Connector behavior | [pt06ch31s02alm27.md](./chs/pt06ch31s02alm27.md) | [pt06ch31s02alm27.md](./eng/pt06ch31s02alm27.md) |
| 31.2.2 连接器弹性行为 | 31.2.2 Connector elastic behavior | [pt06ch31s02alm28.md](./chs/pt06ch31s02alm28.md) | [pt06ch31s02alm28.md](./eng/pt06ch31s02alm28.md) |
| 31.2.3 连接器阻尼行为 | 31.2.3 Connector damping behavior | [pt06ch31s02alm29.md](./chs/pt06ch31s02alm29.md) | [pt06ch31s02alm29.md](./eng/pt06ch31s02alm29.md) |
| 31.2.4 用于耦合行为的连接器函数 | 31.2.4 Connector functions for coupled behavior | [pt06ch31s02alm30.md](./chs/pt06ch31s02alm30.md) | [pt06ch31s02alm30.md](./eng/pt06ch31s02alm30.md) |
| 31.2.5 连接器摩擦行为 | 31.2.5 Connector friction behavior | [pt06ch31s02alm31.md](./chs/pt06ch31s02alm31.md) | [pt06ch31s02alm31.md](./eng/pt06ch31s02alm31.md) |
| 31.2.6 连接器塑性行为 | 31.2.6 Connector plastic behavior | [pt06ch31s02alm32.md](./chs/pt06ch31s02alm32.md) | [pt06ch31s02alm32.md](./eng/pt06ch31s02alm32.md) |
| 31.2.7 连接器损伤行为 | 31.2.7 Connector damage behavior | [pt06ch31s02alm33.md](./chs/pt06ch31s02alm33.md) | [pt06ch31s02alm33.md](./eng/pt06ch31s02alm33.md) |
| 31.2.8 连接器止挡和锁 | 31.2.8 Connector stops and locks | [pt06ch31s02alm34.md](./chs/pt06ch31s02alm34.md) | [pt06ch31s02alm34.md](./eng/pt06ch31s02alm34.md) |
| 31.2.9 连接器失效行为 | 31.2.9 Connector failure behavior | [pt06ch31s02alm35.md](./chs/pt06ch31s02alm35.md) | [pt06ch31s02alm35.md](./eng/pt06ch31s02alm35.md) |
| 31.2.10 连接器单轴行为 | 31.2.10 Connector uniaxial behavior | [pt06ch31s02alm36.md](./chs/pt06ch31s02alm36.md) | [pt06ch31s02alm36.md](./eng/pt06ch31s02alm36.md) |
| 32 Special-Purpose Elements | 32 Special-Purpose Elements | [pt06ch32.md](./chs/pt06ch32.md) | [pt06ch32.md](./eng/pt06ch32.md) |
| 32.1 Spring elements | 32.1 Spring elements | [pt06ch32s01.md](./chs/pt06ch32s01.md) | [pt06ch32s01.md](./eng/pt06ch32s01.md) |
| 32.1.2 弹簧单元库 | 32.1.2 Spring element library | [pt06ch32s01ael26.md](./chs/pt06ch32s01ael26.md) | [pt06ch32s01ael26.md](./eng/pt06ch32s01ael26.md) |
| 32.1.1 弹簧 | 32.1.1 Springs | [pt06ch32s01alm37.md](./chs/pt06ch32s01alm37.md) | [pt06ch32s01alm37.md](./eng/pt06ch32s01alm37.md) |
| 32.2 Dashpot elements | 32.2 Dashpot elements | [pt06ch32s02.md](./chs/pt06ch32s02.md) | [pt06ch32s02.md](./eng/pt06ch32s02.md) |
| 32.2.2 阻尼器单元库 | 32.2.2 Dashpot element library | [pt06ch32s02ael27.md](./chs/pt06ch32s02ael27.md) | [pt06ch32s02ael27.md](./eng/pt06ch32s02ael27.md) |
| 32.2.1 阻尼器 | 32.2.1 Dashpots | [pt06ch32s02alm38.md](./chs/pt06ch32s02alm38.md) | [pt06ch32s02alm38.md](./eng/pt06ch32s02alm38.md) |
| 32.3 Flexible joint elements | 32.3 Flexible joint elements | [pt06ch32s03.md](./chs/pt06ch32s03.md) | [pt06ch32s03.md](./eng/pt06ch32s03.md) |
| 32.3.2 柔性连接单元库 | 32.3.2 Flexible joint element library | [pt06ch32s03ael28.md](./chs/pt06ch32s03ael28.md) | [pt06ch32s03ael28.md](./eng/pt06ch32s03ael28.md) |
| 32.3.1 柔性连接单元 | 32.3.1 Flexible joint element | [pt06ch32s03alm39.md](./chs/pt06ch32s03alm39.md) | [pt06ch32s03alm39.md](./eng/pt06ch32s03alm39.md) |
| 32.4 Distributing coupling elements | 32.4 Distributing coupling elements | [pt06ch32s04.md](./chs/pt06ch32s04.md) | [pt06ch32s04.md](./eng/pt06ch32s04.md) |
| 32.4.2 分布耦合单元库 | 32.4.2 Distributing coupling element library | [pt06ch32s04ael29.md](./chs/pt06ch32s04ael29.md) | [pt06ch32s04ael29.md](./eng/pt06ch32s04ael29.md) |
| 32.4.1 分布耦合单元 | 32.4.1 Distributing coupling elements | [pt06ch32s04alm40.md](./chs/pt06ch32s04alm40.md) | [pt06ch32s04alm40.md](./eng/pt06ch32s04alm40.md) |
| 32.5 Cohesive elements | 32.5 Cohesive elements | [pt06ch32s05.md](./chs/pt06ch32s05.md) | [pt06ch32s05.md](./eng/pt06ch32s05.md) |
| 32.5.1 内聚单元：概述 | 32.5.1 Cohesive elements: overview | [pt06ch32s05abo29.md](./chs/pt06ch32s05abo29.md) | [pt06ch32s05abo29.md](./eng/pt06ch32s05abo29.md) |
| 32.5.9 三维内聚单元库 | 32.5.8 Two-dimensional cohesive element library | [pt06ch32s05ael30.md](./chs/pt06ch32s05ael30.md) | [pt06ch32s05ael30.md](./eng/pt06ch32s05ael30.md) |
| 32.5.8 二维内聚单元库 | 32.5.9 Three-dimensional cohesive element library | [pt06ch32s05ael31.md](./chs/pt06ch32s05ael31.md) | [pt06ch32s05ael31.md](./eng/pt06ch32s05ael31.md) |
| 32.5.2 选择内聚单元 | 32.5.10 Axisymmetric cohesive element library | [pt06ch32s05ael32.md](./chs/pt06ch32s05ael32.md) | [pt06ch32s05ael32.md](./eng/pt06ch32s05ael32.md) |
| 32.5.10 轴对称内聚单元库 | 32.5.2 Choosing a cohesive element | [pt06ch32s05alm41.md](./chs/pt06ch32s05alm41.md) | [pt06ch32s05alm41.md](./eng/pt06ch32s05alm41.md) |
| 32.5.4 定义内聚单元的初始几何 | 32.5.3 Modeling with cohesive elements | [pt06ch32s05alm42.md](./chs/pt06ch32s05alm42.md) | [pt06ch32s05alm42.md](./eng/pt06ch32s05alm42.md) |
| 32.5.5 使用连续体方法定义内聚单元的本构响应 | 32.5.4 Defining the cohesive element's initial geometry | [pt06ch32s05alm43.md](./chs/pt06ch32s05alm43.md) | [pt06ch32s05alm43.md](./eng/pt06ch32s05alm43.md) |
| 32.5.7 定义内聚单元间隙内流体的本构响应 | 32.5.5 Defining the constitutive response of cohesive elements using a continuum approach | [pt06ch32s05alm44.md](./chs/pt06ch32s05alm44.md) | [pt06ch32s05alm44.md](./eng/pt06ch32s05alm44.md) |
| 32.6.1 垫片单元：概述 | 32.5.6 Defining the constitutive response of cohesive elements using a traction-separation description | [pt06ch32s05alm45.md](./chs/pt06ch32s05alm45.md) | [pt06ch32s05alm45.md](./eng/pt06ch32s05alm45.md) |
| 32.5.3 使用内聚单元建模 | 32.5.7 Defining the constitutive response of fluid within the cohesive element gap | [pt06ch32s05alm46.md](./chs/pt06ch32s05alm46.md) | [pt06ch32s05alm46.md](./eng/pt06ch32s05alm46.md) |
| 32.6 Gasket elements | 32.6 Gasket elements | [pt06ch32s06.md](./chs/pt06ch32s06.md) | [pt06ch32s06.md](./eng/pt06ch32s06.md) |
| 32.6.7 二维垫片单元库 | 32.6.1 Gasket elements: overview | [pt06ch32s06abo30.md](./chs/pt06ch32s06abo30.md) | [pt06ch32s06abo30.md](./eng/pt06ch32s06abo30.md) |
| 32.6.8 三维垫片单元库 | 32.6.7 Two-dimensional gasket element library | [pt06ch32s06ael33.md](./chs/pt06ch32s06ael33.md) | [pt06ch32s06ael33.md](./eng/pt06ch32s06ael33.md) |
| 32.6.2 选择垫片单元 | 32.6.8 Three-dimensional gasket element library | [pt06ch32s06ael34.md](./chs/pt06ch32s06ael34.md) | [pt06ch32s06ael34.md](./eng/pt06ch32s06ael34.md) |
| 32.6.9 轴对称垫片单元库 | 32.6.9 Axisymmetric gasket element library | [pt06ch32s06ael35.md](./chs/pt06ch32s06ael35.md) | [pt06ch32s06ael35.md](./eng/pt06ch32s06ael35.md) |
| 32.6.2 选择垫片单元 | 32.6.2 Choosing a gasket element | [pt06ch32s06alm47.md](./chs/pt06ch32s06alm47.md) | [pt06ch32s06alm47.md](./eng/pt06ch32s06alm47.md) |
| 32.6.3 在模型中包含垫片单元 | 32.6.3 Including gasket elements in a model | [pt06ch32s06alm48.md](./chs/pt06ch32s06alm48.md) | [pt06ch32s06alm48.md](./eng/pt06ch32s06alm48.md) |
| 32.6.4 定义垫片单元的初始几何形状 | 32.6.4 Defining the gasket element's initial geometry | [pt06ch32s06alm49.md](./chs/pt06ch32s06alm49.md) | [pt06ch32s06alm49.md](./eng/pt06ch32s06alm49.md) |
| 32.6.5 使用材料模型定义垫片行为 | 32.6.5 Defining the gasket behavior using a material model | [pt06ch32s06alm50.md](./chs/pt06ch32s06alm50.md) | [pt06ch32s06alm50.md](./eng/pt06ch32s06alm50.md) |
| 32.6.6 直接使用垫片行为模型定义垫片行为 | 32.6.6 Defining the gasket behavior directly using a gasket behavior model | [pt06ch32s06alm51.md](./chs/pt06ch32s06alm51.md) | [pt06ch32s06alm51.md](./eng/pt06ch32s06alm51.md) |
| 32.7 Surface elements | 32.7 Surface elements | [pt06ch32s07.md](./chs/pt06ch32s07.md) | [pt06ch32s07.md](./eng/pt06ch32s07.md) |
| 32.7.2 通用表面单元库 | 32.7.2 General surface element library | [pt06ch32s07ael36.md](./chs/pt06ch32s07ael36.md) | [pt06ch32s07ael36.md](./eng/pt06ch32s07ael36.md) |
| 32.7.3 圆柱表面单元库 | 32.7.3 Cylindrical surface element library | [pt06ch32s07ael37.md](./chs/pt06ch32s07ael37.md) | [pt06ch32s07ael37.md](./eng/pt06ch32s07ael37.md) |
| 32.7.4 轴对称表面单元库 | 32.7.4 Axisymmetric surface element library | [pt06ch32s07ael38.md](./chs/pt06ch32s07ael38.md) | [pt06ch32s07ael38.md](./eng/pt06ch32s07ael38.md) |
| 32.7.1 表面单元 | 32.7.1 Surface elements | [pt06ch32s07alm52.md](./chs/pt06ch32s07alm52.md) | [pt06ch32s07alm52.md](./eng/pt06ch32s07alm52.md) |
| 32.8 Tube support elements | 32.8 Tube support elements | [pt06ch32s08.md](./chs/pt06ch32s08.md) | [pt06ch32s08.md](./eng/pt06ch32s08.md) |
| 32.8.2 管道支撑单元库 | 32.8.2 Tube support element library | [pt06ch32s08ael39.md](./chs/pt06ch32s08ael39.md) | [pt06ch32s08ael39.md](./eng/pt06ch32s08ael39.md) |
| 32.8.1 管道支撑单元 | 32.8.1 Tube support elements | [pt06ch32s08alm53.md](./chs/pt06ch32s08alm53.md) | [pt06ch32s08alm53.md](./eng/pt06ch32s08alm53.md) |
| 32.9 Line spring elements | 32.9 Line spring elements | [pt06ch32s09.md](./chs/pt06ch32s09.md) | [pt06ch32s09.md](./eng/pt06ch32s09.md) |
| 32.9.2 线弹簧单元库 | 32.9.2 Line spring element library | [pt06ch32s09ael40.md](./chs/pt06ch32s09ael40.md) | [pt06ch32s09ael40.md](./eng/pt06ch32s09ael40.md) |
| 32.9.1 用于模拟壳体中部分穿透裂纹的线弹簧单元 | 32.9.1 Line spring elements for modeling part-through cracks in shells | [pt06ch32s09alm54.md](./chs/pt06ch32s09alm54.md) | [pt06ch32s09alm54.md](./eng/pt06ch32s09alm54.md) |
| 32.10 Elastic-plastic joints | 32.10 Elastic-plastic joints | [pt06ch32s10.md](./chs/pt06ch32s10.md) | [pt06ch32s10.md](./eng/pt06ch32s10.md) |
| 32.10.2 弹塑性关节单元库 | 32.10.2 Elastic-plastic joint element library | [pt06ch32s10ael41.md](./chs/pt06ch32s10ael41.md) | [pt06ch32s10ael41.md](./eng/pt06ch32s10ael41.md) |
| 32.10.1 弹塑性关节 | 32.10.1 Elastic-plastic joints | [pt06ch32s10alm55.md](./chs/pt06ch32s10alm55.md) | [pt06ch32s10alm55.md](./eng/pt06ch32s10alm55.md) |
| 32.11 Drag chain elements | 32.11 Drag chain elements | [pt06ch32s11.md](./chs/pt06ch32s11.md) | [pt06ch32s11.md](./eng/pt06ch32s11.md) |
| 32.11.2 拖链单元库 | 32.11.2 Drag chain element library | [pt06ch32s11ael42.md](./chs/pt06ch32s11ael42.md) | [pt06ch32s11ael42.md](./eng/pt06ch32s11ael42.md) |
| 32.11.1 拖链 | 32.11.1 Drag chains | [pt06ch32s11alm56.md](./chs/pt06ch32s11alm56.md) | [pt06ch32s11alm56.md](./eng/pt06ch32s11alm56.md) |
| 32.12 Pipe-soil elements | 32.12 Pipe-soil elements | [pt06ch32s12.md](./chs/pt06ch32s12.md) | [pt06ch32s12.md](./eng/pt06ch32s12.md) |
| 32.12.2 管土相互作用单元库 | 32.12.2 Pipe-soil interaction element library | [pt06ch32s12ael43.md](./chs/pt06ch32s12ael43.md) | [pt06ch32s12ael43.md](./eng/pt06ch32s12ael43.md) |
| 32.12.1 管土相互作用单元 | 32.12.1 Pipe-soil interaction elements | [pt06ch32s12alm57.md](./chs/pt06ch32s12alm57.md) | [pt06ch32s12alm57.md](./eng/pt06ch32s12alm57.md) |
| 32.13 Acoustic interface elements | 32.13 Acoustic interface elements | [pt06ch32s13.md](./chs/pt06ch32s13.md) | [pt06ch32s13.md](./eng/pt06ch32s13.md) |
| 32.13.4 声学界面单元库 | 32.13.2 Acoustic interface element library | [pt06ch32s13ael44.md](./chs/pt06ch32s13ael44.md) | [pt06ch32s13ael44.md](./eng/pt06ch32s13ael44.md) |
| 32.13.5 声学界面单元 | 32.13.1 Acoustic interface elements | [pt06ch32s13alm58.md](./chs/pt06ch32s13alm58.md) | [pt06ch32s13alm58.md](./eng/pt06ch32s13alm58.md) |
| 32.14 Eulerian elements | 32.14 Eulerian elements | [pt06ch32s14.md](./chs/pt06ch32s14.md) | [pt06ch32s14.md](./eng/pt06ch32s14.md) |
| 32.14.4 欧拉单元库 | 32.14.2 Eulerian element library | [pt06ch32s14ael45.md](./chs/pt06ch32s14ael45.md) | [pt06ch32s14ael45.md](./eng/pt06ch32s14ael45.md) |
| 32.14.5 欧拉单元 | 32.14.1 Eulerian elements | [pt06ch32s14alm59.md](./chs/pt06ch32s14alm59.md) | [pt06ch32s14alm59.md](./eng/pt06ch32s14alm59.md) |
| 32.15 User-defined elements | 32.15 User-defined elements | [pt06ch32s15.md](./chs/pt06ch32s15.md) | [pt06ch32s15.md](./eng/pt06ch32s15.md) |
| 32.15.4 用户定义单元库 | 32.15.2 User-defined element library | [pt06ch32s15ael46.md](./chs/pt06ch32s15ael46.md) | [pt06ch32s15ael46.md](./eng/pt06ch32s15ael46.md) |
| 32.15.5 用户定义单元 | 32.15.1 User-defined elements | [pt06ch32s15alm60.md](./chs/pt06ch32s15alm60.md) | [pt06ch32s15alm60.md](./eng/pt06ch32s15alm60.md) |
| 33 Particle Elements | 33 Particle Elements | [pt06ch33.md](./chs/pt06ch33.md) | [pt06ch33.md](./eng/pt06ch33.md) |
| 33.1 Discrete particle elements | 33.1 Discrete particle elements | [pt06ch33s01.md](./chs/pt06ch33s01.md) | [pt06ch33s01.md](./eng/pt06ch33s01.md) |
| 33.1.4 离散粒子单元库 | 33.1.2 Discrete particle element library | [pt06ch33s01ael47.md](./chs/pt06ch33s01ael47.md) | [pt06ch33s01ael47.md](./eng/pt06ch33s01ael47.md) |
| 33.1.5 离散粒子单元 | 33.1.1 Discrete particle elements | [pt06ch33s01alm61.md](./chs/pt06ch33s01alm61.md) | [pt06ch33s01alm61.md](./eng/pt06ch33s01alm61.md) |
| 33.2 Continuum particle elements | 33.2 Continuum particle elements | [pt06ch33s02.md](./chs/pt06ch33s02.md) | [pt06ch33s02.md](./eng/pt06ch33s02.md) |
| 33.2.4 连续粒子单元库 | 33.2.2 Continuum particle element library | [pt06ch33s02ael48.md](./chs/pt06ch33s02ael48.md) | [pt06ch33s02ael48.md](./eng/pt06ch33s02ael48.md) |
| 33.2.5 连续粒子单元 | 33.2.1 Continuum particle elements | [pt06ch33s02alm62.md](./chs/pt06ch33s02alm62.md) | [pt06ch33s02alm62.md](./eng/pt06ch33s02alm62.md) |

### PT07
*Prescribed Conditions*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| Prescribed Conditions | Prescribed Conditions | [pt07.md](./chs/pt07.md) | [pt07.md](./eng/pt07.md) |
| 34 Prescribed Conditions | 34 Prescribed Conditions | [pt07ch34.md](./chs/pt07ch34.md) | [pt07ch34.md](./eng/pt07ch34.md) |
| 34.1 Overview | 34.1 Overview | [pt07ch34s01.md](./chs/pt07ch34s01.md) | [pt07ch34s01.md](./eng/pt07ch34s01.md) |
| 34.1.1 Prescribed conditions: overview | 34.1.1 Prescribed conditions: overview | [pt07ch34s01abo31.md](./chs/pt07ch34s01abo31.md) | [pt07ch34s01abo31.md](./eng/pt07ch34s01abo31.md) |
| 34.1.2 幅值曲线 | 34.1.2 Amplitude curves | [pt07ch34s01aus115.md](./chs/pt07ch34s01aus115.md) | [pt07ch34s01aus115.md](./eng/pt07ch34s01aus115.md) |
| 34.2 Initial conditions | 34.2 Initial conditions | [pt07ch34s02.md](./chs/pt07ch34s02.md) | [pt07ch34s02.md](./eng/pt07ch34s02.md) |
| 34.2.2 Abaqus/Standard 和 Abaqus/Explicit 中的初始条件 | 34.2.1 Initial conditions in Abaqus/Standard and Abaqus/Explicit | [pt07ch34s02aus116.md](./chs/pt07ch34s02aus116.md) | [pt07ch34s02aus116.md](./eng/pt07ch34s02aus116.md) |
| 34.2.3 Abaqus/CFD 中的初始条件 | 34.2.2 Initial conditions in Abaqus/CFD | [pt07ch34s02aus117.md](./chs/pt07ch34s02aus117.md) | [pt07ch34s02aus117.md](./eng/pt07ch34s02aus117.md) |
| 34.3 Boundary conditions | 34.3 Boundary conditions | [pt07ch34s03.md](./chs/pt07ch34s03.md) | [pt07ch34s03.md](./eng/pt07ch34s03.md) |
| 34.3.2 Abaqus/Standard 和 Abaqus/Explicit 中的边界条件 | 34.3.1 Boundary conditions in Abaqus/Standard and Abaqus/Explicit | [pt07ch34s03aus118.md](./chs/pt07ch34s03aus118.md) | [pt07ch34s03aus118.md](./eng/pt07ch34s03aus118.md) |
| 34.3.3 Abaqus/CFD 中的边界条件 | 34.3.2 Boundary conditions in Abaqus/CFD | [pt07ch34s03aus119.md](./chs/pt07ch34s03aus119.md) | [pt07ch34s03aus119.md](./eng/pt07ch34s03aus119.md) |
| 34.4 Loads | 34.4 Loads | [pt07ch34s04.md](./chs/pt07ch34s04.md) | [pt07ch34s04.md](./eng/pt07ch34s04.md) |
| 34.4.4 施加载荷：概述 | 34.4.1 Applying loads: overview | [pt07ch34s04aus120.md](./chs/pt07ch34s04aus120.md) | [pt07ch34s04aus120.md](./eng/pt07ch34s04aus120.md) |
| 34.4.4 集中载荷 | 34.4.2 Concentrated loads | [pt07ch34s04aus121.md](./chs/pt07ch34s04aus121.md) | [pt07ch34s04aus121.md](./eng/pt07ch34s04aus121.md) |
| 34.4.4 分布载荷 | 34.4.3 Distributed loads | [pt07ch34s04aus122.md](./chs/pt07ch34s04aus122.md) | [pt07ch34s04aus122.md](./eng/pt07ch34s04aus122.md) |
| 34.4.4 热载荷 | 34.4.4 Thermal loads | [pt07ch34s04aus123.md](./chs/pt07ch34s04aus123.md) | [pt07ch34s04aus123.md](./eng/pt07ch34s04aus123.md) |
| 34.4.5 电磁载荷 | 34.4.5 Electromagnetic loads | [pt07ch34s04aus124.md](./chs/pt07ch34s04aus124.md) | [pt07ch34s04aus124.md](./eng/pt07ch34s04aus124.md) |
| 34.4.6 声学和冲击载荷 | 34.4.6 Acoustic and shock loads | [pt07ch34s04aus125.md](./chs/pt07ch34s04aus125.md) | [pt07ch34s04aus125.md](./eng/pt07ch34s04aus125.md) |
| 34.4.7 孔隙流体流速 | 34.4.7 Pore fluid flow | [pt07ch34s04aus126.md](./chs/pt07ch34s04aus126.md) | [pt07ch34s04aus126.md](./eng/pt07ch34s04aus126.md) |
| 34.5 Prescribed assembly loads | 34.5 Prescribed assembly loads | [pt07ch34s05.md](./chs/pt07ch34s05.md) | [pt07ch34s05.md](./eng/pt07ch34s05.md) |
| 34.5.1 预紧力载荷 | 34.5.1 Prescribed assembly loads | [pt07ch34s05aus127.md](./chs/pt07ch34s05aus127.md) | [pt07ch34s05aus127.md](./eng/pt07ch34s05aus127.md) |
| 34.6 Predefined fields | 34.6 Predefined fields | [pt07ch34s06.md](./chs/pt07ch34s06.md) | [pt07ch34s06.md](./eng/pt07ch34s06.md) |
| 34.6.1 预定义场 | 34.6.1 Predefined fields | [pt07ch34s06aus128.md](./chs/pt07ch34s06aus128.md) | [pt07ch34s06aus128.md](./eng/pt07ch34s06aus128.md) |

### PT08
*Constraints*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| Constraints | Constraints | [pt08.md](./chs/pt08.md) | [pt08.md](./eng/pt08.md) |
| 35 Constraints | 35 Constraints | [pt08ch35.md](./chs/pt08ch35.md) | [pt08ch35.md](./eng/pt08ch35.md) |
| 35.1 Overview | 35.1 Overview | [pt08ch35s01.md](./chs/pt08ch35s01.md) | [pt08ch35s01.md](./eng/pt08ch35s01.md) |
| 35.1.1 Kinematic constraints: overview | 35.1.1 Kinematic constraints: overview | [pt08ch35s01abo32.md](./chs/pt08ch35s01abo32.md) | [pt08ch35s01abo32.md](./eng/pt08ch35s01abo32.md) |
| 35.2 Multi-point constraints | 35.2 Multi-point constraints | [pt08ch35s02.md](./chs/pt08ch35s02.md) | [pt08ch35s02.md](./eng/pt08ch35s02.md) |
| 35.2.2 线性约束方程 | 35.2.1 Linear constraint equations | [pt08ch35s02aus129.md](./chs/pt08ch35s02aus129.md) | [pt08ch35s02aus129.md](./eng/pt08ch35s02aus129.md) |
| 35.2.2 通用多点约束 | 35.2.2 General multi-point constraints | [pt08ch35s02aus130.md](./chs/pt08ch35s02aus130.md) | [pt08ch35s02aus130.md](./eng/pt08ch35s02aus130.md) |
| 35.2.4 运动耦合约束 | 35.2.3 Kinematic coupling constraints | [pt08ch35s02aus131.md](./chs/pt08ch35s02aus131.md) | [pt08ch35s02aus131.md](./eng/pt08ch35s02aus131.md) |
| 35.3 Surface-based constraints | 35.3 Surface-based constraints | [pt08ch35s03.md](./chs/pt08ch35s03.md) | [pt08ch35s03.md](./eng/pt08ch35s03.md) |
| 35.3.2 网格绑定约束 | 35.3.1 Mesh tie constraints | [pt08ch35s03aus132.md](./chs/pt08ch35s03aus132.md) | [pt08ch35s03aus132.md](./eng/pt08ch35s03aus132.md) |
| 35.3.3 耦合约束 | 35.3.2 Coupling constraints | [pt08ch35s03aus133.md](./chs/pt08ch35s03aus133.md) | [pt08ch35s03aus133.md](./eng/pt08ch35s03aus133.md) |
| 35.3.4 壳-实体耦合 | 35.3.3 Shell-to-solid coupling | [pt08ch35s03aus134.md](./chs/pt08ch35s03aus134.md) | [pt08ch35s03aus134.md](./eng/pt08ch35s03aus134.md) |
| 35.3.6 网格无关紧固件 | 35.3.4 Mesh-independent fasteners | [pt08ch35s03aus135.md](./chs/pt08ch35s03aus135.md) | [pt08ch35s03aus135.md](./eng/pt08ch35s03aus135.md) |
| 35.4 Embedded elements | 35.4 Embedded elements | [pt08ch35s04.md](./chs/pt08ch35s04.md) | [pt08ch35s04.md](./eng/pt08ch35s04.md) |
| 35.4.1 埋入单元 | 35.4.1 Embedded elements | [pt08ch35s04aus136.md](./chs/pt08ch35s04aus136.md) | [pt08ch35s04aus136.md](./eng/pt08ch35s04aus136.md) |
| 35.5 Element end release | 35.5 Element end release | [pt08ch35s05.md](./chs/pt08ch35s05.md) | [pt08ch35s05.md](./eng/pt08ch35s05.md) |
| 35.5.1 单元端点释放 | 35.5.1 Element end release | [pt08ch35s05aus137.md](./chs/pt08ch35s05aus137.md) | [pt08ch35s05aus137.md](./eng/pt08ch35s05aus137.md) |
| 35.6 Overconstraint checks | 35.6 Overconstraint checks | [pt08ch35s06.md](./chs/pt08ch35s06.md) | [pt08ch35s06.md](./eng/pt08ch35s06.md) |
| 35.6.1 过约束检查 | 35.6.1 Overconstraint checks | [pt08ch35s06aus138.md](./chs/pt08ch35s06aus138.md) | [pt08ch35s06aus138.md](./eng/pt08ch35s06aus138.md) |

### PT09
*Interactions*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| Interactions | Interactions | [pt09.md](./chs/pt09.md) | [pt09.md](./eng/pt09.md) |
| 36 Defining Contact Interactions | 36 Defining Contact Interactions | [pt09ch36.md](./chs/pt09ch36.md) | [pt09ch36.md](./eng/pt09ch36.md) |
| 36.1 Overview | 36.1 Overview | [pt09ch36s01.md](./chs/pt09ch36s01.md) | [pt09ch36s01.md](./eng/pt09ch36s01.md) |
| 36.1.1 Contact interaction analysis: overview | 36.1.1 Contact interaction analysis: overview | [pt09ch36s01abo33.md](./chs/pt09ch36s01abo33.md) | [pt09ch36s01abo33.md](./eng/pt09ch36s01abo33.md) |
| 36.2 Defining general contact in Abaqus/Standard | 36.2 Defining general contact in Abaqus/Standard | [pt09ch36s02.md](./chs/pt09ch36s02.md) | [pt09ch36s02.md](./eng/pt09ch36s02.md) |
| 36.2.1 在Abaqus/Standard中定义一般接触交互 | 36.2.1 Defining general contact interactions in Abaqus/Standard | [pt09ch36s02aus139.md](./chs/pt09ch36s02aus139.md) | [pt09ch36s02aus139.md](./eng/pt09ch36s02aus139.md) |
| 36.2.2 Abaqus/Standard中一般接触的表面属性 | 36.2.2 Surface properties for general contact in Abaqus/Standard | [pt09ch36s02aus140.md](./chs/pt09ch36s02aus140.md) | [pt09ch36s02aus140.md](./eng/pt09ch36s02aus140.md) |
| 36.2.4 在 Abaqus/Standard 中控制初始接触状态 | 36.2.3 Contact properties for general contact in Abaqus/Standard | [pt09ch36s02aus141.md](./chs/pt09ch36s02aus141.md) | [pt09ch36s02aus141.md](./eng/pt09ch36s02aus141.md) |
| 36.2.3 在 Abaqus/Standard 中定义通用接触的接触属性 | 36.2.4 Controlling initial contact status in Abaqus/Standard | [pt09ch36s02aus142.md](./chs/pt09ch36s02aus142.md) | [pt09ch36s02aus142.md](./eng/pt09ch36s02aus142.md) |
| 36.2.5 在 Abaqus/Standard 中为通用接触建立稳定化 | 36.2.5 Stabilization for general contact in Abaqus/Standard | [pt09ch36s02aus143.md](./chs/pt09ch36s02aus143.md) | [pt09ch36s02aus143.md](./eng/pt09ch36s02aus143.md) |
| 36.2.6 在 Abaqus/Standard 中通用接触的数值控制 | 36.2.6 Numerical controls for general contact in Abaqus/Standard | [pt09ch36s02aus144.md](./chs/pt09ch36s02aus144.md) | [pt09ch36s02aus144.md](./eng/pt09ch36s02aus144.md) |
| 36.3 Defining contact pairs in Abaqus/Standard | 36.3 Defining contact pairs in Abaqus/Standard | [pt09ch36s03.md](./chs/pt09ch36s03.md) | [pt09ch36s03.md](./eng/pt09ch36s03.md) |
| 36.3.1 在 Abaqus/Standard 中定义接触对 | 36.3.1 Defining contact pairs in Abaqus/Standard | [pt09ch36s03aus145.md](./chs/pt09ch36s03aus145.md) | [pt09ch36s03aus145.md](./eng/pt09ch36s03aus145.md) |
| 36.3.2 在 Abaqus/Standard 中为接触对分配表面属性 | 36.3.2 Assigning surface properties for contact pairs in Abaqus/Standard | [pt09ch36s03aus146.md](./chs/pt09ch36s03aus146.md) | [pt09ch36s03aus146.md](./eng/pt09ch36s03aus146.md) |
| 36.3.3 在 Abaqus/Standard 中为接触对分配接触属性 | 36.3.3 Assigning contact properties for contact pairs in Abaqus/Standard | [pt09ch36s03aus147.md](./chs/pt09ch36s03aus147.md) | [pt09ch36s03aus147.md](./eng/pt09ch36s03aus147.md) |
| 36.3.4 在 Abaqus/Standard 中建立接触干扰配合模型 | 36.3.4 Modeling contact interference fits in Abaqus/Standard | [pt09ch36s03aus148.md](./chs/pt09ch36s03aus148.md) | [pt09ch36s03aus148.md](./eng/pt09ch36s03aus148.md) |
| 36.3.5 在 Abaqus/Standard 接触对中调整初始曲面位置并指定初始间隙 | 36.3.5 Adjusting initial surface positions and specifying initial clearances in Abaqus/Standard contact pairs | [pt09ch36s03aus149.md](./chs/pt09ch36s03aus149.md) | [pt09ch36s03aus149.md](./eng/pt09ch36s03aus149.md) |
| 36.3.6 在 Abaqus/Standard 中调整接触控制 | 36.3.6 Adjusting contact controls in Abaqus/Standard | [pt09ch36s03aus150.md](./chs/pt09ch36s03aus150.md) | [pt09ch36s03aus150.md](./eng/pt09ch36s03aus150.md) |
| 36.3.7 在 Abaqus/Standard 中定义粘接接触 | 36.3.7 Defining tied contact in Abaqus/Standard | [pt09ch36s03aus151.md](./chs/pt09ch36s03aus151.md) | [pt09ch36s03aus151.md](./eng/pt09ch36s03aus151.md) |
| 36.3.9 存在子结构时的接触建模 | 36.3.8 Extending master surfaces and slide lines | [pt09ch36s03aus152.md](./chs/pt09ch36s03aus152.md) | [pt09ch36s03aus152.md](./eng/pt09ch36s03aus152.md) |
| 36.3.10 存在非对称轴对称单元时的接触建模 | 36.3.9 Contact modeling if substructures are present | [pt09ch36s03aus153.md](./chs/pt09ch36s03aus153.md) | [pt09ch36s03aus153.md](./eng/pt09ch36s03aus153.md) |
| 36.3.6 在 Abaqus/Standard 中调整接触控制 | 36.3.10 Contact modeling if asymmetric-axisymmetric elements are present | [pt09ch36s03aus154.md](./chs/pt09ch36s03aus154.md) | [pt09ch36s03aus154.md](./eng/pt09ch36s03aus154.md) |
| 36.4 Defining general contact in Abaqus/Explicit | 36.4 Defining general contact in Abaqus/Explicit | [pt09ch36s04.md](./chs/pt09ch36s04.md) | [pt09ch36s04.md](./eng/pt09ch36s04.md) |
| 36.4.1 在 Abaqus/Explicit 中定义通用接触相互作用 | 36.4.1 Defining general contact interactions in Abaqus/Explicit | [pt09ch36s04aus155.md](./chs/pt09ch36s04aus155.md) | [pt09ch36s04aus155.md](./eng/pt09ch36s04aus155.md) |
| 36.4.2 在 Abaqus/Explicit 中为通用接触分配表面属性 | 36.4.2 Assigning surface properties for general contact in Abaqus/Explicit | [pt09ch36s04aus156.md](./chs/pt09ch36s04aus156.md) | [pt09ch36s04aus156.md](./eng/pt09ch36s04aus156.md) |
| 36.4.3 在 Abaqus/Explicit 中为通用接触分配接触属性 | 36.4.3 Assigning contact properties for general contact in Abaqus/Explicit | [pt09ch36s04aus157.md](./chs/pt09ch36s04aus157.md) | [pt09ch36s04aus157.md](./eng/pt09ch36s04aus157.md) |
| 36.4.4 在 Abaqus/Explicit 中控制通用接触的初始接触状态 | 36.4.4 Controlling initial contact status for general contact in Abaqus/Explicit | [pt09ch36s04aus158.md](./chs/pt09ch36s04aus158.md) | [pt09ch36s04aus158.md](./eng/pt09ch36s04aus158.md) |
| 36.4.5 Abaqus/Explicit 中通用接触的接触控制 | 36.4.5 Contact controls for general contact in Abaqus/Explicit | [pt09ch36s04aus159.md](./chs/pt09ch36s04aus159.md) | [pt09ch36s04aus159.md](./eng/pt09ch36s04aus159.md) |
| 36.5 Defining contact pairs in Abaqus/Explicit | 36.5 Defining contact pairs in Abaqus/Explicit | [pt09ch36s05.md](./chs/pt09ch36s05.md) | [pt09ch36s05.md](./eng/pt09ch36s05.md) |
| 36.5.1 在 Abaqus/Explicit 中定义接触对 | 36.5.1 Defining contact pairs in Abaqus/Explicit | [pt09ch36s05aus160.md](./chs/pt09ch36s05aus160.md) | [pt09ch36s05aus160.md](./eng/pt09ch36s05aus160.md) |
| 36.5.2 在 Abaqus/Explicit 中为接触对分配表面属性 | 36.5.2 Assigning surface properties for contact pairs in Abaqus/Explicit | [pt09ch36s05aus161.md](./chs/pt09ch36s05aus161.md) | [pt09ch36s05aus161.md](./eng/pt09ch36s05aus161.md) |
| 36.5.3 在 Abaqus/Explicit 中为接触对分配接触属性 | 36.5.3 Assigning contact properties for contact pairs in Abaqus/Explicit | [pt09ch36s05aus162.md](./chs/pt09ch36s05aus162.md) | [pt09ch36s05aus162.md](./eng/pt09ch36s05aus162.md) |
| 36.5.4 在 Abaqus/Explicit 中为接触对调整初始表面位置和指定初始间隙 | 36.5.4 Adjusting initial surface positions and specifying initial clearances for contact pairs in Abaqus/Explicit | [pt09ch36s05aus163.md](./chs/pt09ch36s05aus163.md) | [pt09ch36s05aus163.md](./eng/pt09ch36s05aus163.md) |
| 36.5.5 Abaqus/Explicit 中接触对的接触控制 | 36.5.5 Contact controls for contact pairs in Abaqus/Explicit | [pt09ch36s05aus164.md](./chs/pt09ch36s05aus164.md) | [pt09ch36s05aus164.md](./eng/pt09ch36s05aus164.md) |
| 37 Contact Property Models | 37 Contact Property Models | [pt09ch37.md](./chs/pt09ch37.md) | [pt09ch37.md](./eng/pt09ch37.md) |
| 37.1 Mechanical contact properties | 37.1 Mechanical contact properties | [pt09ch37s01.md](./chs/pt09ch37s01.md) | [pt09ch37s01.md](./eng/pt09ch37s01.md) |
| 37.1.10 基于表面的内聚行为 | 37.1.10 Surface-based cohesive behavior | [pt09ch37s01alm63.md](./chs/pt09ch37s01alm63.md) | [pt09ch37s01alm63.md](./eng/pt09ch37s01alm63.md) |
| 37.1.1 力学接触属性：概述 | 37.1.1 Mechanical contact properties: overview | [pt09ch37s01aus165.md](./chs/pt09ch37s01aus165.md) | [pt09ch37s01aus165.md](./eng/pt09ch37s01aus165.md) |
| 37.1.2 接触压力-过闭合关系 | 37.1.2 Contact pressure-overclosure relationships | [pt09ch37s01aus166.md](./chs/pt09ch37s01aus166.md) | [pt09ch37s01aus166.md](./eng/pt09ch37s01aus166.md) |
| 37.1.3 接触阻尼 | 37.1.3 Contact damping | [pt09ch37s01aus167.md](./chs/pt09ch37s01aus167.md) | [pt09ch37s01aus167.md](./eng/pt09ch37s01aus167.md) |
| 40.4.2 轴对称滑动线单元库 | 37.1.4 Contact blockage | [pt09ch37s01aus168.md](./chs/pt09ch37s01aus168.md) | [pt09ch37s01aus168.md](./eng/pt09ch37s01aus168.md) |
| 40.4.1 滑动线接触单元 | 37.1.5 Frictional behavior | [pt09ch37s01aus169.md](./chs/pt09ch37s01aus169.md) | [pt09ch37s01aus169.md](./eng/pt09ch37s01aus169.md) |
| 37.1.7 压力渗透载荷 | 37.1.6 User-defined interfacial constitutive behavior | [pt09ch37s01aus170.md](./chs/pt09ch37s01aus170.md) | [pt09ch37s01aus170.md](./eng/pt09ch37s01aus170.md) |
| 37.1.6 用户定义的界面本构行为 | 37.1.7 Pressure penetration loading | [pt09ch37s01aus171.md](./chs/pt09ch37s01aus171.md) | [pt09ch37s01aus171.md](./eng/pt09ch37s01aus171.md) |
| 37.1.8 脱粘表面的相互作用 | 37.1.8 Interaction of debonded surfaces | [pt09ch37s01aus172.md](./chs/pt09ch37s01aus172.md) | [pt09ch37s01aus172.md](./eng/pt09ch37s01aus172.md) |
| 37.1.9 可断裂粘结 | 37.1.9 Breakable bonds | [pt09ch37s01aus173.md](./chs/pt09ch37s01aus173.md) | [pt09ch37s01aus173.md](./eng/pt09ch37s01aus173.md) |
| 37.2 Thermal contact properties | 37.2 Thermal contact properties | [pt09ch37s02.md](./chs/pt09ch37s02.md) | [pt09ch37s02.md](./eng/pt09ch37s02.md) |
| 37.2.1 热接触属性 | 37.2.1 Thermal contact properties | [pt09ch37s02aus174.md](./chs/pt09ch37s02aus174.md) | [pt09ch37s02aus174.md](./eng/pt09ch37s02aus174.md) |
| 37.3 Electrical contact properties | 37.3 Electrical contact properties | [pt09ch37s03.md](./chs/pt09ch37s03.md) | [pt09ch37s03.md](./eng/pt09ch37s03.md) |
| 37.3.1 电气接触属性 | 37.3.1 Electrical contact properties | [pt09ch37s03aus175.md](./chs/pt09ch37s03aus175.md) | [pt09ch37s03aus175.md](./eng/pt09ch37s03aus175.md) |
| 37.4 Pore fluid contact properties | 37.4 Pore fluid contact properties | [pt09ch37s04.md](./chs/pt09ch37s04.md) | [pt09ch37s04.md](./eng/pt09ch37s04.md) |
| 37.4.1 孔隙流体接触属性 | 37.4.1 Pore fluid contact properties | [pt09ch37s04aus176.md](./chs/pt09ch37s04aus176.md) | [pt09ch37s04aus176.md](./eng/pt09ch37s04aus176.md) |
| 38 Contact Formulations and Numerical Methods | 38 Contact Formulations and Numerical Methods | [pt09ch38.md](./chs/pt09ch38.md) | [pt09ch38.md](./eng/pt09ch38.md) |
| 38.1 Contact formulations and numerical methods in Abaqus/Standard | 38.1 Contact formulations and numerical methods in Abaqus/Standard | [pt09ch38s01.md](./chs/pt09ch38s01.md) | [pt09ch38s01.md](./eng/pt09ch38s01.md) |
| 38.1.1 Abaqus/Standard中的接触公式 | 38.1.1 Contact formulations in Abaqus/Standard | [pt09ch38s01aus177.md](./chs/pt09ch38s01aus177.md) | [pt09ch38s01aus177.md](./eng/pt09ch38s01aus177.md) |
| 38.1.2 Abaqus/Standard中接触约束施加方法 | 38.1.2 Contact constraint enforcement methods in Abaqus/Standard | [pt09ch38s01aus178.md](./chs/pt09ch38s01aus178.md) | [pt09ch38s01aus178.md](./eng/pt09ch38s01aus178.md) |
| 38.1.3 Abaqus/Standard中接触表面平滑化 | 38.1.3 Smoothing contact surfaces in Abaqus/Standard | [pt09ch38s01aus179.md](./chs/pt09ch38s01aus179.md) | [pt09ch38s01aus179.md](./eng/pt09ch38s01aus179.md) |
| 38.2 Contact formulations and numerical methods in Abaqus/Explicit | 38.2 Contact formulations and numerical methods in Abaqus/Explicit | [pt09ch38s02.md](./chs/pt09ch38s02.md) | [pt09ch38s02.md](./eng/pt09ch38s02.md) |
| 38.2.1 Abaqus/Explicit中通用接触的接触公式 | 38.2.1 Contact formulation for general contact in Abaqus/Explicit | [pt09ch38s02aus180.md](./chs/pt09ch38s02aus180.md) | [pt09ch38s02aus180.md](./eng/pt09ch38s02aus180.md) |
| 38.2.2 Abaqus/Explicit中接触对的接触公式 | 38.2.2 Contact formulations for contact pairs in Abaqus/Explicit | [pt09ch38s02aus181.md](./chs/pt09ch38s02aus181.md) | [pt09ch38s02aus181.md](./eng/pt09ch38s02aus181.md) |
| 38.2.3 Abaqus/Explicit中接触约束施加方法 | 38.2.3 Contact constraint enforcement methods in Abaqus/Explicit | [pt09ch38s02aus182.md](./chs/pt09ch38s02aus182.md) | [pt09ch38s02aus182.md](./eng/pt09ch38s02aus182.md) |
| 39 Contact Difficulties and Diagnostics | 39 Contact Difficulties and Diagnostics | [pt09ch39.md](./chs/pt09ch39.md) | [pt09ch39.md](./eng/pt09ch39.md) |
| 39.1 Resolving contact difficulties in Abaqus/Standard | 39.1 Resolving contact difficulties in Abaqus/Standard | [pt09ch39s01.md](./chs/pt09ch39s01.md) | [pt09ch39s01.md](./eng/pt09ch39s01.md) |
| 39.1.1 Abaqus/Standard分析中的接触诊断 | 39.1.1 Contact diagnostics in an Abaqus/Standard analysis | [pt09ch39s01aus183.md](./chs/pt09ch39s01aus183.md) | [pt09ch39s01aus183.md](./eng/pt09ch39s01aus183.md) |
| 39.1.2 Abaqus/Standard中接触建模的常见困难 | 39.1.2 Common difficulties associated with contact modeling in Abaqus/Standard | [pt09ch39s01aus184.md](./chs/pt09ch39s01aus184.md) | [pt09ch39s01aus184.md](./eng/pt09ch39s01aus184.md) |
| 39.2 Resolving contact difficulties in Abaqus/Explicit | 39.2 Resolving contact difficulties in Abaqus/Explicit | [pt09ch39s02.md](./chs/pt09ch39s02.md) | [pt09ch39s02.md](./eng/pt09ch39s02.md) |
| 39.2.1 Abaqus/Explicit分析中的接触诊断 | 39.2.1 Contact diagnostics in an Abaqus/Explicit analysis | [pt09ch39s02aus185.md](./chs/pt09ch39s02aus185.md) | [pt09ch39s02aus185.md](./eng/pt09ch39s02aus185.md) |
| 39.2.2 Abaqus/Explicit中使用接触对的接触建模的常见困难 | 39.2.2 Common difficulties associated with contact modeling using contact pairs in Abaqus/Explicit | [pt09ch39s02aus186.md](./chs/pt09ch39s02aus186.md) | [pt09ch39s02aus186.md](./eng/pt09ch39s02aus186.md) |
| 40 Contact Elements in Abaqus/Standard | 40 Contact Elements in Abaqus/Standard | [pt09ch40.md](./chs/pt09ch40.md) | [pt09ch40.md](./eng/pt09ch40.md) |
| 40.1 Contact modeling with elements | 40.1 Contact modeling with elements | [pt09ch40s01.md](./chs/pt09ch40s01.md) | [pt09ch40s01.md](./eng/pt09ch40s01.md) |
| 40.1.1 Contact modeling with elements | 40.1.1 Contact modeling with elements | [pt09ch40s01abo34.md](./chs/pt09ch40s01abo34.md) | [pt09ch40s01abo34.md](./eng/pt09ch40s01abo34.md) |
| 40.2 Gap contact elements | 40.2 Gap contact elements | [pt09ch40s02.md](./chs/pt09ch40s02.md) | [pt09ch40s02.md](./eng/pt09ch40s02.md) |
| 40.2.2 间隙单元库 | 40.2.2 Gap element library | [pt09ch40s02ael49.md](./chs/pt09ch40s02ael49.md) | [pt09ch40s02ael49.md](./eng/pt09ch40s02ael49.md) |
| 40.2.1 间隙接触单元 | 40.2.1 Gap contact elements | [pt09ch40s02alm64.md](./chs/pt09ch40s02alm64.md) | [pt09ch40s02alm64.md](./eng/pt09ch40s02alm64.md) |
| 40.3 Tube-to-tube contact elements | 40.3 Tube-to-tube contact elements | [pt09ch40s03.md](./chs/pt09ch40s03.md) | [pt09ch40s03.md](./eng/pt09ch40s03.md) |
| 40.3.2 管对管接触单元库 | 40.3.2 Tube-to-tube contact element library | [pt09ch40s03ael50.md](./chs/pt09ch40s03ael50.md) | [pt09ch40s03ael50.md](./eng/pt09ch40s03ael50.md) |
| 40.3.1 管对管接触单元 | 40.3.1 Tube-to-tube contact elements | [pt09ch40s03alm65.md](./chs/pt09ch40s03alm65.md) | [pt09ch40s03alm65.md](./eng/pt09ch40s03alm65.md) |
| 40.4 Slide line contact elements | 40.4 Slide line contact elements | [pt09ch40s04.md](./chs/pt09ch40s04.md) | [pt09ch40s04.md](./eng/pt09ch40s04.md) |
| 40.5.2 轴对称刚性表面接触单元库 | 40.4.2 Axisymmetric slide line element library | [pt09ch40s04ael51.md](./chs/pt09ch40s04ael51.md) | [pt09ch40s04ael51.md](./eng/pt09ch40s04ael51.md) |
| 40.5.1 刚性表面接触单元 | 40.4.1 Slide line contact elements | [pt09ch40s04alm66.md](./chs/pt09ch40s04alm66.md) | [pt09ch40s04alm66.md](./eng/pt09ch40s04alm66.md) |
| 40.5 Rigid surface contact elements | 40.5 Rigid surface contact elements | [pt09ch40s05.md](./chs/pt09ch40s05.md) | [pt09ch40s05.md](./eng/pt09ch40s05.md) |
| 37.1.4 接触阻塞 | 40.5.2 Axisymmetric rigid surface contact element library | [pt09ch40s05ael52.md](./chs/pt09ch40s05ael52.md) | [pt09ch40s05ael52.md](./eng/pt09ch40s05ael52.md) |
| 37.1.5 摩擦行为 | 40.5.1 Rigid surface contact elements | [pt09ch40s05alm67.md](./chs/pt09ch40s05alm67.md) | [pt09ch40s05alm67.md](./eng/pt09ch40s05alm67.md) |
| 41 Defining Cavity Radiation in Abaqus/Standard | 41 Defining Cavity Radiation in Abaqus/Standard | [pt09ch41.md](./chs/pt09ch41.md) | [pt09ch41.md](./eng/pt09ch41.md) |
| 41.1 Defining cavity radiation | 41.1 Defining cavity radiation | [pt09ch41s01.md](./chs/pt09ch41s01.md) | [pt09ch41s01.md](./eng/pt09ch41s01.md) |
| 41.1.1 空腔辐射 | 41.1.1 Cavity radiation | [pt09ch41s01aus187.md](./chs/pt09ch41s01aus187.md) | [pt09ch41s01aus187.md](./eng/pt09ch41s01aus187.md) |

### PT10
*Output Variable and Element Indexes*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| Output Variable and Element Indexes | Output Variable and Element Indexes | [pt10.md](./chs/pt10.md) | [pt10.md](./eng/pt10.md) |
| Abaqus/Standard Element Index | Abaqus/Standard Element Index | [pt10eli01.md](./chs/pt10eli01.md) | [pt10eli01.md](./eng/pt10eli01.md) |
| Abaqus/Explicit Element Index | Abaqus/Explicit Element Index | [pt10eli02.md](./chs/pt10eli02.md) | [pt10eli02.md](./eng/pt10eli02.md) |
| Abaqus/CFD Element Index | Abaqus/CFD Element Index | [pt10eli03.md](./chs/pt10eli03.md) | [pt10eli03.md](./eng/pt10eli03.md) |
| Abaqus/Standard Output Variable Index | Abaqus/Standard Output Variable Index | [pt10otv01.md](./chs/pt10otv01.md) | [pt10otv01.md](./eng/pt10otv01.md) |
| Abaqus/Explicit Output Variable Index | Abaqus/Explicit Output Variable Index | [pt10otv02.md](./chs/pt10otv02.md) | [pt10otv02.md](./eng/pt10otv02.md) |
| Abaqus/CFD Output Variable Index | Abaqus/CFD Output Variable Index | [pt10otv03.md](./chs/pt10otv03.md) | [pt10otv03.md](./eng/pt10otv03.md) |

---

## 资源文件 / Resource Files

图片资源位于 `graphics/` 目录。

---

## 版权声明 / Copyright Notice

本翻译仅供学习研究使用，原文档版权归 Dassault Systèmes Simulia Corp. 所有。
This translation is for study and research purposes only. Original documentation copyright Dassault Systèmes Simulia Corp.