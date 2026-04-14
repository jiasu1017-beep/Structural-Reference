# Abaqus Benchmarks Guide (6.14)

## 文档索引 / Documentation Index

本手册为 ABAQUS 6.14 Abaqus Benchmarks Guide 的中文翻译版本。

**来源 / Source:** D:\SIMULIA\Documentation\docs\v6.14\books\bmk\

---

## 双语目录对照 / Bilingual Table of Contents

### CH01
*1 分析测试*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 1 分析测试 | 1 Analysis Tests | [ch01.md](./chs/ch01.md) | [ch01.md](./eng/ch01.md) |
| Abaqus 基准测试指南 | 1.1 Static stress/displacement analysis | [ch01s01.md](./chs/ch01s01.md) | [ch01s01.md](./eng/ch01s01.md) |
| 1.1.1 梁/间隙示例 | 1.1.1 Beam/gap example | [ch01s01ach01.md](./chs/ch01s01ach01.md) | [ch01s01ach01.md](./eng/ch01s01ach01.md) |
| 1.1.2 各向异性层合板分析 | 1.1.2 Analysis of an anisotropic layered plate | [ch01s01ach02.md](./chs/ch01s01ach02.md) | [ch01s01ach02.md](./eng/ch01s01ach02.md) |
| 1.1.3 圆柱弯曲中的复合壳 | 1.1.3 Composite shells in cylindrical bending | [ch01s01ach03.md](./chs/ch01s01ach03.md) | [ch01s01ach03.md](./eng/ch01s01ach03.md) |
| 1.1.4 承受内压的厚复合圆柱体 | 1.1.4 Thick composite cylinder subjected to internal pressure | [ch01s01ach04.md](./chs/ch01s01ach04.md) | [ch01s01ach04.md](./eng/ch01s01ach04.md) |
| 1.1.5 直管段和弯管段的均匀坍塌 | 1.1.5 Uniform collapse of straight and curved pipe segments | [ch01s01ach05.md](./chs/ch01s01ach05.md) | [ch01s01ach05.md](./eng/ch01s01ach05.md) |
| 1.1.6 浅圆柱形穹顶在点载荷下的突弹跳变 | 1.1.6 Snap-through of a shallow, cylindrical roof under a point load | [ch01s01ach06.md](./chs/ch01s01ach06.md) | [ch01s01ach06.md](./eng/ch01s01ach06.md) |
| 1.1.7 加压橡胶圆盘 | 1.1.7 Pressurized rubber disc | [ch01s01ach07.md](./chs/ch01s01ach07.md) | [ch01s01ach07.md](./eng/ch01s01ach07.md) |
| 1.1.8 带圆孔的弹性板单轴拉伸 | 1.1.8 Uniaxial stretching of an elastic sheet with a circular hole | [ch01s01ach08.md](./chs/ch01s01ach08.md) | [ch01s01ach08.md](./eng/ch01s01ach08.md) |
| 1.1.9 圆拉伸棒的颈缩 | 1.1.9 Necking of a round tensile bar | [ch01s01ach09.md](./chs/ch01s01ach09.md) | [ch01s01ach09.md](./eng/ch01s01ach09.md) |
| 1.1.10 混凝土坍落度测试 | 1.1.10 Concrete slump test | [ch01s01ach10.md](./chs/ch01s01ach10.md) | [ch01s01ach10.md](./eng/ch01s01ach10.md) |
| 1.1.11 Hertz接触问题 | 1.1.11 The Hertz contact problem | [ch01s01ach11.md](./chs/ch01s01ach11.md) | [ch01s01ach11.md](./eng/ch01s01ach11.md) |
| 1.1.12 管道的压溃 | 1.1.12 Crushing of a pipe | [ch01s01ach12.md](./chs/ch01s01ach12.md) | [ch01s01ach12.md](./eng/ch01s01ach12.md) |
| 1.1.13 圆柱的径向拉伸 | 1.1.13 Radial stretching of a cylinder | [ch01s01ach13.md](./chs/ch01s01ach13.md) | [ch01s01ach13.md](./eng/ch01s01ach13.md) |
| 1.2 屈曲分析 | 1.2 Buckling analysis | [ch01s02.md](./chs/ch01s02.md) | [ch01s02.md](./eng/ch01s02.md) |
| 1.2.1 梁的屈曲分析 | 1.2.1 Buckling analysis of beams | [ch01s02ach14.md](./chs/ch01s02ach14.md) | [ch01s02ach14.md](./eng/ch01s02ach14.md) |
| 1.2.2 平面外压作用下圆环的屈曲 | 1.2.2 Buckling of a ring in a plane under external pressure | [ch01s02ach15.md](./chs/ch01s02ach15.md) | [ch01s02ach15.md](./eng/ch01s02ach15.md) |
| 1.2.3 均匀轴向压力作用下圆柱壳的屈曲 | 1.2.3 Buckling of a cylindrical shell under uniform axial pressure | [ch01s02ach16.md](./chs/ch01s02ach16.md) | [ch01s02ach16.md](./eng/ch01s02ach16.md) |
| 1.2.4 简支方板的屈曲 | 1.2.4 Buckling of a simply supported square plate | [ch01s02ach17.md](./chs/ch01s02ach17.md) | [ch01s02ach17.md](./eng/ch01s02ach17.md) |
| 1.2.5 L型支架的侧向屈曲 | 1.2.5 Lateral buckling of an L-bracket | [ch01s02ach18.md](./chs/ch01s02ach18.md) | [ch01s02ach18.md](./eng/ch01s02ach18.md) |
| 1.2.6 具有一般接触的柱的屈曲 | 1.2.6 Buckling of a column with general contact | [ch01s02ach19.md](./chs/ch01s02ach19.md) | [ch01s02ach19.md](./eng/ch01s02ach19.md) |
| 1.3 动态应力/位移分析 | 1.3 Dynamic stress/displacement analysis | [ch01s03.md](./chs/ch01s03.md) | [ch01s03.md](./eng/ch01s03.md) |
| 1.3.1 悬臂梁的子空间动力分析 | 1.3.1 Subspace dynamic analysis of a cantilever beam | [ch01s03ach20.md](./chs/ch01s03ach20.md) | [ch01s03ach20.md](./eng/ch01s03ach20.md) |
| 1.3.2 点载荷下的双悬臂弹性梁 | 1.3.2 Double cantilever elastic beam under point load | [ch01s03ach21.md](./chs/ch01s03ach21.md) | [ch01s03ach21.md](./eng/ch01s03ach21.md) |
| 1.3.3 爆炸载荷圆柱面板 | 1.3.3 Explosively loaded cylindrical panel | [ch01s03ach22.md](./chs/ch01s03ach22.md) | [ch01s03ach22.md](./eng/ch01s03ach22.md) |
| 1.3.4 初始速度下的自由环：率无关与率相关塑性比较 | 1.3.4 Free ring under initial velocity: comparison of rate-independent and rate-dependent plasticity | [ch01s03ach23.md](./chs/ch01s03ach23.md) | [ch01s03ach23.md](./eng/ch01s03ach23.md) |
| 1.3.5 单自由度系统的大转动 | 1.3.5 Large rotation of a one degree of freedom system | [ch01s03ach24.md](./chs/ch01s03ach24.md) | [ch01s03ach24.md](./eng/ch01s03ach24.md) |
| 1.3.6 Abaqus/Standard 中刚体的运动 | 1.3.6 Motion of a rigid body in Abaqus/Standard | [ch01s03ach25.md](./chs/ch01s03ach25.md) | [ch01s03ach25.md](./eng/ch01s03ach25.md) |
| 1.3.7 Abaqus/Explicit 刚体动力学 | 1.3.7 Rigid body dynamics with Abaqus/Explicit | [ch01s03ach26.md](./chs/ch01s03ach26.md) | [ch01s03ach26.md](./eng/ch01s03ach26.md) |
| 1.3.8 旋转 MPC 验证：曲柄转动 | 1.3.8 Revolute MPC verification: rotation of a crank | [ch01s03ach27.md](./chs/ch01s03ach27.md) | [ch01s03ach27.md](./eng/ch01s03ach27.md) |
| 1.3.9 管道甩击模拟 | 1.3.9 Pipe whip simulation | [ch01s03ach28.md](./chs/ch01s03ach28.md) | [ch01s03ach28.md](./eng/ch01s03ach28.md) |
| 1.3.10 铜棒撞击 | 1.3.10 Impact of a copper rod | [ch01s03ach29.md](./chs/ch01s03ach29.md) | [ch01s03ach29.md](./eng/ch01s03ach29.md) |
| 1.3.11 旋转刚体的摩擦制动 | 1.3.11 Frictional braking of a rotating rigid body | [ch01s03ach30.md](./chs/ch01s03ach30.md) | [ch01s03ach30.md](./eng/ch01s03ach30.md) |
| 1.3.12 广义接触圆柱壳的压缩 | 1.3.12 Compression of cylindrical shells with general contact | [ch01s03ach31.md](./chs/ch01s03ach31.md) | [ch01s03ach31.md](./eng/ch01s03ach31.md) |
| 1.3.13 带驱动器的稳态滑动 | 1.3.13 Steady-state slip of a belt drive | [ch01s03ach32.md](./chs/ch01s03ach32.md) | [ch01s03ach32.md](./eng/ch01s03ach32.md) |
| 1.3.14 机动车碰撞模拟 | 1.3.14 Crash simulation of a motor vehicle | [ch01s03ach33.md](./chs/ch01s03ach33.md) | [ch01s03ach33.md](./eng/ch01s03ach33.md) |
| 1.3.15 桁架撞击刚性墙 | 1.3.15 Truss impact on a rigid wall | [ch01s03ach34.md](./chs/ch01s03ach34.md) | [ch01s03ach34.md](./eng/ch01s03ach34.md) |
| 1.3.16 弹丸贯穿板 | 1.3.16 Plate penetration by a projectile | [ch01s03ach35.md](./chs/ch01s03ach35.md) | [ch01s03ach35.md](./eng/ch01s03ach35.md) |
| 1.3.17 斜激波反射 | 1.3.17 Oblique shock reflections | [ch01s03ach36.md](./chs/ch01s03ach36.md) | [ch01s03ach36.md](./eng/ch01s03ach36.md) |
| 1.4 基于模态的动态分析 | 1.4 Mode-based dynamic analysis | [ch01s04.md](./chs/ch01s04.md) | [ch01s04.md](./eng/ch01s04.md) |
| 1.4.1 球壳的自由振动 | 1.4.1 Free vibrations of a spherical shell | [ch01s04ach37.md](./chs/ch01s04ach37.md) | [ch01s04ach37.md](./eng/ch01s04ach37.md) |
| 1.4.2 不同端部约束和载荷下梁的特征值分析 | 1.4.2 Eigenvalue analysis of a beam under various end constraints and loadings | [ch01s04ach38.md](./chs/ch01s04ach38.md) | [ch01s04ach38.md](./eng/ch01s04ach38.md) |
| 1.4.3 张力下电缆的振动 | 1.4.3 Vibration of a cable under tension | [ch01s04ach39.md](./chs/ch01s04ach39.md) | [ch01s04ach39.md](./eng/ch01s04ach39.md) |
| 1.4.4 带阻尼的自由振动和受迫振动 | 1.4.4 Free and forced vibrations with damping | [ch01s04ach40.md](./chs/ch01s04ach40.md) | [ch01s04ach40.md](./eng/ch01s04ach40.md) |
| 1.4.5 直接积分和模态叠加 Rayleigh 阻尼选项的验证 | 1.4.5 Verification of Rayleigh damping options with direct integration and modal superposition | [ch01s04ach41.md](./chs/ch01s04ach41.md) | [ch01s04ach41.md](./eng/ch01s04ach41.md) |
| 1.4.6 悬臂板特征值分析 | 1.4.6 Eigenvalue analysis of a cantilever plate | [ch01s04ach42.md](./chs/ch01s04ach42.md) | [ch01s04ach42.md](./eng/ch01s04ach42.md) |
| 1.4.7 旋转悬臂板的振动 | 1.4.7 Vibration of a rotating cantilever plate | [ch01s04ach43.md](./chs/ch01s04ach43.md) | [ch01s04ach43.md](./eng/ch01s04ach43.md) |
| 1.4.8 简支梁响应谱分析 | 1.4.8 Response spectrum analysis of a simply supported beam | [ch01s04ach44.md](./chs/ch01s04ach44.md) | [ch01s04ach44.md](./eng/ch01s04ach44.md) |
| 1.4.9 动态载荷下杆的线性分析 | 1.4.9 Linear analysis of a rod under dynamic loading | [ch01s04ach45.md](./chs/ch01s04ach45.md) | [ch01s04ach45.md](./eng/ch01s04ach45.md) |
| 1.4.10 喷气噪声激励的随机响应 | 1.4.10 Random response to jet noise excitation | [ch01s04ach46.md](./chs/ch01s04ach46.md) | [ch01s04ach46.md](./eng/ch01s04ach46.md) |
| 1.4.11 基座运动激励下悬臂的随机响应 | 1.4.11 Random response of a cantilever subjected to base motion | [ch01s04ach47.md](./chs/ch01s04ach47.md) | [ch01s04ach47.md](./eng/ch01s04ach47.md) |
| 1.4.12 受多基座运动激励的双悬臂 | 1.4.12 Double cantilever subjected to multiple base motions | [ch01s04ach48.md](./chs/ch01s04ach48.md) | [ch01s04ach48.md](./eng/ch01s04ach48.md) |
| 1.4.13 悬臂梁地震运动分析 | 1.4.13 Analysis of a cantilever subject to earthquake motion | [ch01s04ach49.md](./chs/ch01s04ach49.md) | [ch01s04ach49.md](./eng/ch01s04ach49.md) |
| 1.4.14 模态响应分析的残余模态 | 1.4.14 Residual modes for modal response analysis | [ch01s04ach50.md](./chs/ch01s04ach50.md) | [ch01s04ach50.md](./eng/ch01s04ach50.md) |
| 1.5 稳态传输分析 | 1.5 Steady-state transport analysis | [ch01s05.md](./chs/ch01s05.md) | [ch01s05.md](./eng/ch01s05.md) |
| 1.5.1 稳态传输分析 | 1.5.1 Steady-state transport analysis | [ch01s05ach51.md](./chs/ch01s05ach51.md) | [ch01s05ach51.md](./eng/ch01s05ach51.md) |
| 1.5.2 圆盘与基础接触的稳态旋转 | 1.5.2 Steady-state spinning of a disk in contact with a foundation | [ch01s05ach52.md](./chs/ch01s05ach52.md) | [ch01s05ach52.md](./eng/ch01s05ach52.md) |
| 1.6 热传递和热应力分析 | 1.6 Heat transfer and thermal-stress analysis | [ch01s06.md](./chs/ch01s06.md) | [ch01s06.md](./eng/ch01s06.md) |
| 1.6.1 温度脉冲的对流和扩散 | 1.6.1 Convection and diffusion of a temperature pulse | [ch01s06ach53.md](./chs/ch01s06ach53.md) | [ch01s06ach53.md](./eng/ch01s06ach53.md) |
| 1.6.2 方形固体冻结：二维斯蒂芬问题 | 1.6.2 Freezing of a square solid: the two-dimensional Stefan problem | [ch01s06ach54.md](./chs/ch01s06ach54.md) | [ch01s06ach54.md](./eng/ch01s06ach54.md) |
| 1.6.3 耦合温度-位移分析：一维间隙传导和辐射 | 1.6.3 Coupled temperature-displacement analysis: one-dimensional gap conductance and radiation | [ch01s06ach55.md](./chs/ch01s06ach55.md) | [ch01s06ach55.md](./eng/ch01s06ach55.md) |
| 1.6.4 无限板的淬火 | 1.6.4 Quenching of an infinite plate | [ch01s06ach56.md](./chs/ch01s06ach56.md) | [ch01s06ach56.md](./eng/ch01s06ach56.md) |
| 1.6.5 二维单元腔体辐射视角因子计算 | 1.6.5 Two-dimensional elemental cavity radiation view factor calculations | [ch01s06ach57.md](./chs/ch01s06ach57.md) | [ch01s06ach57.md](./eng/ch01s06ach57.md) |
| 1.6.6 轴对称单元腔体辐射视角因子计算 | 1.6.6 Axisymmetric elemental cavity radiation view factor calculations | [ch01s06ach58.md](./chs/ch01s06ach58.md) | [ch01s06ach58.md](./eng/ch01s06ach58.md) |
| 1.6.7 三维单元腔体辐射视角因子计算 | 1.6.7  Three-dimensional elemental cavity radiation view factor calculations | [ch01s06ach59.md](./chs/ch01s06ach59.md) | [ch01s06ach59.md](./eng/ch01s06ach59.md) |
| 1.6.8 平面翅片表面的辐射分析 | 1.6.8 Radiation analysis of a plane finned surface | [ch01s06ach60.md](./chs/ch01s06ach60.md) | [ch01s06ach60.md](./eng/ch01s06ach60.md) |
| 1.7 欧拉分析 | 1.7 Eulerian analysis | [ch01s07.md](./chs/ch01s07.md) | [ch01s07.md](./eng/ch01s07.md) |
| 1.7.1 坍塌水柱的欧拉分析 | 1.7.1 Eulerian analysis of a collapsing water column | [ch01s07ach61.md](./chs/ch01s07ach61.md) | [ch01s07ach61.md](./eng/ch01s07ach61.md) |
| 1.7.2 水压力作用下弹性坝的挠度 | 1.7.2 Deflection of an elastic dam under water pressure | [ch01s07ach62.md](./chs/ch01s07ach62.md) | [ch01s07ach62.md](./eng/ch01s07ach62.md) |
| 1.8 电磁分析 | 1.8 Electromagnetic analysis | [ch01s08.md](./chs/ch01s08.md) | [ch01s08.md](./eng/ch01s08.md) |
| 1.8.1 具有各种电极配置的压电立方体的特征值分析 | 1.8.1 Eigenvalue analysis of a piezoelectric cube with various electrode configurations | [ch01s08ach63.md](./chs/ch01s08ach63.md) | [ch01s08ach63.md](./eng/ch01s08ach63.md) |
| 1.8.2 压电材料的模态动态分析 | 1.8.2 Modal dynamic analysis for piezoelectric materials | [ch01s08ach64.md](./chs/ch01s08ach64.md) | [ch01s08ach64.md](./eng/ch01s08ach64.md) |
| 1.8.3 压电材料的稳态动态分析 | 1.8.3 Steady-state dynamic analysis for piezoelectric materials | [ch01s08ach65.md](./chs/ch01s08ach65.md) | [ch01s08ach65.md](./eng/ch01s08ach65.md) |
| 1.8.4 TEAM 2：振荡磁场中长圆柱导体的涡流模拟 | 1.8.4 TEAM 2: Eddy current simulations of long cylindrical conductors in an oscillating magnetic field | [ch01s08ach66.md](./chs/ch01s08ach66.md) | [ch01s08ach66.md](./eng/ch01s08ach66.md) |
| 1.8.5 TEAM 4：衰减磁场中导电砖块的涡流模拟 | 1.8.5 TEAM 4: Eddy current simulation of a conducting brick in a decaying magnetic field | [ch01s08ach67.md](./chs/ch01s08ach67.md) | [ch01s08ach67.md](./eng/ch01s08ach67.md) |
| 1.8.6 TEAM 6：振荡磁场中球形导体的涡流模拟 | 1.8.6 TEAM 6: Eddy current simulations for spherical conductors in an oscillating magnetic field | [ch01s08ach68.md](./chs/ch01s08ach68.md) | [ch01s08ach68.md](./eng/ch01s08ach68.md) |
| 1.8.7 TEAM 13：三维非线性静磁分析 | 1.8.7 TEAM 13: Three-dimensional nonlinear magnetostatic analysis | [ch01s08ach69.md](./chs/ch01s08ach69.md) | [ch01s08ach69.md](./eng/ch01s08ach69.md) |
| 1.8.8 携带时间谐电流的环绕线圈对圆柱棒的感应加热 | 1.8.8 Induction heating of a cylindrical rod by an encircling coil carrying time-harmonic current | [ch01s08ach70.md](./chs/ch01s08ach70.md) | [ch01s08ach70.md](./eng/ch01s08ach70.md) |
| 1.9 耦合孔隙流体流动和应力分析 | 1.9 Coupled pore fluid flow and stress analysis | [ch01s09.md](./chs/ch01s09.md) | [ch01s09.md](./eng/ch01s09.md) |
| 1.9.1 多孔介质中的部分饱和流动 | 1.9.1 Partially saturated flow in a porous medium | [ch01s09ach71.md](./chs/ch01s09ach71.md) | [ch01s09ach71.md](./eng/ch01s09ach71.md) |
| 1.9.2 多孔介质的润湿性需求：耦合分析 | 1.9.2 Demand wettability of a porous medium: coupled analysis | [ch01s09ach72.md](./chs/ch01s09ach72.md) | [ch01s09ach72.md](./eng/ch01s09ach72.md) |
| 1.9.3 部分饱和多孔介质中的毛细吸水 | 1.9.3 Wicking in a partially saturated porous medium | [ch01s09ach73.md](./chs/ch01s09ach73.md) | [ch01s09ach73.md](./eng/ch01s09ach73.md) |
| 1.9.4 多孔材料柱中的排水 | 1.9.4 Desaturation in a column of porous material | [ch01s09ach74.md](./chs/ch01s09ach74.md) | [ch01s09ach74.md](./eng/ch01s09ach74.md) |
| 1.10 质量扩散分析 | 1.10 Mass diffusion analysis | [ch01s10.md](./chs/ch01s10.md) | [ch01s10.md](./eng/ch01s10.md) |
| 1.10.1 弯曲梁中氢的热机械扩散 | 1.10.1 Thermo-mechanical diffusion of hydrogen in a bending beam | [ch01s10ach75.md](./chs/ch01s10ach75.md) | [ch01s10ach75.md](./eng/ch01s10ach75.md) |
| 1.11 声学分析 | 1.11 Acoustic analysis | [ch01s11.md](./chs/ch01s11.md) | [ch01s11.md](./eng/ch01s11.md) |
| 1.11.1 简单的耦合声学-结构分析 | 1.11.1 A simple coupled acoustic-structural analysis | [ch01s11ach76.md](./chs/ch01s11ach76.md) | [ch01s11ach76.md](./eng/ch01s11ach76.md) |
| 1.11.2 点载荷充液球壳的分析 | 1.11.2 Analysis of a point-loaded, fluid-filled, spherical shell | [ch01s11ach77.md](./chs/ch01s11ach77.md) | [ch01s11ach77.md](./eng/ch01s11ach77.md) |
| 1.11.3 呼吸模式下球体的声辐射阻抗 | 1.11.3 Acoustic radiation impedance of a sphere in breathing mode | [ch01s11ach78.md](./chs/ch01s11ach78.md) | [ch01s11ach78.md](./eng/ch01s11ach78.md) |
| 1.11.4 无限声学介质中的声-结构相互作用 | 1.11.4 Acoustic-structural interaction in an infinite acoustic medium | [ch01s11ach79.md](./chs/ch01s11ach79.md) | [ch01s11ach79.md](./eng/ch01s11ach79.md) |
| 1.11.5 二维声学-声学绑定约束 | 1.11.5 Acoustic-acoustic tie constraint in two dimensions | [ch01s11ach80.md](./chs/ch01s11ach80.md) | [ch01s11ach80.md](./eng/ch01s11ach80.md) |
| 1.11.6 三维声学-声学绑定约束 | 1.11.6 Acoustic-acoustic tie constraint in three dimensions | [ch01s11ach81.md](./chs/ch01s11ach81.md) | [ch01s11ach81.md](./eng/ch01s11ach81.md) |
| 1.11.7 简单的稳态动态声学分析 | 1.11.7 A simple steady-state dynamic acoustic analysis | [ch01s11ach82.md](./chs/ch01s11ach82.md) | [ch01s11ach82.md](./eng/ch01s11ach82.md) |
| 1.11.8 带平均流动的导管声学分析 | 1.11.8 Acoustic analysis of a duct with mean flow | [ch01s11ach83.md](./chs/ch01s11ach83.md) | [ch01s11ach83.md](./eng/ch01s11ach83.md) |
| 1.11.9 外部声学特征分析 | 1.11.9 Real exterior acoustic eigenanalysis | [ch01s11ach84.md](./chs/ch01s11ach84.md) | [ch01s11ach84.md](./eng/ch01s11ach84.md) |
| 1.11.10 耦合外部声学特征分析 | 1.11.10 Coupled exterior acoustic eigenanalysis | [ch01s11ach85.md](./chs/ch01s11ach85.md) | [ch01s11ach85.md](./eng/ch01s11ach85.md) |
| 1.11.11 刚性球体的声散射 | 1.11.11 Acoustic scattering from a rigid sphere | [ch01s11ach86.md](./chs/ch01s11ach86.md) | [ch01s11ach86.md](./eng/ch01s11ach86.md) |
| 1.11.12 弹性球壳的声散射 | 1.11.12 Acoustic scattering from an elastic spherical shell | [ch01s11ach87.md](./chs/ch01s11ach87.md) | [ch01s11ach87.md](./eng/ch01s11ach87.md) |
| 1.12 自适应分析 | 1.12 Adaptivity analysis | [ch01s12.md](./chs/ch01s12.md) | [ch01s12.md](./eng/ch01s12.md) |
| 1.12.1 不同材料的压痕 | 1.12.1 Indentation with different materials | [ch01s12ach88.md](./chs/ch01s12ach88.md) | [ch01s12ach88.md](./eng/ch01s12ach88.md) |
| 1.12.2 不同材料的波传播 | 1.12.2 Wave propagation with different materials | [ch01s12ach89.md](./chs/ch01s12ach89.md) | [ch01s12ach89.md](./eng/ch01s12ach89.md) |
| 1.12.3 不同材料的自适应网格划分补丁测试 | 1.12.3 Adaptivity patch test with different materials | [ch01s12ach90.md](./chs/ch01s12ach90.md) | [ch01s12ach90.md](./eng/ch01s12ach90.md) |
| 1.12.4 冲击管中的波传播 | 1.12.4 Wave propagation in a shock tube | [ch01s12ach91.md](./chs/ch01s12ach91.md) | [ch01s12ach91.md](./eng/ch01s12ach91.md) |
| 1.12.5 冲击管中压实波的传播 | 1.12.5 Propagation of a compaction wave in a shock tube | [ch01s12ach92.md](./chs/ch01s12ach92.md) | [ch01s12ach92.md](./eng/ch01s12ach92.md) |
| 1.12.6 旋转坐标系中的平流 | 1.12.6 Advection in a rotating frame | [ch01s12ach93.md](./chs/ch01s12ach93.md) | [ch01s12ach93.md](./eng/ch01s12ach93.md) |
| 1.12.7 俯仰水箱中的水晃动 | 1.12.7 Water sloshing in a pitching tank | [ch01s12ach94.md](./chs/ch01s12ach94.md) | [ch01s12ach94.md](./eng/ch01s12ach94.md) |
| 1.13 Abaqus/Aqua 分析 | 1.13 Abaqus/Aqua analysis | [ch01s13.md](./chs/ch01s13.md) | [ch01s13.md](./eng/ch01s13.md) |
| 1.13.1 直接铺设于海底的管道拉入 | 1.13.1 Pull-in of a pipeline lying directly on the seafloor | [ch01s13ach95.md](./chs/ch01s13ach95.md) | [ch01s13ach95.md](./eng/ch01s13ach95.md) |
| 1.13.2 海底管道拉入和拖曳 | 1.13.2 Near bottom pipeline pull-in and tow | [ch01s13ach96.md](./chs/ch01s13ach96.md) | [ch01s13ach96.md](./eng/ch01s13ach96.md) |
| 1.13.3 承受曳引的细长管道："风中的芦苇" | 1.13.3 Slender pipe subject to drag: the “reed in the wind” | [ch01s13ach97.md](./chs/ch01s13ach97.md) | [ch01s13ach97.md](./eng/ch01s13ach97.md) |
| 1.14 水下冲击分析 | 1.14 Underwater shock analysis | [ch01s14.md](./chs/ch01s14.md) | [ch01s14.md](./eng/ch01s14.md) |
| 1.14.3 浸没无限圆柱问题 | 1.14.3 The submerged infinite cylinder problem | [ch01s14ach100.md](./chs/ch01s14ach100.md) | [ch01s14ach100.md](./eng/ch01s14ach100.md) |
| 1.14.4 一维空化问题 | 1.14.4 The one-dimensional cavitation problem | [ch01s14ach101.md](./chs/ch01s14ach101.md) | [ch01s14ach101.md](./eng/ch01s14ach101.md) |
| 1.14.5 平板对平面指数衰减冲击波的响应 | 1.14.5 Plate response to a planar exponentially decaying shock wave | [ch01s14ach102.md](./chs/ch01s14ach102.md) | [ch01s14ach102.md](./eng/ch01s14ach102.md) |
| 1.14.6 圆柱壳对平面阶跃冲击波的响应 | 1.14.6 Cylindrical shell response to a planar step shock wave | [ch01s14ach103.md](./chs/ch01s14ach103.md) | [ch01s14ach103.md](./eng/ch01s14ach103.md) |
| 1.14.7 圆柱壳对平面指数衰减冲击波的响应 | 1.14.7 Cylindrical shell response to a planar exponentially decaying shock wave | [ch01s14ach104.md](./chs/ch01s14ach104.md) | [ch01s14ach104.md](./eng/ch01s14ach104.md) |
| 1.14.8 球壳对平面阶跃波的响应 | 1.14.8 Spherical shell response to a planar step wave | [ch01s14ach105.md](./chs/ch01s14ach105.md) | [ch01s14ach105.md](./eng/ch01s14ach105.md) |
| 1.14.9 球壳对平面指数衰减波的响应 | 1.14.9 Spherical shell response to a planar exponentially decaying wave | [ch01s14ach106.md](./chs/ch01s14ach106.md) | [ch01s14ach106.md](./eng/ch01s14ach106.md) |
| 1.14.10 球壳对球形指数衰减波的响应 | 1.14.10 Spherical shell response to a spherical exponentially decaying wave | [ch01s14ach107.md](./chs/ch01s14ach107.md) | [ch01s14ach107.md](./eng/ch01s14ach107.md) |
| 1.14.11 空气背衬耦合板对平面指数衰减波的响应 | 1.14.11 Air-backed coupled plate response to a planar exponentially decaying wave | [ch01s14ach108.md](./chs/ch01s14ach108.md) | [ch01s14ach108.md](./eng/ch01s14ach108.md) |
| 1.14.12 水背衬耦合板对平面指数衰减波的响应 | 1.14.12 Water-backed coupled plate response to a planar exponentially decaying wave | [ch01s14ach109.md](./chs/ch01s14ach109.md) | [ch01s14ach109.md](./eng/ch01s14ach109.md) |
| 1.14.13 耦合圆柱壳对平面阶跃波的响应 | 1.14.13 Coupled cylindrical shell response to a planar step wave | [ch01s14ach110.md](./chs/ch01s14ach110.md) | [ch01s14ach110.md](./eng/ch01s14ach110.md) |
| 1.14.14 耦合球壳对平面阶跃波的响应 | 1.14.14 Coupled spherical shell response to a planar step wave | [ch01s14ach111.md](./chs/ch01s14ach111.md) | [ch01s14ach111.md](./eng/ch01s14ach111.md) |
| 1.14.15 流体填充球壳对平面阶跃波的响应 | 1.14.15 Fluid-filled spherical shell response to a planar step wave | [ch01s14ach112.md](./chs/ch01s14ach112.md) | [ch01s14ach112.md](./eng/ch01s14ach112.md) |
| 1.14.16 梁单元对平面波的响应 | 1.14.16 Response of beam elements to a planar wave | [ch01s14ach113.md](./chs/ch01s14ach113.md) | [ch01s14ach113.md](./eng/ch01s14ach113.md) |
| 1.14.1 一维水下冲击分析 | 1.14.1 One-dimensional underwater shock analysis | [ch01s14ach98.md](./chs/ch01s14ach98.md) | [ch01s14ach98.md](./eng/ch01s14ach98.md) |
| 1.14.2 浸没球体问题 | 1.14.2 The submerged sphere problem | [ch01s14ach99.md](./chs/ch01s14ach99.md) | [ch01s14ach99.md](./eng/ch01s14ach99.md) |
| 1.15 土力学分析 | 1.15 Soils analysis | [ch01s15.md](./chs/ch01s15.md) | [ch01s15.md](./eng/ch01s15.md) |
| 1.15.1 Terzaghi 固结问题 | 1.15.1 The Terzaghi consolidation problem | [ch01s15ach114.md](./chs/ch01s15ach114.md) | [ch01s15ach114.md](./eng/ch01s15ach114.md) |
| 1.15.2 三轴测试样本的固结 | 1.15.2 Consolidation of a triaxial test specimen | [ch01s15ach115.md](./chs/ch01s15ach115.md) | [ch01s15ach115.md](./eng/ch01s15ach115.md) |
| 1.15.3 二维固体的有限应变固结 | 1.15.3 Finite-strain consolidation of a two-dimensional solid | [ch01s15ach116.md](./chs/ch01s15ach116.md) | [ch01s15ach116.md](./eng/ch01s15ach116.md) |
| 1.15.4 粒状材料极限载荷计算 | 1.15.4 Limit load calculations with granular materials | [ch01s15ach117.md](./chs/ch01s15ach117.md) | [ch01s15ach117.md](./eng/ch01s15ach117.md) |
| 1.15.5 弹塑性粒状材料的有限变形 | 1.15.5 Finite deformation of an elastic-plastic granular material | [ch01s15ach118.md](./chs/ch01s15ach118.md) | [ch01s15ach118.md](./eng/ch01s15ach118.md) |
| 1.15.6 一维热固结问题 | 1.15.6 The one-dimensional thermal consolidation problem | [ch01s15ach119.md](./chs/ch01s15ach119.md) | [ch01s15ach119.md](./eng/ch01s15ach119.md) |
| 1.15.7 圆柱热源周围的固结 | 1.15.7 Consolidation around a cylindrical heat source | [ch01s15ach120.md](./chs/ch01s15ach120.md) | [ch01s15ach120.md](./eng/ch01s15ach120.md) |
| 1.16 断裂力学 | 1.16 Fracture mechanics | [ch01s16.md](./chs/ch01s16.md) | [ch01s16.md](./eng/ch01s16.md) |
| 1.16.1 轮廓积分评估：二维情况 | 1.16.1 Contour integral evaluation: two-dimensional case | [ch01s16ach121.md](./chs/ch01s16ach121.md) | [ch01s16ach121.md](./eng/ch01s16ach121.md) |
| 1.16.3 中心斜裂纹板在拉力作用下 | 1.16.2 Contour integral evaluation: three-dimensional case | [ch01s16ach122.md](./chs/ch01s16ach122.md) | [ch01s16ach122.md](./eng/ch01s16ach122.md) |
| 1.16.2 轮廓积分评估：三维情况 | 1.16.3 Center slant cracked plate under tension | [ch01s16ach123.md](./chs/ch01s16ach123.md) | [ch01s16ach123.md](./eng/ch01s16ach123.md) |
| 1.16.4 集中力作用下的币形裂纹 | 1.16.4 A penny-shaped crack under concentrated forces | [ch01s16ach124.md](./chs/ch01s16ach124.md) | [ch01s16ach124.md](./eng/ch01s16ach124.md) |
| 1.16.5 完全塑性 J 积分评估 | 1.16.5 Fully plastic J-integral evaluation | [ch01s16ach125.md](./chs/ch01s16ach125.md) | [ch01s16ach125.md](./eng/ch01s16ach125.md) |
| 1.16.6 Ct 积分评估 | 1.16.6 Ct-integral evaluation | [ch01s16ach126.md](./chs/ch01s16ach126.md) | [ch01s16ach126.md](./eng/ch01s16ach126.md) |
| 1.16.7 非均匀裂纹面加载和 J 积分 | 1.16.7 Nonuniform crack-face loading and J-integrals | [ch01s16ach127.md](./chs/ch01s16ach127.md) | [ch01s16ach127.md](./eng/ch01s16ach127.md) |
| 1.16.8 热载荷下的单边缺口标本 | 1.16.8 Single-edged notched specimen under a thermal load | [ch01s16ach128.md](./chs/ch01s16ach128.md) | [ch01s16ach128.md](./eng/ch01s16ach128.md) |
| 1.17 子结构 | 1.17 Substructures | [ch01s17.md](./chs/ch01s17.md) | [ch01s17.md](./eng/ch01s17.md) |
| 1.17.1 使用子结构的框架分析 | 1.17.1 Analysis of a frame using substructures | [ch01s17ach129.md](./chs/ch01s17ach129.md) | [ch01s17ach129.md](./eng/ch01s17ach129.md) |
| 1.18 设计灵敏度分析 | 1.18 Design sensitivity analysis | [ch01s18.md](./chs/ch01s18.md) | [ch01s18.md](./eng/ch01s18.md) |
| 1.18.1 悬臂梁设计灵敏度分析 | 1.18.1 Design sensitivity analysis for cantilever beam | [ch01s18ach130.md](./chs/ch01s18ach130.md) | [ch01s18ach130.md](./eng/ch01s18ach130.md) |
| 1.18.2 单轴拉伸下圆形孔板应力集中系数灵敏度 | 1.18.2 Sensitivity of the stress concentration factor around a circular hole in a plate under uniaxial tension | [ch01s18ach131.md](./chs/ch01s18ach131.md) | [ch01s18ach131.md](./eng/ch01s18ach131.md) |
| 1.18.3 修改后的 NAFEMS 问题 3DNLG-1 灵敏度分析：端载荷下 Z 形悬臂梁的大挠度 | 1.18.3 Sensitivity analysis of modified NAFEMS problem 3DNLG-1: Large deflection of Z-shaped cantilever under an end load | [ch01s18ach132.md](./chs/ch01s18ach132.md) | [ch01s18ach132.md](./eng/ch01s18ach132.md) |
| 1.19 使用 XFEM 建模不连续性 | 1.19 Modeling discontinuities using XFEM | [ch01s19.md](./chs/ch01s19.md) | [ch01s19.md](./eng/ch01s19.md) |
| 1.19.1 使用 XFEM 模拟的单边缺口裂纹扩展 | 1.19.1 Crack propagation of a single-edge notch simulated using XFEM | [ch01s19ach133.md](./chs/ch01s19ach133.md) | [ch01s19ach133.md](./eng/ch01s19ach133.md) |
| 1.19.2 使用 XFEM 模拟的带孔板中裂纹扩展 | 1.19.2 Crack propagation in a plate with a hole simulated using XFEM | [ch01s19ach134.md](./chs/ch01s19ach134.md) | [ch01s19ach134.md](./eng/ch01s19ach134.md) |
| 1.19.3 使用 XFEM 模拟冲击载荷下梁中的裂纹扩展 | 1.19.3 Crack propagation in a beam under impact loading simulated using XFEM | [ch01s19ach135.md](./chs/ch01s19ach135.md) | [ch01s19ach135.md](./eng/ch01s19ach135.md) |
| 1.19.4 使用 XFEM 模拟单边缺口的动态剪切失效 | 1.19.4 Dynamic shear failure of a single-edge notch simulated using XFEM | [ch01s19ach136.md](./chs/ch01s19ach136.md) | [ch01s19ach136.md](./eng/ch01s19ach136.md) |
| 1.19.5 使用 XFEM 的水力驱动断裂扩展 | 1.19.5 Propagation of hydraulically driven fracture using XFEM | [ch01s19ach137.md](./chs/ch01s19ach137.md) | [ch01s19ach137.md](./eng/ch01s19ach137.md) |

