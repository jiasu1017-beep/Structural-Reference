# 49.12 FlowStep 对象

FlowStep 对象用于创建用于 CFD 分析的分析步骤。

FlowStep 对象派生于 [AnalysisStep](pt01ch49pyo02.md) 对象。

**访问**

```
import step
mdb.models[*name*].steps[*name*]
```

### 49.12.1 FlowStep(...)

此方法创建一个 FlowStep 对象。

**路径**

```
mdb.models[*name*].FlowStep
```

**必需参数**

*name*

一个字符串，指定存储库键。

*previous*

一个字符串，指定前一步的名称。新步骤将出现在分析步骤列表中该步骤之后。

**可选参数**

*description*

一个字符串，指定新步骤的描述。默认值为空字符串。

*timePeriod*

一个 Float，指定步骤的总时间周期。默认值为 1.0。

*energyEquation*

一个 SymbolicConstant，指定要使用的能量方程方法。可选值为 ENERGY_NONE 和 TEMPERATURE。默认值为 ENERGY_NONE。

*incrementation*

一个 SymbolicConstant，指定要使用的时间增量方法。可选值为 FIXED_TIME 和 FIXED_CFL。默认值为 FIXED_TIME。

*initialInc*

一个 Float，指定步骤的时间增量，或当 *incrementation*=FIXED_CFL 时的初始时间增量。默认值为 0.01。

*divergenceTol*

一个 Float，指定发散容差。默认值为 10-10。

*maximumCFL*

一个 Float，指定最大 Courant-Friedrichs-Levy 增量。此成员仅在 *incrementation*=FIXED_CFL 时适用。默认值为 0.45。

*incAdjustmentFreq*

一个 Int，指定增量调整频率。此成员仅在 *incrementation*=FIXED_CFL 时适用。默认值为 1。

*stepGrowthFactor*

一个 Float，指定时间步长增长比例因子。此成员仅在 *incrementation*=FIXED_CFL 时适用。默认值为 0.025。

*viscousFactor*

一个 SymbolicConstant，指定粘性时间积分参数。可选值为 TRAPEZOID、GALERKIN 和 BACKWARD_EULER。默认值为 TRAPEZOID。

*boundaryFactor*

一个 SymbolicConstant，指定载荷和边界条件时间积分参数。可选值为 TRAPEZOID、GALERKIN 和 BACKWARD_EULER。默认值为 TRAPEZOID。

*advectionFactor*

一个 SymbolicConstant，指定平流参数。可选值为 TRAPEZOID、GALERKIN 和 BACKWARD_EULER。默认值为 TRAPEZOID。

*momOutputDiagnostics*

一个布尔值，指定是否输出动量方程求解器的诊断信息。默认值为 OFF。

*momOutputConvergence*

一个布尔值，指定是否输出动量方程求解器的收敛数据。默认值为 OFF。

*momIterationLimit*

一个 Int，指定动量方程求解器的迭代限制。默认值为 50。

*momCheckingFreq*

一个 Int，指定动量方程求解器的检查频率。默认值为 2。

*momConvergenceLimit*

一个 Float，指定动量方程求解器的线性收敛极限。默认值为 10-5。

*pressureType*

一个 SymbolicConstant，指定压力方程预处理程序类型。可选值为 AMG 和 SSOR。默认值为 AMG。

*pressSolverType*

一个 SymbolicConstant，指定压力方程求解器类型。当 *pressureType*=SSOR 时，此成员不能从默认值更改。可选值为 CG、BCGS 和 FGMRES。默认值为 CG。

*pressSmootherType*

一个 SymbolicConstant，指定压力方程残差平滑器类型。此成员仅在 *pressureType*=AMG 时适用。可选值为 ICC 和 CHEBYCHEV。默认值为 ICC。

*pressPreSweeps*

一个 Int，指定残差平滑器使用的预扫描次数。此成员仅在 *pressureType*=AMG 时适用。默认值为 1。

*pressPostSweeps*

