# Abaqus Verification Guide (6.14)

## 文档索引 / Documentation Index

本手册为 ABAQUS 6.14 Abaqus Verification Guide 的中文翻译版本。

**来源 / Source:** D:\SIMULIA\Documentation\docs\v6.14\books\gsa\

---

## 双语目录对照 / Bilingual Table of Contents

### CH01
*1 单元验证*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 1 单元验证 | 1 Element Verification | [ch01.md](./chs/ch01.md) | [ch01.md](./eng/ch01.md) |
| 1.1 概述 | 1.1 Overview | [ch01s01.md](./chs/ch01s01.md) | [ch01s01.md](./eng/ch01s01.md) |
| 1.1.1 单元验证测试：概述 | 1.1.1 Element verification tests: overview | [ch01s01abo01.md](./chs/ch01s01abo01.md) | [ch01s01abo01.md](./eng/ch01s01abo01.md) |
| 1.2 特征值测试 | 1.2 Eigenvalue tests | [ch01s02.md](./chs/ch01s02.md) | [ch01s02.md](./eng/ch01s02.md) |
| 1.2.1 单无约束单元的特征值提取 | 1.2.1 Eigenvalue extraction for single unconstrained elements | [ch01s02abv01.md](./chs/ch01s02abv01.md) | [ch01s02abv01.md](./eng/ch01s02abv01.md) |
| 1.2.2 无约束单元分片的特征值提取 | 1.2.2 Eigenvalue extraction for unconstrained patches of elements | [ch01s02abv02.md](./chs/ch01s02abv02.md) | [ch01s02abv02.md](./eng/ch01s02abv02.md) |
| 1.2.3 声学模态 | 1.2.3 Acoustic modes | [ch01s02abv03.md](./chs/ch01s02abv03.md) | [ch01s02abv03.md](./eng/ch01s02abv03.md) |
| 1.3 简单载荷测试 | 1.3 Simple load tests | [ch01s03.md](./chs/ch01s03.md) | [ch01s03.md](./eng/ch01s03.md) |
| 1.3.1 平面应力、平面应变、膜和壳单元的膜载荷 | 1.3.1 Membrane loading of plane stress, plane strain, membrane, and shell elements | [ch01s03abv04.md](./chs/ch01s03abv04.md) | [ch01s03abv04.md](./eng/ch01s03abv04.md) |
| 1.3.2 具有边界平面相对运动的广义平面应变单元 | 1.3.2 Generalized plane strain elements with relative motion of bounding planes | [ch01s03abv05.md](./chs/ch01s03abv05.md) | [ch01s03abv05.md](./eng/ch01s03abv05.md) |
| 1.3.3 三维实体单元 | 1.3.3 Three-dimensional solid elements | [ch01s03abv06.md](./chs/ch01s03abv06.md) | [ch01s03abv06.md](./eng/ch01s03abv06.md) |
| 1.3.4 轴对称实体单元 | 1.3.4 Axisymmetric solid elements | [ch01s03abv07.md](./chs/ch01s03abv07.md) | [ch01s03abv07.md](./eng/ch01s03abv07.md) |
| 1.3.6 圆柱坐标单元 | 1.3.5 Axisymmetric solid elements with twist | [ch01s03abv08.md](./chs/ch01s03abv08.md) | [ch01s03abv08.md](./eng/ch01s03abv08.md) |
| 1.3.6 圆柱单元 | 1.3.6 Cylindrical elements | [ch01s03abv09.md](./chs/ch01s03abv09.md) | [ch01s03abv09.md](./eng/ch01s03abv09.md) |
| 1.3.7 压电单元的载荷 | 1.3.7 Loading of piezoelectric elements | [ch01s03abv10.md](./chs/ch01s03abv10.md) | [ch01s03abv10.md](./eng/ch01s03abv10.md) |
| 1.3.5 带扭转的轴对称实体单元 | 1.3.8 Love-Kirchhoff beams and shells | [ch01s03abv11.md](./chs/ch01s03abv11.md) | [ch01s03abv11.md](./eng/ch01s03abv11.md) |
| 1.3.9 剪切柔性梁和壳：I | 1.3.9 Shear flexible beams and shells: I | [ch01s03abv12.md](./chs/ch01s03abv12.md) | [ch01s03abv12.md](./eng/ch01s03abv12.md) |
| 1.3.11 梁和壳的初始曲率 | 1.3.10 Shear flexible beams and shells: II | [ch01s03abv13.md](./chs/ch01s03abv13.md) | [ch01s03abv13.md](./eng/ch01s03abv13.md) |
| 1.3.11 梁和壳的初始曲率 | 1.3.11 Initial curvature of beams and shells | [ch01s03abv14.md](./chs/ch01s03abv14.md) | [ch01s03abv14.md](./eng/ch01s03abv14.md) |
| 1.3.10 剪切柔性梁和壳：II | 1.3.12 Normal definitions of beams and shells | [ch01s03abv15.md](./chs/ch01s03abv15.md) | [ch01s03abv15.md](./eng/ch01s03abv15.md) |
| 1.3.12 梁和壳的法线定义 | 1.3.13 Constant curvature test for shells | [ch01s03abv16.md](./chs/ch01s03abv16.md) | [ch01s03abv16.md](./eng/ch01s03abv16.md) |
| 1.3.16 悬臂夹芯梁：剪切柔性壳 | 1.3.14 Verification of section forces for shells | [ch01s03abv17.md](./chs/ch01s03abv17.md) | [ch01s03abv17.md](./eng/ch01s03abv17.md) |
| 1.3.15 复合壳截面 | 1.3.15 Composite shell sections | [ch01s03abv18.md](./chs/ch01s03abv18.md) | [ch01s03abv18.md](./eng/ch01s03abv18.md) |
| 1.3.17 圆柱壳的热应力 | 1.3.16 Cantilever sandwich beam: shear flexible shells | [ch01s03abv19.md](./chs/ch01s03abv19.md) | [ch01s03abv19.md](./eng/ch01s03abv19.md) |
| 1.3.15 复合壳截面 | 1.3.17 Thermal stress in a cylindrical shell | [ch01s03abv20.md](./chs/ch01s03abv20.md) | [ch01s03abv20.md](./eng/ch01s03abv20.md) |
| 1.3.18 变厚度壳和膜单元 | 1.3.18 Variable thickness shells and membranes | [ch01s03abv21.md](./chs/ch01s03abv21.md) | [ch01s03abv21.md](./eng/ch01s03abv21.md) |
| 1.3.22 梁单元和截面类型的验证 | 1.3.19 Shell offset | [ch01s03abv22.md](./chs/ch01s03abv22.md) | [ch01s03abv22.md](./eng/ch01s03abv22.md) |
| 1.3.23 梁附加惯性 | 1.3.20 Axisymmetric membrane elements | [ch01s03abv23.md](./chs/ch01s03abv23.md) | [ch01s03abv23.md](./eng/ch01s03abv23.md) |
| 1.3.24 梁流体惯性 | 1.3.21 Cylindrical membrane elements | [ch01s03abv24.md](./chs/ch01s03abv24.md) | [ch01s03abv24.md](./eng/ch01s03abv24.md) |
| 1.3.25 端点力矩梁 | 1.3.22 Verification of beam elements and section types | [ch01s03abv25.md](./chs/ch01s03abv25.md) | [ch01s03abv25.md](./eng/ch01s03abv25.md) |
| 1.3.23 梁的附加惯性 | 1.3.23 Beam added inertia | [ch01s03abv26.md](./chs/ch01s03abv26.md) | [ch01s03abv26.md](./eng/ch01s03abv26.md) |
| 1.3.27 梁运动学简单测试 | 1.3.24 Beam fluid inertia | [ch01s03abv27.md](./chs/ch01s03abv27.md) | [ch01s03abv27.md](./eng/ch01s03abv27.md) |
| 1.3.24 梁的流体惯性 | 1.3.25 Beam with end moment | [ch01s03abv28.md](./chs/ch01s03abv28.md) | [ch01s03abv28.md](./eng/ch01s03abv28.md) |
| 1.3.26 深梁的弯曲 | 1.3.26 Flexure of a deep beam | [ch01s03abv29.md](./chs/ch01s03abv29.md) | [ch01s03abv29.md](./eng/ch01s03abv29.md) |
| 1.3.24 梁流体惯性 | 1.3.27 Simple tests of beam kinematics | [ch01s03abv30.md](./chs/ch01s03abv30.md) | [ch01s03abv30.md](./eng/ch01s03abv30.md) |
| 1.3.30 框架单元弹性行为的验证 | 1.3.28 Tensile test | [ch01s03abv31.md](./chs/ch01s03abv31.md) | [ch01s03abv31.md](./eng/ch01s03abv31.md) |
| 1.3.28 拉伸测试 | 1.3.29 Simple shear | [ch01s03abv32.md](./chs/ch01s03abv32.md) | [ch01s03abv32.md](./eng/ch01s03abv32.md) |
| 1.3.27 梁运动学的简单测试 | 1.3.30 Verification of the elastic behavior of frame elements | [ch01s03abv33.md](./chs/ch01s03abv33.md) | [ch01s03abv33.md](./eng/ch01s03abv33.md) |
| 1.3.32 三杆桁架 | 1.3.31 Verification of the plastic behavior of frame elements | [ch01s03abv34.md](./chs/ch01s03abv34.md) | [ch01s03abv34.md](./eng/ch01s03abv34.md) |
| 1.3.31 框架单元塑性行为的验证 | 1.3.32 Three-bar truss | [ch01s03abv35.md](./chs/ch01s03abv35.md) | [ch01s03abv35.md](./eng/ch01s03abv35.md) |
| 1.3.33 圆柱的纯弯曲：CAXA 单元 | 1.3.33 Pure bending of a cylinder: CAXA elements | [ch01s03abv36.md](./chs/ch01s03abv36.md) | [ch01s03abv36.md](./eng/ch01s03abv36.md) |
| 1.3.34 承受非对称温度场的圆柱：CAXA 单元 | 1.3.34 Cylinder subjected to an asymmetric temperature field: CAXA elements | [ch01s03abv37.md](./chs/ch01s03abv37.md) | [ch01s03abv37.md](./eng/ch01s03abv37.md) |
| 1.3.35 承受非对称压力载荷的圆柱：CAXA 单元 | 1.3.35 Cylinder subjected to asymmetric pressure loads: CAXA elements | [ch01s03abv38.md](./chs/ch01s03abv38.md) | [ch01s03abv38.md](./eng/ch01s03abv38.md) |
| 1.3.36 承受非对称孔隙压力场的圆柱：CAXA 单元 | 1.3.36 Cylinder subjected to an asymmetric pore pressure field: CAXA elements | [ch01s03abv39.md](./chs/ch01s03abv39.md) | [ch01s03abv39.md](./eng/ch01s03abv39.md) |
| 1.3.37 使用 CAXA 和 SAXA 单元的模态动态和瞬态动态分析 | 1.3.37 Modal dynamic and transient dynamic analysis with CAXA and SAXA elements | [ch01s03abv40.md](./chs/ch01s03abv40.md) | [ch01s03abv40.md](./eng/ch01s03abv40.md) |
| 1.3.38 热电元件的简单载荷测试 | 1.3.38 Simple load tests for thermal-electrical elements | [ch01s03abv41.md](./chs/ch01s03abv41.md) | [ch01s03abv41.md](./eng/ch01s03abv41.md) |
| 1.3.39 静水压流体元件 | 1.3.39 Hydrostatic fluid elements | [ch01s03abv42.md](./chs/ch01s03abv42.md) | [ch01s03abv42.md](./eng/ch01s03abv42.md) |
| 1.3.40 流体连接元件 | 1.3.40 Fluid link element | [ch01s03abv43.md](./chs/ch01s03abv43.md) | [ch01s03abv43.md](./eng/ch01s03abv43.md) |
| 1.3.42 基于表面的压力渗透 | 1.3.41 Temperature-dependent film condition | [ch01s03abv44.md](./chs/ch01s03abv44.md) | [ch01s03abv44.md](./eng/ch01s03abv44.md) |
| 1.3.41 温度依赖的薄膜条件 | 1.3.42 Surface-based pressure penetration | [ch01s03abv45.md](./chs/ch01s03abv45.md) | [ch01s03abv45.md](./eng/ch01s03abv45.md) |
| 1.3.46 直接求解稳态动力学分析的科里奥利载荷 | 1.3.43 Gasket behavior verification | [ch01s03abv46.md](./chs/ch01s03abv46.md) | [ch01s03abv46.md](./eng/ch01s03abv46.md) |
| 1.3.44 垫片元件装配 | 1.3.44 Gasket element assembly | [ch01s03abv47.md](./chs/ch01s03abv47.md) | [ch01s03abv47.md](./eng/ch01s03abv47.md) |
| 1.3.43 垫片行为验证 | 1.3.45 Cohesive elements | [ch01s03abv48.md](./chs/ch01s03abv48.md) | [ch01s03abv48.md](./eng/ch01s03abv48.md) |
| 1.3.47 管-土相互作用元件 | 1.3.46 Coriolis loading for direct-solution steady-state dynamic analysis | [ch01s03abv49.md](./chs/ch01s03abv49.md) | [ch01s03abv49.md](./eng/ch01s03abv49.md) |
| 1.3.45 内聚元件 | 1.3.47 Pipe-soil interaction elements | [ch01s03abv50.md](./chs/ch01s03abv50.md) | [ch01s03abv50.md](./eng/ch01s03abv50.md) |
| 1.4 单元载荷选项 | 1.4 Element loading options | [ch01s04.md](./chs/ch01s04.md) | [ch01s04.md](./eng/ch01s04.md) |
| 1.4.1 连续体应力/位移单元 | 1.4.1 Continuum stress/displacement elements | [ch01s04abv51.md](./chs/ch01s04abv51.md) | [ch01s04abv51.md](./eng/ch01s04abv51.md) |
| 1.4.4 壳单元、膜单元和桁架单元应力/位移 | 1.4.2 Beam stress/displacement elements | [ch01s04abv52.md](./chs/ch01s04abv52.md) | [ch01s04abv52.md](./eng/ch01s04abv52.md) |
| 1.4.5 内聚力元件载荷验证 | 1.4.3 Pipe stress/displacement elements | [ch01s04abv53.md](./chs/ch01s04abv53.md) | [ch01s04abv53.md](./eng/ch01s04abv53.md) |
| 1.4.4 壳单元、膜单元和桁架单元应力/位移 | 1.4.4 Shell, membrane, and truss stress/displacement elements | [ch01s04abv54.md](./chs/ch01s04abv54.md) | [ch01s04abv54.md](./eng/ch01s04abv54.md) |
| 1.4.5 内聚力元件载荷验证 | 1.4.5 Cohesive element load verification | [ch01s04abv55.md](./chs/ch01s04abv55.md) | [ch01s04abv55.md](./eng/ch01s04abv55.md) |
| 1.4.6 ELBOW（弯头）元件 | 1.4.6 ELBOW elements | [ch01s04abv56.md](./chs/ch01s04abv56.md) | [ch01s04abv56.md](./eng/ch01s04abv56.md) |
| 1.4.7 连续体孔隙压力元件 | 1.4.7 Continuum pore pressure elements | [ch01s04abv57.md](./chs/ch01s04abv57.md) | [ch01s04abv57.md](./eng/ch01s04abv57.md) |
| 1.4.8 连续体和壳单元热传导元件 | 1.4.8 Continuum and shell heat transfer elements | [ch01s04abv58.md](./chs/ch01s04abv58.md) | [ch01s04abv58.md](./eng/ch01s04abv58.md) |
| 1.4.9 耦合温度-位移单元 | 1.4.9 Coupled temperature-displacement elements | [ch01s04abv59.md](./chs/ch01s04abv59.md) | [ch01s04abv59.md](./eng/ch01s04abv59.md) |
| 1.4.10 耦合热-电-结构单元 | 1.4.10 Coupled thermal-electrical-structural elements | [ch01s04abv60.md](./chs/ch01s04abv60.md) | [ch01s04abv60.md](./eng/ch01s04abv60.md) |
| 1.4.11 压电单元 | 1.4.11 Piezoelectric elements | [ch01s04abv61.md](./chs/ch01s04abv61.md) | [ch01s04abv61.md](./eng/ch01s04abv61.md) |
| 1.4.12 连续体质量扩散单元 | 1.4.12 Continuum mass diffusion elements | [ch01s04abv62.md](./chs/ch01s04abv62.md) | [ch01s04abv62.md](./eng/ch01s04abv62.md) |
| 1.4.13 热电单元 | 1.4.13 Thermal-electrical elements | [ch01s04abv63.md](./chs/ch01s04abv63.md) | [ch01s04abv63.md](./eng/ch01s04abv63.md) |
| 1.4.14 刚性单元 | 1.4.14 Rigid elements | [ch01s04abv64.md](./chs/ch01s04abv64.md) | [ch01s04abv64.md](./eng/ch01s04abv64.md) |
| 1.4.15 质量和转动惯量单元 | 1.4.15 Mass and rotary inertia elements | [ch01s04abv65.md](./chs/ch01s04abv65.md) | [ch01s04abv65.md](./eng/ch01s04abv65.md) |
| 1.4.16 Abaqus/Explicit单元载荷验证 | 1.4.16 Abaqus/Explicit element loading verification | [ch01s04abv66.md](./chs/ch01s04abv66.md) | [ch01s04abv66.md](./eng/ch01s04abv66.md) |
| 1.4.17 入射波载荷 | 1.4.17 Incident wave loading | [ch01s04abv67.md](./chs/ch01s04abv67.md) | [ch01s04abv67.md](./eng/ch01s04abv67.md) |
| 1.4.18 分布牵引和边缘载荷 | 1.4.18 Distributed traction and edge loads | [ch01s04abv68.md](./chs/ch01s04abv68.md) | [ch01s04abv68.md](./eng/ch01s04abv68.md) |
| 1.5 分片测试 | 1.5 Patch tests | [ch01s05.md](./chs/ch01s05.md) | [ch01s05.md](./eng/ch01s05.md) |
| 1.5.1 膜片测试 | 1.5.1 Membrane patch test | [ch01s05abv69.md](./chs/ch01s05abv69.md) | [ch01s05abv69.md](./eng/ch01s05abv69.md) |
| 1.5.2 三维实体单元片测试 | 1.5.2 Patch test for three-dimensional solid elements | [ch01s05abv70.md](./chs/ch01s05abv70.md) | [ch01s05abv70.md](./eng/ch01s05abv70.md) |
| 1.5.3 圆柱单元片测试 | 1.5.3 Patch test for cylindrical elements | [ch01s05abv71.md](./chs/ch01s05abv71.md) | [ch01s05abv71.md](./eng/ch01s05abv71.md) |
| 1.5.4 轴对称单元片测试 | 1.5.4 Patch test for axisymmetric elements | [ch01s05abv72.md](./chs/ch01s05abv72.md) | [ch01s05abv72.md](./eng/ch01s05abv72.md) |
| 1.5.5 带扭曲的轴对称单元片测试 | 1.5.5 Patch test for axisymmetric elements with twist | [ch01s05abv73.md](./chs/ch01s05abv73.md) | [ch01s05abv73.md](./eng/ch01s05abv73.md) |
| 1.5.6 板弯曲片测试 | 1.5.6 Patch test for plate bending | [ch01s05abv74.md](./chs/ch01s05abv74.md) | [ch01s05abv74.md](./eng/ch01s05abv74.md) |
| 1.5.7 梁单元片测试 | 1.5.7 Patch test for beam elements | [ch01s05abv75.md](./chs/ch01s05abv75.md) | [ch01s05abv75.md](./eng/ch01s05abv75.md) |
| 1.5.8 热传导单元片测试 | 1.5.8 Patch test for heat transfer elements | [ch01s05abv76.md](./chs/ch01s05abv76.md) | [ch01s05abv76.md](./eng/ch01s05abv76.md) |
| 1.5.9 热电单元片测试 | 1.5.9 Patch test for thermal-electrical elements | [ch01s05abv77.md](./chs/ch01s05abv77.md) | [ch01s05abv77.md](./eng/ch01s05abv77.md) |
| 1.5.10 声学单元片测试 | 1.5.10 Patch test for acoustic elements | [ch01s05abv78.md](./chs/ch01s05abv78.md) | [ch01s05abv78.md](./eng/ch01s05abv78.md) |
| 1.6 接触测试 | 1.6 Contact tests | [ch01s06.md](./chs/ch01s06.md) | [ch01s06.md](./eng/ch01s06.md) |
| 1.6.22 对称平面处接触表面法向量的调整 | 1.6.22 Adjusting contact surface normals at symmetry planes | [ch01s06abv100.md](./chs/ch01s06abv100.md) | [ch01s06abv100.md](./eng/ch01s06abv100.md) |
| 1.6.23 接触控制 | 1.6.23 Contact controls | [ch01s06abv101.md](./chs/ch01s06abv101.md) | [ch01s06abv101.md](./eng/ch01s06abv101.md) |
| 1.6.24 解析刚性表面的接触搜索 | 1.6.24 Contact searching for analytical rigid surfaces | [ch01s06abv102.md](./chs/ch01s06abv102.md) | [ch01s06abv102.md](./eng/ch01s06abv102.md) |
| 1.6.25 使用惩罚法的多表面接触 | 1.6.25 Multiple surface contact with penalty method | [ch01s06abv103.md](./chs/ch01s06abv103.md) | [ch01s06abv103.md](./eng/ch01s06abv103.md) |
| 1.6.26 有限滑动可变形表面的自动接触片算法 | 1.6.26 Automated contact patch algorithm for finite-sliding deformable surfaces | [ch01s06abv104.md](./chs/ch01s06abv104.md) | [ch01s06abv104.md](./eng/ch01s06abv104.md) |
| 1.6.27 有限滑动接触的表面-表面方法 | 1.6.27 Surface-to-surface approach for finite-sliding contact | [ch01s06abv105.md](./chs/ch01s06abv105.md) | [ch01s06abv105.md](./eng/ch01s06abv105.md) |
| 1.6.28 表面-表面接触的表面平滑技术 | 1.6.28 Surface smoothing for surface-to-surface contact | [ch01s06abv106.md](./chs/ch01s06abv106.md) | [ch01s06abv106.md](./eng/ch01s06abv106.md) |
| 1.6.29 Abaqus/Standard中的通用接触 | 1.6.29 General contact in Abaqus/Standard | [ch01s06abv107.md](./chs/ch01s06abv107.md) | [ch01s06abv107.md](./eng/ch01s06abv107.md) |
| 1.6.2 耦合温度-位移曲面间的小滑动接触 | 1.6.1 Small-sliding contact between stress/displacement elements | [ch01s06abv79.md](./chs/ch01s06abv79.md) | [ch01s06abv79.md](./eng/ch01s06abv79.md) |
| 1.6.1 应力/位移单元间的小滑动接触 | 1.6.2 Small-sliding contact between coupled temperature-displacement surfaces | [ch01s06abv80.md](./chs/ch01s06abv80.md) | [ch01s06abv80.md](./eng/ch01s06abv80.md) |
| 1.6.3 耦合热-电-结构曲面间的小滑动接触 | 1.6.3 Small-sliding contact between coupled thermal-electrical-structural surfaces | [ch01s06abv81.md](./chs/ch01s06abv81.md) | [ch01s06abv81.md](./eng/ch01s06abv81.md) |
| 1.6.5 应力/位移单元间的有限滑动接触 | 1.6.4 Small-sliding contact between coupled pore pressure-displacement elements | [ch01s06abv82.md](./chs/ch01s06abv82.md) | [ch01s06abv82.md](./eng/ch01s06abv82.md) |
| 1.6.7 可变形体与网格化刚性表面间的有限滑动接触 | 1.6.5 Finite-sliding contact between stress/displacement elements | [ch01s06abv83.md](./chs/ch01s06abv83.md) | [ch01s06abv83.md](./eng/ch01s06abv83.md) |
| 1.6.4 耦合孔隙压力-位移单元间的小滑动接触 | 1.6.6 Finite-sliding contact between a deformable body and a rigid surface | [ch01s06abv84.md](./chs/ch01s06abv84.md) | [ch01s06abv84.md](./eng/ch01s06abv84.md) |
| 1.6.6 可变形体与刚性表面间的有限滑动接触 | 1.6.7 Finite-sliding contact between a deformable body and a meshed rigid surface | [ch01s06abv85.md](./chs/ch01s06abv85.md) | [ch01s06abv85.md](./eng/ch01s06abv85.md) |
| 1.6.9 耦合热-电-结构单元间的有限滑动接触 | 1.6.8 Finite-sliding contact between coupled temperature-displacement elements | [ch01s06abv86.md](./chs/ch01s06abv86.md) | [ch01s06abv86.md](./eng/ch01s06abv86.md) |
| 1.6.8 耦合温度-位移单元间的有限滑动接触 | 1.6.9 Finite-sliding contact between coupled thermal-electrical-structural elements | [ch01s06abv87.md](./chs/ch01s06abv87.md) | [ch01s06abv87.md](./eng/ch01s06abv87.md) |
| 1.6.10 耦合孔隙压力-位移单元间的有限滑动接触 | 1.6.10 Finite-sliding contact between coupled pore pressure-displacement elements | [ch01s06abv88.md](./chs/ch01s06abv88.md) | [ch01s06abv88.md](./eng/ch01s06abv88.md) |
| 1.6.11 钢板轧制 | 1.6.11 Rolling of steel plate | [ch01s06abv89.md](./chs/ch01s06abv89.md) | [ch01s06abv89.md](./eng/ch01s06abv89.md) |
| 1.6.12 梁撞击圆柱体 | 1.6.12 Beam impact on cylinder | [ch01s06abv90.md](./chs/ch01s06abv90.md) | [ch01s06abv90.md](./eng/ch01s06abv90.md) |
| 1.6.13 具有时间相关规定干涉值的接触 | 1.6.13 Contact with time-dependent prescribed interference values | [ch01s06abv91.md](./chs/ch01s06abv91.md) | [ch01s06abv91.md](./eng/ch01s06abv91.md) |
| 1.6.14 离散点之间的接触 | 1.6.14 Contact between discrete points | [ch01s06abv92.md](./chs/ch01s06abv92.md) | [ch01s06abv92.md](./eng/ch01s06abv92.md) |
| 1.6.16 表面接触的自动单元转换 | 1.6.15 Finite sliding between concentric cylinders—axisymmetric and CAXA models | [ch01s06abv93.md](./chs/ch01s06abv93.md) | [ch01s06abv93.md](./eng/ch01s06abv93.md) |
| 1.6.17 曲面初始过闭合的接触 | 1.6.16 Automatic element conversion for surface contact | [ch01s06abv94.md](./chs/ch01s06abv94.md) | [ch01s06abv94.md](./eng/ch01s06abv94.md) |
| 1.6.15 同心圆柱体之间的有限滑动——轴对称和CAXA模型 | 1.6.17 Contact with initial overclosure of curved surfaces | [ch01s06abv95.md](./chs/ch01s06abv95.md) | [ch01s06abv95.md](./eng/ch01s06abv95.md) |
| 1.6.19 自动表面定义和表面修整 | 1.6.18 Small-sliding contact with specified clearance or overclosure values | [ch01s06abv96.md](./chs/ch01s06abv96.md) | [ch01s06abv96.md](./eng/ch01s06abv96.md) |
| 1.6.18 具有规定间隙或过闭合值的小滑动接触 | 1.6.19 Automatic surface definition and surface trimming | [ch01s06abv97.md](./chs/ch01s06abv97.md) | [ch01s06abv97.md](./eng/ch01s06abv97.md) |
| 1.6.20 自接触有限滑动可变形表面 | 1.6.20 Self-contact of finite-sliding deformable surfaces | [ch01s06abv98.md](./chs/ch01s06abv98.md) | [ch01s06abv98.md](./eng/ch01s06abv98.md) |
| 1.6.21 接触表面扩展 | 1.6.21 Contact surface extensions | [ch01s06abv99.md](./chs/ch01s06abv99.md) | [ch01s06abv99.md](./eng/ch01s06abv99.md) |
| 1.7 界面测试 | 1.7 Interface tests | [ch01s07.md](./chs/ch01s07.md) | [ch01s07.md](./eng/ch01s07.md) |
| 1.7.1 热表面相互作用 | 1.7.1 Thermal surface interaction | [ch01s07abv108.md](./chs/ch01s07abv108.md) | [ch01s07abv108.md](./eng/ch01s07abv108.md) |
| 1.7.2 声学和结构单元的耦合 | 1.7.2 Coupling of acoustic and structural elements | [ch01s07abv109.md](./chs/ch01s07abv109.md) | [ch01s07abv109.md](./eng/ch01s07abv109.md) |
| 1.7.3 耦合热-电表面相互作用 | 1.7.3 Coupled thermal-electrical surface interaction | [ch01s07abv110.md](./chs/ch01s07abv110.md) | [ch01s07abv110.md](./eng/ch01s07abv110.md) |
| 1.7.4 Abaqus/Standard中的摩擦模型 | 1.7.4 Friction models in Abaqus/Standard | [ch01s07abv111.md](./chs/ch01s07abv111.md) | [ch01s07abv111.md](./eng/ch01s07abv111.md) |
| 1.7.5 Abaqus/Explicit中的摩擦模型 | 1.7.5 Friction models in Abaqus/Explicit | [ch01s07abv112.md](./chs/ch01s07abv112.md) | [ch01s07abv112.md](./eng/ch01s07abv112.md) |
| 1.7.6 内聚表面相互作用 | 1.7.6 Cohesive surface interaction | [ch01s07abv113.md](./chs/ch01s07abv113.md) | [ch01s07abv113.md](./eng/ch01s07abv113.md) |
| 1.8 刚体验证 | 1.8 Rigid body verification | [ch01s08.md](./chs/ch01s08.md) | [ch01s08.md](./eng/ch01s08.md) |
| 1.8.1 刚体质量属性 | 1.8.1 Rigid body mass properties | [ch01s08abv114.md](./chs/ch01s08abv114.md) | [ch01s08abv114.md](./eng/ch01s08abv114.md) |
| 1.8.2 绑定和销节点集 | 1.8.2 Tie and pin node sets | [ch01s08abv115.md](./chs/ch01s08abv115.md) | [ch01s08abv115.md](./eng/ch01s08abv115.md) |
| 1.8.3 作为MPC的刚体 | 1.8.3 Rigid body as an MPC | [ch01s08abv116.md](./chs/ch01s08abv116.md) | [ch01s08abv116.md](./eng/ch01s08abv116.md) |
| 1.8.4 刚体约束 | 1.8.4 Rigid body constraint | [ch01s08abv117.md](./chs/ch01s08abv117.md) | [ch01s08abv117.md](./eng/ch01s08abv117.md) |
| 1.8.5 在刚体中包含可变形单元类型 | 1.8.5 Including deformable element types in a rigid body | [ch01s08abv118.md](./chs/ch01s08abv118.md) | [ch01s08abv118.md](./eng/ch01s08abv118.md) |
| 1.9 连接器单元验证 | 1.9 Connector element verification | [ch01s09.md](./chs/ch01s09.md) | [ch01s09.md](./eng/ch01s09.md) |
| 1.9.1 带初始条件的阻尼自由振动 | 1.9.1 Damped free vibration with initial conditions | [ch01s09abv119.md](./chs/ch01s09abv119.md) | [ch01s09abv119.md](./eng/ch01s09abv119.md) |
| 1.9.2 阻尼弹簧-质量系统的正弦激励 | 1.9.2 Sinusoidal excitation of a damped spring-mass system | [ch01s09abv120.md](./chs/ch01s09abv120.md) | [ch01s09abv120.md](./eng/ch01s09abv120.md) |
| 1.9.3 连接器单元的多个实例 | 1.9.3 Multiple instances of connector elements | [ch01s09abv121.md](./chs/ch01s09abv121.md) | [ch01s09abv121.md](./eng/ch01s09abv121.md) |
| 1.9.4 单个连接器选项测试 | 1.9.4 Individual connector option tests | [ch01s09abv122.md](./chs/ch01s09abv122.md) | [ch01s09abv122.md](./eng/ch01s09abv122.md) |
| 1.9.5 连接器单元在扰动分析中的应用 | 1.9.5 Connector elements in perturbation analyses | [ch01s09abv123.md](./chs/ch01s09abv123.md) | [ch01s09abv123.md](./eng/ch01s09abv123.md) |
| 1.9.6 专用连接器测试 | 1.9.6 Tests for special-purpose connectors | [ch01s09abv124.md](./chs/ch01s09abv124.md) | [ch01s09abv124.md](./eng/ch01s09abv124.md) |
| 1.10 专用应力/位移单元 | 1.10 Special-purpose stress/displacement elements | [ch01s10.md](./chs/ch01s10.md) | [ch01s10.md](./eng/ch01s10.md) |
| 1.10.1 柔性关节单元 | 1.10.1 Flexible joint element | [ch01s10abv125.md](./chs/ch01s10abv125.md) | [ch01s10abv125.md](./eng/ch01s10abv125.md) |
| 1.10.2 线弹簧单元 | 1.10.2 Line spring elements | [ch01s10abv126.md](./chs/ch01s10abv126.md) | [ch01s10abv126.md](./eng/ch01s10abv126.md) |
| 1.10.3 分布耦合单元 | 1.10.3 Distributing coupling elements | [ch01s10abv127.md](./chs/ch01s10abv127.md) | [ch01s10abv127.md](./eng/ch01s10abv127.md) |
| 1.10.4 拖链单元 | 1.10.4 Drag chain elements | [ch01s10abv128.md](./chs/ch01s10abv128.md) | [ch01s10abv128.md](./eng/ch01s10abv128.md) |
| 1.11 其他测试 | 1.11 Miscellaneous tests | [ch01s11.md](./chs/ch01s11.md) | [ch01s11.md](./eng/ch01s11.md) |
| 1.11.1 Abaqus/Standard中的钢筋 | 1.11.1 Rebar in Abaqus/Standard | [ch01s11abv129.md](./chs/ch01s11abv129.md) | [ch01s11abv129.md](./eng/ch01s11abv129.md) |
| 1.11.2 Abaqus/Explicit中的钢筋 | 1.11.2 Rebar in Abaqus/Explicit | [ch01s11abv130.md](./chs/ch01s11abv130.md) | [ch01s11abv130.md](./eng/ch01s11abv130.md) |
| 1.11.3 对流单元：温度脉冲的传输 | 1.11.3 Convection elements: transport of a temperature pulse | [ch01s11abv131.md](./chs/ch01s11abv131.md) | [ch01s11abv131.md](./eng/ch01s11abv131.md) |
| 1.11.4 连续体壳：基本单元模式 | 1.11.4 Continuum shells: basic element modes | [ch01s11abv132.md](./chs/ch01s11abv132.md) | [ch01s11abv132.md](./eng/ch01s11abv132.md) |
| 1.11.5 剪切柔性壳的横向剪切 | 1.11.5 Transverse shear for shear-flexible shells | [ch01s11abv133.md](./chs/ch01s11abv133.md) | [ch01s11abv133.md](./eng/ch01s11abv133.md) |
| 1.11.6 流体连接的线性动态分析 | 1.11.6 Linear dynamic analysis with fluid link | [ch01s11abv134.md](./chs/ch01s11abv134.md) | [ch01s11abv134.md](./eng/ch01s11abv134.md) |
| 1.11.7 具有温度自由度、热容和基于节点的热载荷的刚体 | 1.11.7 Rigid bodies with temperature DOFs, heat capacitance, and nodal-based thermal loads | [ch01s11abv135.md](./chs/ch01s11abv135.md) | [ch01s11abv135.md](./eng/ch01s11abv135.md) |
| 1.11.8 无界声学区域的分析 | 1.11.8 Analysis of unbounded acoustic regions | [ch01s11abv136.md](./chs/ch01s11abv136.md) | [ch01s11abv136.md](./eng/ch01s11abv136.md) |
| 1.11.9 非结构质量验证 | 1.11.9 Nonstructural mass verification | [ch01s11abv137.md](./chs/ch01s11abv137.md) | [ch01s11abv137.md](./eng/ch01s11abv137.md) |
| 1.11.10 质量调整验证 | 1.11.10 Mass adjust verification | [ch01s11abv138.md](./chs/ch01s11abv138.md) | [ch01s11abv138.md](./eng/ch01s11abv138.md) |