### CH02
*2 单元测试*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 2 单元测试 | 2 Element Tests | [ch02.md](./chs/ch02.md) | [ch02.md](./eng/ch02.md) |
| 2.1 连续体单元 | 2.1 Continuum elements | [ch02s01.md](./chs/ch02s01.md) | [ch02s01.md](./eng/ch02s01.md) |
| 2.1.1 空心圆柱的扭转 | 2.1.1 Torsion of a hollow cylinder | [ch02s01ach138.md](./chs/ch02s01ach138.md) | [ch02s01ach138.md](./eng/ch02s01ach138.md) |
| 2.1.2 悬臂梁的几何非线性分析 | 2.1.2 Geometrically nonlinear analysis of a cantilever beam | [ch02s01ach139.md](./chs/ch02s01ach139.md) | [ch02s01ach139.md](./eng/ch02s01ach139.md) |
| 2.1.3 使用CAXA和SAXA单元分析悬臂梁 | 2.1.3 Cantilever beam analyzed with CAXA and SAXA elements | [ch02s01ach140.md](./chs/ch02s01ach140.md) | [ch02s01ach140.md](./eng/ch02s01ach140.md) |
| 2.1.4 管道自重引起的双点弯曲：CAXA和SAXA单元 | 2.1.4 Two-point bending of a pipe due to self weight: CAXA and SAXA elements | [ch02s01ach141.md](./chs/ch02s01ach141.md) | [ch02s01ach141.md](./eng/ch02s01ach141.md) |
| 2.1.5 Cook膜问题 | 2.1.5 Cook's membrane problem | [ch02s01ach142.md](./chs/ch02s01ach142.md) | [ch02s01ach142.md](./eng/ch02s01ach142.md) |
| 2.2 无限单元 | 2.2 Infinite elements | [ch02s02.md](./chs/ch02s02.md) | [ch02s02.md](./eng/ch02s02.md) |
| 2.2.1 无限介质中的波传播 | 2.2.1 Wave propagation in an infinite medium | [ch02s02ach143.md](./chs/ch02s02ach143.md) | [ch02s02ach143.md](./eng/ch02s02ach143.md) |
| 2.2.2 无限单元：布西内斯克问题和弗拉芒问题 | 2.2.2 Infinite elements: the Boussinesq and Flamant problems | [ch02s02ach144.md](./chs/ch02s02ach144.md) | [ch02s02ach144.md](./eng/ch02s02ach144.md) |
| 2.2.3 无限单元：半空间上的圆形荷载 | 2.2.3 Infinite elements: circular load on half-space | [ch02s02ach145.md](./chs/ch02s02ach145.md) | [ch02s02ach145.md](./eng/ch02s02ach145.md) |
| 2.2.4 无限介质中的球形空腔 | 2.2.4 Spherical cavity in an infinite medium | [ch02s02ach146.md](./chs/ch02s02ach146.md) | [ch02s02ach146.md](./eng/ch02s02ach146.md) |
| 2.3 结构单元 | 2.3 Structural elements | [ch02s03.md](./chs/ch02s03.md) | [ch02s03.md](./eng/ch02s03.md) |
| 2.3.1 筒拱屋顶问题 | 2.3.1 The barrel vault roof problem | [ch02s03ach147.md](./chs/ch02s03ach147.md) | [ch02s03ach147.md](./eng/ch02s03ach147.md) |
| 2.3.2 圆柱压痕问题 | 2.3.2 The pinched cylinder problem | [ch02s03ach148.md](./chs/ch02s03ach148.md) | [ch02s03ach148.md](./eng/ch02s03ach148.md) |
| 2.3.3 球壳压痕问题 | 2.3.3 The pinched sphere problem | [ch02s03ach149.md](./chs/ch02s03ach149.md) | [ch02s03ach149.md](./eng/ch02s03ach149.md) |
| 2.3.4 壳单元的斜交敏感性 | 2.3.4 Skew sensitivity of shell elements | [ch02s03ach150.md](./chs/ch02s03ach150.md) | [ch02s03ach150.md](./eng/ch02s03ach150.md) |
| 2.3.5 连续体单元和壳单元在弯曲问题线性分析中的性能 | 2.3.5 Performance of continuum and shell elements for linear analysis of bending problems | [ch02s03ach151.md](./chs/ch02s03ach151.md) | [ch02s03ach151.md](./eng/ch02s03ach151.md) |
| 2.3.6 悬臂钩端部的平面内剪切荷载 | 2.3.6 Tip in-plane shear load on a cantilevered hook | [ch02s03ach152.md](./chs/ch02s03ach152.md) | [ch02s03ach152.md](./eng/ch02s03ach152.md) |
| 2.3.7 扭曲梁的分析 | 2.3.7 Analysis of a twisted beam | [ch02s03ach153.md](./chs/ch02s03ach153.md) | [ch02s03ach153.md](./eng/ch02s03ach153.md) |
| 2.3.8 壳的扭曲带测试 | 2.3.8 Twisted ribbon test for shells | [ch02s03ach154.md](./chs/ch02s03ach154.md) | [ch02s03ach154.md](./eng/ch02s03ach154.md) |
| 2.3.9 带施加弯矩的壳带测试 | 2.3.9 Ribbon test for shells with applied moments | [ch02s03ach155.md](./chs/ch02s03ach155.md) | [ch02s03ach155.md](./eng/ch02s03ach155.md) |
| 2.3.10 三点支撑的三角形板弯曲 | 2.3.10 Triangular plate-bending on three point supports | [ch02s03ach156.md](./chs/ch02s03ach156.md) | [ch02s03ach156.md](./eng/ch02s03ach156.md) |
| 2.3.11 承受均匀热载荷的壳单元 | 2.3.11 Shell elements subjected to uniform thermal loading | [ch02s03ach157.md](./chs/ch02s03ach157.md) | [ch02s03ach157.md](./eng/ch02s03ach157.md) |
| 2.3.12 端部荷载下的壳弯曲 | 2.3.12 Shell bending under a tip load | [ch02s03ach158.md](./chs/ch02s03ach158.md) | [ch02s03ach158.md](./eng/ch02s03ach158.md) |
| 2.3.13 变厚度壳和膜 | 2.3.13 Variable thickness shells and membranes | [ch02s03ach159.md](./chs/ch02s03ach159.md) | [ch02s03ach159.md](./eng/ch02s03ach159.md) |
| 2.3.14 浅球壳的瞬态响应 | 2.3.14 Transient response of a shallow spherical cap | [ch02s03ach160.md](./chs/ch02s03ach160.md) | [ch02s03ach160.md](./eng/ch02s03ach160.md) |
| 2.3.15 螺旋桨旋转模拟 | 2.3.15 Simulation of propeller rotation | [ch02s03ach161.md](./chs/ch02s03ach161.md) | [ch02s03ach161.md](./eng/ch02s03ach161.md) |
| 2.4 声学单元 | 2.4 Acoustic elements | [ch02s04.md](./chs/ch02s04.md) | [ch02s04.md](./eng/ch02s04.md) |
| 2.4.1 密闭空腔的声学模态 | 2.4.1 Acoustic modes of an enclosed cavity | [ch02s04ach162.md](./chs/ch02s04ach162.md) | [ch02s04ach162.md](./eng/ch02s04ach162.md) |
| 2.5 流体单元 | 2.5 Fluid elements | [ch02s05.md](./chs/ch02s05.md) | [ch02s05.md](./eng/ch02s05.md) |
| 2.5.1 充液橡胶囊 | 2.5.1 Fluid filled rubber bladders | [ch02s05ach163.md](./chs/ch02s05ach163.md) | [ch02s05ach163.md](./eng/ch02s05ach163.md) |
| 2.6 连接器单元 | 2.6 Connector elements | [ch02s06.md](./chs/ch02s06.md) | [ch02s06.md](./eng/ch02s06.md) |
| 2.6.1 二自由度系统的动态响应 | 2.6.1 Dynamic response of a two degree of freedom system | [ch02s06ach164.md](./chs/ch02s06ach164.md) | [ch02s06ach164.md](./eng/ch02s06ach164.md) |
| 2.6.2 弹簧和阻尼元件的线性行为 | 2.6.2 Linear behavior of spring and dashpot elements | [ch02s06ach165.md](./chs/ch02s06ach165.md) | [ch02s06ach165.md](./eng/ch02s06ach165.md) |
| 2.7 专用单元 | 2.7 Special-purpose elements | [ch02s07.md](./chs/ch02s07.md) | [ch02s07.md](./eng/ch02s07.md) |
| 2.7.1 层合复合材料的分层分析 | 2.7.1 Delamination analysis of laminated composites | [ch02s07ach166.md](./chs/ch02s07ach166.md) | [ch02s07ach166.md](./eng/ch02s07ach166.md) |

