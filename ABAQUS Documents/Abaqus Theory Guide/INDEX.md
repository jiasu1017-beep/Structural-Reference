# Abaqus Theory Guide (6.14)

## 文档索引 / Documentation Index

本手册为 ABAQUS 6.14 Abaqus Theory Guide 的中文翻译版本。

**来源 / Source:** D:\SIMULIA\Documentation\docs\v6.14\books\stm\

---

## 双语目录对照 / Bilingual Table of Contents

### OTHER
*1.1 引言*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 1.1 引言 | 1.1 Introduction | [01s01-Section.md](./chs/01s01-Section.md) | [01s01-Section.md](./eng/01s01-Section.md) |
| 1.1.1 引言：概述 | 1.1.1 Introduction: general | [01s01a01-Introduction-general.md](./chs/01s01a01-Introduction-general.md) | [01s01a01-Introduction-general.md](./eng/01s01a01-Introduction-general.md) |
| 1.2 符号表示 | 1.2 Notation | [01s02-Section.md](./chs/01s02-Section.md) | [01s02-Section.md](./eng/01s02-Section.md) |
| 1.2.1 符号表示 | 1.2.1 Notation | [01s02a02-Notation.md](./chs/01s02a02-Notation.md) | [01s02a02-Notation.md](./eng/01s02a02-Notation.md) |
| 1.3 有限旋转 | 1.3 Finite rotations | [01s03-Section.md](./chs/01s03-Section.md) | [01s03-Section.md](./eng/01s03-Section.md) |
| 1.3.1 旋转变量 | 1.3.1 Rotation variables | [01s03a03-Rotation-variables.md](./chs/01s03a03-Rotation-variables.md) | [01s03a03-Rotation-variables.md](./eng/01s03a03-Rotation-variables.md) |
| 1.4 变形、应变与应变率 | 1.4 Deformation, strain, and strain rates | [01s04-Section.md](./chs/01s04-Section.md) | [01s04-Section.md](./eng/01s04-Section.md) |
| 1.4.1 变形 | 1.4.1 Deformation | [01s04a04-Deformation.md](./chs/01s04a04-Deformation.md) | [01s04a04-Deformation.md](./eng/01s04a04-Deformation.md) |
| 1.4.2 应变度量 | 1.4.2 Strain measures | [01s04a05-Strain-measures.md](./chs/01s04a05-Strain-measures.md) | [01s04a05-Strain-measures.md](./eng/01s04a05-Strain-measures.md) |
| 1.4.3 变形率与应变增量 | 1.4.3 Rate of deformation and strain increment | [01s04a06-Rate-of-deformation-and-strain-increment.md](./chs/01s04a06-Rate-of-deformation-and-strain-increment.md) | [01s04a06-Rate-of-deformation-and-strain-increment.md](./eng/01s04a06-Rate-of-deformation-and-strain-increment.md) |
| 1.4.4 加法应变率分解 | 1.4.4 The additive strain rate decomposition | [01s04a07-The-additive-strain-rate-decomposition.md](./chs/01s04a07-The-additive-strain-rate-decomposition.md) | [01s04a07-The-additive-strain-rate-decomposition.md](./eng/01s04a07-The-additive-strain-rate-decomposition.md) |
| 1.5 平衡、应力与状态存储 | 1.5 Equilibrium, stress, and state storage | [01s05-Section.md](./chs/01s05-Section.md) | [01s05-Section.md](./eng/01s05-Section.md) |
| 1.5.1 平衡与虚功 | 1.5.1 Equilibrium and virtual work | [01s05a08-Equilibrium-and-virtual-work.md](./chs/01s05a08-Equilibrium-and-virtual-work.md) | [01s05a08-Equilibrium-and-virtual-work.md](./eng/01s05a08-Equilibrium-and-virtual-work.md) |
| 1.5.2 应力度量 | 1.5.2 Stress measures | [01s05a09-Stress-measures.md](./chs/01s05a09-Stress-measures.md) | [01s05a09-Stress-measures.md](./eng/01s05a09-Stress-measures.md) |
| 1.5.3 应力率 | 1.5.3 Stress rates | [01s05a10-Stress-rates.md](./chs/01s05a10-Stress-rates.md) | [01s05a10-Stress-rates.md](./eng/01s05a10-Stress-rates.md) |
| 1.5.4 状态存储 | 1.5.4 State storage | [01s05a11-State-storage.md](./chs/01s05a11-State-storage.md) | [01s05a11-State-storage.md](./eng/01s05a11-State-storage.md) |
| 1.5.5 能量平衡 | 1.5.5 Energy balance | [01s05a12-Energy-balance.md](./chs/01s05a12-Energy-balance.md) | [01s05a12-Energy-balance.md](./eng/01s05a12-Energy-balance.md) |
| 2 过程 | 2.1 Overview | [02s01-Section.md](./chs/02s01-Section.md) | [02s01-Section.md](./eng/02s01-Section.md) |
| 2.1.1 过程：概述与基本方程 | 2.1.1 Procedures: overview and basic equations | [02s01a13-Procedures-overview-and-basic-equations.md](./chs/02s01a13-Procedures-overview-and-basic-equations.md) | [02s01a13-Procedures-overview-and-basic-equations.md](./eng/02s01a13-Procedures-overview-and-basic-equations.md) |
| 2.2 非线性求解方法 | 2.2 Nonlinear solution methods | [02s02-Section.md](./chs/02s02-Section.md) | [02s02-Section.md](./eng/02s02-Section.md) |
| 2.2.1 Abaqus/Standard中的非线性求解方法 | 2.2.1 Nonlinear solution methods in Abaqus/Standard | [02s02a14-Nonlinear-solution-methods-in-AbaqusStan.md](./chs/02s02a14-Nonlinear-solution-methods-in-AbaqusStan.md) | [02s02a14-Nonlinear-solution-methods-in-AbaqusStan.md](./eng/02s02a14-Nonlinear-solution-methods-in-AbaqusStan.md) |
| 2.2.2 拟Newton求解技术 | 2.2.2 Quasi-Newton solution technique | [02s02a15-Quasi-Newton-solution-technique.md](./chs/02s02a15-Quasi-Newton-solution-technique.md) | [02s02a15-Quasi-Newton-solution-technique.md](./eng/02s02a15-Quasi-Newton-solution-technique.md) |
| 2.2.3 直接循环算法 | 2.2.3 Direct cyclic algorithm | [02s02a16-Direct-cyclic-algorithm.md](./chs/02s02a16-Direct-cyclic-algorithm.md) | [02s02a16-Direct-cyclic-algorithm.md](./eng/02s02a16-Direct-cyclic-algorithm.md) |
| 2.3 屈曲与后屈曲 | 2.3 Buckling and postbuckling | [02s03-Section.md](./chs/02s03-Section.md) | [02s03-Section.md](./eng/02s03-Section.md) |
| 2.3.1 特征值屈曲预测 | 2.3.1 Eigenvalue buckling prediction | [02s03a17-Eigenvalue-buckling-prediction.md](./chs/02s03a17-Eigenvalue-buckling-prediction.md) | [02s03a17-Eigenvalue-buckling-prediction.md](./eng/02s03a17-Eigenvalue-buckling-prediction.md) |
| 2.3.2 修正Riks算法 | 2.3.2 Modified Riks algorithm | [02s03a18-Modified-Riks-algorithm.md](./chs/02s03a18-Modified-Riks-algorithm.md) | [02s03a18-Modified-Riks-algorithm.md](./eng/02s03a18-Modified-Riks-algorithm.md) |
| 2.4 非线性动力学 | 2.4 Nonlinear dynamics | [02s04-Section.md](./chs/02s04-Section.md) | [02s04-Section.md](./eng/02s04-Section.md) |
| 2.4.1 隐式动力学分析 | 2.4.1 Implicit dynamic analysis | [02s04a19-Implicit-dynamic-analysis.md](./chs/02s04a19-Implicit-dynamic-analysis.md) | [02s04a19-Implicit-dynamic-analysis.md](./eng/02s04a19-Implicit-dynamic-analysis.md) |
| 2.4.2 间歇接触/冲击 | 2.4.2 Intermittent contact/impact | [02s04a20-Intermittent-contactimpact.md](./chs/02s04a20-Intermittent-contactimpact.md) | [02s04a20-Intermittent-contactimpact.md](./eng/02s04a20-Intermittent-contactimpact.md) |
| 2.4.3 子空间动力学 | 2.4.3 Subspace dynamics | [02s04a21-Subspace-dynamics.md](./chs/02s04a21-Subspace-dynamics.md) | [02s04a21-Subspace-dynamics.md](./eng/02s04a21-Subspace-dynamics.md) |
| 2.4.4 等效刚体动力运动 | 2.4.4 Equivalent rigid body dynamic motion | [02s04a22-Equivalent-rigid-body-dynamic-motion.md](./chs/02s04a22-Equivalent-rigid-body-dynamic-motion.md) | [02s04a22-Equivalent-rigid-body-dynamic-motion.md](./eng/02s04a22-Equivalent-rigid-body-dynamic-motion.md) |
| 2.4.5 显式动力学分析 | 2.4.5 Explicit dynamic analysis | [02s04a23-Explicit-dynamic-analysis.md](./chs/02s04a23-Explicit-dynamic-analysis.md) | [02s04a23-Explicit-dynamic-analysis.md](./eng/02s04a23-Explicit-dynamic-analysis.md) |
| 2.5 模态动力学 | 2.5 Modal dynamics | [02s05-Section.md](./chs/02s05-Section.md) | [02s05-Section.md](./eng/02s05-Section.md) |
| 2.5.1 特征值提取 | 2.5.1 Eigenvalue extraction | [02s05a24-Eigenvalue-extraction.md](./chs/02s05a24-Eigenvalue-extraction.md) | [02s05a24-Eigenvalue-extraction.md](./eng/02s05a24-Eigenvalue-extraction.md) |
| 2.5.2 与模型固有模态相关的变量 | 2.5.2 Variables associated with the natural modes of a model | [02s05a25-Variables-associated-with-the-natural-mo.md](./chs/02s05a25-Variables-associated-with-the-natural-mo.md) | [02s05a25-Variables-associated-with-the-natural-mo.md](./eng/02s05a25-Variables-associated-with-the-natural-mo.md) |
| 2.5.3 使用模态叠加的线性动力学分析 | 2.5.3 Linear dynamic analysis using modal superposition | [02s05a26-Linear-dynamic-analysis-using-modal-supe.md](./chs/02s05a26-Linear-dynamic-analysis-using-modal-supe.md) | [02s05a26-Linear-dynamic-analysis-using-modal-supe.md](./eng/02s05a26-Linear-dynamic-analysis-using-modal-supe.md) |
| 2.5.4 模态动力学的阻尼选项 | 2.5.4 Damping options for modal dynamics | [02s05a27-Damping-options-for-modal-dynamics.md](./chs/02s05a27-Damping-options-for-modal-dynamics.md) | [02s05a27-Damping-options-for-modal-dynamics.md](./eng/02s05a27-Damping-options-for-modal-dynamics.md) |
| 2.5.5 模态动力学分析 | 2.5.5 Modal dynamic analysis | [02s05a28-Modal-dynamic-analysis.md](./chs/02s05a28-Modal-dynamic-analysis.md) | [02s05a28-Modal-dynamic-analysis.md](./eng/02s05a28-Modal-dynamic-analysis.md) |
| 2.5.6 响应谱分析 | 2.5.6 Response spectrum analysis | [02s05a29-Response-spectrum-analysis.md](./chs/02s05a29-Response-spectrum-analysis.md) | [02s05a29-Response-spectrum-analysis.md](./eng/02s05a29-Response-spectrum-analysis.md) |
| 2.5.7 稳态线性动力学分析 | 2.5.7 Steady-state linear dynamic analysis | [02s05a30-Steady-state-linear-dynamic-analysis.md](./chs/02s05a30-Steady-state-linear-dynamic-analysis.md) | [02s05a30-Steady-state-linear-dynamic-analysis.md](./eng/02s05a30-Steady-state-linear-dynamic-analysis.md) |
| 2.5.8 随机响应分析 | 2.5.8 Random response analysis | [02s05a31-Random-response-analysis.md](./chs/02s05a31-Random-response-analysis.md) | [02s05a31-Random-response-analysis.md](./eng/02s05a31-Random-response-analysis.md) |
| 2.5.9 基于模态过程的基础运动 | 2.5.9 Base motions in modal-based procedures | [02s05a32-Base-motions-in-modal-based-procedures.md](./chs/02s05a32-Base-motions-in-modal-based-procedures.md) | [02s05a32-Base-motions-in-modal-based-procedures.md](./eng/02s05a32-Base-motions-in-modal-based-procedures.md) |
| 2.6 直接和基于子空间的稳态动力学分析 | 2.6 Complex harmonic oscillations | [02s06-Section.md](./chs/02s06-Section.md) | [02s06-Section.md](./eng/02s06-Section.md) |
| 2.6.1 直接稳态动力学分析 | 2.6.1 Direct steady-state dynamic analysis | [02s06a33-Direct-steady-state-dynamic-analysis.md](./chs/02s06a33-Direct-steady-state-dynamic-analysis.md) | [02s06a33-Direct-steady-state-dynamic-analysis.md](./eng/02s06a33-Direct-steady-state-dynamic-analysis.md) |
| 2.6.2 基于子空间的稳态动力学分析 | 2.6.2 Subspace-based steady-state dynamic analysis | [02s06a34-Subspace-based-steady-state-dynamic-anal.md](./chs/02s06a34-Subspace-based-steady-state-dynamic-anal.md) | [02s06a34-Subspace-based-steady-state-dynamic-anal.md](./eng/02s06a34-Subspace-based-steady-state-dynamic-anal.md) |
| 2.7 稳态传输分析 | 2.7 Steady-state transport analysis | [02s07-Section.md](./chs/02s07-Section.md) | [02s07-Section.md](./eng/02s07-Section.md) |
| 2.7.1 稳态传输分析 | 2.7.1 Steady-state transport analysis | [02s07a35-Steady-state-transport-analysis.md](./chs/02s07a35-Steady-state-transport-analysis.md) | [02s07a35-Steady-state-transport-analysis.md](./eng/02s07a35-Steady-state-transport-analysis.md) |
| 2.8 多孔介质分析 | 2.8 Analysis of porous media | [02s08-Section.md](./chs/02s08-Section.md) | [02s08-Section.md](./eng/02s08-Section.md) |
| 2.8.1 多孔介质的有效应力原理 | 2.8.1 Effective stress principle for porous media | [02s08a36-Effective-stress-principle-for-porous-me.md](./chs/02s08a36-Effective-stress-principle-for-porous-me.md) | [02s08a36-Effective-stress-principle-for-porous-me.md](./eng/02s08a36-Effective-stress-principle-for-porous-me.md) |
| 2.8.2 多孔介质离散平衡方程 | 2.8.2 Discretized equilibrium statement for a porous medium | [02s08a37-Discretized-equilibrium-statement-for-a-.md](./chs/02s08a37-Discretized-equilibrium-statement-for-a-.md) | [02s08a37-Discretized-equilibrium-statement-for-a-.md](./eng/02s08a37-Discretized-equilibrium-statement-for-a-.md) |
| 2.8.3 多孔介质中的本构行为 | 2.8.3 Constitutive behavior in a porous medium | [02s08a38-Constitutive-behavior-in-a-porous-medium.md](./chs/02s08a38-Constitutive-behavior-in-a-porous-medium.md) | [02s08a38-Constitutive-behavior-in-a-porous-medium.md](./eng/02s08a38-Constitutive-behavior-in-a-porous-medium.md) |
| 2.8.4 多孔介质中润湿液相的连续性方程 | 2.8.4 Continuity statement for the wetting liquid phase in a porous medium | [02s08a39-Continuity-statement-for-the-wetting-liq.md](./chs/02s08a39-Continuity-statement-for-the-wetting-liq.md) | [02s08a39-Continuity-statement-for-the-wetting-liq.md](./eng/02s08a39-Continuity-statement-for-the-wetting-liq.md) |
| 2.8.5 耦合扩散/变形求解策略 | 2.8.5 Solution strategy for coupled diffusion/deformation | [02s08a40-Solution-strategy-for-coupled-diffusiond.md](./chs/02s08a40-Solution-strategy-for-coupled-diffusiond.md) | [02s08a40-Solution-strategy-for-coupled-diffusiond.md](./eng/02s08a40-Solution-strategy-for-coupled-diffusiond.md) |
| 2.9 耦合流体-固体分析 | 2.9 Coupled fluid-solid analysis | [02s09-Section.md](./chs/02s09-Section.md) | [02s09-Section.md](./eng/02s09-Section.md) |
| 2.9.1 耦合声学-结构介质分析 | 2.9.1 Coupled acoustic-structural medium analysis | [02s09a41-Coupled-acoustic-structural-medium-analy.md](./chs/02s09a41-Coupled-acoustic-structural-medium-analy.md) | [02s09a41-Coupled-acoustic-structural-medium-analy.md](./eng/02s09a41-Coupled-acoustic-structural-medium-analy.md) |
| 2.10 压电分析 | 2.10 Piezoelectric analysis | [02s10-Section.md](./chs/02s10-Section.md) | [02s10-Section.md](./eng/02s10-Section.md) |
| 2.10.1 压电分析 | 2.10.1 Piezoelectric analysis | [02s10a42-Piezoelectric-analysis.md](./chs/02s10a42-Piezoelectric-analysis.md) | [02s10a42-Piezoelectric-analysis.md](./eng/02s10a42-Piezoelectric-analysis.md) |
| 2.11 热传递 | 2.11 Heat transfer | [02s11-Section.md](./chs/02s11-Section.md) | [02s11-Section.md](./eng/02s11-Section.md) |
| 2.11.1 非耦合热传递分析 | 2.11.1 Uncoupled heat transfer analysis | [02s11a43-Uncoupled-heat-transfer-analysis.md](./chs/02s11a43-Uncoupled-heat-transfer-analysis.md) | [02s11a43-Uncoupled-heat-transfer-analysis.md](./eng/02s11a43-Uncoupled-heat-transfer-analysis.md) |
| 2.11.2 壳体热传导 | 2.11.2 Shell heat conduction | [02s11a44-Shell-heat-conduction.md](./chs/02s11a44-Shell-heat-conduction.md) | [02s11a44-Shell-heat-conduction.md](./eng/02s11a44-Shell-heat-conduction.md) |
| 2.11.3 对流/扩散 | 2.11.3 Convection/diffusion | [02s11a45-Convectiondiffusion.md](./chs/02s11a45-Convectiondiffusion.md) | [02s11a45-Convectiondiffusion.md](./eng/02s11a45-Convectiondiffusion.md) |
| 2.11.4 腔体辐射 | 2.11.4 Cavity radiation | [02s11a46-Cavity-radiation.md](./chs/02s11a46-Cavity-radiation.md) | [02s11a46-Cavity-radiation.md](./eng/02s11a46-Cavity-radiation.md) |
| 2.11.5 视角因子计算 | 2.11.5 View factor calculation | [02s11a47-View-factor-calculation.md](./chs/02s11a47-View-factor-calculation.md) | [02s11a47-View-factor-calculation.md](./eng/02s11a47-View-factor-calculation.md) |
| 2.12 耦合热-电分析 | 2.12 Coupled thermal-electrical analysis | [02s12-Section.md](./chs/02s12-Section.md) | [02s12-Section.md](./eng/02s12-Section.md) |
| 2.12.1 耦合热-电分析 | 2.12.1 Coupled thermal-electrical analysis | [02s12a48-Coupled-thermal-electrical-analysis.md](./chs/02s12a48-Coupled-thermal-electrical-analysis.md) | [02s12a48-Coupled-thermal-electrical-analysis.md](./eng/02s12a48-Coupled-thermal-electrical-analysis.md) |
| 2.13 质量扩散 | 2.13 Mass diffusion | [02s13-Section.md](./chs/02s13-Section.md) | [02s13-Section.md](./eng/02s13-Section.md) |
| 2.13.1 质量扩散分析 | 2.13.1 Mass diffusion analysis | [02s13a49-Mass-diffusion-analysis.md](./chs/02s13a49-Mass-diffusion-analysis.md) | [02s13a49-Mass-diffusion-analysis.md](./eng/02s13a49-Mass-diffusion-analysis.md) |
| 2.14 子结构 | 2.14 Substructuring | [02s14-Section.md](./chs/02s14-Section.md) | [02s14-Section.md](./eng/02s14-Section.md) |
| 2.14.1 子结构与子结构分析 | 2.14.1 Substructuring and substructure analysis | [02s14a50-Substructuring-and-substructure-analysis.md](./chs/02s14a50-Substructuring-and-substructure-analysis.md) | [02s14a50-Substructuring-and-substructure-analysis.md](./eng/02s14a50-Substructuring-and-substructure-analysis.md) |
| 2.15 子模型 | 2.15 Submodeling | [02s15-Section.md](./chs/02s15-Section.md) | [02s15-Section.md](./eng/02s15-Section.md) |
| 2.15.1 子模型分析 | 2.15.1 Submodeling analysis | [02s15a51-Submodeling-analysis.md](./chs/02s15a51-Submodeling-analysis.md) | [02s15a51-Submodeling-analysis.md](./eng/02s15a51-Submodeling-analysis.md) |
| 2.16 断裂力学 | 2.16 Fracture mechanics | [02s16-Section.md](./chs/02s16-Section.md) | [02s16-Section.md](./eng/02s16-Section.md) |
| 2.16.1 J积分评估 | 2.16.1 J-integral evaluation | [02s16a52-J-integral-evaluation.md](./chs/02s16a52-J-integral-evaluation.md) | [02s16a52-J-integral-evaluation.md](./eng/02s16a52-J-integral-evaluation.md) |
| 2.16.2 应力强度因子提取 | 2.16.2 Stress intensity factor extraction | [02s16a53-Stress-intensity-factor-extraction.md](./chs/02s16a53-Stress-intensity-factor-extraction.md) | [02s16a53-Stress-intensity-factor-extraction.md](./eng/02s16a53-Stress-intensity-factor-extraction.md) |
| 2.16.3 T应力提取 | 2.16.3 T-stress extraction | [02s16a54-T-stress-extraction.md](./chs/02s16a54-T-stress-extraction.md) | [02s16a54-T-stress-extraction.md](./eng/02s16a54-T-stress-extraction.md) |
| 2.16.4 裂纹扩展方向预测 | 2.16.4 Prediction of the direction of crack propagation | [02s16a55-Prediction-of-the-direction-of-crack-pro.md](./chs/02s16a55-Prediction-of-the-direction-of-crack-pro.md) | [02s16a55-Prediction-of-the-direction-of-crack-pro.md](./eng/02s16a55-Prediction-of-the-direction-of-crack-pro.md) |
| 2.17 应力线性化 | 2.17 Stress linearization | [02s17-Section.md](./chs/02s17-Section.md) | [02s17-Section.md](./eng/02s17-Section.md) |
| 2.17.1 应力线性化 | 2.17.1 Stress linearization | [02s17a56-Stress-linearization.md](./chs/02s17a56-Stress-linearization.md) | [02s17a56-Stress-linearization.md](./eng/02s17a56-Stress-linearization.md) |
| 2.18 设计灵敏度分析 | 2.18 Design sensitivity analysis | [02s18-Section.md](./chs/02s18-Section.md) | [02s18-Section.md](./eng/02s18-Section.md) |
| 2.18.1 设计灵敏度分析 | 2.18.1 Design sensitivity analysis | [02s18a57-Design-sensitivity-analysis.md](./chs/02s18a57-Design-sensitivity-analysis.md) | [02s18a57-Design-sensitivity-analysis.md](./eng/02s18a57-Design-sensitivity-analysis.md) |
| 3.1 概述 | 3.1 Overview | [03s01-Section.md](./chs/03s01-Section.md) | [03s01-Section.md](./eng/03s01-Section.md) |
| 3.1.1 单元库：概述 | 3.1.1 Element library: overview | [03s01a58-Element-library-overview.md](./chs/03s01a58-Element-library-overview.md) | [03s01a58-Element-library-overview.md](./eng/03s01a58-Element-library-overview.md) |
| 3.2 连续体单元 | 3.2 Continuum elements | [03s02-Section.md](./chs/03s02-Section.md) | [03s02-Section.md](./eng/03s02-Section.md) |
| 3.2.1 实体单元概述 | 3.2.1 Solid element overview | [03s02a59-Solid-element-overview.md](./chs/03s02a59-Solid-element-overview.md) | [03s02a59-Solid-element-overview.md](./eng/03s02a59-Solid-element-overview.md) |
| 3.2.2 实体单元公式 | 3.2.2 Solid element formulation | [03s02a60-Solid-element-formulation.md](./chs/03s02a60-Solid-element-formulation.md) | [03s02a60-Solid-element-formulation.md](./eng/03s02a60-Solid-element-formulation.md) |
| 3.2.3 混合不可压缩实体单元公式 | 3.2.3 Hybrid incompressible solid element formulation | [03s02a61-Hybrid-incompressible-solid-element-form.md](./chs/03s02a61-Hybrid-incompressible-solid-element-form.md) | [03s02a61-Hybrid-incompressible-solid-element-form.md](./eng/03s02a61-Hybrid-incompressible-solid-element-form.md) |
| 3.2.4 实体等参数四边形和六面体 | 3.2.4 Solid isoparametric quadrilaterals and hexahedra | [03s02a62-Solid-isoparametric-quadrilaterals-and-h.md](./chs/03s02a62-Solid-isoparametric-quadrilaterals-and-h.md) | [03s02a62-Solid-isoparametric-quadrilaterals-and-h.md](./eng/03s02a62-Solid-isoparametric-quadrilaterals-and-h.md) |
| 3.2.5 带不兼容模式的连续体单元 | 3.2.5 Continuum elements with incompatible modes | [03s02a63-Continuum-elements-with-incompatible-mod.md](./chs/03s02a63-Continuum-elements-with-incompatible-mod.md) | [03s02a63-Continuum-elements-with-incompatible-mod.md](./eng/03s02a63-Continuum-elements-with-incompatible-mod.md) |
| 3.2.6 三角形、四面体和楔形单元 | 3.2.6 Triangular, tetrahedral, and wedge elements | [03s02a64-Triangular-tetrahedral-and-wedge-element.md](./chs/03s02a64-Triangular-tetrahedral-and-wedge-element.md) | [03s02a64-Triangular-tetrahedral-and-wedge-element.md](./eng/03s02a64-Triangular-tetrahedral-and-wedge-element.md) |
| 3.2.7 广义平面应变单元 | 3.2.7 Generalized plane strain elements | [03s02a65-Generalized-plane-strain-elements.md](./chs/03s02a65-Generalized-plane-strain-elements.md) | [03s02a65-Generalized-plane-strain-elements.md](./eng/03s02a65-Generalized-plane-strain-elements.md) |
| 3.2.8 轴对称单元 | 3.2.8 Axisymmetric elements | [03s02a66-Axisymmetric-elements.md](./chs/03s02a66-Axisymmetric-elements.md) | [03s02a66-Axisymmetric-elements.md](./eng/03s02a66-Axisymmetric-elements.md) |
| 3.2.9 允许非线性弯曲的轴对称单元 | 3.2.9 Axisymmetric elements allowing nonlinear bending | [03s02a67-Axisymmetric-elements-allowing-nonlinear.md](./chs/03s02a67-Axisymmetric-elements-allowing-nonlinear.md) | [03s02a67-Axisymmetric-elements-allowing-nonlinear.md](./eng/03s02a67-Axisymmetric-elements-allowing-nonlinear.md) |
| 3.3 无限单元 | 3.3 Infinite elements | [03s03-Section.md](./chs/03s03-Section.md) | [03s03-Section.md](./eng/03s03-Section.md) |
| 3.3.1 实体无限单元 | 3.3.1 Solid infinite elements | [03s03a68-Solid-infinite-elements.md](./chs/03s03a68-Solid-infinite-elements.md) | [03s03a68-Solid-infinite-elements.md](./eng/03s03a68-Solid-infinite-elements.md) |
| 3.3.2 声学无限单元 | 3.3.2 Acoustic infinite elements | [03s03a69-Acoustic-infinite-elements.md](./chs/03s03a69-Acoustic-infinite-elements.md) | [03s03a69-Acoustic-infinite-elements.md](./eng/03s03a69-Acoustic-infinite-elements.md) |
| 3.4 薄膜和桁架单元 | 3.4 Membrane and truss elements | [03s04-Section.md](./chs/03s04-Section.md) | [03s04-Section.md](./eng/03s04-Section.md) |
| 3.4.1 薄膜单元 | 3.4.1 Membrane elements | [03s04a70-Membrane-elements.md](./chs/03s04a70-Membrane-elements.md) | [03s04a70-Membrane-elements.md](./eng/03s04a70-Membrane-elements.md) |
| 3.4.2 桁架单元 | 3.4.2 Truss elements | [03s04a71-Truss-elements.md](./chs/03s04a71-Truss-elements.md) | [03s04a71-Truss-elements.md](./eng/03s04a71-Truss-elements.md) |
| 3.4.3 轴对称薄膜 | 3.4.3 Axisymmetric membranes | [03s04a72-Axisymmetric-membranes.md](./chs/03s04a72-Axisymmetric-membranes.md) | [03s04a72-Axisymmetric-membranes.md](./eng/03s04a72-Axisymmetric-membranes.md) |
| 3.5 梁单元 | 3.5 Beam elements | [03s05-Section.md](./chs/03s05-Section.md) | [03s05-Section.md](./eng/03s05-Section.md) |
| 3.5.1 梁单元概述 | 3.5.1 Beam element overview | [03s05a73-Beam-element-overview.md](./chs/03s05a73-Beam-element-overview.md) | [03s05a73-Beam-element-overview.md](./eng/03s05a73-Beam-element-overview.md) |
| 3.5.2 梁单元公式 | 3.5.2 Beam element formulation | [03s05a74-Beam-element-formulation.md](./chs/03s05a74-Beam-element-formulation.md) | [03s05a74-Beam-element-formulation.md](./eng/03s05a74-Beam-element-formulation.md) |
| 3.5.3 Euler-Bernoulli梁单元 | 3.5.3 Euler-Bernoulli beam elements | [03s05a75-Euler-Bernoulli-beam-elements.md](./chs/03s05a75-Euler-Bernoulli-beam-elements.md) | [03s05a75-Euler-Bernoulli-beam-elements.md](./eng/03s05a75-Euler-Bernoulli-beam-elements.md) |
| 3.5.4 混合梁单元 | 3.5.4 Hybrid beam elements | [03s05a76-Hybrid-beam-elements.md](./chs/03s05a76-Hybrid-beam-elements.md) | [03s05a76-Hybrid-beam-elements.md](./eng/03s05a76-Hybrid-beam-elements.md) |
| 3.5.5 Timoshenko梁的质量和惯性 | 3.5.5 Mass and inertia for Timoshenko beams | [03s05a77-Mass-and-inertia-for-Timoshenko-beams.md](./chs/03s05a77-Mass-and-inertia-for-Timoshenko-beams.md) | [03s05a77-Mass-and-inertia-for-Timoshenko-beams.md](./eng/03s05a77-Mass-and-inertia-for-Timoshenko-beams.md) |
| 3.5.6 网格化梁横截面 | 3.5.6 Meshed beam cross-sections | [03s05a78-Meshed-beam-cross-sections.md](./chs/03s05a78-Meshed-beam-cross-sections.md) | [03s05a78-Meshed-beam-cross-sections.md](./eng/03s05a78-Meshed-beam-cross-sections.md) |
| 3.6 壳单元 | 3.6 Shell elements | [03s06-Section.md](./chs/03s06-Section.md) | [03s06-Section.md](./eng/03s06-Section.md) |
| 3.6.1 壳单元概述 | 3.6.1 Shell element overview | [03s06a79-Shell-element-overview.md](./chs/03s06a79-Shell-element-overview.md) | [03s06a79-Shell-element-overview.md](./eng/03s06a79-Shell-element-overview.md) |
| 3.6.2 轴对称壳单元 | 3.6.2 Axisymmetric shell elements | [03s06a80-Axisymmetric-shell-elements.md](./chs/03s06a80-Axisymmetric-shell-elements.md) | [03s06a80-Axisymmetric-shell-elements.md](./eng/03s06a80-Axisymmetric-shell-elements.md) |
| 3.6.3 剪切柔性小应变壳单元 | 3.6.3 Shear flexible small-strain shell elements | [03s06a81-Shear-flexible-small-strain-shell-elemen.md](./chs/03s06a81-Shear-flexible-small-strain-shell-elemen.md) | [03s06a81-Shear-flexible-small-strain-shell-elemen.md](./eng/03s06a81-Shear-flexible-small-strain-shell-elemen.md) |
| 3.6.4 三角形面壳单元 | 3.6.4 Triangular facet shell elements | [03s06a82-Triangular-facet-shell-elements.md](./chs/03s06a82-Triangular-facet-shell-elements.md) | [03s06a82-Triangular-facet-shell-elements.md](./eng/03s06a82-Triangular-facet-shell-elements.md) |
| 3.6.5 有限应变壳单元公式 | 3.6.5 Finite-strain shell element formulation | [03s06a83-Finite-strain-shell-element-formulation.md](./chs/03s06a83-Finite-strain-shell-element-formulation.md) | [03s06a83-Finite-strain-shell-element-formulation.md](./eng/03s06a83-Finite-strain-shell-element-formulation.md) |
| 3.6.6 Abaqus/Explicit中的小应变壳单元 | 3.6.6 Small-strain shell elements in Abaqus/Explicit | [03s06a84-Small-strain-shell-elements-in-AbaqusExp.md](./chs/03s06a84-Small-strain-shell-elements-in-AbaqusExp.md) | [03s06a84-Small-strain-shell-elements-in-AbaqusExp.md](./eng/03s06a84-Small-strain-shell-elements-in-AbaqusExp.md) |
| 3.6.7 允许非对称加载的轴对称壳单元 | 3.6.7 Axisymmetric shell element allowing asymmetric loading | [03s06a85-Axisymmetric-shell-element-allowing-asym.md](./chs/03s06a85-Axisymmetric-shell-element-allowing-asym.md) | [03s06a85-Axisymmetric-shell-element-allowing-asym.md](./eng/03s06a85-Axisymmetric-shell-element-allowing-asym.md) |
| 3.6.8 复合壳中的横向剪切刚度及从中面的偏移 | 3.6.8 Transverse shear stiffness in composite shells and offsets from the midsurface | [03s06a86-Transverse-shear-stiffness-in-composite-.md](./chs/03s06a86-Transverse-shear-stiffness-in-composite-.md) | [03s06a86-Transverse-shear-stiffness-in-composite-.md](./eng/03s06a86-Transverse-shear-stiffness-in-composite-.md) |
| 3.6.9 5自由度壳单元的旋转惯性 | 3.6.9 Rotary inertia for 5 degree of freedom shell elements | [03s06a87-Rotary-inertia-for-5-degree-of-freedom-s.md](./chs/03s06a87-Rotary-inertia-for-5-degree-of-freedom-s.md) | [03s06a87-Rotary-inertia-for-5-degree-of-freedom-s.md](./eng/03s06a87-Rotary-inertia-for-5-degree-of-freedom-s.md) |
| 3.7 钢筋 | 3.7 Rebar | [03s07-Section.md](./chs/03s07-Section.md) | [03s07-Section.md](./eng/03s07-Section.md) |
| 3.7.1 二维中的钢筋建模 | 3.7.1 Rebar modeling in two dimensions | [03s07a88-Rebar-modeling-in-two-dimensions.md](./chs/03s07a88-Rebar-modeling-in-two-dimensions.md) | [03s07a88-Rebar-modeling-in-two-dimensions.md](./eng/03s07a88-Rebar-modeling-in-two-dimensions.md) |
| 3.7.2 三维中的钢筋建模 | 3.7.2 Rebar modeling in three dimensions | [03s07a89-Rebar-modeling-in-three-dimensions.md](./chs/03s07a89-Rebar-modeling-in-three-dimensions.md) | [03s07a89-Rebar-modeling-in-three-dimensions.md](./eng/03s07a89-Rebar-modeling-in-three-dimensions.md) |
| 3.7.3 壳、膜和表面单元中的钢筋建模 | 3.7.3 Rebar modeling in shell, membrane, and surface elements | [03s07a90-Rebar-modeling-in-shell-membrane-and-sur.md](./chs/03s07a90-Rebar-modeling-in-shell-membrane-and-sur.md) | [03s07a90-Rebar-modeling-in-shell-membrane-and-sur.md](./eng/03s07a90-Rebar-modeling-in-shell-membrane-and-sur.md) |
| 3.8 静水压流体计算 | 3.8 Hydrostatic fluid calculations | [03s08-Section.md](./chs/03s08-Section.md) | [03s08-Section.md](./eng/03s08-Section.md) |
| 3.8.1 静水压流体计算 | 3.8.1 Hydrostatic fluid calculations | [03s08a91-Hydrostatic-fluid-calculations.md](./chs/03s08a91-Hydrostatic-fluid-calculations.md) | [03s08a91-Hydrostatic-fluid-calculations.md](./eng/03s08a91-Hydrostatic-fluid-calculations.md) |
| 3.9 专用单元 | 3.9 Special-purpose elements | [03s09-Section.md](./chs/03s09-Section.md) | [03s09-Section.md](./eng/03s09-Section.md) |
| 3.9.1 弯管单元 | 3.9.1 Elbow elements | [03s09a92-Elbow-elements.md](./chs/03s09a92-Elbow-elements.md) | [03s09a92-Elbow-elements.md](./eng/03s09a92-Elbow-elements.md) |
| 3.9.2 带集中塑性的框架单元 | 3.9.2 Frame elements with lumped plasticity | [03s09a93-Frame-elements-with-lumped-plasticity.md](./chs/03s09a93-Frame-elements-with-lumped-plasticity.md) | [03s09a93-Frame-elements-with-lumped-plasticity.md](./eng/03s09a93-Frame-elements-with-lumped-plasticity.md) |
| 3.9.3 框架单元的屈曲支撑响应 | 3.9.3 Buckling strut response for frame elements | [03s09a94-Buckling-strut-response-for-frame-elemen.md](./chs/03s09a94-Buckling-strut-response-for-frame-elemen.md) | [03s09a94-Buckling-strut-response-for-frame-elemen.md](./eng/03s09a94-Buckling-strut-response-for-frame-elemen.md) |
| 3.9.4 管道支撑单元 | 3.9.4 Tube support elements | [03s09a95-Tube-support-elements.md](./chs/03s09a95-Tube-support-elements.md) | [03s09a95-Tube-support-elements.md](./eng/03s09a95-Tube-support-elements.md) |
| 3.9.5 线弹簧单元 | 3.9.5 Line spring elements | [03s09a96-Line-spring-elements.md](./chs/03s09a96-Line-spring-elements.md) | [03s09a96-Line-spring-elements.md](./eng/03s09a96-Line-spring-elements.md) |
| 3.9.6 柔性关节单元 | 3.9.6 Flexible joint element | [03s09a97-Flexible-joint-element.md](./chs/03s09a97-Flexible-joint-element.md) | [03s09a97-Flexible-joint-element.md](./eng/03s09a97-Flexible-joint-element.md) |
| 3.9.7 旋转惯性单元 | 3.9.7 Rotary inertia element | [03s09a98-Rotary-inertia-element.md](./chs/03s09a98-Rotary-inertia-element.md) | [03s09a98-Rotary-inertia-element.md](./eng/03s09a98-Rotary-inertia-element.md) |
| 3.9.8 分布耦合单元 | 3.9.8 Distributing coupling elements | [03s09a99-Distributing-coupling-elements.md](./chs/03s09a99-Distributing-coupling-elements.md) | [03s09a99-Distributing-coupling-elements.md](./eng/03s09a99-Distributing-coupling-elements.md) |
| 4.1 概述 | 4.1 Overview | [04s01-Section.md](./chs/04s01-Section.md) | [04s01-Section.md](./eng/04s01-Section.md) |
| 4.1.1 机械本构模型 | 4.1.1 Mechanical constitutive models | [04s01a100-Mechanical-constitutive-models.md](./chs/04s01a100-Mechanical-constitutive-models.md) | [04s01a100-Mechanical-constitutive-models.md](./eng/04s01a100-Mechanical-constitutive-models.md) |
| 4.2 塑性概述 | 4.2 Plasticity overview | [04s02-Section.md](./chs/04s02-Section.md) | [04s02-Section.md](./eng/04s02-Section.md) |
| 4.2.1 塑性模型：一般讨论 | 4.2.1 Plasticity models: general discussion | [04s02a101-Plasticity-models-general-discussion.md](./chs/04s02a101-Plasticity-models-general-discussion.md) | [04s02a101-Plasticity-models-general-discussion.md](./eng/04s02a101-Plasticity-models-general-discussion.md) |
| 4.2.2 塑性模型的积分 | 4.2.2 Integration of plasticity models | [04s02a102-Integration-of-plasticity-models.md](./chs/04s02a102-Integration-of-plasticity-models.md) | [04s02a102-Integration-of-plasticity-models.md](./eng/04s02a102-Integration-of-plasticity-models.md) |
| 4.3 金属塑性 | 4.3 Metal plasticity | [04s03-Section.md](./chs/04s03-Section.md) | [04s03-Section.md](./eng/04s03-Section.md) |
| 4.3.1 金属塑性模型 | 4.3.1 Metal plasticity models | [04s03a103-Metal-plasticity-models.md](./chs/04s03a103-Metal-plasticity-models.md) | [04s03a103-Metal-plasticity-models.md](./eng/04s03a103-Metal-plasticity-models.md) |
| 4.3.2 各向同性弹塑性 | 4.3.2 Isotropic elasto-plasticity | [04s03a104-Isotropic-elasto-plasticity.md](./chs/04s03a104-Isotropic-elasto-plasticity.md) | [04s03a104-Isotropic-elasto-plasticity.md](./eng/04s03a104-Isotropic-elasto-plasticity.md) |
| 4.3.3 各向异性金属塑性的应力势 | 4.3.3 Stress potentials for anisotropic metal plasticity | [04s03a105-Stress-potentials-for-anisotropic-metal-.md](./chs/04s03a105-Stress-potentials-for-anisotropic-metal-.md) | [04s03a105-Stress-potentials-for-anisotropic-metal-.md](./eng/04s03a105-Stress-potentials-for-anisotropic-metal-.md) |
| 4.3.4 率相关金属塑性（蠕变） | 4.3.4 Rate-dependent metal plasticity (creep) | [04s03a106-Rate-dependent-metal-plasticity-creep.md](./chs/04s03a106-Rate-dependent-metal-plasticity-creep.md) | [04s03a106-Rate-dependent-metal-plasticity-creep.md](./eng/04s03a106-Rate-dependent-metal-plasticity-creep.md) |
| 4.3.5 经受循环加载的金属模型 | 4.3.5 Models for metals subjected to cyclic loading | [04s03a107-Models-for-metals-subjected-to-cyclic-lo.md](./chs/04s03a107-Models-for-metals-subjected-to-cyclic-lo.md) | [04s03a107-Models-for-metals-subjected-to-cyclic-lo.md](./eng/04s03a107-Models-for-metals-subjected-to-cyclic-lo.md) |
| 4.3.6 多孔金属塑性 | 4.3.6 Porous metal plasticity | [04s03a108-Porous-metal-plasticity.md](./chs/04s03a108-Porous-metal-plasticity.md) | [04s03a108-Porous-metal-plasticity.md](./eng/04s03a108-Porous-metal-plasticity.md) |
| 4.3.7 铸铁塑性 | 4.3.7 Cast iron plasticity | [04s03a109-Cast-iron-plasticity.md](./chs/04s03a109-Cast-iron-plasticity.md) | [04s03a109-Cast-iron-plasticity.md](./eng/04s03a109-Cast-iron-plasticity.md) |
| 4.3.8 ORNL本构理论 | 4.3.8 ORNL constitutive theory | [04s03a110-ORNL-constitutive-theory.md](./chs/04s03a110-ORNL-constitutive-theory.md) | [04s03a110-ORNL-constitutive-theory.md](./eng/04s03a110-ORNL-constitutive-theory.md) |
| 4.3.9 变形塑性 | 4.3.9 Deformation plasticity | [04s03a111-Deformation-plasticity.md](./chs/04s03a111-Deformation-plasticity.md) | [04s03a111-Deformation-plasticity.md](./eng/04s03a111-Deformation-plasticity.md) |
| 4.3.10 塑性应变引起的热生成 | 4.3.10 Heat generation caused by plastic straining | [04s03a112-Heat-generation-caused-by-plastic-strain.md](./chs/04s03a112-Heat-generation-caused-by-plastic-strain.md) | [04s03a112-Heat-generation-caused-by-plastic-strain.md](./eng/04s03a112-Heat-generation-caused-by-plastic-strain.md) |
| 4.4 非金属塑性 | 4.4 Plasticity for non-metals | [04s04-Section.md](./chs/04s04-Section.md) | [04s04-Section.md](./eng/04s04-Section.md) |
| 4.4.1 多孔弹性 | 4.4.1 Porous elasticity | [04s04a113-Porous-elasticity.md](./chs/04s04a113-Porous-elasticity.md) | [04s04a113-Porous-elasticity.md](./eng/04s04a113-Porous-elasticity.md) |
| 4.4.2 颗粒或聚合物行为模型 | 4.4.2 Models for granular or polymer behavior | [04s04a114-Models-for-granular-or-polymer-behavior.md](./chs/04s04a114-Models-for-granular-or-polymer-behavior.md) | [04s04a114-Models-for-granular-or-polymer-behavior.md](./eng/04s04a114-Models-for-granular-or-polymer-behavior.md) |
| 4.4.3 临界状态模型 | 4.4.3 Critical state models | [04s04a115-Critical-state-models.md](./chs/04s04a115-Critical-state-models.md) | [04s04a115-Critical-state-models.md](./eng/04s04a115-Critical-state-models.md) |
| 4.4.4 地质材料的Drucker-Prager/帽模型 | 4.4.4 Drucker-Prager/Cap model for geological materials | [04s04a116-Drucker-PragerCap-model-for-geological-m.md](./chs/04s04a116-Drucker-PragerCap-model-for-geological-m.md) | [04s04a116-Drucker-PragerCap-model-for-geological-m.md](./eng/04s04a116-Drucker-PragerCap-model-for-geological-m.md) |
| 4.4.5 Mohr-Coulomb模型 | 4.4.5 Mohr-Coulomb model | [04s04a117-Mohr-Coulomb-model.md](./chs/04s04a117-Mohr-Coulomb-model.md) | [04s04a117-Mohr-Coulomb-model.md](./eng/04s04a117-Mohr-Coulomb-model.md) |
| 4.4.6 可压碎泡沫模型 | 4.4.6 Models for crushable foams | [04s04a118-Models-for-crushable-foams.md](./chs/04s04a118-Models-for-crushable-foams.md) | [04s04a118-Models-for-crushable-foams.md](./eng/04s04a118-Models-for-crushable-foams.md) |
| 4.5 其他非弹性模型 | 4.5 Other inelastic models | [04s05-Section.md](./chs/04s05-Section.md) | [04s05-Section.md](./eng/04s05-Section.md) |
| 4.5.1 混凝土的非弹性本构模型 | 4.5.1 An inelastic constitutive model for concrete | [04s05a119-An-inelastic-constitutive-model-for-conc.md](./chs/04s05a119-An-inelastic-constitutive-model-for-conc.md) | [04s05a119-An-inelastic-constitutive-model-for-conc.md](./eng/04s05a119-An-inelastic-constitutive-model-for-conc.md) |
| 4.5.2 混凝土和其他准脆性材料的损伤塑性模型 | 4.5.2 Damaged plasticity model for concrete and other quasi-brittle materials | [04s05a120-Damaged-plasticity-model-for-concrete-an.md](./chs/04s05a120-Damaged-plasticity-model-for-concrete-an.md) | [04s05a120-Damaged-plasticity-model-for-concrete-an.md](./eng/04s05a120-Damaged-plasticity-model-for-concrete-an.md) |
| 4.5.3 混凝土和其他脆性材料的裂缝模型 | 4.5.3 A cracking model for concrete and other brittle materials | [04s05a121-A-cracking-model-for-concrete-and-other-.md](./chs/04s05a121-A-cracking-model-for-concrete-and-other-.md) | [04s05a121-A-cracking-model-for-concrete-and-other-.md](./eng/04s05a121-A-cracking-model-for-concrete-and-other-.md) |
| 4.5.4 节理材料本构模型 | 4.5.4 Constitutive model for jointed materials | [04s05a122-Constitutive-model-for-jointed-materials.md](./chs/04s05a122-Constitutive-model-for-jointed-materials.md) | [04s05a122-Constitutive-model-for-jointed-materials.md](./eng/04s05a122-Constitutive-model-for-jointed-materials.md) |
| 4.6 大应变弹性 | 4.6 Large-strain elasticity | [04s06-Section.md](./chs/04s06-Section.md) | [04s06-Section.md](./eng/04s06-Section.md) |
| 4.6.1 超弹性材料行为 | 4.6.1 Hyperelastic material behavior | [04s06a123-Hyperelastic-material-behavior.md](./chs/04s06a123-Hyperelastic-material-behavior.md) | [04s06a123-Hyperelastic-material-behavior.md](./eng/04s06a123-Hyperelastic-material-behavior.md) |
| 4.6.2 超弹性和超泡沫常数的拟合 | 4.6.2 Fitting of hyperelastic and hyperfoam constants | [04s06a124-Fitting-of-hyperelastic-and-hyperfoam-co.md](./chs/04s06a124-Fitting-of-hyperelastic-and-hyperfoam-co.md) | [04s06a124-Fitting-of-hyperelastic-and-hyperfoam-co.md](./eng/04s06a124-Fitting-of-hyperelastic-and-hyperfoam-co.md) |
| 4.6.3 各向异性超弹性材料行为 | 4.6.3 Anisotropic hyperelastic material behavior | [04s06a125-Anisotropic-hyperelastic-material-behavi.md](./chs/04s06a125-Anisotropic-hyperelastic-material-behavi.md) | [04s06a125-Anisotropic-hyperelastic-material-behavi.md](./eng/04s06a125-Anisotropic-hyperelastic-material-behavi.md) |
| 4.7 Mullins效应和永久变形 | 4.7 Mullins effect and permanent set | [04s07-Section.md](./chs/04s07-Section.md) | [04s07-Section.md](./eng/04s07-Section.md) |
| 4.7 Mullins效应和永久变形 | 4.7.1 Mullins effect | [04s07a126-Mullins-effect.md](./chs/04s07a126-Mullins-effect.md) | [04s07a126-Mullins-effect.md](./eng/04s07a126-Mullins-effect.md) |
| 4.7.2 永久变形 | 4.7.2 Permanent set | [04s07a127-Permanent-set.md](./chs/04s07a127-Permanent-set.md) | [04s07a127-Permanent-set.md](./eng/04s07a127-Permanent-set.md) |
| 4.8 粘弹性 | 4.8 Viscoelasticity | [04s08-Section.md](./chs/04s08-Section.md) | [04s08-Section.md](./eng/04s08-Section.md) |
| 4.8 粘弹性 | 4.8.1 Viscoelasticity | [04s08a128-Viscoelasticity.md](./chs/04s08a128-Viscoelasticity.md) | [04s08a128-Viscoelasticity.md](./eng/04s08a128-Viscoelasticity.md) |
| 4.8.2 有限应变粘弹性 | 4.8.2 Finite-strain viscoelasticity | [04s08a129-Finite-strain-viscoelasticity.md](./chs/04s08a129-Finite-strain-viscoelasticity.md) | [04s08a129-Finite-strain-viscoelasticity.md](./eng/04s08a129-Finite-strain-viscoelasticity.md) |
| 4.8.3 频域粘弹性 | 4.8.3 Frequency domain viscoelasticity | [04s08a130-Frequency-domain-viscoelasticity.md](./chs/04s08a130-Frequency-domain-viscoelasticity.md) | [04s08a130-Frequency-domain-viscoelasticity.md](./eng/04s08a130-Frequency-domain-viscoelasticity.md) |
| 4.9 滞后 | 4.9 Hysteresis | [04s09-Section.md](./chs/04s09-Section.md) | [04s09-Section.md](./eng/04s09-Section.md) |
| 4.9 滞后 | 4.9.1 Hysteresis | [04s09a131-Hysteresis.md](./chs/04s09a131-Hysteresis.md) | [04s09a131-Hysteresis.md](./eng/04s09a131-Hysteresis.md) |
| 5.1 接触建模 | 5.1 Contact modeling | [05s01-Section.md](./chs/05s01-Section.md) | [05s01-Section.md](./eng/05s01-Section.md) |
| 5.1.1 物体间的小滑动相互作用 | 5.1.1 Small-sliding interaction between bodies | [05s01a132-Small-sliding-interaction-between-bodies.md](./chs/05s01a132-Small-sliding-interaction-between-bodies.md) | [05s01a132-Small-sliding-interaction-between-bodies.md](./eng/05s01a132-Small-sliding-interaction-between-bodies.md) |
| 5.1.2 可变形体之间的有限滑动相互作用 | 5.1.2 Finite-sliding interaction between deformable bodies | [05s01a133-Finite-sliding-interaction-between-defor.md](./chs/05s01a133-Finite-sliding-interaction-between-defor.md) | [05s01a133-Finite-sliding-interaction-between-defor.md](./eng/05s01a133-Finite-sliding-interaction-between-defor.md) |
| 5.1.3 可变形体与刚性体之间的有限滑动相互作用 | 5.1.3 Finite-sliding interaction between a deformable and a rigid body | [05s01a134-Finite-sliding-interaction-between-a-def.md](./chs/05s01a134-Finite-sliding-interaction-between-a-def.md) | [05s01a134-Finite-sliding-interaction-between-a-def.md](./eng/05s01a134-Finite-sliding-interaction-between-a-def.md) |
| 5.2 表面相互作用 | 5.2 Surface interactions | [05s02-Section.md](./chs/05s02-Section.md) | [05s02-Section.md](./eng/05s02-Section.md) |
| 5.2.1 接触压力定义 | 5.2.1 Contact pressure definition | [05s02a135-Contact-pressure-definition.md](./chs/05s02a135-Contact-pressure-definition.md) | [05s02a135-Contact-pressure-definition.md](./eng/05s02a135-Contact-pressure-definition.md) |
| 5.2.2 孔隙压力接触中的压力和流体流动 | 5.2.2 Pressure and fluid flow in pore pressure contact | [05s02a136-Pressure-and-fluid-flow-in-pore-pressure.md](./chs/05s02a136-Pressure-and-fluid-flow-in-pore-pressure.md) | [05s02a136-Pressure-and-fluid-flow-in-pore-pressure.md](./eng/05s02a136-Pressure-and-fluid-flow-in-pore-pressure.md) |
| 5.2.3 库仑摩擦 | 5.2.3 Coulomb friction | [05s02a137-Coulomb-friction.md](./chs/05s02a137-Coulomb-friction.md) | [05s02a137-Coulomb-friction.md](./eng/05s02a137-Coulomb-friction.md) |
| 5.2.4 热界面定义 | 5.2.4 Thermal interface definition | [05s02a138-Thermal-interface-definition.md](./chs/05s02a138-Thermal-interface-definition.md) | [05s02a138-Thermal-interface-definition.md](./eng/05s02a138-Thermal-interface-definition.md) |
| 5.2.5 由摩擦滑动引起的热生成 | 5.2.5 Heat generation caused by frictional sliding | [05s02a139-Heat-generation-caused-by-frictional-sli.md](./chs/05s02a139-Heat-generation-caused-by-frictional-sli.md) | [05s02a139-Heat-generation-caused-by-frictional-sli.md](./eng/05s02a139-Heat-generation-caused-by-frictional-sli.md) |
| 5.2.6 由电流引起的热生成 | 5.2.6 Heat generation caused by electrical current | [05s02a140-Heat-generation-caused-by-electrical-cur.md](./chs/05s02a140-Heat-generation-caused-by-electrical-cur.md) | [05s02a140-Heat-generation-caused-by-electrical-cur.md](./eng/05s02a140-Heat-generation-caused-by-electrical-cur.md) |
| 5.2.7 基于表面的声学-结构介质相互作用 | 5.2.7 Surface-based acoustic-structural medium interaction | [05s02a141-Surface-based-acoustic-structural-medium.md](./chs/05s02a141-Surface-based-acoustic-structural-medium.md) | [05s02a141-Surface-based-acoustic-structural-medium.md](./eng/05s02a141-Surface-based-acoustic-structural-medium.md) |
| 6.1 动态载荷 | 6.1 Dynamic loading | [06s01-Section.md](./chs/06s01-Section.md) | [06s01-Section.md](./eng/06s01-Section.md) |
| 6.1.1 离心、科里奥利和旋转加速度力 | 6.1.1 Centrifugal, Coriolis, and rotary acceleration forces | [06s01a142-Centrifugal-Coriolis-and-rotary-accelera.md](./chs/06s01a142-Centrifugal-Coriolis-and-rotary-accelera.md) | [06s01a142-Centrifugal-Coriolis-and-rotary-accelera.md](./eng/06s01a142-Centrifugal-Coriolis-and-rotary-accelera.md) |
| 6.1.2 加速度图的基线校正 | 6.1.2 Baseline correction of accelerograms | [06s01a143-Baseline-correction-of-accelerograms.md](./chs/06s01a143-Baseline-correction-of-accelerograms.md) | [06s01a143-Baseline-correction-of-accelerograms.md](./eng/06s01a143-Baseline-correction-of-accelerograms.md) |
| 6.2 Abaqus/Aqua载荷 | 6.2 Abaqus/Aqua loading | [06s02-Section.md](./chs/06s02-Section.md) | [06s02-Section.md](./eng/06s02-Section.md) |
| 6.2.1 拖曳、惯性和浮力载荷 | 6.2.1 Drag, inertia, and buoyancy loading | [06s02a144-Drag-inertia-and-buoyancy-loading.md](./chs/06s02a144-Drag-inertia-and-buoyancy-loading.md) | [06s02a144-Drag-inertia-and-buoyancy-loading.md](./eng/06s02a144-Drag-inertia-and-buoyancy-loading.md) |
|  | 6.2.2 Airy wave theory | [06s02a145-Airy-wave-theory.md](./chs/06s02a145-Airy-wave-theory.md) | [06s02a145-Airy-wave-theory.md](./eng/06s02a145-Airy-wave-theory.md) |
|  | 6.2.3 Stokes wave theory | [06s02a146-Stokes-wave-theory.md](./chs/06s02a146-Stokes-wave-theory.md) | [06s02a146-Stokes-wave-theory.md](./eng/06s02a146-Stokes-wave-theory.md) |
| 6.3 入射波载荷 | 6.3 Incident wave loading | [06s03-Section.md](./chs/06s03-Section.md) | [06s03-Section.md](./eng/06s03-Section.md) |
| 6.3 入射波载荷 | 6.3.1 Loading due to an incident dilatational wave field | [06s03a147-Loading-due-to-an-incident-dilatational-.md](./chs/06s03a147-Loading-due-to-an-incident-dilatational-.md) | [06s03a147-Loading-due-to-an-incident-dilatational-.md](./eng/06s03a147-Loading-due-to-an-incident-dilatational-.md) |
| 6.4 压力渗透载荷 | 6.4 Pressure penetration loading | [06s04-Section.md](./chs/06s04-Section.md) | [06s04-Section.md](./eng/06s04-Section.md) |
| 6.4.1 带表面接触的压力渗透载荷 | 6.4.1 Pressure penetration loading with surface-based contact | [06s04a148-Pressure-penetration-loading-with-surfac.md](./chs/06s04a148-Pressure-penetration-loading-with-surfac.md) | [06s04a148-Pressure-penetration-loading-with-surfac.md](./eng/06s04a148-Pressure-penetration-loading-with-surfac.md) |
| 6.5 载荷刚度 | 6.5 Load stiffness | [06s05-Section.md](./chs/06s05-Section.md) | [06s05-Section.md](./eng/06s05-Section.md) |
| 6.5.1 压力载荷刚度 | 6.5.1 Pressure load stiffness | [06s05a149-Pressure-load-stiffness.md](./chs/06s05a149-Pressure-load-stiffness.md) | [06s05a149-Pressure-load-stiffness.md](./eng/06s05a149-Pressure-load-stiffness.md) |
| 6.5.2 梁单元载荷刚度 | 6.5.2 Load stiffness for beam elements | [06s05a150-Load-stiffness-for-beam-elements.md](./chs/06s05a150-Load-stiffness-for-beam-elements.md) | [06s05a150-Load-stiffness-for-beam-elements.md](./eng/06s05a150-Load-stiffness-for-beam-elements.md) |
| 6.5.3 肘单元上的压力载荷 | 6.5.3 Pressure loadings on elbow elements | [06s05a151-Pressure-loadings-on-elbow-elements.md](./chs/06s05a151-Pressure-loadings-on-elbow-elements.md) | [06s05a151-Pressure-loadings-on-elbow-elements.md](./eng/06s05a151-Pressure-loadings-on-elbow-elements.md) |
| 6.6 多点约束 | 6.6 Multi-point constraints | [06s06-Section.md](./chs/06s06-Section.md) | [06s06-Section.md](./eng/06s06-Section.md) |
| 6.6.1 滑动约束 | 6.6.1 Sliding constraint | [06s06a152-Sliding-constraint.md](./chs/06s06a152-Sliding-constraint.md) | [06s06a152-Sliding-constraint.md](./eng/06s06a152-Sliding-constraint.md) |
| 6.6.2 壳到实体约束 | 6.6.2 Shell to solid constraint | [06s06a153-Shell-to-solid-constraint.md](./chs/06s06a153-Shell-to-solid-constraint.md) | [06s06a153-Shell-to-solid-constraint.md](./eng/06s06a153-Shell-to-solid-constraint.md) |
| 6.6.3 旋转关节 | 6.6.3 Revolute joint | [06s06a154-Revolute-joint.md](./chs/06s06a154-Revolute-joint.md) | [06s06a154-Revolute-joint.md](./eng/06s06a154-Revolute-joint.md) |
| 6.6.4 万向节 | 6.6.4 Universal joint | [06s06a155-Universal-joint.md](./chs/06s06a155-Universal-joint.md) | [06s06a155-Universal-joint.md](./eng/06s06a155-Universal-joint.md) |
| 6.6.5 局部速度约束 | 6.6.5 Local velocity constraint | [06s06a156-Local-velocity-constraint.md](./chs/06s06a156-Local-velocity-constraint.md) | [06s06a156-Local-velocity-constraint.md](./eng/06s06a156-Local-velocity-constraint.md) |
| 6.6.6 运动耦合 | 6.6.6 Kinematic coupling | [06s06a157-Kinematic-coupling.md](./chs/06s06a157-Kinematic-coupling.md) | [06s06a157-Kinematic-coupling.md](./eng/06s06a157-Kinematic-coupling.md) |
| 7.1 参考 | 7.1 References | [07s01-Section.md](./chs/07s01-Section.md) | [07s01-Section.md](./eng/07s01-Section.md) |
| 7.1.1 参考 | 7.1.1 References | [07s01a01-References.md](./chs/07s01a01-References.md) | [07s01a01-References.md](./eng/07s01a01-References.md) |