一个 Int，指定残差平滑器使用的后扫描次数。此成员仅在 *pressureType*=AMG 时适用。默认值为 1。

*pressOutputDiagnostics*

一个布尔值，指定是否输出压力方程求解器的诊断信息。默认值为 OFF。

*pressOutputConvergence*

一个布尔值，指定是否输出压力方程求解器的收敛数据。默认值为 OFF。

*pressIterationLimit*

一个 Int，指定压力方程求解器的迭代限制。当 *pressureType*=AMG 时默认值为 250，当 *pressureType*=SSOR 时默认值为 1000。

*pressCheckingFreq*

一个 Int，指定压力方程求解器的检查频率。默认值为 2。

*pressConvergenceLimit*

一个 Float，指定压力方程求解器的线性收敛极限。默认值为 10-5。

*transOutputDiagnostics*

一个布尔值，指定是否输出输运方程求解器的诊断信息。默认值为 OFF。

*transOutputConvergence*

一个布尔值，指定是否输出输运方程求解器的收敛数据。默认值为 OFF。

*transIterationLimit*

一个 Int，指定输运方程求解器的迭代限制。默认值为 50。

*transCheckingFreq*

一个 Int，指定输运方程求解器的检查频率。默认值为 2。

*transConvergenceLimit*

一个 Float，指定输运方程求解器的线性收敛极限。默认值为 10-5。

*turbulenceModel*

一个 SymbolicConstant，指定湍流模型。可选值为 TURB_NONE、SPALART 和 KEPS_RNG。默认值为 TURB_NONE。

*turbPrandtlNumber*

一个 Float，指定湍流 Prandtl 数。此成员仅在 *energyEquation*=TEMPERATURE 且 *turbulenceModel*!=TURB_NONE 时适用。默认值为 0.8889。

*turbCb1*

一个 Float，指定湍流常数 Cb1。此成员仅在 *turbulenceModel*=SPALART 时适用。默认值为 0.1355。

*turbCb2*

一个 Float，指定湍流常数 Cb2。此成员仅在 *turbulenceModel*=SPALART 时适用。默认值为 0.622。

*turbCv1*

一个 Float，指定湍流常数 Cv1。此成员仅在 *turbulenceModel*=SPALART 时适用。默认值为 7.1。

*turbCv2*

一个 Float，指定湍流常数 Cv2。此成员仅在 *turbulenceModel*=SPALART 时适用。默认值为 5.0。

*turbCw1*

一个 Float，指定湍流常数 Cw1。此成员仅在 *turbulenceModel*=SPALART 时适用。默认值为 3.2391。

*turbCw2*

一个 Float，指定湍流常数 Cw2。此成员仅在 *turbulenceModel*=SPALART 时适用。默认值为 0.3。

*turbCw3*

一个 Float，指定湍流常数 Cw3。此成员仅在 *turbulenceModel*=SPALART 时适用。默认值为 2.0。

*turbSigma*

一个 Float，指定湍流常数 Sigma。此成员仅在 *turbulenceModel*=SPALART 时适用。默认值为 0.6667。

*turbKappa*

一个 Float，指定湍流常数 Kappa。此成员仅在 *turbulenceModel*=SPALART 时适用。默认值为 0.41。

*turbCmu*

一个 Float，指定湍流常数 Cmu。此成员仅在 *turbulenceModel*=KEPS_RNG 时适用。默认值为 0.085。

*turbCeps1*

一个 Float，指定湍流常数 cps1。此成员仅在 *turbulenceModel*=KEPS_RNG 时适用。默认值为 1.42。

*turbCeps2t*

一个 Float，指定湍流常数 cps2t。此成员仅在 *turbulenceModel*=KEPS_RNG 时适用。默认值为 1.68。

*turbSigma_k*

一个 Float，指定湍流常数 sigma_k。此成员仅在 *turbulenceModel*=KEPS_RNG 时适用。默认值为 0.72。

*turbSigma_eps*

一个 Float，指定湍流常数 sigma_eps。此成员仅在 *turbulenceModel*=KEPS_RNG 时适用。默认值为 0.72。