### CH03
*3 材料测试*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 3 材料测试 | 3 Material Tests | [ch03.md](./chs/ch03.md) | [ch03.md](./eng/ch03.md) |
| 3.1 弹性 | 3.1 Elasticity | [ch03s01.md](./chs/ch03s01.md) | [ch03s01.md](./eng/ch03s01.md) |
| 3.1.1 承受恒定轴向荷载的粘弹性杆 | 3.1.1 Viscoelastic rod subjected to constant axial load | [ch03s01ach167.md](./chs/ch03s01ach167.md) | [ch03s01ach167.md](./eng/ch03s01ach167.md) |
| 3.1.2 粘弹性板的热瞬态加载 | 3.1.2 Transient thermal loading of a viscoelastic slab | [ch03s01ach168.md](./chs/ch03s01ach168.md) | [ch03s01ach168.md](./eng/ch03s01ach168.md) |
| 3.1.3 均匀应变的粘塑性桁架 | 3.1.3 Uniform strain, viscoplastic truss | [ch03s01ach169.md](./chs/ch03s01ach169.md) | [ch03s01ach169.md](./eng/ch03s01ach169.md) |
| 3.1.4 橡胶试验数据的拟合 | 3.1.4 Fitting of rubber test data | [ch03s01ach170.md](./chs/ch03s01ach170.md) | [ch03s01ach170.md](./eng/ch03s01ach170.md) |
| 3.1.5 弹性泡沫试验数据的拟合 | 3.1.5 Fitting of elastomeric foam test data | [ch03s01ach171.md](./chs/ch03s01ach171.md) | [ch03s01ach171.md](./eng/ch03s01ach171.md) |
| 3.1.6 单轴拉伸下的橡胶 | 3.1.6 Rubber under uniaxial tension | [ch03s01ach172.md](./chs/ch03s01ach172.md) | [ch03s01ach172.md](./eng/ch03s01ach172.md) |
| 3.1.7 动脉层的各向异性超弹性建模 | 3.1.7 Anisotropic hyperelastic modeling of arterial layers | [ch03s01ach173.md](./chs/ch03s01ach173.md) | [ch03s01ach173.md](./eng/ch03s01ach173.md) |
| 3.2 塑性和蠕变 | 3.2 Plasticity and creep | [ch03s02.md](./chs/ch03s02.md) | [ch03s02.md](./eng/ch03s02.md) |
| 3.2.1 均匀加载的弹塑性板 | 3.2.1 Uniformly loaded, elastic-plastic plate | [ch03s02ach174.md](./chs/ch03s02ach174.md) | [ch03s02ach174.md](./eng/ch03s02ach174.md) |
| 3.2.2 ORNL塑性理论在双轴加载下的测试 | 3.2.2 Test of ORNL plasticity theory under biaxial loading | [ch03s02ach175.md](./chs/ch03s02ach175.md) | [ch03s02ach175.md](./eng/ch03s02ach175.md) |
| 3.2.3 单向钢筋混凝土板 | 3.2.3 One-way reinforced concrete slab | [ch03s02ach176.md](./chs/ch03s02ach176.md) | [ch03s02ach176.md](./eng/ch03s02ach176.md) |
| 3.2.4 饱和粘土的三轴测试 | 3.2.4 Triaxial tests on a saturated clay | [ch03s02ach177.md](./chs/ch03s02ach177.md) | [ch03s02ach177.md](./eng/ch03s02ach177.md) |
| 3.2.5 节理材料的单轴测试 | 3.2.5 Uniaxial tests on jointed material | [ch03s02ach178.md](./chs/ch03s02ach178.md) | [ch03s02ach178.md](./eng/ch03s02ach178.md) |
| 3.2.6 蠕变积分的验证 | 3.2.6 Verification of creep integration | [ch03s02ach179.md](./chs/ch03s02ach179.md) | [ch03s02ach179.md](./eng/ch03s02ach179.md) |
| 3.2.7 可压碎泡沫试件的简单测试 | 3.2.7 Simple tests on a crushable foam specimen | [ch03s02ach180.md](./chs/ch03s02ach180.md) | [ch03s02ach180.md](./eng/ch03s02ach180.md) |
| 3.2.8 简单比例和非比例循环测试 | 3.2.8 Simple proportional and nonproportional cyclic tests | [ch03s02ach181.md](./chs/ch03s02ach181.md) | [ch03s02ach181.md](./eng/ch03s02ach181.md) |
| 3.2.9 灰铸铁的双轴测试 | 3.2.9 Biaxial tests on gray cast iron | [ch03s02ach182.md](./chs/ch03s02ach182.md) | [ch03s02ach182.md](./eng/ch03s02ach182.md) |
| 3.2.10 可压碎泡沫板的压痕 | 3.2.10 Indentation of a crushable foam plate | [ch03s02ach183.md](./chs/ch03s02ach183.md) | [ch03s02ach183.md](./eng/ch03s02ach183.md) |
| 3.2.11 三点弯曲下无筋混凝土梁的切口 | 3.2.11 Notched unreinforced concrete beam under 3-point bending | [ch03s02ach184.md](./chs/ch03s02ach184.md) | [ch03s02ach184.md](./eng/ch03s02ach184.md) |
| 3.2.12 无筋混凝土切口梁的混合模式失效 | 3.2.12 Mixed-mode failure of a notched unreinforced concrete beam | [ch03s02ach185.md](./chs/ch03s02ach185.md) | [ch03s02ach185.md](./eng/ch03s02ach185.md) |
| 3.2.13 带滑移率相关摩擦的滑块机制 | 3.2.13 Slider mechanism with slip-rate-dependent friction | [ch03s02ach186.md](./chs/ch03s02ach186.md) | [ch03s02ach186.md](./eng/ch03s02ach186.md) |
| 3.2.14 内压下的圆筒 | 3.2.14 Cylinder under internal pressure | [ch03s02ach187.md](./chs/ch03s02ach187.md) | [ch03s02ach187.md](./eng/ch03s02ach187.md) |
| 3.2.15 内压下厚壁圆筒的蠕变 | 3.2.15 Creep of a thick cylinder under internal pressure | [ch03s02ach188.md](./chs/ch03s02ach188.md) | [ch03s02ach188.md](./eng/ch03s02ach188.md) |
| 3.2.16 厚壁圆筒的加压 | 3.2.16 Pressurization of a thick-walled cylinder | [ch03s02ach189.md](./chs/ch03s02ach189.md) | [ch03s02ach189.md](./eng/ch03s02ach189.md) |
| 3.2.17 带孔板的拉伸 | 3.2.17 Stretching of a plate with a hole | [ch03s02ach190.md](./chs/ch03s02ach190.md) | [ch03s02ach190.md](./eng/ch03s02ach190.md) |
| 3.2.18 无限地质介质的压力 | 3.2.18 Pressure on infinite geostatic medium | [ch03s02ach191.md](./chs/ch03s02ach191.md) | [ch03s02ach191.md](./eng/ch03s02ach191.md) |