### CH02
*2 材料验证*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 2 材料验证 | 2 Material Verification | [ch02.md](./chs/ch02.md) | [ch02.md](./eng/ch02.md) |
| 2.1 概述 | 2.1 Overview | [ch02s01.md](./chs/ch02s01.md) | [ch02s01.md](./eng/ch02s01.md) |
| 2.1.1 材料验证：概述 | 2.1.1 Material verification: overview | [ch02s01abo02.md](./chs/ch02s01abo02.md) | [ch02s01abo02.md](./eng/ch02s01abo02.md) |
| 2.2 力学性能 | 2.2 Mechanical properties | [ch02s02.md](./chs/ch02s02.md) | [ch02s02.md](./eng/ch02s02.md) |
| 2.2.1 弹性材料 | 2.2.1 Elastic materials | [ch02s02abv139.md](./chs/ch02s02abv139.md) | [ch02s02abv139.md](./eng/ch02s02abv139.md) |
| 2.2.2 粘弹性材料 | 2.2.2 Viscoelastic materials | [ch02s02abv140.md](./chs/ch02s02abv140.md) | [ch02s02abv140.md](./eng/ch02s02abv140.md) |
| 2.2.3 Mullins效应和永久变形 | 2.2.3 Mullins effect and permanent set | [ch02s02abv141.md](./chs/ch02s02abv141.md) | [ch02s02abv141.md](./eng/ch02s02abv141.md) |
| 2.2.4 滞回材料 | 2.2.4 Hysteretic materials | [ch02s02abv142.md](./chs/ch02s02abv142.md) | [ch02s02abv142.md](./eng/ch02s02abv142.md) |
| 2.2.5 温度依赖弹性材料 | 2.2.5 Temperature-dependent elastic materials | [ch02s02abv143.md](./chs/ch02s02abv143.md) | [ch02s02abv143.md](./eng/ch02s02abv143.md) |
| 2.2.6 场变量依赖弹性材料 | 2.2.6 Field-variable-dependent elastic materials | [ch02s02abv144.md](./chs/ch02s02abv144.md) | [ch02s02abv144.md](./eng/ch02s02abv144.md) |
| 2.2.7 超弹性大应变粘弹性 | 2.2.7 Large-strain viscoelasticity with hyperelasticity | [ch02s02abv145.md](./chs/ch02s02abv145.md) | [ch02s02abv145.md](./eng/ch02s02abv145.md) |
| 2.2.8 超弹性非线性大应变粘弹性 | 2.2.8 Nonlinear large-strain viscoelasticity with hyperelasticity | [ch02s02abv146.md](./chs/ch02s02abv146.md) | [ch02s02abv146.md](./eng/ch02s02abv146.md) |
| 2.2.9 粘弹性圆柱体的瞬态内压加载 | 2.2.9 Transient internal pressure loading of a viscoelastic cylinder | [ch02s02abv147.md](./chs/ch02s02abv147.md) | [ch02s02abv147.md](./eng/ch02s02abv147.md) |
| 2.2.10 与速率无关的塑性 | 2.2.10 Rate-independent plasticity | [ch02s02abv148.md](./chs/ch02s02abv148.md) | [ch02s02abv148.md](./eng/ch02s02abv148.md) |
| 2.2.11 Abaqus/Standard中与速率相关的塑性 | 2.2.11 Rate-dependent plasticity in Abaqus/Standard | [ch02s02abv149.md](./chs/ch02s02abv149.md) | [ch02s02abv149.md](./eng/ch02s02abv149.md) |
| 2.2.12 Abaqus/Explicit中与速率相关的塑性 | 2.2.12 Rate-dependent plasticity in Abaqus/Explicit | [ch02s02abv150.md](./chs/ch02s02abv150.md) | [ch02s02abv150.md](./eng/ch02s02abv150.md) |
| 2.2.13 退火温度 | 2.2.13 Annealing temperature | [ch02s02abv151.md](./chs/ch02s02abv151.md) | [ch02s02abv151.md](./eng/ch02s02abv151.md) |
| 2.2.14 温度依赖的非弹性材料 | 2.2.14 Temperature-dependent inelastic materials | [ch02s02abv152.md](./chs/ch02s02abv152.md) | [ch02s02abv152.md](./eng/ch02s02abv152.md) |
| 2.2.15 场变量依赖的非弹性材料 | 2.2.15 Field-variable-dependent inelastic materials | [ch02s02abv153.md](./chs/ch02s02abv153.md) | [ch02s02abv153.md](./eng/ch02s02abv153.md) |
| 2.2.16 Johnson-Cook塑性 | 2.2.16 Johnson-Cook plasticity | [ch02s02abv154.md](./chs/ch02s02abv154.md) | [ch02s02abv154.md](./eng/ch02s02abv154.md) |
| 2.2.17 多孔金属塑性 | 2.2.17 Porous metal plasticity | [ch02s02abv155.md](./chs/ch02s02abv155.md) | [ch02s02abv155.md](./eng/ch02s02abv155.md) |
| 2.2.18 Drucker-Prager塑性 | 2.2.18 Drucker-Prager plasticity | [ch02s02abv156.md](./chs/ch02s02abv156.md) | [ch02s02abv156.md](./eng/ch02s02abv156.md) |
| 2.2.19 Drucker-Prager/盖塑性模型 | 2.2.19 Drucker-Prager/Cap plasticity model | [ch02s02abv157.md](./chs/ch02s02abv157.md) | [ch02s02abv157.md](./eng/ch02s02abv157.md) |
| 2.2.20 状态方程材料 | 2.2.20 Equation of state material | [ch02s02abv158.md](./chs/ch02s02abv158.md) | [ch02s02abv158.md](./eng/ch02s02abv158.md) |
| 2.2.21 韧性金属的渐进损伤与失效 | 2.2.21 Progressive damage and failure of ductile metals | [ch02s02abv159.md](./chs/ch02s02abv159.md) | [ch02s02abv159.md](./eng/ch02s02abv159.md) |
| 2.2.22 纤维增强材料的渐进损伤与失效 | 2.2.22 Progressive damage and failure in fiber-reinforced materials | [ch02s02abv160.md](./chs/ch02s02abv160.md) | [ch02s02abv160.md](./eng/ch02s02abv160.md) |
| 2.2.23 蠕变 | 2.2.23 Creep | [ch02s02abv161.md](./chs/ch02s02abv161.md) | [ch02s02abv161.md](./eng/ch02s02abv161.md) |
| 2.2.24 混凝土弥散裂纹 | 2.2.24 Concrete smeared cracking | [ch02s02abv162.md](./chs/ch02s02abv162.md) | [ch02s02abv162.md](./eng/ch02s02abv162.md) |
| 2.2.25 混凝土损伤塑性 | 2.2.25 Concrete damaged plasticity | [ch02s02abv163.md](./chs/ch02s02abv163.md) | [ch02s02abv163.md](./eng/ch02s02abv163.md) |
| 2.2.26 双层粘塑性 | 2.2.26 Two-layer viscoplasticity | [ch02s02abv164.md](./chs/ch02s02abv164.md) | [ch02s02abv164.md](./eng/ch02s02abv164.md) |
| 2.2.27 脆性裂纹本构模型 | 2.2.27 Brittle cracking constitutive model | [ch02s02abv165.md](./chs/ch02s02abv165.md) | [ch02s02abv165.md](./eng/ch02s02abv165.md) |
| 2.2.28 裂纹模型：张拉剪切试验 | 2.2.28 Cracking model: tension shear test | [ch02s02abv166.md](./chs/ch02s02abv166.md) | [ch02s02abv166.md](./eng/ch02s02abv166.md) |
| 2.2.29 静水流体 | 2.2.29 Hydrostatic fluid | [ch02s02abv167.md](./chs/ch02s02abv167.md) | [ch02s02abv167.md](./eng/ch02s02abv167.md) |
| 2.2.30 Abaqus/Standard中的复合、质量比例和旋转惯性比例阻尼 | 2.2.30 Composite, mass proportional, and rotary inertia proportional damping in Abaqus/Standard | [ch02s02abv168.md](./chs/ch02s02abv168.md) | [ch02s02abv168.md](./eng/ch02s02abv168.md) |
| 2.2.31 Abaqus/Explicit中的材料阻尼 | 2.2.31 Material damping in Abaqus/Explicit | [ch02s02abv169.md](./chs/ch02s02abv169.md) | [ch02s02abv169.md](./eng/ch02s02abv169.md) |
| 2.2.32 Abaqus/Explicit中的质量比例阻尼 | 2.2.32 Mass proportional damping in Abaqus/Explicit | [ch02s02abv170.md](./chs/ch02s02abv170.md) | [ch02s02abv170.md](./eng/ch02s02abv170.md) |
| 2.2.33 热膨胀试验 | 2.2.33 Thermal expansion test | [ch02s02abv171.md](./chs/ch02s02abv171.md) | [ch02s02abv171.md](./eng/ch02s02abv171.md) |
| 2.3 热性能 | 2.3 Thermal properties | [ch02s03.md](./chs/ch02s03.md) | [ch02s03.md](./eng/ch02s03.md) |
| 2.3.1 热性能 | 2.3.1 Thermal properties | [ch02s03abv172.md](./chs/ch02s03abv172.md) | [ch02s03abv172.md](./eng/ch02s03abv172.md) |

