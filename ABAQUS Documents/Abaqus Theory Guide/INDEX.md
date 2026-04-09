# Abaqus Theory Guide (6.14)

## 文档索引 / Documentation Index

本手册为 ABAQUS 6.14 Theory Guide 的中文翻译版本。
This is the Chinese translation of the Abaqus 6.14 Theory Guide documentation.

**来源 / Source:** D:\SIMULIA\Documentation\docs\v6.14\books\stm\

---

## 双语目录对照 / Bilingual Table of Contents

### 第01章：引言和基本方程 / Chapter 01: Introduction and Basic Equations

| 章节 Chapter | 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|--------------|----------------|-----------------|-----------------|-----------------|
| 01.01.01 | | Introduction General | [chs/01s01a01-Introduction-general.md](./chs/01s01a01-Introduction-general.md) | [eng/01s01a01-Introduction-general.md](./eng/01s01a01-Introduction-general.md) |
| 01.02.02 | | Notation | [chs/01s02a02-Notation.md](./chs/01s02a02-Notation.md) | [eng/01s02a02-Notation.md](./eng/01s02a02-Notation.md) |
| 01.03.03 | | Rotation Variables | [chs/01s03a03-Rotation-variables.md](./chs/01s03a03-Rotation-variables.md) | [eng/01s03a03-Rotation-variables.md](./eng/01s03a03-Rotation-variables.md) |
| 01.04.04 | | Deformation | [chs/01s04a04-Deformation.md](./chs/01s04a04-Deformation.md) | [eng/01s04a04-Deformation.md](./eng/01s04a04-Deformation.md) |
| 01.04.05 | | Strain Measures | [chs/01s04a05-Strain-measures.md](./chs/01s04a05-Strain-measures.md) | [eng/01s04a05-Strain-measures.md](./eng/01s04a05-Strain-measures.md) |
| 01.04.06 | | Rate Of Deformation And Strain Increment | [chs/01s04a06-Rate-of-deformation-and-strain-increment.md](./chs/01s04a06-Rate-of-deformation-and-strain-increment.md) | [eng/01s04a06-Rate-of-deformation-and-strain-increment.md](./eng/01s04a06-Rate-of-deformation-and-strain-increment.md) |
| 01.04.07 | | The Additive Strain Rate Decomposition | [chs/01s04a07-The-additive-strain-rate-decomposition.md](./chs/01s04a07-The-additive-strain-rate-decomposition.md) | [eng/01s04a07-The-additive-strain-rate-decomposition.md](./eng/01s04a07-The-additive-strain-rate-decomposition.md) |
| 01.05.08 | | Equilibrium And Virtual Work | [chs/01s05a08-Equilibrium-and-virtual-work.md](./chs/01s05a08-Equilibrium-and-virtual-work.md) | [eng/01s05a08-Equilibrium-and-virtual-work.md](./eng/01s05a08-Equilibrium-and-virtual-work.md) |
| 01.05.09 | | Stress Measures | [chs/01s05a09-Stress-measures.md](./chs/01s05a09-Stress-measures.md) | [eng/01s05a09-Stress-measures.md](./eng/01s05a09-Stress-measures.md) |
| 01.05.10 | | Stress Rates | [chs/01s05a10-Stress-rates.md](./chs/01s05a10-Stress-rates.md) | [eng/01s05a10-Stress-rates.md](./eng/01s05a10-Stress-rates.md) |
| 01.05.11 | | State Storage | [chs/01s05a11-State-storage.md](./chs/01s05a11-State-storage.md) | [eng/01s05a11-State-storage.md](./eng/01s05a11-State-storage.md) |
| 01.05.12 | | Energy Balance | [chs/01s05a12-Energy-balance.md](./chs/01s05a12-Energy-balance.md) | [eng/01s05a12-Energy-balance.md](./eng/01s05a12-Energy-balance.md) |
### 第02章：分析步骤 / Chapter 02: Procedures