### CH04
*4.1.1 NAFEMS基准测试：概述*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 4.1.1 NAFEMS基准测试：概述 | 4 NAFEMS Benchmarks | [ch04.md](./chs/ch04.md) | [ch04.md](./eng/ch04.md) |
| 4 NAFEMS基准测试 | 4.1 Overview | [ch04s01.md](./chs/ch04s01.md) | [ch04s01.md](./eng/ch04s01.md) |
| 4.1.1 NAFEMS 基准测试：概述 | 4.1.1 NAFEMS benchmarks: overview | [ch04s01ovv01.md](./chs/ch04s01ovv01.md) | [ch04s01ovv01.md](./eng/ch04s01ovv01.md) |
| 4.2 标准基准测试：线弹性测试 | 4.2 Standard benchmarks: linear elastic tests | [ch04s02.md](./chs/ch04s02.md) | [ch04s02.md](./eng/ch04s02.md) |
| 4.2.1 LE1：平面应力单元——椭圆薄膜 | 4.2.1 LE1: Plane stress elements—elliptic membrane | [ch04s02anf01.md](./chs/ch04s02anf01.md) | [ch04s02anf01.md](./eng/ch04s02anf01.md) |
| 4.2.2 LE2：圆柱壳弯曲补丁测试 | 4.2.2 LE2: Cylindrical shell bending patch test | [ch04s02anf02.md](./chs/ch04s02anf02.md) | [ch04s02anf02.md](./eng/ch04s02anf02.md) |
| 4.2.3 LE3：点载荷作用的半球壳 | 4.2.3 LE3: Hemispherical shell with point loads | [ch04s02anf03.md](./chs/ch04s02anf03.md) | [ch04s02anf03.md](./eng/ch04s02anf03.md) |
| 4.2.4 LE4：均匀内压作用下的轴对称双曲壳 | 4.2.4 LE4: Axisymmetric hyperbolic shell under uniform internal pressure | [ch04s02anf04.md](./chs/ch04s02anf04.md) | [ch04s02anf04.md](./eng/ch04s02anf04.md) |
| 4.2.5 LE5：Z形截面悬臂梁 | 4.2.5 LE5: Z-section cantilever | [ch04s02anf05.md](./chs/ch04s02anf05.md) | [ch04s02anf05.md](./eng/ch04s02anf05.md) |
| 4.2.6 LE6：法向压力作用下的斜板 | 4.2.6 LE6: Skew plate under normal pressure | [ch04s02anf06.md](./chs/ch04s02anf06.md) | [ch04s02anf06.md](./eng/ch04s02anf06.md) |
| 4.2.7 LE7：压力作用下的轴对称圆柱体/球体 | 4.2.7 LE7: Axisymmetric cylinder/sphere under pressure | [ch04s02anf07.md](./chs/ch04s02anf07.md) | [ch04s02anf07.md](./eng/ch04s02anf07.md) |
| 4.2.8 LE8：压力作用下的轴对称壳 | 4.2.8 LE8: Axisymmetric shell under pressure | [ch04s02anf08.md](./chs/ch04s02anf08.md) | [ch04s02anf08.md](./eng/ch04s02anf08.md) |
| 4.2.9 LE9：压力作用下的轴对称分支壳 | 4.2.9 LE9: Axisymmetric branched shell under pressure | [ch04s02anf09.md](./chs/ch04s02anf09.md) | [ch04s02anf09.md](./eng/ch04s02anf09.md) |
| 4.2.10 LE10：压力作用下的厚板 | 4.2.10 LE10: Thick plate under pressure | [ch04s02anf10.md](./chs/ch04s02anf10.md) | [ch04s02anf10.md](./eng/ch04s02anf10.md) |
| 4.2.11 LE11：实体圆柱体/锥体/球体——温度载荷 | 4.2.11 LE11: Solid cylinder/taper/sphere—temperature loading | [ch04s02anf11.md](./chs/ch04s02anf11.md) | [ch04s02anf11.md](./eng/ch04s02anf11.md) |
| 4.3 标准基准测试：线性热弹性测试 | 4.3 Standard benchmarks: linear thermo-elastic tests | [ch04s03.md](./chs/ch04s03.md) | [ch04s03.md](./eng/ch04s03.md) |
| 4.3.1 T1：平面应力单元——带热点的薄膜 | 4.3.1 T1: Plane stress elements—membrane with hot-spot | [ch04s03anf12.md](./chs/ch04s03anf12.md) | [ch04s03anf12.md](./eng/ch04s03anf12.md) |
| 4.3.2 T2：带辐射的一维热传递 | 4.3.2 T2: One-dimensional heat transfer with radiation | [ch04s03anf13.md](./chs/ch04s03anf13.md) | [ch04s03anf13.md](./eng/ch04s03anf13.md) |
| 4.3.3 T3：一维瞬态热传递 | 4.3.3 T3: One-dimensional transient heat transfer | [ch04s03anf14.md](./chs/ch04s03anf14.md) | [ch04s03anf14.md](./eng/ch04s03anf14.md) |
| 4.3.4 T4：带对流的二维热传递 | 4.3.4 T4: Two-dimensional heat transfer with convection | [ch04s03anf15.md](./chs/ch04s03anf15.md) | [ch04s03anf15.md](./eng/ch04s03anf15.md) |
| 4.4 标准基准测试：自由振动测试 | 4.4 Standard benchmarks: free vibration tests | [ch04s04.md](./chs/ch04s04.md) | [ch04s04.md](./eng/ch04s04.md) |
| 4.4.1 FV2：销接双十字：面内振动 | 4.4.1 FV2: Pin-ended double cross: in-plane vibration | [ch04s04anf16.md](./chs/ch04s04anf16.md) | [ch04s04anf16.md](./eng/ch04s04anf16.md) |
| 4.4.2 FV4：带偏心点质量的悬臂梁 | 4.4.2 FV4: Cantilever with off-center point masses | [ch04s04anf17.md](./chs/ch04s04anf17.md) | [ch04s04anf17.md](./eng/ch04s04anf17.md) |
| 4.4.3 FV12：自由薄方形板 | 4.4.3 FV12: Free thin square plate | [ch04s04anf18.md](./chs/ch04s04anf18.md) | [ch04s04anf18.md](./eng/ch04s04anf18.md) |
| 4.4.4 FV15：固定薄菱形板 | 4.4.4 FV15: Clamped thin rhombic plate | [ch04s04anf19.md](./chs/ch04s04anf19.md) | [ch04s04anf19.md](./eng/ch04s04anf19.md) |
| 4.4.5 FV16：悬臂薄方形板 | 4.4.5 FV16: Cantilevered thin square plate | [ch04s04anf20.md](./chs/ch04s04anf20.md) | [ch04s04anf20.md](./eng/ch04s04anf20.md) |
| 4.4.6 FV22：固定厚菱形板 | 4.4.6 FV22: Clamped thick rhombic plate | [ch04s04anf21.md](./chs/ch04s04anf21.md) | [ch04s04anf21.md](./eng/ch04s04anf21.md) |
| 4.4.7 FV32：悬臂锥形薄膜 | 4.4.7 FV32: Cantilevered tapered membrane | [ch04s04anf22.md](./chs/ch04s04anf22.md) | [ch04s04anf22.md](./eng/ch04s04anf22.md) |
| 4.4.8 FV41：自由圆柱体：轴对称振动 | 4.4.8 FV41: Free cylinder: axisymmetric vibration | [ch04s04anf23.md](./chs/ch04s04anf23.md) | [ch04s04anf23.md](./eng/ch04s04anf23.md) |
| 4.4.9 FV42：厚空心球：均匀径向振动 | 4.4.9 FV42: Thick hollow sphere: uniform radial vibration | [ch04s04anf24.md](./chs/ch04s04anf24.md) | [ch04s04anf24.md](./eng/ch04s04anf24.md) |
| 4.4.10 FV52：简支"实体"方形板 | 4.4.10 FV52: Simply supported “solid” square plate | [ch04s04anf25.md](./chs/ch04s04anf25.md) | [ch04s04anf25.md](./eng/ch04s04anf25.md) |
| 4.5 建议的强迫振动基准测试 | 4.5 Proposed forced vibration benchmarks | [ch04s05.md](./chs/ch04s05.md) | [ch04s05.md](./eng/ch04s05.md) |
| 4.5.1 测试5：深简支梁：频率提取 | 4.5.1 Test 5: Deep simply supported beam: frequency extraction | [ch04s05anf26.md](./chs/ch04s05anf26.md) | [ch04s05anf26.md](./eng/ch04s05anf26.md) |
| 4.5.2 测试5H：深简支梁：谐波强迫振动 | 4.5.2 Test 5H: Deep simply supported beam: harmonic forced vibration | [ch04s05anf27.md](./chs/ch04s05anf27.md) | [ch04s05anf27.md](./eng/ch04s05anf27.md) |
| 4.5.3 测试5T：深简支梁：瞬态强迫振动 | 4.5.3 Test 5T: Deep simply supported beam: transient forced vibration | [ch04s05anf28.md](./chs/ch04s05anf28.md) | [ch04s05anf28.md](./eng/ch04s05anf28.md) |
| 4.5.4 测试5R：深简支梁：随机强迫振动 | 4.5.4 Test 5R: Deep simply supported beam: random forced vibration | [ch04s05anf29.md](./chs/ch04s05anf29.md) | [ch04s05anf29.md](./eng/ch04s05anf29.md) |
| 4.5.5 测试13：简支薄方形板：频率提取 | 4.5.5 Test 13: Simply supported thin square plate: frequency extraction | [ch04s05anf30.md](./chs/ch04s05anf30.md) | [ch04s05anf30.md](./eng/ch04s05anf30.md) |
| 4.5.6 测试13H：简支薄方形板：谐波强迫振动 | 4.5.6 Test 13H: Simply supported thin square plate: harmonic forced vibration | [ch04s05anf31.md](./chs/ch04s05anf31.md) | [ch04s05anf31.md](./eng/ch04s05anf31.md) |
| 4.5.7 测试13T：简支薄方形板：瞬态强迫振动 | 4.5.7 Test 13T: Simply supported thin square plate: transient forced vibration | [ch04s05anf32.md](./chs/ch04s05anf32.md) | [ch04s05anf32.md](./eng/ch04s05anf32.md) |
| 4.5.8 测试13R：简支薄方形板：随机强迫振动 | 4.5.8 Test 13R: Simply supported thin square plate: random forced vibration | [ch04s05anf33.md](./chs/ch04s05anf33.md) | [ch04s05anf33.md](./eng/ch04s05anf33.md) |
| 4.5.9 测试21：简支厚方形板：频率提取 | 4.5.9 Test 21: Simply supported thick square plate: frequency extraction | [ch04s05anf34.md](./chs/ch04s05anf34.md) | [ch04s05anf34.md](./eng/ch04s05anf34.md) |
| 4.5.10 测试21H：简支厚方形板：谐波强迫振动 | 4.5.10 Test 21H: Simply supported thick square plate: harmonic forced vibration | [ch04s05anf35.md](./chs/ch04s05anf35.md) | [ch04s05anf35.md](./eng/ch04s05anf35.md) |
| 4.5.11 测试21T：简支厚方形板：瞬态强迫振动 | 4.5.11 Test 21T: Simply supported thick square plate: transient forced vibration | [ch04s05anf36.md](./chs/ch04s05anf36.md) | [ch04s05anf36.md](./eng/ch04s05anf36.md) |
| 4.5.12 测试21R：简支厚方形板：随机强迫振动 | 4.5.12 Test 21R: Simply supported thick square plate: random forced vibration | [ch04s05anf37.md](./chs/ch04s05anf37.md) | [ch04s05anf37.md](./eng/ch04s05anf37.md) |
| 4.6 建议的非线性基准测试 | 4.6 Proposed nonlinear benchmarks | [ch04s06.md](./chs/ch04s06.md) | [ch04s06.md](./eng/ch04s06.md) |
| 4.6.1 NL1：规定双轴应变历史，平面应变 | 4.6.1 NL1: Prescribed biaxial strain history, plane strain | [ch04s06anf38.md](./chs/ch04s06anf38.md) | [ch04s06anf38.md](./eng/ch04s06anf38.md) |
| 4.6.3 NL3：载荷控制下具有两个变量的硬化 | 4.6.2 NL2: Axisymmetric thick cylinder | [ch04s06anf39.md](./chs/ch04s06anf39.md) | [ch04s06anf39.md](./eng/ch04s06anf39.md) |
| 4.6.2 NL2：轴对称厚壁圆柱筒 | 4.6.3 NL3: Hardening with two variables under load control | [ch04s06anf40.md](./chs/ch04s06anf40.md) | [ch04s06anf40.md](./eng/ch04s06anf40.md) |
| 4.6.4 NL4：位移控制下的snap-back | 4.6.4 NL4: Snap-back under displacement control | [ch04s06anf41.md](./chs/ch04s06anf41.md) | [ch04s06anf41.md](./eng/ch04s06anf41.md) |
| 4.6.6 NL6：直悬臂带轴向端点载荷 | 4.6.5 NL5: Straight cantilever with end moment | [ch04s06anf42.md](./chs/ch04s06anf42.md) | [ch04s06anf42.md](./eng/ch04s06anf42.md) |
| 4.6.5 NL5：直悬臂带端部弯矩 | 4.6.6 NL6: Straight cantilever with axial end point load | [ch04s06anf43.md](./chs/ch04s06anf43.md) | [ch04s06anf43.md](./eng/ch04s06anf43.md) |
| 4.6.7 NL7：Lee框架屈曲问题 | 4.6.7 NL7: Lee's frame buckling problem | [ch04s06anf44.md](./chs/ch04s06anf44.md) | [ch04s06anf44.md](./eng/ch04s06anf44.md) |
| 4.7 线弹性断裂力学中的二维测试案例 | 4.7 Two-dimensional test cases in linear elastic fracture mechanics | [ch04s07.md](./chs/ch04s07.md) | [ch04s07.md](./eng/ch04s07.md) |
| 4.7.1 测试1.1：受拉中心裂纹板 | 4.7.1 Test 1.1: Center cracked plate in tension | [ch04s07anf45.md](./chs/ch04s07anf45.md) | [ch04s07anf45.md](./eng/ch04s07anf45.md) |
| 4.7.2 测试1.2：带热载荷的中心裂纹板 | 4.7.2 Test 1.2: Center cracked plate with thermal load | [ch04s07anf46.md](./chs/ch04s07anf46.md) | [ch04s07anf46.md](./eng/ch04s07anf46.md) |
| 4.7.4 测试3：嵌入板中的角度裂纹 | 4.7.3 Test 2.1: Single edge cracked plate in tension | [ch04s07anf47.md](./chs/ch04s07anf47.md) | [ch04s07anf47.md](./eng/ch04s07anf47.md) |
| 4.7.3 测试2.1：受拉单边裂纹板 | 4.7.4 Test 3: Angle crack embedded in a plate | [ch04s07anf48.md](./chs/ch04s07anf48.md) | [ch04s07anf48.md](./eng/ch04s07anf48.md) |
| 4.7.5 测试4：板中孔处裂纹 | 4.7.5 Test 4: Cracks at a hole in a plate | [ch04s07anf49.md](./chs/ch04s07anf49.md) | [ch04s07anf49.md](./eng/ch04s07anf49.md) |
| 4.7.6 测试5：杆中轴对称裂纹 | 4.7.6 Test 5: Axisymmetric crack in a bar | [ch04s07anf50.md](./chs/ch04s07anf50.md) | [ch04s07anf50.md](./eng/ch04s07anf50.md) |
| 4.7.7 测试6：紧凑拉伸试样 | 4.7.7 Test 6: Compact tension specimen | [ch04s07anf51.md](./chs/ch04s07anf51.md) | [ch04s07anf51.md](./eng/ch04s07anf51.md) |
| 4.7.8 测试7.1：T形焊接接头 | 4.7.8 Test 7.1: T-joint weld attachment | [ch04s07anf52.md](./chs/ch04s07anf52.md) | [ch04s07anf52.md](./eng/ch04s07anf52.md) |
| 4.7.9 测试8.1：受拉V形缺口试样 | 4.7.9 Test 8.1: V-notch specimen in tension | [ch04s07anf53.md](./chs/ch04s07anf53.md) | [ch04s07anf53.md](./eng/ch04s07anf53.md) |
| 4.8 蠕变行为的基础测试 | 4.8 Fundamental tests of creep behavior | [ch04s08.md](./chs/ch04s08.md) | [ch04s08.md](./eng/ch04s08.md) |
| 4.8.1 测试1A：2D平面应力——单轴载荷，二次蠕变 | 4.8.1 Test 1A: 2D plane stress – uniaxial load, secondary creep | [ch04s08anf54.md](./chs/ch04s08anf54.md) | [ch04s08anf54.md](./eng/ch04s08anf54.md) |
| 4.8.2 测试1B：2D平面应力——单轴位移，二次蠕变 | 4.8.2 Test 1B: 2D plane stress – uniaxial displacement, secondary creep | [ch04s08anf55.md](./chs/ch04s08anf55.md) | [ch04s08anf55.md](./eng/ch04s08anf55.md) |
| 4.8.3 测试2A：2D平面应力——双轴载荷，二次蠕变 | 4.8.3 Test 2A: 2D plane stress – biaxial load, secondary creep | [ch04s08anf56.md](./chs/ch04s08anf56.md) | [ch04s08anf56.md](./eng/ch04s08anf56.md) |
| 4.8.4 测试2B：2D平面应力——双轴位移，二次蠕变 | 4.8.4 Test 2B: 2D plane stress – biaxial displacement, secondary creep | [ch04s08anf57.md](./chs/ch04s08anf57.md) | [ch04s08anf57.md](./eng/ch04s08anf57.md) |
| 4.8.6 测试3B：2D平面应力——双轴（负）位移，二次蠕变 | 4.8.5 Test 3A: 2D plane stress – biaxial (negative) load, secondary creep | [ch04s08anf58.md](./chs/ch04s08anf58.md) | [ch04s08anf58.md](./eng/ch04s08anf58.md) |
| 4.8.7 测试4A：2D平面应力——双轴（双）载荷，二次蠕变 | 4.8.6 Test 3B: 2D plane stress – biaxial (negative) displacement, secondary creep | [ch04s08anf59.md](./chs/ch04s08anf59.md) | [ch04s08anf59.md](./eng/ch04s08anf59.md) |
| 4.8.5 测试3A：2D平面应力——双轴（负）载荷，二次蠕变 | 4.8.7 Test 4A: 2D plane stress – biaxial (double) load, secondary creep | [ch04s08anf60.md](./chs/ch04s08anf60.md) | [ch04s08anf60.md](./eng/ch04s08anf60.md) |
| 4.8.9 测试4C：2D平面应力——剪切载荷，二次蠕变 | 4.8.8 Test 4B: 2D plane stress – biaxial (double) displacement, secondary creep | [ch04s08anf61.md](./chs/ch04s08anf61.md) | [ch04s08anf61.md](./eng/ch04s08anf61.md) |
| 4.8.8 测试4B：2D平面应力——双轴（双）位移，二次蠕变 | 4.8.9 Test 4C: 2D plane stress – shear loading, secondary creep | [ch04s08anf62.md](./chs/ch04s08anf62.md) | [ch04s08anf62.md](./eng/ch04s08anf62.md) |
| 4.8.10 测试5A：2D平面应变——双轴载荷，二次蠕变 | 4.8.10 Test 5A: 2D plane strain – biaxial load, secondary creep | [ch04s08anf63.md](./chs/ch04s08anf63.md) | [ch04s08anf63.md](./eng/ch04s08anf63.md) |
| 4.8.11 测试5B：2D平面应变——双轴位移，二次蠕变 | 4.8.11 Test 5B: 2D plane strain – biaxial displacement, secondary creep | [ch04s08anf64.md](./chs/ch04s08anf64.md) | [ch04s08anf64.md](./eng/ch04s08anf64.md) |
| 4.8.12 测试6A：3D——三轴载荷，二次蠕变 | 4.8.12 Test 6A: 3D – triaxial load, secondary creep | [ch04s08anf65.md](./chs/ch04s08anf65.md) | [ch04s08anf65.md](./eng/ch04s08anf65.md) |
| 4.8.13 测试6B：3D——三轴位移，二次蠕变 | 4.8.13 Test 6B: 3D – triaxial displacement, secondary creep | [ch04s08anf66.md](./chs/ch04s08anf66.md) | [ch04s08anf66.md](./eng/ch04s08anf66.md) |
| 4.8.14 测试7：轴对称——加压圆柱筒，二次蠕变 | 4.8.14 Test 7: Axisymmetric – pressurized cylinder, secondary creep | [ch04s08anf67.md](./chs/ch04s08anf67.md) | [ch04s08anf67.md](./eng/ch04s08anf67.md) |
| 4.8.15 测试8A：2D平面应力——单轴载荷，一次蠕变 | 4.8.15 Test 8A: 2D plane stress – uniaxial load, primary creep | [ch04s08anf68.md](./chs/ch04s08anf68.md) | [ch04s08anf68.md](./eng/ch04s08anf68.md) |
| 4.8.16 测试8B：2D平面应力——单轴位移，一次蠕变 | 4.8.16 Test 8B: 2D plane stress – uniaxial displacement, primary creep | [ch04s08anf69.md](./chs/ch04s08anf69.md) | [ch04s08anf69.md](./eng/ch04s08anf69.md) |
| 4.8.17 测试8C：2D平面应力——阶梯载荷，一次蠕变 | 4.8.17 Test 8C: 2D plane stress – stepped load, primary creep | [ch04s08anf70.md](./chs/ch04s08anf70.md) | [ch04s08anf70.md](./eng/ch04s08anf70.md) |
| 4.8.18 测试9A：2D平面应力——双轴载荷，一次蠕变 | 4.8.18 Test 9A: 2D plane stress – biaxial load, primary creep | [ch04s08anf71.md](./chs/ch04s08anf71.md) | [ch04s08anf71.md](./eng/ch04s08anf71.md) |
| 4.8.19 测试9B：2D平面应力——双轴位移，一次蠕变 | 4.8.19 Test 9B: 2D plane stress – biaxial displacement, primary creep | [ch04s08anf72.md](./chs/ch04s08anf72.md) | [ch04s08anf72.md](./eng/ch04s08anf72.md) |
| 4.8.21 测试10A：2D平面应力——双轴（负）载荷，一次蠕变 | 4.8.20 Test 9C: 2D plane stress – biaxial stepped load, primary creep | [ch04s08anf73.md](./chs/ch04s08anf73.md) | [ch04s08anf73.md](./eng/ch04s08anf73.md) |
| 4.8.20 测试9C：2D平面应力——双轴阶梯载荷，一次蠕变 | 4.8.21 Test 10A: 2D plane stress – biaxial (negative) load, primary creep | [ch04s08anf74.md](./chs/ch04s08anf74.md) | [ch04s08anf74.md](./eng/ch04s08anf74.md) |
| 4.8.22 测试10B：2D平面应力——双轴（负）位移，一次蠕变 | 4.8.22 Test 10B: 2D plane stress – biaxial (negative) displacement, primary creep | [ch04s08anf75.md](./chs/ch04s08anf75.md) | [ch04s08anf75.md](./eng/ch04s08anf75.md) |
| 4.8.24 测试11：3D——三轴载荷，一次蠕变 | 4.8.23 Test 10C: 2D plane stress – biaxial (negative) stepped load, primary creep | [ch04s08anf76.md](./chs/ch04s08anf76.md) | [ch04s08anf76.md](./eng/ch04s08anf76.md) |
| 4.8.25 测试12A：2D平面应力——单轴载荷，一次-二次蠕变 | 4.8.24 Test 11: 3D – triaxial load, primary creep | [ch04s08anf77.md](./chs/ch04s08anf77.md) | [ch04s08anf77.md](./eng/ch04s08anf77.md) |
| 4.8.23 测试10C：2D平面应力——双轴（负）阶梯载荷，一次蠕变 | 4.8.25 Test 12A: 2D plane stress – uniaxial load, primary-secondary creep | [ch04s08anf78.md](./chs/ch04s08anf78.md) | [ch04s08anf78.md](./eng/ch04s08anf78.md) |
| 4.8.26 测试12B：2D平面应力——单轴位移，一次-二次蠕变 | 4.8.26 Test 12B: 2D plane stress – uniaxial displacement, primary-secondary creep | [ch04s08anf79.md](./chs/ch04s08anf79.md) | [ch04s08anf79.md](./eng/ch04s08anf79.md) |
| 4.8.27 测试12C：2D平面应力——阶梯载荷，一次-二次蠕变 | 4.8.27 Test 12C: 2D plane stress – stepped load, primary-secondary creep | [ch04s08anf80.md](./chs/ch04s08anf80.md) | [ch04s08anf80.md](./eng/ch04s08anf80.md) |
| 4.9 复合材料测试 | 4.9 Composite tests | [ch04s09.md](./chs/ch04s09.md) | [ch04s09.md](./eng/ch04s09.md) |
| 4.9.1 R0031(1)：三点弯曲下的层合条 | 4.9.1 R0031(1): Laminated strip under three-point bending | [ch04s09anf81.md](./chs/ch04s09anf81.md) | [ch04s09anf81.md](./eng/ch04s09anf81.md) |
| 4.9.2 R0031(2)：压力和热载荷作用下的缠绕厚壁圆柱筒 | 4.9.2 R0031(2): Wrapped thick cylinder under pressure and thermal loading | [ch04s09anf82.md](./chs/ch04s09anf82.md) | [ch04s09anf82.md](./eng/ch04s09anf82.md) |
| 4.9.3 R0031(3)：法向压力载荷下的三层夹芯壳 | 4.9.3 R0031(3): Three-layer sandwich shell under normal pressure loading | [ch04s09anf83.md](./chs/ch04s09anf83.md) | [ch04s09anf83.md](./eng/ch04s09anf83.md) |
| 4.10 几何非线性测试 | 4.10 Geometric nonlinear tests | [ch04s10.md](./chs/ch04s10.md) | [ch04s10.md](./eng/ch04s10.md) |
| 4.10.2 3DNLG-2：端部缩短下梨形圆柱体的弹性大挠度响应 | 4.10.1 3DNLG-1: Elastic large deflection response of a Z-shaped cantilever under an end load | [ch04s10anf84.md](./chs/ch04s10anf84.md) | [ch04s10anf84.md](./eng/ch04s10anf84.md) |
| 4.10.3 3DNLG-3：平面内端部力矩作用下直角框架的弹性侧向屈曲 | 4.10.2 3DNLG-2: Elastic large deflection response of a pear-shaped cylinder under end shortening | [ch04s10anf85.md](./chs/ch04s10anf85.md) | [ch04s10anf85.md](./eng/ch04s10anf85.md) |
| 4.10.1 3DNLG-1：端部载荷作用下Z形悬臂的弹性大挠度响应 | 4.10.3 3DNLG-3: Elastic lateral buckling of a right angle frame under in-plane end moments | [ch04s10anf86.md](./chs/ch04s10anf86.md) | [ch04s10anf86.md](./eng/ch04s10anf86.md) |
| 4.10.5 3DNLG-5：横向端部载荷作用下曲线弹性悬臂的大挠度 | 4.10.4 3DNLG-4: Lateral torsional buckling of an elastic cantilever subjected to a transverse end load | [ch04s10anf87.md](./chs/ch04s10anf87.md) | [ch04s10anf87.md](./eng/ch04s10anf87.md) |
| 4.10.4 3DNLG-4：横向端部载荷作用下弹性悬臂的侧向扭转屈曲 | 4.10.5 3DNLG-5: Large deflection of a curved elastic cantilever under transverse end load | [ch04s10anf88.md](./chs/ch04s10anf88.md) | [ch04s10anf88.md](./eng/ch04s10anf88.md) |
| 4.10.7 3DNLG-7：压力载荷作用下铰接球壳的弹性大挠度响应 | 4.10.6 3DNLG-6: Buckling of a flat plate when subjected to in-plane shear | [ch04s10anf89.md](./chs/ch04s10anf89.md) | [ch04s10anf89.md](./eng/ch04s10anf89.md) |
| 4.10.6 3DNLG-6：平面内剪切作用下平板的屈曲 | 4.10.7 3DNLG-7: Elastic large deflection response of a hinged spherical shell under pressure loading | [ch04s10anf90.md](./chs/ch04s10anf90.md) | [ch04s10anf90.md](./eng/ch04s10anf90.md) |
| 4.10.8 3DNLG-8：纯弯曲作用下直管段的塌陷 | 4.10.8 3DNLG-8: Collapse of a straight pipe segment under pure bending | [ch04s10anf91.md](./chs/ch04s10anf91.md) | [ch04s10anf91.md](./eng/ch04s10anf91.md) |
| 4.10.9 3DNLG-9： pinched hemispherical shell的大弹性挠度 | 4.10.9 3DNLG-9: Large elastic deflection of a pinched hemispherical shell | [ch04s10anf92.md](./chs/ch04s10anf92.md) | [ch04s10anf92.md](./eng/ch04s10anf92.md) |
| 4.10.10 3DNLG-10：压缩端部载荷作用下加筋圆柱面板的弹塑性行为 | 4.10.10 3DNLG-10: Elastic-plastic behavior of a stiffened cylindrical panel under compressive end load | [ch04s10anf93.md](./chs/ch04s10anf93.md) | [ch04s10anf93.md](./eng/ch04s10anf93.md) |