### CH03
*3 分析步骤和技术*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 3 分析步骤和技术 | 3 Analysis Procedures and Techniques | [ch03.md](./chs/ch03.md) | [ch03.md](./eng/ch03.md) |
| 3.1 概述 | 3.1 Overview | [ch03s01.md](./chs/ch03s01.md) | [ch03s01.md](./eng/ch03s01.md) |
| 3.1.1 步骤选项：概述 | 3.1.1 Procedures options: overview | [ch03s01abo03.md](./chs/ch03s01abo03.md) | [ch03s01abo03.md](./eng/ch03s01abo03.md) |
| 3.2 动态分析 | 3.2 Dynamic analysis | [ch03s02.md](./chs/ch03s02.md) | [ch03s02.md](./eng/ch03s02.md) |
| 3.2.1 具有基准校正的模态动态分析 | 3.2.1 Modal dynamic analysis with baseline correction | [ch03s02abv173.md](./chs/ch03s02abv173.md) | [ch03s02abv173.md](./eng/ch03s02abv173.md) |
| 3.2.2 二维单元的稳态动态分析 | 3.2.2 Steady-state dynamic analysis for two-dimensional elements | [ch03s02abv174.md](./chs/ch03s02abv174.md) | [ch03s02abv174.md](./eng/ch03s02abv174.md) |
| 3.2.3 无限单元的稳态动态分析 | 3.2.3 Steady-state dynamic analysis for infinite elements | [ch03s02abv175.md](./chs/ch03s02abv175.md) | [ch03s02abv175.md](./eng/ch03s02abv175.md) |
| 3.2.4 随机响应分析 | 3.2.4 Random response analysis | [ch03s02abv176.md](./chs/ch03s02abv176.md) | [ch03s02abv176.md](./eng/ch03s02abv176.md) |
| 3.2.5 单自由度弹簧-质量系统 | 3.2.5 Single degree of freedom spring-mass systems | [ch03s02abv177.md](./chs/ch03s02abv177.md) | [ch03s02abv177.md](./eng/ch03s02abv177.md) |
| 3.2.6 线性运动学单元测试 | 3.2.6 Linear kinematics element tests | [ch03s02abv178.md](./chs/ch03s02abv178.md) | [ch03s02abv178.md](./eng/ch03s02abv178.md) |
| 3.2.7 质量缩放 | 3.2.7 Mass scaling | [ch03s02abv179.md](./chs/ch03s02abv179.md) | [ch03s02abv179.md](./eng/ch03s02abv179.md) |
| 3.3 流体动力学分析 | 3.3 Fluid dynamic analysis | [ch03s03.md](./chs/ch03s03.md) | [ch03s03.md](./eng/ch03s03.md) |
| 3.3.1 时间精确的层流涡旋脱落 | 3.3.1 Time accurate laminar vortex shedding | [ch03s03abv180.md](./chs/ch03s03abv180.md) | [ch03s03abv180.md](./eng/ch03s03abv180.md) |
| 3.3.2 二维湍流通道流动 | 3.3.2 Two-dimensional turbulent channel flow | [ch03s03abv181.md](./chs/ch03s03abv181.md) | [ch03s03abv181.md](./eng/ch03s03abv181.md) |
| 3.3.3 方腔和斜腔中的盖驱动流动 | 3.3.3 Lid-driven flow in square and skewed cavities | [ch03s03abv182.md](./chs/ch03s03abv182.md) | [ch03s03abv182.md](./eng/ch03s03abv182.md) |
| 3.3.4 雷诺数800下后向台阶流动 | 3.3.4 Flow over a backward-facing step at Reynolds number 800 | [ch03s03abv183.md](./chs/ch03s03abv183.md) | [ch03s03abv183.md](./eng/ch03s03abv183.md) |
| 3.3.5 多孔介质流动 | 3.3.5 Flow through porous media | [ch03s03abv184.md](./chs/ch03s03abv184.md) | [ch03s03abv184.md](./eng/ch03s03abv184.md) |
| 3.4 裂纹扩展 | 3.4 Crack propagation | [ch03s04.md](./chs/ch03s04.md) | [ch03s04.md](./eng/ch03s04.md) |
| 3.4.1 裂纹扩展分析 | 3.4.1 Crack propagation analysis | [ch03s04abv185.md](./chs/ch03s04abv185.md) | [ch03s04abv185.md](./eng/ch03s04abv185.md) |
| 3.4.2 水力驱动裂缝的扩展 | 3.4.2 Propagation of hydraulically driven fracture | [ch03s04abv186.md](./chs/ch03s04abv186.md) | [ch03s04abv186.md](./eng/ch03s04abv186.md) |
| 3.5 子结构 | 3.5 Substructuring | [ch03s05.md](./chs/ch03s05.md) | [ch03s05.md](./eng/ch03s05.md) |
| 3.5.1 子结构旋转、镜像、变换和约束 | 3.5.1 Substructure rotation, mirroring, transformation, and constraints | [ch03s05abv187.md](./chs/ch03s05abv187.md) | [ch03s05abv187.md](./eng/ch03s05abv187.md) |
| 3.5.2 使用节点变换的子结构恢复 | 3.5.2 Substructure recovery with The nodal Transformation | [ch03s05abv188.md](./chs/ch03s05abv188.md) | [ch03s05abv188.md](./eng/ch03s05abv188.md) |
| 3.5.3 子结构中的退化单元 | 3.5.3 Degenerated elements within a substructure | [ch03s05abv189.md](./chs/ch03s05abv189.md) | [ch03s05abv189.md](./eng/ch03s05abv189.md) |
| 3.5.4 具有离心载荷的子结构载荷情况 | 3.5.4 substructure load case with centrifugal loads | [ch03s05abv190.md](./chs/ch03s05abv190.md) | [ch03s05abv190.md](./eng/ch03s05abv190.md) |
| 3.5.5 使用子结构的热应力分析 | 3.5.5 Thermal-stress analysis with substructures | [ch03s05abv191.md](./chs/ch03s05abv191.md) | [ch03s05abv191.md](./eng/ch03s05abv191.md) |
| 3.5.6 子结构预加载历史 | 3.5.6 Substructure preload history | [ch03s05abv192.md](./chs/ch03s05abv192.md) | [ch03s05abv192.md](./eng/ch03s05abv192.md) |
| 3.5.7 子结构移除 | 3.5.7 Substructure removal | [ch03s05abv193.md](./chs/ch03s05abv193.md) | [ch03s05abv193.md](./eng/ch03s05abv193.md) |
| 3.5.8 子结构库工具 | 3.5.8 Substructure library utilities | [ch03s05abv194.md](./chs/ch03s05abv194.md) | [ch03s05abv194.md](./eng/ch03s05abv194.md) |
| 3.5.9 子结构阻尼 | 3.5.9 Substructure damping | [ch03s05abv195.md](./chs/ch03s05abv195.md) | [ch03s05abv195.md](./eng/ch03s05abv195.md) |
| 3.5.10 具有钢筋的子结构 | 3.5.10 Substructures with rebar | [ch03s05abv196.md](./chs/ch03s05abv196.md) | [ch03s05abv196.md](./eng/ch03s05abv196.md) |
| 3.5.11 子结构的频率提取 | 3.5.11 Frequency extraction for substructures | [ch03s05abv197.md](./chs/ch03s05abv197.md) | [ch03s05abv197.md](./eng/ch03s05abv197.md) |
| 3.5.12 具有大旋转的子结构 | 3.5.12 Substructures with large rotations | [ch03s05abv198.md](./chs/ch03s05abv198.md) | [ch03s05abv198.md](./eng/ch03s05abv198.md) |
| 3.5.13 使用子结构的耦合结构声学分析 | 3.5.13 Coupled structural-acoustic analysis with substructures | [ch03s05abv199.md](./chs/ch03s05abv199.md) | [ch03s05abv199.md](./eng/ch03s05abv199.md) |
| 3.6 电磁分析 | 3.6 Electromagnetic analysis | [ch03s06.md](./chs/ch03s06.md) | [ch03s06.md](./eng/ch03s06.md) |
| 3.6.1 涡流分析 | 3.6.1 Eddy current analysis | [ch03s06abv200.md](./chs/ch03s06abv200.md) | [ch03s06abv200.md](./eng/ch03s06abv200.md) |
| 3.6.2 静磁分析 | 3.6.2 Magnetostatic analysis | [ch03s06abv201.md](./chs/ch03s06abv201.md) | [ch03s06abv201.md](./eng/ch03s06abv201.md) |
| 3.7 压电分析 | 3.7 Piezoelectric analysis | [ch03s07.md](./chs/ch03s07.md) | [ch03s07.md](./eng/ch03s07.md) |
| 3.7.1 压电材料的静态分析 | 3.7.1 Static analysis for piezoelectric materials | [ch03s07abv202.md](./chs/ch03s07abv202.md) | [ch03s07abv202.md](./eng/ch03s07abv202.md) |
| 3.7.2 压电材料的频率提取分析 | 3.7.2 Frequency extraction analysis for piezoelectric materials | [ch03s07abv203.md](./chs/ch03s07abv203.md) | [ch03s07abv203.md](./eng/ch03s07abv203.md) |
| 3.7.3 压电材料的一般分析过程 | 3.7.3 General analysis procedures for piezoelectric materials | [ch03s07abv204.md](./chs/ch03s07abv204.md) | [ch03s07abv204.md](./eng/ch03s07abv204.md) |
| 3.8 子模型 | 3.8 Submodeling | [ch03s08.md](./chs/ch03s08.md) | [ch03s08.md](./eng/ch03s08.md) |
| 3.8.1 子模型：概述 | 3.8.1 Submodeling: overview | [ch03s08abo04.md](./chs/ch03s08abo04.md) | [ch03s08abo04.md](./eng/ch03s08abo04.md) |
| 3.8.2 二维连续体应力/位移子模型 | 3.8.2 Two-dimensional continuum stress/displacement submodeling | [ch03s08abv205.md](./chs/ch03s08abv205.md) | [ch03s08abv205.md](./eng/ch03s08abv205.md) |
| 3.8.3 三维连续体应力/位移子模型 | 3.8.3 Three-dimensional continuum stress/displacement submodeling | [ch03s08abv206.md](./chs/ch03s08abv206.md) | [ch03s08abv206.md](./eng/ch03s08abv206.md) |
| 3.8.4 圆柱连续体应力/位移子模型 | 3.8.4 Cylindrical continuum stress/displacement submodeling | [ch03s08abv207.md](./chs/ch03s08abv207.md) | [ch03s08abv207.md](./eng/ch03s08abv207.md) |
| 3.8.5 轴对称连续体应力/位移子模型 | 3.8.5 Axisymmetric continuum stress/displacement submodeling | [ch03s08abv208.md](./chs/ch03s08abv208.md) | [ch03s08abv208.md](./eng/ch03s08abv208.md) |
| 3.8.6 带扭转的轴对称应力/位移子模型 | 3.8.6 Axisymmetric stress/displacement submodeling with twist | [ch03s08abv209.md](./chs/ch03s08abv209.md) | [ch03s08abv209.md](./eng/ch03s08abv209.md) |
| 3.8.7 膜子模型 | 3.8.7 Membrane submodeling | [ch03s08abv210.md](./chs/ch03s08abv210.md) | [ch03s08abv210.md](./eng/ch03s08abv210.md) |
| 3.8.8 壳子模型 | 3.8.8 Shell submodeling | [ch03s08abv211.md](./chs/ch03s08abv211.md) | [ch03s08abv211.md](./eng/ch03s08abv211.md) |
| 3.8.9 表面单元子模型 | 3.8.9 Surface element submodeling | [ch03s08abv212.md](./chs/ch03s08abv212.md) | [ch03s08abv212.md](./eng/ch03s08abv212.md) |
| 3.8.10 热传递子模型 | 3.8.10 Heat transfer submodeling | [ch03s08abv213.md](./chs/ch03s08abv213.md) | [ch03s08abv213.md](./eng/ch03s08abv213.md) |
| 3.8.11 耦合温度-位移子模型 | 3.8.11 Coupled temperature-displacement submodeling | [ch03s08abv214.md](./chs/ch03s08abv214.md) | [ch03s08abv214.md](./eng/ch03s08abv214.md) |
| 3.8.12 孔隙压力子模型 | 3.8.12 Pore pressure submodeling | [ch03s08abv215.md](./chs/ch03s08abv215.md) | [ch03s08abv215.md](./eng/ch03s08abv215.md) |
| 3.8.13 压电子模型 | 3.8.13 Piezoelectric submodeling | [ch03s08abv216.md](./chs/ch03s08abv216.md) | [ch03s08abv216.md](./eng/ch03s08abv216.md) |
| 3.8.14 声学子模型 | 3.8.14 Acoustic submodeling | [ch03s08abv217.md](./chs/ch03s08abv217.md) | [ch03s08abv217.md](./eng/ch03s08abv217.md) |
| 3.8.15 壳-实体子模型 | 3.8.15 Shell-to-solid submodeling | [ch03s08abv218.md](./chs/ch03s08abv218.md) | [ch03s08abv218.md](./eng/ch03s08abv218.md) |
| 3.8.16 垫片子模型 | 3.8.16 Gasket submodeling | [ch03s08abv219.md](./chs/ch03s08abv219.md) | [ch03s08abv219.md](./eng/ch03s08abv219.md) |
| 3.8.17 其他子模型测试 | 3.8.17 Miscellaneous submodeling tests | [ch03s08abv220.md](./chs/ch03s08abv220.md) | [ch03s08abv220.md](./eng/ch03s08abv220.md) |
| 3.9 声学和冲击分析 | 3.9 Acoustic and shock analyses | [ch03s09.md](./chs/ch03s09.md) | [ch03s09.md](./eng/ch03s09.md) |
| 3.9.1 体积拖曳 | 3.9.1 Volumetric drag | [ch03s09abv221.md](./chs/ch03s09abv221.md) | [ch03s09abv221.md](./eng/ch03s09abv221.md) |
| 3.9.2 阻抗边界条件 | 3.9.2 Impedance boundary conditions | [ch03s09abv222.md](./chs/ch03s09abv222.md) | [ch03s09abv222.md](./eng/ch03s09abv222.md) |
| 3.9.3 瞬态声波传播 | 3.9.3 Transient acoustic wave propagation | [ch03s09abv223.md](./chs/ch03s09abv223.md) | [ch03s09abv223.md](./eng/ch03s09abv223.md) |
| 3.9.4 自适应网格划分的耦合结构-声学问题应用 | 3.9.4 Adaptive meshing applied to coupled structural-acoustic problems | [ch03s09abv224.md](./chs/ch03s09abv224.md) | [ch03s09abv224.md](./eng/ch03s09abv224.md) |
| 3.9.5 CONWEP爆炸载荷压力 | 3.9.5 CONWEP blast loading pressures | [ch03s09abv225.md](./chs/ch03s09abv225.md) | [ch03s09abv225.md](./eng/ch03s09abv225.md) |
| 3.9.6 使用CONWEP模型的圆板爆炸载荷 | 3.9.6 Blast loading of a circular plate using the CONWEP model | [ch03s09abv226.md](./chs/ch03s09abv226.md) | [ch03s09abv226.md](./eng/ch03s09abv226.md) |
| 3.10 模型变更 | 3.10 Model change | [ch03s10.md](./chs/ch03s10.md) | [ch03s10.md](./eng/ch03s10.md) |
| 3.10.1 模型变更：概述 | 3.10.1 Model change: overview | [ch03s10abo05.md](./chs/ch03s10abo05.md) | [ch03s10abo05.md](./eng/ch03s10abo05.md) |
| 3.10.2 应力/位移模型变化：静态 | 3.10.2 Stress/displacement model change: static | [ch03s10abv227.md](./chs/ch03s10abv227.md) | [ch03s10abv227.md](./eng/ch03s10abv227.md) |
| 3.10.3 应力/位移模型变化：动态 | 3.10.3 Stress/displacement model change: dynamic | [ch03s10abv228.md](./chs/ch03s10abv228.md) | [ch03s10abv228.md](./eng/ch03s10abv228.md) |
| 3.10.4 应力/位移模型变化：通用测试 | 3.10.4 Stress/displacement model change: general tests | [ch03s10abv229.md](./chs/ch03s10abv229.md) | [ch03s10abv229.md](./eng/ch03s10abv229.md) |
| 3.10.5 热传递模型变化：稳态 | 3.10.5 Heat transfer model change: steady state | [ch03s10abv230.md](./chs/ch03s10abv230.md) | [ch03s10abv230.md](./eng/ch03s10abv230.md) |
| 3.10.6 耦合温度-位移模型变化：稳态 | 3.10.6 Coupled temperature-displacement model change: steady state | [ch03s10abv231.md](./chs/ch03s10abv231.md) | [ch03s10abv231.md](./eng/ch03s10abv231.md) |
| 3.10.7 接触模型变化 | 3.10.7 Contact model change | [ch03s10abv232.md](./chs/ch03s10abv232.md) | [ch03s10abv232.md](./eng/ch03s10abv232.md) |
| 3.10.8 声学模型变化：稳态 | 3.10.8 Acoustic model change: steady state | [ch03s10abv233.md](./chs/ch03s10abv233.md) | [ch03s10abv233.md](./eng/ch03s10abv233.md) |
| 3.10.9 孔隙-热模型变化 | 3.10.9 Pore-thermal model change | [ch03s10abv234.md](./chs/ch03s10abv234.md) | [ch03s10abv234.md](./eng/ch03s10abv234.md) |
| 3.11 对称模型生成和循环对称模型分析 | 3.11 Symmetric model generation and analysis of cyclic symmetry models | [ch03s11.md](./chs/ch03s11.md) | [ch03s11.md](./eng/ch03s11.md) |
| 3.11.1 对称模型生成和结果传递 | 3.11.1 Symmetric model generation and results transfer | [ch03s11abv235.md](./chs/ch03s11abv235.md) | [ch03s11abv235.md](./eng/ch03s11abv235.md) |
| 3.11.2 循环对称模型分析 | 3.11.2 Analysis of cyclic symmetric models | [ch03s11abv236.md](./chs/ch03s11abv236.md) | [ch03s11abv236.md](./eng/ch03s11abv236.md) |
| 3.12 Abaqus/Aqua 分析 | 3.12 Abaqus/Aqua analysis | [ch03s12.md](./chs/ch03s12.md) | [ch03s12.md](./eng/ch03s12.md) |
| 3.12.1 水荷载工况 | 3.12.1 Aqua load cases | [ch03s12abv237.md](./chs/ch03s12abv237.md) | [ch03s12abv237.md](./eng/ch03s12abv237.md) |
| 3.12.2 自升式基础分析 | 3.12.2 Jack-up foundation analysis | [ch03s12abv238.md](./chs/ch03s12abv238.md) | [ch03s12abv238.md](./eng/ch03s12abv238.md) |
| 3.12.3 弹塑性接头单元 | 3.12.3 Elastic-plastic joint elements | [ch03s12abv239.md](./chs/ch03s12abv239.md) | [ch03s12abv239.md](./eng/ch03s12abv239.md) |
| 3.13 设计灵敏度分析 | 3.13 Design sensitivity analysis | [ch03s13.md](./chs/ch03s13.md) | [ch03s13.md](./eng/ch03s13.md) |
| 3.13.1 设计灵敏度分析 | 3.13.1 Design sensitivity analysis | [ch03s13abv240.md](./chs/ch03s13abv240.md) | [ch03s13abv240.md](./eng/ch03s13abv240.md) |
| 3.14 Abaqus/Standard 和 Abaqus/Explicit 之间的结果传递 | 3.14 Transferring results between Abaqus/Standard and Abaqus/Explicit | [ch03s14.md](./chs/ch03s14.md) | [ch03s14.md](./eng/ch03s14.md) |
| 3.14.1 在 Abaqus/Explicit 和 Abaqus/Standard 之间传输结果 | 3.14.1 Transferring results between Abaqus/Explicit and Abaqus/Standard | [ch03s14abv241.md](./chs/ch03s14abv241.md) | [ch03s14abv241.md](./eng/ch03s14abv241.md) |
| 3.14.2 在一个Abaqus/Standard分析到另一个Abaqus/Standard分析之间传输结果 | 3.14.2 Transferring results from one Abaqus/Standard analysis to another Abaqus/Standard analysis | [ch03s14abv242.md](./chs/ch03s14abv242.md) | [ch03s14abv242.md](./eng/ch03s14abv242.md) |
| 3.14.3 在不同Abaqus/Explicit分析之间传递结果 | 3.14.3 Transferring results from one Abaqus/Explicit analysis to another Abaqus/Explicit analysis | [ch03s14abv243.md](./chs/ch03s14abv243.md) | [ch03s14abv243.md](./eng/ch03s14abv243.md) |
| 3.14.4 使用通用梁截面传递结果 | 3.14.4 Transferring results with general beam sections | [ch03s14abv244.md](./chs/ch03s14abv244.md) | [ch03s14abv244.md](./eng/ch03s14abv244.md) |
| 3.14.5 使用通用壳截面传递结果 | 3.14.5 Transferring results with general shell sections | [ch03s14abv245.md](./chs/ch03s14abv245.md) | [ch03s14abv245.md](./eng/ch03s14abv245.md) |
| 3.14.6 在结果传递过程中添加和移除单元 | 3.14.6 Adding and removing elements during results transfer | [ch03s14abv246.md](./chs/ch03s14abv246.md) | [ch03s14abv246.md](./eng/ch03s14abv246.md) |
| 3.14.8 传递质量和转动惯量单元 | 3.14.7 Transferring rigid elements | [ch03s14abv247.md](./chs/ch03s14abv247.md) | [ch03s14abv247.md](./eng/ch03s14abv247.md) |
| 3.14.9 将连接器单元导入到Abaqus/Explicit | 3.14.8 Transferring mass and rotary inertia elements | [ch03s14abv248.md](./chs/ch03s14abv248.md) | [ch03s14abv248.md](./eng/ch03s14abv248.md) |
| 3.14.7 传递刚性单元 | 3.14.9 Transferring connector elements into Abaqus/Explicit | [ch03s14abv249.md](./chs/ch03s14abv249.md) | [ch03s14abv249.md](./eng/ch03s14abv249.md) |
| 3.14.11 在导入期间更改材料定义 | 3.14.10 Transferring hourglass forces | [ch03s14abv250.md](./chs/ch03s14abv250.md) | [ch03s14abv250.md](./eng/ch03s14abv250.md) |
| 3.14.10 传递沙漏力 | 3.14.11 Changing the material definition during import | [ch03s14abv251.md](./chs/ch03s14abv251.md) | [ch03s14abv251.md](./eng/ch03s14abv251.md) |
| 3.14.12 使用塑性传递结果 | 3.14.12 Transferring results with plasticity | [ch03s14abv252.md](./chs/ch03s14abv252.md) | [ch03s14abv252.md](./eng/ch03s14abv252.md) |
| 3.14.13 使用损伤传递结果 | 3.14.13 Transferring results with damage | [ch03s14abv253.md](./chs/ch03s14abv253.md) | [ch03s14abv253.md](./eng/ch03s14abv253.md) |
| 3.14.14 使用超弹性传递结果 | 3.14.14 Transferring results with hyperelasticity | [ch03s14abv254.md](./chs/ch03s14abv254.md) | [ch03s14abv254.md](./eng/ch03s14abv254.md) |
| 3.14.15 使用粘弹性传递结果 | 3.14.15 Transferring results with viscoelasticity | [ch03s14abv255.md](./chs/ch03s14abv255.md) | [ch03s14abv255.md](./eng/ch03s14abv255.md) |
| 3.14.16 传递具有圆形孔的超弹性薄片的结果 | 3.14.16 Transferring results for a hyperelastic sheet with a circular hole | [ch03s14abv256.md](./chs/ch03s14abv256.md) | [ch03s14abv256.md](./eng/ch03s14abv256.md) |
| 3.14.17 使用超泡沫传递结果 | 3.14.17 Transferring results with hyperfoam | [ch03s14abv257.md](./chs/ch03s14abv257.md) | [ch03s14abv257.md](./eng/ch03s14abv257.md) |
| 3.14.18 通过方向进行结果传递 | 3.14.18 Transferring results with orientation | [ch03s14abv258.md](./chs/ch03s14abv258.md) | [ch03s14abv258.md](./eng/ch03s14abv258.md) |
| 3.14.20 通过并行流变框架传递结果 | 3.14.19 Miscellaneous results transfer tests | [ch03s14abv259.md](./chs/ch03s14abv259.md) | [ch03s14abv259.md](./eng/ch03s14abv259.md) |
| 3.14.19 其他结果传递测试 | 3.14.20 Transferring results with parallel rheological framework | [ch03s14abv260.md](./chs/ch03s14abv260.md) | [ch03s14abv260.md](./eng/ch03s14abv260.md) |
| 3.15 不同网格之间的结果传递 | 3.15 Transferring results between dissimilar meshes | [ch03s15.md](./chs/ch03s15.md) | [ch03s15.md](./eng/ch03s15.md) |
| 3.15.1 在Abaqus/Standard中不同网格之间传递结果 | 3.15.1 Transferring results between dissimilar meshes in Abaqus/Standard | [ch03s15abv261.md](./chs/ch03s15abv261.md) | [ch03s15abv261.md](./eng/ch03s15abv261.md) |
| 3.16 直接循环分析 | 3.16 Direct cyclic analysis | [ch03s16.md](./chs/ch03s16.md) | [ch03s16.md](./eng/ch03s16.md) |
| 3.16.1 直接循环和低周疲劳分析 | 3.16.1 Direct cyclic and low-cycle fatigue analyses | [ch03s16abv262.md](./chs/ch03s16abv262.md) | [ch03s16abv262.md](./eng/ch03s16abv262.md) |
| 3.17 网格化梁截面 | 3.17 Meshed beam cross-sections | [ch03s17.md](./chs/ch03s17.md) | [ch03s17.md](./eng/ch03s17.md) |
| 3.17.1 网格化梁截面：概述 | 3.17.1 Meshed beam cross-sections: overview | [ch03s17abo06.md](./chs/ch03s17abo06.md) | [ch03s17abo06.md](./eng/ch03s17abo06.md) |
| 3.17.2 梁截面二维模型的网格划分与分析 | 3.17.2 Meshing and analyzing a two-dimensional model of a beam cross-section | [ch03s17abv263.md](./chs/ch03s17abv263.md) | [ch03s17abv263.md](./eng/ch03s17abv263.md) |
| 3.17.3 在梁分析中使用生成的截面属性 | 3.17.3 Using generated cross-section properties in a beam analysis | [ch03s17abv264.md](./chs/ch03s17abv264.md) | [ch03s17abv264.md](./eng/ch03s17abv264.md) |
| 3.18 复特征值提取 | 3.18 Complex eigenvalue extraction | [ch03s18.md](./chs/ch03s18.md) | [ch03s18.md](./eng/ch03s18.md) |
| 3.18.1 复特征值提取 | 3.18.1 Complex eigenvalue extraction | [ch03s18abv265.md](./chs/ch03s18abv265.md) | [ch03s18abv265.md](./eng/ch03s18abv265.md) |
| 3.19 欧拉分析 | 3.19 Eulerian analysis | [ch03s19.md](./chs/ch03s19.md) | [ch03s19.md](./eng/ch03s19.md) |
| 3.19.1 旋转水盘的CEL分析 | 3.19.1 CEL analysis of a rotating water disk | [ch03s19abv266.md](./chs/ch03s19abv266.md) | [ch03s19abv266.md](./eng/ch03s19abv266.md) |
| 3.20 光滑粒子流体力学分析 | 3.20 Smoothed particle hydrodynamic analysis | [ch03s20.md](./chs/ch03s20.md) | [ch03s20.md](./eng/ch03s20.md) |
| 3.20.1 光滑粒子流体动力学分析 | 3.20.1 Smoothed particle hydrodynamic analysis | [ch03s20abv267.md](./chs/ch03s20abv267.md) | [ch03s20abv267.md](./eng/ch03s20abv267.md) |
| 3.21 协同仿真 | 3.21 Co-simulation | [ch03s21.md](./chs/ch03s21.md) | [ch03s21.md](./eng/ch03s21.md) |
| 3.21.1 通道内悬臂梁的流固耦合 | 3.21.1 Fluid-structure interaction of a cantilever beam inside a channel | [ch03s21abv268.md](./chs/ch03s21abv268.md) | [ch03s21abv268.md](./eng/ch03s21abv268.md) |
| 3.21.2 Abaqus/Standard到Abaqus/Explicit协同仿真 | 3.21.2 Abaqus/Standard to Abaqus/Explicit co-simulation | [ch03s21abv269.md](./chs/ch03s21abv269.md) | [ch03s21abv269.md](./eng/ch03s21abv269.md) |
| 3.22 自适应重划分 | 3.22 Adaptive remeshing | [ch03s22.md](./chs/ch03s22.md) | [ch03s22.md](./eng/ch03s22.md) |
| 3.22.1 受压厚壁圆筒 | 3.22.1 Pressurized thick-walled cylinder | [ch03s22abv270.md](./chs/ch03s22abv270.md) | [ch03s22abv270.md](./eng/ch03s22abv270.md) |
| 3.22.2 误差指示器 | 3.22.2 Error indicators | [ch03s22abv271.md](./chs/ch03s22abv271.md) | [ch03s22abv271.md](./eng/ch03s22abv271.md) |
| 3.23 使用 AMS 特征值求解器进行频率提取 | 3.23 Frequency extraction using the AMS eigensolver | [ch03s23.md](./chs/ch03s23.md) | [ch03s23.md](./eng/ch03s23.md) |
| 3.23.1 使用AMS特征求解器进行频率提取 | 3.23.1 Frequency extraction using the AMS eigensolver | [ch03s23abv272.md](./chs/ch03s23abv272.md) | [ch03s23abv272.md](./eng/ch03s23abv272.md) |
| 3.24 使用 AMS 特征值求解器进行具有非对角阻尼的稳态动力学分析 | 3.24 Steady-state dynamics with nondiagonal damping using the AMS eigensolver | [ch03s24.md](./chs/ch03s24.md) | [ch03s24.md](./eng/ch03s24.md) |
| 3.24.1 使用AMS特征求解器的具有非对角阻尼的稳态动力学 | 3.24.1 Steady-state dynamics with nondiagonal damping using the AMS eigensolver | [ch03s24abv273.md](./chs/ch03s24abv273.md) | [ch03s24abv273.md](./eng/ch03s24abv273.md) |
| 3.25 周期介质分析 | 3.25 Periodic media analysis | [ch03s25.md](./chs/ch03s25.md) | [ch03s25.md](./eng/ch03s25.md) |
| 3.25.1 介质传输 | 3.25.1 Media transport | [ch03s25abv274.md](./chs/ch03s25abv274.md) | [ch03s25abv274.md](./eng/ch03s25abv274.md) |
| 3.26 离散元方法分析 | 3.26 Discrete element method analysis | [ch03s26.md](./chs/ch03s26.md) | [ch03s26.md](./eng/ch03s26.md) |
| 3.26.1 离散单元方法分析 | 3.26.1 Discrete element method analysis | [ch03s26abv275.md](./chs/ch03s26abv275.md) | [ch03s26abv275.md](./eng/ch03s26abv275.md) |