| 章节 Chapter | 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|--------------|----------------|-----------------|-----------------|-----------------|
| 02.01.13 | | Procedures Overview And Basic Equations | [chs/02s01a13-Procedures-overview-and-basic-equations.md](./chs/02s01a13-Procedures-overview-and-basic-equations.md) | [eng/02s01a13-Procedures-overview-and-basic-equations.md](./eng/02s01a13-Procedures-overview-and-basic-equations.md) |
| 02.02.14 | | Nonlinear Solution Methods In Abaqusstan | [chs/02s02a14-Nonlinear-solution-methods-in-AbaqusStan.md](./chs/02s02a14-Nonlinear-solution-methods-in-AbaqusStan.md) | [eng/02s02a14-Nonlinear-solution-methods-in-AbaqusStan.md](./eng/02s02a14-Nonlinear-solution-methods-in-AbaqusStan.md) |
| 02.02.15 | | Quasi Newton Solution Technique | [chs/02s02a15-Quasi-Newton-solution-technique.md](./chs/02s02a15-Quasi-Newton-solution-technique.md) | [eng/02s02a15-Quasi-Newton-solution-technique.md](./eng/02s02a15-Quasi-Newton-solution-technique.md) |
| 02.02.16 | | Direct Cyclic Algorithm | [chs/02s02a16-Direct-cyclic-algorithm.md](./chs/02s02a16-Direct-cyclic-algorithm.md) | [eng/02s02a16-Direct-cyclic-algorithm.md](./eng/02s02a16-Direct-cyclic-algorithm.md) |
| 02.03.17 | | Eigenvalue Buckling Prediction | [chs/02s03a17-Eigenvalue-buckling-prediction.md](./chs/02s03a17-Eigenvalue-buckling-prediction.md) | [eng/02s03a17-Eigenvalue-buckling-prediction.md](./eng/02s03a17-Eigenvalue-buckling-prediction.md) |
| 02.03.18 | | Modified Riks Algorithm | [chs/02s03a18-Modified-Riks-algorithm.md](./chs/02s03a18-Modified-Riks-algorithm.md) | [eng/02s03a18-Modified-Riks-algorithm.md](./eng/02s03a18-Modified-Riks-algorithm.md) |
| 02.04.19 | | Implicit Dynamic Analysis | [chs/02s04a19-Implicit-dynamic-analysis.md](./chs/02s04a19-Implicit-dynamic-analysis.md) | [eng/02s04a19-Implicit-dynamic-analysis.md](./eng/02s04a19-Implicit-dynamic-analysis.md) |
| 02.04.20 | | Intermittent Contactimpact | [chs/02s04a20-Intermittent-contactimpact.md](./chs/02s04a20-Intermittent-contactimpact.md) | [eng/02s04a20-Intermittent-contactimpact.md](./eng/02s04a20-Intermittent-contactimpact.md) |
| 02.04.21 | | Subspace Dynamics | [chs/02s04a21-Subspace-dynamics.md](./chs/02s04a21-Subspace-dynamics.md) | [eng/02s04a21-Subspace-dynamics.md](./eng/02s04a21-Subspace-dynamics.md) |
| 02.04.22 | | Equivalent Rigid Body Dynamic Motion | [chs/02s04a22-Equivalent-rigid-body-dynamic-motion.md](./chs/02s04a22-Equivalent-rigid-body-dynamic-motion.md) | [eng/02s04a22-Equivalent-rigid-body-dynamic-motion.md](./eng/02s04a22-Equivalent-rigid-body-dynamic-motion.md) |
| 02.04.23 | | Explicit Dynamic Analysis | [chs/02s04a23-Explicit-dynamic-analysis.md](./chs/02s04a23-Explicit-dynamic-analysis.md) | [eng/02s04a23-Explicit-dynamic-analysis.md](./eng/02s04a23-Explicit-dynamic-analysis.md) |
| 02.05.24 | | Eigenvalue Extraction | [chs/02s05a24-Eigenvalue-extraction.md](./chs/02s05a24-Eigenvalue-extraction.md) | [eng/02s05a24-Eigenvalue-extraction.md](./eng/02s05a24-Eigenvalue-extraction.md) |
| 02.05.25 | | Variables Associated With The Natural Mo | [chs/02s05a25-Variables-associated-with-the-natural-mo.md](./chs/02s05a25-Variables-associated-with-the-natural-mo.md) | [eng/02s05a25-Variables-associated-with-the-natural-mo.md](./eng/02s05a25-Variables-associated-with-the-natural-mo.md) |
| 02.05.26 | | Linear Dynamic Analysis Using Modal Supe | [chs/02s05a26-Linear-dynamic-analysis-using-modal-supe.md](./chs/02s05a26-Linear-dynamic-analysis-using-modal-supe.md) | [eng/02s05a26-Linear-dynamic-analysis-using-modal-supe.md](./eng/02s05a26-Linear-dynamic-analysis-using-modal-supe.md) |
| 02.05.27 | | Damping Options For Modal Dynamics | [chs/02s05a27-Damping-options-for-modal-dynamics.md](./chs/02s05a27-Damping-options-for-modal-dynamics.md) | [eng/02s05a27-Damping-options-for-modal-dynamics.md](./eng/02s05a27-Damping-options-for-modal-dynamics.md) |
| 02.05.28 | | Modal Dynamic Analysis | [chs/02s05a28-Modal-dynamic-analysis.md](./chs/02s05a28-Modal-dynamic-analysis.md) | [eng/02s05a28-Modal-dynamic-analysis.md](./eng/02s05a28-Modal-dynamic-analysis.md) |
| 02.05.29 | | Response Spectrum Analysis | [chs/02s05a29-Response-spectrum-analysis.md](./chs/02s05a29-Response-spectrum-analysis.md) | [eng/02s05a29-Response-spectrum-analysis.md](./eng/02s05a29-Response-spectrum-analysis.md) |
| 02.05.30 | | Steady State Linear Dynamic Analysis | [chs/02s05a30-Steady-state-linear-dynamic-analysis.md](./chs/02s05a30-Steady-state-linear-dynamic-analysis.md) | [eng/02s05a30-Steady-state-linear-dynamic-analysis.md](./eng/02s05a30-Steady-state-linear-dynamic-analysis.md) |
| 02.05.31 | | Random Response Analysis | [chs/02s05a31-Random-response-analysis.md](./chs/02s05a31-Random-response-analysis.md) | [eng/02s05a31-Random-response-analysis.md](./eng/02s05a31-Random-response-analysis.md) |
| 02.05.32 | | Base Motions In Modal Based Procedures | [chs/02s05a32-Base-motions-in-modal-based-procedures.md](./chs/02s05a32-Base-motions-in-modal-based-procedures.md) | [eng/02s05a32-Base-motions-in-modal-based-procedures.md](./eng/02s05a32-Base-motions-in-modal-based-procedures.md) |
| 02.06.33 | | Direct Steady State Dynamic Analysis | [chs/02s06a33-Direct-steady-state-dynamic-analysis.md](./chs/02s06a33-Direct-steady-state-dynamic-analysis.md) | [eng/02s06a33-Direct-steady-state-dynamic-analysis.md](./eng/02s06a33-Direct-steady-state-dynamic-analysis.md) |
| 02.06.34 | | Subspace Based Steady State Dynamic Anal | [chs/02s06a34-Subspace-based-steady-state-dynamic-anal.md](./chs/02s06a34-Subspace-based-steady-state-dynamic-anal.md) | [eng/02s06a34-Subspace-based-steady-state-dynamic-anal.md](./eng/02s06a34-Subspace-based-steady-state-dynamic-anal.md) |
| 02.07.35 | | Steady State Transport Analysis | [chs/02s07a35-Steady-state-transport-analysis.md](./chs/02s07a35-Steady-state-transport-analysis.md) | [eng/02s07a35-Steady-state-transport-analysis.md](./eng/02s07a35-Steady-state-transport-analysis.md) |
| 02.08.36 | | Effective Stress Principle For Porous Me | [chs/02s08a36-Effective-stress-principle-for-porous-me.md](./chs/02s08a36-Effective-stress-principle-for-porous-me.md) | [eng/02s08a36-Effective-stress-principle-for-porous-me.md](./eng/02s08a36-Effective-stress-principle-for-porous-me.md) |
| 02.08.37 | | Discretized Equilibrium Statement For A  | [chs/02s08a37-Discretized-equilibrium-statement-for-a-.md](./chs/02s08a37-Discretized-equilibrium-statement-for-a-.md) | [eng/02s08a37-Discretized-equilibrium-statement-for-a-.md](./eng/02s08a37-Discretized-equilibrium-statement-for-a-.md) |
| 02.08.38 | | Constitutive Behavior In A Porous Medium | [chs/02s08a38-Constitutive-behavior-in-a-porous-medium.md](./chs/02s08a38-Constitutive-behavior-in-a-porous-medium.md) | [eng/02s08a38-Constitutive-behavior-in-a-porous-medium.md](./eng/02s08a38-Constitutive-behavior-in-a-porous-medium.md) |
| 02.08.39 | | Continuity Statement For The Wetting Liq | [chs/02s08a39-Continuity-statement-for-the-wetting-liq.md](./chs/02s08a39-Continuity-statement-for-the-wetting-liq.md) | [eng/02s08a39-Continuity-statement-for-the-wetting-liq.md](./eng/02s08a39-Continuity-statement-for-the-wetting-liq.md) |
| 02.08.40 | | Solution Strategy For Coupled Diffusiond | [chs/02s08a40-Solution-strategy-for-coupled-diffusiond.md](./chs/02s08a40-Solution-strategy-for-coupled-diffusiond.md) | [eng/02s08a40-Solution-strategy-for-coupled-diffusiond.md](./eng/02s08a40-Solution-strategy-for-coupled-diffusiond.md) |
| 02.09.41 | | Coupled Acoustic Structural Medium Analy | [chs/02s09a41-Coupled-acoustic-structural-medium-analy.md](./chs/02s09a41-Coupled-acoustic-structural-medium-analy.md) | [eng/02s09a41-Coupled-acoustic-structural-medium-analy.md](./eng/02s09a41-Coupled-acoustic-structural-medium-analy.md) |
| 02.10.42 | | Piezoelectric Analysis | [chs/02s10a42-Piezoelectric-analysis.md](./chs/02s10a42-Piezoelectric-analysis.md) | [eng/02s10a42-Piezoelectric-analysis.md](./eng/02s10a42-Piezoelectric-analysis.md) |
| 02.11.43 | | Uncoupled Heat Transfer Analysis | [chs/02s11a43-Uncoupled-heat-transfer-analysis.md](./chs/02s11a43-Uncoupled-heat-transfer-analysis.md) | [eng/02s11a43-Uncoupled-heat-transfer-analysis.md](./eng/02s11a43-Uncoupled-heat-transfer-analysis.md) |
| 02.11.44 | | Shell Heat Conduction | [chs/02s11a44-Shell-heat-conduction.md](./chs/02s11a44-Shell-heat-conduction.md) | [eng/02s11a44-Shell-heat-conduction.md](./eng/02s11a44-Shell-heat-conduction.md) |
| 02.11.45 | | Convectiondiffusion | [chs/02s11a45-Convectiondiffusion.md](./chs/02s11a45-Convectiondiffusion.md) | [eng/02s11a45-Convectiondiffusion.md](./eng/02s11a45-Convectiondiffusion.md) |
| 02.11.46 | | Cavity Radiation | [chs/02s11a46-Cavity-radiation.md](./chs/02s11a46-Cavity-radiation.md) | [eng/02s11a46-Cavity-radiation.md](./eng/02s11a46-Cavity-radiation.md) |
| 02.11.47 | | View Factor Calculation | [chs/02s11a47-View-factor-calculation.md](./chs/02s11a47-View-factor-calculation.md) | [eng/02s11a47-View-factor-calculation.md](./eng/02s11a47-View-factor-calculation.md) |
| 02.12.48 | | Coupled Thermal Electrical Analysis | [chs/02s12a48-Coupled-thermal-electrical-analysis.md](./chs/02s12a48-Coupled-thermal-electrical-analysis.md) | [eng/02s12a48-Coupled-thermal-electrical-analysis.md](./eng/02s12a48-Coupled-thermal-electrical-analysis.md) |
| 02.13.49 | | Mass Diffusion Analysis | [chs/02s13a49-Mass-diffusion-analysis.md](./chs/02s13a49-Mass-diffusion-analysis.md) | [eng/02s13a49-Mass-diffusion-analysis.md](./eng/02s13a49-Mass-diffusion-analysis.md) |
| 02.14.50 | | Substructuring And Substructure Analysis | [chs/02s14a50-Substructuring-and-substructure-analysis.md](./chs/02s14a50-Substructuring-and-substructure-analysis.md) | [eng/02s14a50-Substructuring-and-substructure-analysis.md](./eng/02s14a50-Substructuring-and-substructure-analysis.md) |
| 02.15.51 | | Submodeling Analysis | [chs/02s15a51-Submodeling-analysis.md](./chs/02s15a51-Submodeling-analysis.md) | [eng/02s15a51-Submodeling-analysis.md](./eng/02s15a51-Submodeling-analysis.md) |
| 02.16.52 | | J Integral Evaluation | [chs/02s16a52-J-integral-evaluation.md](./chs/02s16a52-J-integral-evaluation.md) | [eng/02s16a52-J-integral-evaluation.md](./eng/02s16a52-J-integral-evaluation.md) |
| 02.16.53 | | Stress Intensity Factor Extraction | [chs/02s16a53-Stress-intensity-factor-extraction.md](./chs/02s16a53-Stress-intensity-factor-extraction.md) | [eng/02s16a53-Stress-intensity-factor-extraction.md](./eng/02s16a53-Stress-intensity-factor-extraction.md) |
| 02.16.54 | | T Stress Extraction | [chs/02s16a54-T-stress-extraction.md](./chs/02s16a54-T-stress-extraction.md) | [eng/02s16a54-T-stress-extraction.md](./eng/02s16a54-T-stress-extraction.md) |
| 02.16.55 | | Prediction Of The Direction Of Crack Pro | [chs/02s16a55-Prediction-of-the-direction-of-crack-pro.md](./chs/02s16a55-Prediction-of-the-direction-of-crack-pro.md) | [eng/02s16a55-Prediction-of-the-direction-of-crack-pro.md](./eng/02s16a55-Prediction-of-the-direction-of-crack-pro.md) |
| 02.17.56 | | Stress Linearization | [chs/02s17a56-Stress-linearization.md](./chs/02s17a56-Stress-linearization.md) | [eng/02s17a56-Stress-linearization.md](./eng/02s17a56-Stress-linearization.md) |
| 02.18.57 | | Design Sensitivity Analysis | [chs/02s18a57-Design-sensitivity-analysis.md](./chs/02s18a57-Design-sensitivity-analysis.md) | [eng/02s18a57-Design-sensitivity-analysis.md](./eng/02s18a57-Design-sensitivity-analysis.md) |
### 第03章：单元 / Chapter 03: Elements