### OTHER
*简介*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 简介 | Introduction | [ami01.md](./chs/ami01.md) | [ami01.md](./eng/ami01.md) |
| Abaqus/Aqua | Product Index | [pdx01.md](./chs/pdx01.md) | [pdx01.md](./eng/pdx01.md) |
| Abaqus/Aqua | Abaqus/Standard | [pdx01pdd01.md](./chs/pdx01pdd01.md) | [pdx01pdd01.md](./eng/pdx01pdd01.md) |
| Abaqus/CAE | Abaqus/Explicit | [pdx01pdd02.md](./chs/pdx01pdd02.md) | [pdx01pdd02.md](./eng/pdx01pdd02.md) |
| Abaqus/Explicit | Abaqus/CAE | [pdx01pdd03.md](./chs/pdx01pdd03.md) | [pdx01pdd03.md](./eng/pdx01pdd03.md) |
| Abaqus/Design | Abaqus/Aqua | [pdx01pdd04.md](./chs/pdx01pdd04.md) | [pdx01pdd04.md](./eng/pdx01pdd04.md) |
| Abaqus/Standard | Abaqus/Design | [pdx01pdd05.md](./chs/pdx01pdd05.md) | [pdx01pdd05.md](./eng/pdx01pdd05.md) |

---

## 资源文件 / Resource Files

图片资源位于 `graphics/` 目录。

---

## 版权声明 / Copyright Notice

本翻译仅供学习研究使用，原文档版权归 Dassault Systèmes Simulia Corp. 所有。
This translation is for study and research purposes only. Original documentation copyright Dassault Systèmes Simulia Corp.