*turbBeta*

一个 Float，指定湍流常数 beta。此成员仅在 *turbulenceModel*=KEPS_RNG 时适用。默认值为 0.012。

*turbLambda0*

一个 Float，指定湍流常数 lambda0。此成员仅在 *turbulenceModel*=KEPS_RNG 时适用。默认值为 4.38。

**返回值**

一个 FlowStep 对象。

**异常**

RangeError。

### 49.12.2 setValues(...)

此方法修改 FlowStep 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [FlowStep](pt01ch49pyo12.md#ker-flowstep-flowstep-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

RangeError。

### 49.12.3 成员

FlowStep 对象具有与 [FlowStep](pt01ch49pyo12.md#ker-flowstep-flowstep-pyc) 方法参数相同名称和描述的成员。

此外，FlowStep 对象可以具有以下成员：

*explicit*

一个 SymbolicConstant，指定该步骤是否具有显式过程类型（*procedureType*=ANNEAL、DYNAMIC_EXPLICIT 或 DYNAMIC_TEMP_DISPLACEMENT）。

*perturbation*

一个布尔值，指定该步骤是否具有扰动过程类型。

*nonmechanical*

一个布尔值，指定该步骤是否具有力学过程类型。

*procedureType*

一个 SymbolicConstant，指定 Abaqus 过程。可选值包括：
- ANNEAL
- BUCKLE
- COMPLEX_FREQUENCY
- COUPLED_TEMP_DISPLACEMENT
- COUPLED_THERMAL_ELECTRIC
- DIRECT_CYCLIC
- DYNAMIC_IMPLICIT
- DYNAMIC_EXPLICIT
- DYNAMIC_SUBSPACE
- DYNAMIC_TEMP_DISPLACEMENT
- COUPLED_THERMAL_ELECTRICAL_STRUCTURAL
- FLOW
- FREQUENCY
- GEOSTATIC
- HEAT_TRANSFER
- MASS_DIFFUSION
- MODAL_DYNAMICS
- RANDOM_RESPONSE
- RESPONSE_SPECTRUM
- SOILS
- STATIC_GENERAL
- STATIC_LINEAR_PERTURBATION
- STATIC_RIKS
- STEADY_STATE_DIRECT
- STEADY_STATE_MODAL
- STEADY_STATE_SUBSPACE
- VISCO

*suppressed*

一个布尔值，指定该步骤是否被抑制。默认值为 OFF。

*fieldOutputRequestState*

[FieldOutputRequestState](pt01ch51pyo03.md) 对象的存储库。

*historyOutputRequestState*

[HistoryOutputRequestState](pt01ch51pyo05.md) 对象的存储库。

*diagnosticPrint*

[DiagnosticPrint](pt01ch51pyo01.md) 对象。

*monitor*

[Monitor](pt01ch51pyo07.md) 对象。

*restart*

[Restart](pt01ch51pyo08.md) 对象。

*adaptiveMeshConstraintStates*

[AdaptiveMeshConstraintState](pt01ch02pyo02.md) 对象的存储库。

*adaptiveMeshDomains*

[AdaptiveMeshDomain](pt01ch02pyo04.md) 对象的存储库。

*control*

[Control](pt01ch50pyo03.md) 对象。

*solverControl*

[SolverControl](pt01ch50pyo16.md) 对象。

*boundaryConditionStates*

[BoundaryConditionState](pt01ch09pyo08.md) 对象的存储库。

*interactionStates*

[InteractionState](pt01ch25pyo49.md) 对象的存储库。

*loadStates*

[LoadState](pt01ch27pyo42.md) 对象的存储库。

*loadCases*

[LoadCase](pt01ch28pyo01.md) 对象的存储库。

*predefinedFieldStates*

[PredefinedFieldState](pt01ch42pyo12.md) 对象的存储库。

### 49.12.4 对应的分析关键字

| [*CFD](../key/key-link.md#usb-kws-hcfd) |
| --- |
| [*STEP](../key/key-link.md#usb-kws-hstep) |