### CH04
*4 用户子程序*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 4 用户子程序 | 4 User Subroutines | [ch04.md](./chs/ch04.md) | [ch04.md](./eng/ch04.md) |
| 4.1 用户子程序 | 4.1 User subroutines | [ch04s01.md](./chs/ch04s01.md) | [ch04s01.md](./eng/ch04s01.md) |
| 4.1.1 DFLUX | 4.1.1 DFLUX | [ch04s01abv276.md](./chs/ch04s01abv276.md) | [ch04s01abv276.md](./eng/ch04s01abv276.md) |
| 4.1.2 DISP | 4.1.2 DISP | [ch04s01abv277.md](./chs/ch04s01abv277.md) | [ch04s01abv277.md](./eng/ch04s01abv277.md) |
| 4.1.3 DLOAD | 4.1.3 DLOAD | [ch04s01abv278.md](./chs/ch04s01abv278.md) | [ch04s01abv278.md](./eng/ch04s01abv278.md) |
| 4.1.4 FRIC | 4.1.4 FRIC | [ch04s01abv279.md](./chs/ch04s01abv279.md) | [ch04s01abv279.md](./eng/ch04s01abv279.md) |
| 4.1.5 FRIC_COEF | 4.1.5 FRIC_COEF | [ch04s01abv280.md](./chs/ch04s01abv280.md) | [ch04s01abv280.md](./eng/ch04s01abv280.md) |
| 4.1.6 GAPCON | 4.1.6 GAPCON | [ch04s01abv281.md](./chs/ch04s01abv281.md) | [ch04s01abv281.md](./eng/ch04s01abv281.md) |
| 4.1.7 GAPELECTR | 4.1.7 GAPELECTR | [ch04s01abv282.md](./chs/ch04s01abv282.md) | [ch04s01abv282.md](./eng/ch04s01abv282.md) |
| 4.1.8 HARDINI | 4.1.8 HARDINI | [ch04s01abv283.md](./chs/ch04s01abv283.md) | [ch04s01abv283.md](./eng/ch04s01abv283.md) |
| 4.1.9 HETVAL | 4.1.9 HETVAL | [ch04s01abv284.md](./chs/ch04s01abv284.md) | [ch04s01abv284.md](./eng/ch04s01abv284.md) |
| 4.1.10 RSURFU | 4.1.10 RSURFU | [ch04s01abv285.md](./chs/ch04s01abv285.md) | [ch04s01abv285.md](./eng/ch04s01abv285.md) |
| 4.1.11 SDVINI | 4.1.11 SDVINI | [ch04s01abv286.md](./chs/ch04s01abv286.md) | [ch04s01abv286.md](./eng/ch04s01abv286.md) |
| 4.1.12 UAMP | 4.1.12 UAMP | [ch04s01abv287.md](./chs/ch04s01abv287.md) | [ch04s01abv287.md](./eng/ch04s01abv287.md) |
| 4.1.13 UANISOHYPER_INV 和 VUANISOHYPER_INV | 4.1.13 UANISOHYPER_INV and VUANISOHYPER_INV | [ch04s01abv288.md](./chs/ch04s01abv288.md) | [ch04s01abv288.md](./eng/ch04s01abv288.md) |
| 4.1.14 UEL | 4.1.14 UEL | [ch04s01abv289.md](./chs/ch04s01abv289.md) | [ch04s01abv289.md](./eng/ch04s01abv289.md) |
| 4.1.15 UELMAT | 4.1.15 UELMAT | [ch04s01abv290.md](./chs/ch04s01abv290.md) | [ch04s01abv290.md](./eng/ch04s01abv290.md) |
| 4.1.16 UEXPAN | 4.1.16 UEXPAN | [ch04s01abv291.md](./chs/ch04s01abv291.md) | [ch04s01abv291.md](./eng/ch04s01abv291.md) |
| 4.1.17 UFLUID | 4.1.17 UFLUID | [ch04s01abv292.md](./chs/ch04s01abv292.md) | [ch04s01abv292.md](./eng/ch04s01abv292.md) |
| 4.1.18 UGENS | 4.1.18 UGENS | [ch04s01abv293.md](./chs/ch04s01abv293.md) | [ch04s01abv293.md](./eng/ch04s01abv293.md) |
| 4.1.19 UHARD | 4.1.19 UHARD | [ch04s01abv294.md](./chs/ch04s01abv294.md) | [ch04s01abv294.md](./eng/ch04s01abv294.md) |
| 4.1.20 UINTER | 4.1.20 UINTER | [ch04s01abv295.md](./chs/ch04s01abv295.md) | [ch04s01abv295.md](./eng/ch04s01abv295.md) |
| 4.1.21 UMAT 和 UHYPER | 4.1.21 UMAT and UHYPER | [ch04s01abv296.md](./chs/ch04s01abv296.md) | [ch04s01abv296.md](./eng/ch04s01abv296.md) |
| 4.1.22 UMATHT | 4.1.22 UMATHT | [ch04s01abv297.md](./chs/ch04s01abv297.md) | [ch04s01abv297.md](./eng/ch04s01abv297.md) |
| 4.1.23 URDFIL | 4.1.23 URDFIL | [ch04s01abv298.md](./chs/ch04s01abv298.md) | [ch04s01abv298.md](./eng/ch04s01abv298.md) |
| 4.1.24 USDFLD | 4.1.24 USDFLD | [ch04s01abv299.md](./chs/ch04s01abv299.md) | [ch04s01abv299.md](./eng/ch04s01abv299.md) |
| 4.1.25 UTEMP、UFIELD、UMASFL和UPRESS | 4.1.25 UTEMP, UFIELD, UMASFL, and UPRESS | [ch04s01abv300.md](./chs/ch04s01abv300.md) | [ch04s01abv300.md](./eng/ch04s01abv300.md) |
| 4.1.26 UVARM | 4.1.26 UVARM | [ch04s01abv301.md](./chs/ch04s01abv301.md) | [ch04s01abv301.md](./eng/ch04s01abv301.md) |
| 4.1.27 UWAVE 和 UEXTERNALDB | 4.1.27 UWAVE and UEXTERNALDB | [ch04s01abv302.md](./chs/ch04s01abv302.md) | [ch04s01abv302.md](./eng/ch04s01abv302.md) |
| 4.1.28 VDISP | 4.1.28 VDISP | [ch04s01abv303.md](./chs/ch04s01abv303.md) | [ch04s01abv303.md](./eng/ch04s01abv303.md) |
| 4.1.29 VDLOAD：非均匀载荷 | 4.1.29 VDLOAD: nonuniform loads | [ch04s01abv304.md](./chs/ch04s01abv304.md) | [ch04s01abv304.md](./eng/ch04s01abv304.md) |
| 4.1.30 VFRIC、VFRIC_COEF和VFRICTION | 4.1.30 VFRIC, VFRIC_COEF, and VFRICTION | [ch04s01abv305.md](./chs/ch04s01abv305.md) | [ch04s01abv305.md](./eng/ch04s01abv305.md) |
| 4.1.41 VWAVE | 4.1.31 VUAMP | [ch04s01abv306.md](./chs/ch04s01abv306.md) | [ch04s01abv306.md](./eng/ch04s01abv306.md) |
| 4.1.32 VUCHARLENGTH | 4.1.32 VUCHARLENGTH | [ch04s01abv307.md](./chs/ch04s01abv307.md) | [ch04s01abv307.md](./eng/ch04s01abv307.md) |
| 4.1.33 VUEL | 4.1.33 VUEL | [ch04s01abv308.md](./chs/ch04s01abv308.md) | [ch04s01abv308.md](./eng/ch04s01abv308.md) |
| 4.1.34 VUFIELD | 4.1.34 VUFIELD | [ch04s01abv309.md](./chs/ch04s01abv309.md) | [ch04s01abv309.md](./eng/ch04s01abv309.md) |
| 4.1.37 VUINTERACTION | 4.1.35 VUHARD | [ch04s01abv310.md](./chs/ch04s01abv310.md) | [ch04s01abv310.md](./eng/ch04s01abv310.md) |
| 4.1.36 VUINTER | 4.1.36 VUINTER | [ch04s01abv311.md](./chs/ch04s01abv311.md) | [ch04s01abv311.md](./eng/ch04s01abv311.md) |
| 4.1.35 VUHARD | 4.1.37 VUINTERACTION | [ch04s01abv312.md](./chs/ch04s01abv312.md) | [ch04s01abv312.md](./eng/ch04s01abv312.md) |
| 4.1.39 VUSDFLD | 4.1.38 VUMAT: rotating cylinder | [ch04s01abv313.md](./chs/ch04s01abv313.md) | [ch04s01abv313.md](./eng/ch04s01abv313.md) |
| 4.1.40 VUVISCOSITY | 4.1.39 VUSDFLD | [ch04s01abv314.md](./chs/ch04s01abv314.md) | [ch04s01abv314.md](./eng/ch04s01abv314.md) |
| 4.1.38 VUMAT：旋转圆柱体 | 4.1.40 VUVISCOSITY | [ch04s01abv315.md](./chs/ch04s01abv315.md) | [ch04s01abv315.md](./eng/ch04s01abv315.md) |
| 4.1.41 VWAVE | 4.1.41 VWAVE | [ch04s01abv316.md](./chs/ch04s01abv316.md) | [ch04s01abv316.md](./eng/ch04s01abv316.md) |