| 章节 Chapter | 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|--------------|----------------|-----------------|-----------------|-----------------|
| 03.01.58 | | Element Library Overview | [chs/03s01a58-Element-library-overview.md](./chs/03s01a58-Element-library-overview.md) | [eng/03s01a58-Element-library-overview.md](./eng/03s01a58-Element-library-overview.md) |
| 03.02.59 | | Solid Element Overview | [chs/03s02a59-Solid-element-overview.md](./chs/03s02a59-Solid-element-overview.md) | [eng/03s02a59-Solid-element-overview.md](./eng/03s02a59-Solid-element-overview.md) |
| 03.02.60 | | Solid Element Formulation | [chs/03s02a60-Solid-element-formulation.md](./chs/03s02a60-Solid-element-formulation.md) | [eng/03s02a60-Solid-element-formulation.md](./eng/03s02a60-Solid-element-formulation.md) |
| 03.02.61 | | Hybrid Incompressible Solid Element Form | [chs/03s02a61-Hybrid-incompressible-solid-element-form.md](./chs/03s02a61-Hybrid-incompressible-solid-element-form.md) | [eng/03s02a61-Hybrid-incompressible-solid-element-form.md](./eng/03s02a61-Hybrid-incompressible-solid-element-form.md) |
| 03.02.62 | | Solid Isoparametric Quadrilaterals And H | [chs/03s02a62-Solid-isoparametric-quadrilaterals-and-h.md](./chs/03s02a62-Solid-isoparametric-quadrilaterals-and-h.md) | [eng/03s02a62-Solid-isoparametric-quadrilaterals-and-h.md](./eng/03s02a62-Solid-isoparametric-quadrilaterals-and-h.md) |
| 03.02.63 | | Continuum Elements With Incompatible Mod | [chs/03s02a63-Continuum-elements-with-incompatible-mod.md](./chs/03s02a63-Continuum-elements-with-incompatible-mod.md) | [eng/03s02a63-Continuum-elements-with-incompatible-mod.md](./eng/03s02a63-Continuum-elements-with-incompatible-mod.md) |
| 03.02.64 | | Triangular Tetrahedral And Wedge Element | [chs/03s02a64-Triangular-tetrahedral-and-wedge-element.md](./chs/03s02a64-Triangular-tetrahedral-and-wedge-element.md) | [eng/03s02a64-Triangular-tetrahedral-and-wedge-element.md](./eng/03s02a64-Triangular-tetrahedral-and-wedge-element.md) |
| 03.02.65 | | Generalized Plane Strain Elements | [chs/03s02a65-Generalized-plane-strain-elements.md](./chs/03s02a65-Generalized-plane-strain-elements.md) | [eng/03s02a65-Generalized-plane-strain-elements.md](./eng/03s02a65-Generalized-plane-strain-elements.md) |
| 03.02.66 | | Axisymmetric Elements | [chs/03s02a66-Axisymmetric-elements.md](./chs/03s02a66-Axisymmetric-elements.md) | [eng/03s02a66-Axisymmetric-elements.md](./eng/03s02a66-Axisymmetric-elements.md) |
| 03.02.67 | | Axisymmetric Elements Allowing Nonlinear | [chs/03s02a67-Axisymmetric-elements-allowing-nonlinear.md](./chs/03s02a67-Axisymmetric-elements-allowing-nonlinear.md) | [eng/03s02a67-Axisymmetric-elements-allowing-nonlinear.md](./eng/03s02a67-Axisymmetric-elements-allowing-nonlinear.md) |
| 03.03.68 | | Solid Infinite Elements | [chs/03s03a68-Solid-infinite-elements.md](./chs/03s03a68-Solid-infinite-elements.md) | [eng/03s03a68-Solid-infinite-elements.md](./eng/03s03a68-Solid-infinite-elements.md) |
| 03.03.69 | | Acoustic Infinite Elements | [chs/03s03a69-Acoustic-infinite-elements.md](./chs/03s03a69-Acoustic-infinite-elements.md) | [eng/03s03a69-Acoustic-infinite-elements.md](./eng/03s03a69-Acoustic-infinite-elements.md) |
| 03.04.70 | | Membrane Elements | [chs/03s04a70-Membrane-elements.md](./chs/03s04a70-Membrane-elements.md) | [eng/03s04a70-Membrane-elements.md](./eng/03s04a70-Membrane-elements.md) |
| 03.04.71 | | Truss Elements | [chs/03s04a71-Truss-elements.md](./chs/03s04a71-Truss-elements.md) | [eng/03s04a71-Truss-elements.md](./eng/03s04a71-Truss-elements.md) |
| 03.04.72 | | Axisymmetric Membranes | [chs/03s04a72-Axisymmetric-membranes.md](./chs/03s04a72-Axisymmetric-membranes.md) | [eng/03s04a72-Axisymmetric-membranes.md](./eng/03s04a72-Axisymmetric-membranes.md) |
| 03.05.73 | | Beam Element Overview | [chs/03s05a73-Beam-element-overview.md](./chs/03s05a73-Beam-element-overview.md) | [eng/03s05a73-Beam-element-overview.md](./eng/03s05a73-Beam-element-overview.md) |
| 03.05.74 | | Beam Element Formulation | [chs/03s05a74-Beam-element-formulation.md](./chs/03s05a74-Beam-element-formulation.md) | [eng/03s05a74-Beam-element-formulation.md](./eng/03s05a74-Beam-element-formulation.md) |
| 03.05.75 | | Euler Bernoulli Beam Elements | [chs/03s05a75-Euler-Bernoulli-beam-elements.md](./chs/03s05a75-Euler-Bernoulli-beam-elements.md) | [eng/03s05a75-Euler-Bernoulli-beam-elements.md](./eng/03s05a75-Euler-Bernoulli-beam-elements.md) |
| 03.05.76 | | Hybrid Beam Elements | [chs/03s05a76-Hybrid-beam-elements.md](./chs/03s05a76-Hybrid-beam-elements.md) | [eng/03s05a76-Hybrid-beam-elements.md](./eng/03s05a76-Hybrid-beam-elements.md) |
| 03.05.77 | | Mass And Inertia For Timoshenko Beams | [chs/03s05a77-Mass-and-inertia-for-Timoshenko-beams.md](./chs/03s05a77-Mass-and-inertia-for-Timoshenko-beams.md) | [eng/03s05a77-Mass-and-inertia-for-Timoshenko-beams.md](./eng/03s05a77-Mass-and-inertia-for-Timoshenko-beams.md) |
| 03.05.78 | | Meshed Beam Cross Sections | [chs/03s05a78-Meshed-beam-cross-sections.md](./chs/03s05a78-Meshed-beam-cross-sections.md) | [eng/03s05a78-Meshed-beam-cross-sections.md](./eng/03s05a78-Meshed-beam-cross-sections.md) |
| 03.06.79 | | Shell Element Overview | [chs/03s06a79-Shell-element-overview.md](./chs/03s06a79-Shell-element-overview.md) | [eng/03s06a79-Shell-element-overview.md](./eng/03s06a79-Shell-element-overview.md) |
| 03.06.80 | | Axisymmetric Shell Elements | [chs/03s06a80-Axisymmetric-shell-elements.md](./chs/03s06a80-Axisymmetric-shell-elements.md) | [eng/03s06a80-Axisymmetric-shell-elements.md](./eng/03s06a80-Axisymmetric-shell-elements.md) |
| 03.06.81 | | Shear Flexible Small Strain Shell Elemen | [chs/03s06a81-Shear-flexible-small-strain-shell-elemen.md](./chs/03s06a81-Shear-flexible-small-strain-shell-elemen.md) | [eng/03s06a81-Shear-flexible-small-strain-shell-elemen.md](./eng/03s06a81-Shear-flexible-small-strain-shell-elemen.md) |
| 03.06.82 | | Triangular Facet Shell Elements | [chs/03s06a82-Triangular-facet-shell-elements.md](./chs/03s06a82-Triangular-facet-shell-elements.md) | [eng/03s06a82-Triangular-facet-shell-elements.md](./eng/03s06a82-Triangular-facet-shell-elements.md) |
| 03.06.83 | | Finite Strain Shell Element Formulation | [chs/03s06a83-Finite-strain-shell-element-formulation.md](./chs/03s06a83-Finite-strain-shell-element-formulation.md) | [eng/03s06a83-Finite-strain-shell-element-formulation.md](./eng/03s06a83-Finite-strain-shell-element-formulation.md) |
| 03.06.84 | | Small Strain Shell Elements In Abaqusexp | [chs/03s06a84-Small-strain-shell-elements-in-AbaqusExp.md](./chs/03s06a84-Small-strain-shell-elements-in-AbaqusExp.md) | [eng/03s06a84-Small-strain-shell-elements-in-AbaqusExp.md](./eng/03s06a84-Small-strain-shell-elements-in-AbaqusExp.md) |
| 03.06.85 | | Axisymmetric Shell Element Allowing Asym | [chs/03s06a85-Axisymmetric-shell-element-allowing-asym.md](./chs/03s06a85-Axisymmetric-shell-element-allowing-asym.md) | [eng/03s06a85-Axisymmetric-shell-element-allowing-asym.md](./eng/03s06a85-Axisymmetric-shell-element-allowing-asym.md) |
| 03.06.86 | | Transverse Shear Stiffness In Composite  | [chs/03s06a86-Transverse-shear-stiffness-in-composite-.md](./chs/03s06a86-Transverse-shear-stiffness-in-composite-.md) | [eng/03s06a86-Transverse-shear-stiffness-in-composite-.md](./eng/03s06a86-Transverse-shear-stiffness-in-composite-.md) |
| 03.06.87 | | Rotary Inertia For 5 Degree Of Freedom S | [chs/03s06a87-Rotary-inertia-for-5-degree-of-freedom-s.md](./chs/03s06a87-Rotary-inertia-for-5-degree-of-freedom-s.md) | [eng/03s06a87-Rotary-inertia-for-5-degree-of-freedom-s.md](./eng/03s06a87-Rotary-inertia-for-5-degree-of-freedom-s.md) |
| 03.07.88 | | Rebar Modeling In Two Dimensions | [chs/03s07a88-Rebar-modeling-in-two-dimensions.md](./chs/03s07a88-Rebar-modeling-in-two-dimensions.md) | [eng/03s07a88-Rebar-modeling-in-two-dimensions.md](./eng/03s07a88-Rebar-modeling-in-two-dimensions.md) |
| 03.07.89 | | Rebar Modeling In Three Dimensions | [chs/03s07a89-Rebar-modeling-in-three-dimensions.md](./chs/03s07a89-Rebar-modeling-in-three-dimensions.md) | [eng/03s07a89-Rebar-modeling-in-three-dimensions.md](./eng/03s07a89-Rebar-modeling-in-three-dimensions.md) |
| 03.07.90 | | Rebar Modeling In Shell Membrane And Sur | [chs/03s07a90-Rebar-modeling-in-shell-membrane-and-sur.md](./chs/03s07a90-Rebar-modeling-in-shell-membrane-and-sur.md) | [eng/03s07a90-Rebar-modeling-in-shell-membrane-and-sur.md](./eng/03s07a90-Rebar-modeling-in-shell-membrane-and-sur.md) |
| 03.08.91 | | Hydrostatic Fluid Calculations | [chs/03s08a91-Hydrostatic-fluid-calculations.md](./chs/03s08a91-Hydrostatic-fluid-calculations.md) | [eng/03s08a91-Hydrostatic-fluid-calculations.md](./eng/03s08a91-Hydrostatic-fluid-calculations.md) |
| 03.09.92 | | Elbow Elements | [chs/03s09a92-Elbow-elements.md](./chs/03s09a92-Elbow-elements.md) | [eng/03s09a92-Elbow-elements.md](./eng/03s09a92-Elbow-elements.md) |
| 03.09.93 | | Frame Elements With Lumped Plasticity | [chs/03s09a93-Frame-elements-with-lumped-plasticity.md](./chs/03s09a93-Frame-elements-with-lumped-plasticity.md) | [eng/03s09a93-Frame-elements-with-lumped-plasticity.md](./eng/03s09a93-Frame-elements-with-lumped-plasticity.md) |
| 03.09.94 | | Buckling Strut Response For Frame Elemen | [chs/03s09a94-Buckling-strut-response-for-frame-elemen.md](./chs/03s09a94-Buckling-strut-response-for-frame-elemen.md) | [eng/03s09a94-Buckling-strut-response-for-frame-elemen.md](./eng/03s09a94-Buckling-strut-response-for-frame-elemen.md) |
| 03.09.95 | | Tube Support Elements | [chs/03s09a95-Tube-support-elements.md](./chs/03s09a95-Tube-support-elements.md) | [eng/03s09a95-Tube-support-elements.md](./eng/03s09a95-Tube-support-elements.md) |
| 03.09.96 | | Line Spring Elements | [chs/03s09a96-Line-spring-elements.md](./chs/03s09a96-Line-spring-elements.md) | [eng/03s09a96-Line-spring-elements.md](./eng/03s09a96-Line-spring-elements.md) |
| 03.09.97 | | Flexible Joint Element | [chs/03s09a97-Flexible-joint-element.md](./chs/03s09a97-Flexible-joint-element.md) | [eng/03s09a97-Flexible-joint-element.md](./eng/03s09a97-Flexible-joint-element.md) |
| 03.09.98 | | Rotary Inertia Element | [chs/03s09a98-Rotary-inertia-element.md](./chs/03s09a98-Rotary-inertia-element.md) | [eng/03s09a98-Rotary-inertia-element.md](./eng/03s09a98-Rotary-inertia-element.md) |
| 03.09.99 | | Distributing Coupling Elements | [chs/03s09a99-Distributing-coupling-elements.md](./chs/03s09a99-Distributing-coupling-elements.md) | [eng/03s09a99-Distributing-coupling-elements.md](./eng/03s09a99-Distributing-coupling-elements.md) |
### 第04章：机械本构理论 / Chapter 04: Mechanical Constitutive Theories

| 章节 Chapter | 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|--------------|----------------|-----------------|-----------------|-----------------|
### 第05章：界面建模 / Chapter 05: Interface Modeling

| 章节 Chapter | 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|--------------|----------------|-----------------|-----------------|-----------------|
### 第06章：载荷和约束 / Chapter 06: Loading and Constraints

| 章节 Chapter | 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|--------------|----------------|-----------------|-----------------|-----------------|
### 第07章：参考文献 / Chapter 07: References

| 章节 Chapter | 中文标题 Chinese | 英文标题 English | 中文文件 Chinese | 英文文件 English |
|--------------|----------------|-----------------|-----------------|-----------------|
| 07.01.01 | | References | [chs/07s01a01-References.md](./chs/07s01a01-References.md) | [eng/07s01a01-References.md](./eng/07s01a01-References.md) |

---

## 资源文件 / Resource Files

图片资源位于 `graphics/` 目录。
Images and formulas are located in the `graphics/` directory.

---

## 版权声明 / Copyright Notice

本翻译仅供学习研究使用，原文档版权归 Dassault Systèmes Simulia Corp. 所有。
This translation is for study and research purposes only. Original documentation copyright Dassault Systèmes Simulia Corp.