### 00
*Abaqus Theory Guide*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| Abaqus Theory Guide | Abaqus Theory Guide | [00-Book.md](./chs/00-Book.md) | [00-Book.md](./eng/00-Book.md) |

### 01
*1 引言与基本方程*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 1 引言与基本方程 | 1 Introduction and Basic Equations | [01-Introduction-and-Basic-Equations.md](./chs/01-Introduction-and-Basic-Equations.md) | [01-Introduction-and-Basic-Equations.md](./eng/01-Introduction-and-Basic-Equations.md) |

### 02
*2 分析步骤*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 2 分析步骤 | 2 Procedures | [02-Procedures.md](./chs/02-Procedures.md) | [02-Procedures.md](./eng/02-Procedures.md) |

### 03
*3 单元*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 3 单元 | 3 Elements | [03-Elements.md](./chs/03-Elements.md) | [03-Elements.md](./eng/03-Elements.md) |

### 04
*4 机械本构理论*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 4 机械本构理论 | 4 Mechanical Constitutive Theories | [04-Mechanical-Constitutive-Theories.md](./chs/04-Mechanical-Constitutive-Theories.md) | [04-Mechanical-Constitutive-Theories.md](./eng/04-Mechanical-Constitutive-Theories.md) |

### 05
*5 界面建模*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 5 界面建模 | 5 Interface Modeling | [05-Interface-Modeling.md](./chs/05-Interface-Modeling.md) | [05-Interface-Modeling.md](./eng/05-Interface-Modeling.md) |

### 06
*6 载荷与约束*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 6 载荷与约束 | 6 Loading and Constraints | [06-Loading-and-Constraints.md](./chs/06-Loading-and-Constraints.md) | [06-Loading-and-Constraints.md](./eng/06-Loading-and-Constraints.md) |

### 07
*7 参考*

| 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|-----------------|-----------------|-----------------|-----------------|
| 7 参考 | 7 References | [07-References.md](./chs/07-References.md) | [07-References.md](./eng/07-References.md) |

---

## 资源文件 / Resource Files

图片资源位于 `graphics/` 目录。

---

## 版权声明 / Copyright Notice

本翻译仅供学习研究使用，原文档版权归 Dassault Systèmes Simulia Corp. 所有。
This translation is for study and research purposes only. Original documentation copyright Dassault Systèmes Simulia Corp.