### CH05
*5 杂项选项*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 5 杂项选项 | 5 Miscellaneous Options | [ch05.md](./chs/ch05.md) | [ch05.md](./eng/ch05.md) |
| 5.1 杂项建模选项 | 5.1 Miscellaneous modeling options | [ch05s01.md](./chs/ch05s01.md) | [ch05s01.md](./eng/ch05s01.md) |
| 5.1.1 Abaqus/Standard中实体单元的自适应网格 | 5.1.1 Adaptive mesh for solid elements in Abaqus/Standard | [ch05s01abv317.md](./chs/ch05s01abv317.md) | [ch05s01abv317.md](./eng/ch05s01abv317.md) |
| 5.1.2 调整节点坐标 | 5.1.2 Adjusting nodal coordinates | [ch05s01abv318.md](./chs/ch05s01abv318.md) | [ch05s01abv318.md](./eng/ch05s01abv318.md) |
| 5.1.3 幅值 | 5.1.3 Amplitude | [ch05s01abv319.md](./chs/ch05s01abv319.md) | [ch05s01abv319.md](./eng/ch05s01abv319.md) |
| 5.1.4 空间变化的单元特性 | 5.1.4 Spatially varying element properties | [ch05s01abv320.md](./chs/ch05s01abv320.md) | [ch05s01abv320.md](./eng/ch05s01abv320.md) |
| 5.1.5 边界条件 | 5.1.5 Boundary conditions | [ch05s01abv321.md](./chs/ch05s01abv321.md) | [ch05s01abv321.md](./eng/ch05s01abv321.md) |
| 5.1.8 定义仅用于显示的部件实例 | 5.1.6 Reset overconstraint checking controls | [ch05s01abv322.md](./chs/ch05s01abv322.md) | [ch05s01abv322.md](./eng/ch05s01abv322.md) |
| 5.1.6 重置过约束检查控制 | 5.1.7 Coupling constraints | [ch05s01abv323.md](./chs/ch05s01abv323.md) | [ch05s01abv323.md](./eng/ch05s01abv323.md) |
| 5.1.7 耦合约束 | 5.1.8 Define a part instance that will be used for display only | [ch05s01abv324.md](./chs/ch05s01abv324.md) | [ch05s01abv324.md](./eng/ch05s01abv324.md) |
| 5.1.11 指定几何缺陷和参数形状变化 | 5.1.9 Embedded element technique | [ch05s01abv325.md](./chs/ch05s01abv325.md) | [ch05s01abv325.md](./eng/ch05s01abv325.md) |
| 5.1.9 嵌入单元技术 | 5.1.10 Establishing geostatic equilibrium when the initial stress state is unknown | [ch05s01abv326.md](./chs/ch05s01abv326.md) | [ch05s01abv326.md](./eng/ch05s01abv326.md) |
| 5.1.10 在初始应力状态未知时建立地静平衡 | 5.1.11 Specifying geometric imperfection and parameter shape variation | [ch05s01abv327.md](./chs/ch05s01abv327.md) | [ch05s01abv327.md](./eng/ch05s01abv327.md) |
| 5.1.14 运动耦合约束 | 5.1.12 Inertia-based load balancing | [ch05s01abv328.md](./chs/ch05s01abv328.md) | [ch05s01abv328.md](./eng/ch05s01abv328.md) |
| 5.1.12 基于惯性的载荷平衡 | 5.1.13 Defining the cutting surface | [ch05s01abv329.md](./chs/ch05s01abv329.md) | [ch05s01abv329.md](./eng/ch05s01abv329.md) |
| 5.1.13 定义切割面 | 5.1.14 Kinematic coupling constraint | [ch05s01abv330.md](./chs/ch05s01abv330.md) | [ch05s01abv330.md](./eng/ch05s01abv330.md) |
| 5.1.15 定义模型一部分的矩阵 | 5.1.15 Defining a matrix for part of a model | [ch05s01abv331.md](./chs/ch05s01abv331.md) | [ch05s01abv331.md](./eng/ch05s01abv331.md) |
| 5.1.16 网格无关的点焊 | 5.1.16 Mesh-independent spot welds | [ch05s01abv332.md](./chs/ch05s01abv332.md) | [ch05s01abv332.md](./eng/ch05s01abv332.md) |
| 5.1.17 多点约束 | 5.1.17 Multi-point constraints | [ch05s01abv333.md](./chs/ch05s01abv333.md) | [ch05s01abv333.md](./eng/ch05s01abv333.md) |
| 5.1.18 用户定义的坐标系 | 5.1.18 User-defined coordinate system | [ch05s01abv334.md](./chs/ch05s01abv334.md) | [ch05s01abv334.md](./eng/ch05s01abv334.md) |
| 5.1.19 预拉伸截面 | 5.1.19 Pre-tension section | [ch05s01abv335.md](./chs/ch05s01abv335.md) | [ch05s01abv335.md](./eng/ch05s01abv335.md) |
| 5.1.20 辐射视角因子定义：对称性和遮挡 | 5.1.20 Radiation view factor definition: symmetries and blocking | [ch05s01abv336.md](./chs/ch05s01abv336.md) | [ch05s01abv336.md](./eng/ch05s01abv336.md) |
| 5.1.21 释放旋转自由度 | 5.1.21 Release rotational degrees of freedom | [ch05s01abv337.md](./chs/ch05s01abv337.md) | [ch05s01abv337.md](./eng/ch05s01abv337.md) |
| 5.1.22 壳-实体耦合约束 | 5.1.22 Shell-to-solid coupling constraints | [ch05s01abv338.md](./chs/ch05s01abv338.md) | [ch05s01abv338.md](./eng/ch05s01abv338.md) |
| 5.1.23 外推 | 5.1.23 Extrapolation | [ch05s01abv339.md](./chs/ch05s01abv339.md) | [ch05s01abv339.md](./eng/ch05s01abv339.md) |
| 5.1.24 基于表面的流体空腔 | 5.1.24 Surface-based fluid cavities | [ch05s01abv340.md](./chs/ch05s01abv340.md) | [ch05s01abv340.md](./eng/ch05s01abv340.md) |
| 5.1.25 修正的接触压力-闭合关系 | 5.1.25 Modified contact pressure-overclosure relationship | [ch05s01abv341.md](./chs/ch05s01abv341.md) | [ch05s01abv341.md](./eng/ch05s01abv341.md) |
| 5.1.26 定义温度、场变量和压力应力值 | 5.1.26 Defining temperature, field variable, and pressure stress values | [ch05s01abv342.md](./chs/ch05s01abv342.md) | [ch05s01abv342.md](./eng/ch05s01abv342.md) |
| 5.1.27 基于表面的绑定约束 | 5.1.27 Surface-based tie constraint | [ch05s01abv343.md](./chs/ch05s01abv343.md) | [ch05s01abv343.md](./eng/ch05s01abv343.md) |
| 5.1.28 耦合孔隙-热单元 | 5.1.28 Coupled pore-thermal elements | [ch05s01abv344.md](./chs/ch05s01abv344.md) | [ch05s01abv344.md](./eng/ch05s01abv344.md) |
| 5.2 杂项输出选项 | 5.2 Miscellaneous output options | [ch05s02.md](./chs/ch05s02.md) | [ch05s02.md](./eng/ch05s02.md) |
| 5.2.1 编写单元矩阵输出记录 | 5.2.1 Writing element matrix output records | [ch05s02abv345.md](./chs/ch05s02abv345.md) | [ch05s02abv345.md](./eng/ch05s02abv345.md) |
| 5.2.2 子结构矩阵输出请求 | 5.2.2 Substructure matrix output request | [ch05s02abv346.md](./chs/ch05s02abv346.md) | [ch05s02abv346.md](./eng/ch05s02abv346.md) |
| 5.2.3 积分输出变量 | 5.2.3 Integrated output variables | [ch05s02abv347.md](./chs/ch05s02abv347.md) | [ch05s02abv347.md](./eng/ch05s02abv347.md) |
| 5.2.4 刚体运动输出变量 | 5.2.4 Rigid body motion output variables | [ch05s02abv348.md](./chs/ch05s02abv348.md) | [ch05s02abv348.md](./eng/ch05s02abv348.md) |
| 5.2.5 梁截面方向上的单元节点力 | 5.2.5 Element nodal forces in beam section orientation | [ch05s02abv349.md](./chs/ch05s02abv349.md) | [ch05s02abv349.md](./eng/ch05s02abv349.md) |

### OTHER
*Abaqus验证指南*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| Abaqus验证指南 | Introduction | [ami01.md](./chs/ami01.md) | [ami01.md](./eng/ami01.md) |
| Abaqus/Explicit | Product Index | [pdx01.md](./chs/pdx01.md) | [pdx01.md](./eng/pdx01.md) |
| Abaqus/Standard | Abaqus/Standard | [pdx01pdd01.md](./chs/pdx01pdd01.md) | [pdx01pdd01.md](./eng/pdx01pdd01.md) |
| Abaqus/Explicit | Abaqus/Explicit | [pdx01pdd02.md](./chs/pdx01pdd02.md) | [pdx01pdd02.md](./eng/pdx01pdd02.md) |
| Abaqus/CFD | Abaqus/CFD | [pdx01pdd03.md](./chs/pdx01pdd03.md) | [pdx01pdd03.md](./eng/pdx01pdd03.md) |
| Abaqus/CAE | Abaqus/CAE | [pdx01pdd04.md](./chs/pdx01pdd04.md) | [pdx01pdd04.md](./eng/pdx01pdd04.md) |
| Abaqus/AMS | Abaqus/AMS | [pdx01pdd05.md](./chs/pdx01pdd05.md) | [pdx01pdd05.md](./eng/pdx01pdd05.md) |
| Abaqus/Aqua | Abaqus/Aqua | [pdx01pdd06.md](./chs/pdx01pdd06.md) | [pdx01pdd06.md](./eng/pdx01pdd06.md) |
| Abaqus/Design | Abaqus/Design | [pdx01pdd07.md](./chs/pdx01pdd07.md) | [pdx01pdd07.md](./eng/pdx01pdd07.md) |

---

## 资源文件 / Resource Files

图片资源位于 `graphics/` 目录。

---

## 版权声明 / Copyright Notice

本翻译仅供学习研究使用，原文档版权归 Dassault Systèmes Simulia Corp. 所有。
This translation is for study and research purposes only. Original documentation copyright Dassault Systèmes Simulia Corp.