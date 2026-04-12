# 49.24 StaticRiksStep 对象

StaticRiksStep 对象用于指示该步骤应使用修正 Riks 方法作为静态载荷步骤进行分析，适用于比例加载情况。

StaticRiksStep 对象派生于 [AnalysisStep](pt01ch49pyo02.md) 对象。

**访问**

```
import step
mdb.models[*name*].steps[*name*]
```

### 49.24.1 StaticRiksStep(...)

此方法创建一个 StaticRiksStep 对象。

**路径**

```
mdb.models[*name*].StaticRiksStep
```

**必需参数**

*name*

一个字符串，指定存储库键。

*previous*

一个字符串，指定前一步的名称。新步骤将出现在分析步骤列表中该步骤之后。

**可选参数**

*description*

一个字符串，指定新步骤的描述。默认值为空字符串。

*nlgeom*

一个布尔值，指定是否允许几何非线性。默认值为 OFF。

*adiabatic*

一个布尔值，指定是否执行绝热应力分析。默认值为 OFF。

*maxLPF*

`None` 或一个 Float，指定载荷比例系数的最大值。默认值为 `None`。

*nodeOn*

一个布尔值，指定是否监测节点的最终位移值。默认值为 OFF。

*maximumDisplacement*

一个 Float，指定节点处和自由度处的总位移（或旋转）值，如果在增量期间越过该值，则在当前增量结束步骤。当 *nodeOn*=ON 时需要此参数。默认值为 0.0。

*dof*

一个 Int，指定被监测的自由度。当 *nodeOn*=ON 时需要此参数。默认值为 0。

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定正在监测最终位移值的顶点。当 *nodeOn*=ON 时需要此参数。

*timeIncrementationMethod*

一个 SymbolicConstant，指定要使用的时间增量方法。可选值为 FIXED 和 AUTOMATIC。默认值为 AUTOMATIC。

*maxNumInc*

一个 Int，指定步骤中的最大增量数。默认值为 100。

*totalArcLength*

一个 Float，指定与此步骤中的载荷相关的总载荷比例系数。默认值为 1.0。

*initialArcInc*

一个 Float，指定初始载荷比例系数。默认值为步骤的总载荷比例系数。

*minArcInc*

一个 Float，指定允许的最小弧长增量。默认值为建议的初始载荷比例系数或步骤的总载荷比例系数乘以 105 中的较小值。

*maxArcInc*

一个 Float，指定允许的最大弧长增量。默认值为步骤的总载荷比例系数。

*matrixStorage*

一个 SymbolicConstant，指定矩阵存储类型。可选值为 SYMMETRIC、UNSYMMETRIC 和 SOLVER_DEFAULT。默认值为 SOLVER_DEFAULT。

*extrapolation*

一个 SymbolicConstant，指定用于确定非线性分析的增量解的外推类型。可选值为 NONE、LINEAR 和 PARABOLIC。默认值为 LINEAR。

*fullyPlastic*

一个字符串，指定被监测完全塑性行为的区域名称。默认值为空字符串。

*noStop*

一个布尔值，指定在完成允许的最大迭代次数后，即使未满足平衡容差，是否接受增量的解。默认值为 OFF。

**警告：**仅在您对如何解释结果有充分理解的特殊情况下，才应将 *noStop* 设置为 ON。

*maintainAttributes*

一个布尔值，指定是否保留具有相同名称的现有步骤的属性。默认值为 False。

*useLongTermSolution*

一个布尔值，指定是否获取时域粘弹性或双层粘塑性的完全松弛长期弹性解或长期弹塑性解。默认值为 OFF。

*convertSDI*

一个 SymbolicConstant，指定在迭代期间发生严重不连续时是否强制进行新迭代。可选值为 PROPAGATED、CONVERT_SDI_OFF 和 CONVERT_SDI_ON。默认值为 PROPAGATED。

**返回值**

一个 StaticRiksStep 对象。

**异常**

RangeError。

### 49.24.2 setValues(...)

此方法修改 StaticRiksStep 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [StaticRiksStep](pt01ch49pyo24.md#ker-staticriksstep-staticriksstep-pyc) 方法的参数相同，但 *name*、*previous* 和 *maintainAttributes* 参数除外。

**返回值**

无

**异常**

RangeError。

### 49.24.3 成员

StaticRiksStep 对象可以具有以下成员：

*name*

一个字符串，指定存储库键。

*nlgeom*

一个布尔值，指定是否允许几何非线性。默认值为 OFF。

*adiabatic*

一个布尔值，指定是否执行绝热应力分析。默认值为 OFF。

*maxLPF*

`None` 或一个 Float，指定载荷比例系数的最大值。默认值为 `None`。

*nodeOn*

一个布尔值，指定是否监测节点的最终位移值。默认值为 OFF。

*maximumDisplacement*

一个 Float，指定节点处和自由度处的总位移（或旋转）值，如果在增量期间越过该值，则在当前增量结束步骤。当 *nodeOn*=ON 时需要此参数。默认值为 0.0。

*dof*

一个 Int，指定被监测的自由度。当 *nodeOn*=ON 时需要此参数。默认值为 0。

*timeIncrementationMethod*

一个 SymbolicConstant，指定要使用的时间增量方法。可选值为 FIXED 和 AUTOMATIC。默认值为 AUTOMATIC。

*maxNumInc*

一个 Int，指定步骤中的最大增量数。默认值为 100。

*totalArcLength*

一个 Float，指定与此步骤中的载荷相关的总载荷比例系数。默认值为 1.0。

*initialArcInc*

一个 Float，指定初始载荷比例系数。默认值为步骤的总载荷比例系数。

*minArcInc*

一个 Float，指定允许的最小弧长增量。默认值为建议的初始载荷比例系数或步骤的总载荷比例系数乘以 105 中的较小值。

*maxArcInc*

一个 Float，指定允许的最大弧长增量。默认值为步骤的总载荷比例系数。

*matrixStorage*

一个 SymbolicConstant，指定矩阵存储类型。可选值为 SYMMETRIC、UNSYMMETRIC 和 SOLVER_DEFAULT。默认值为 SOLVER_DEFAULT。

*extrapolation*

一个 SymbolicConstant，指定用于确定非线性分析的增量解的外推类型。可选值为 NONE、LINEAR 和 PARABOLIC。默认值为 LINEAR。

*noStop*

一个布尔值，指定在完成允许的最大迭代次数后，即使未满足平衡容差，是否接受增量的解。默认值为 OFF。

**警告：**仅在您对如何解释结果有充分理解的特殊情况下，才应将 *noStop* 设置为 ON。

*useLongTermSolution*

一个布尔值，指定是否获取时域粘弹性或双层粘塑性的完全松弛长期弹性解或长期弹塑性解。默认值为 OFF。

*convertSDI*

一个 SymbolicConstant，指定在迭代期间发生严重不连续时是否强制进行新迭代。可选值为 PROPAGATED、CONVERT_SDI_OFF 和 CONVERT_SDI_ON。默认值为 PROPAGATED。

*previous*

一个字符串，指定前一步的名称。新步骤将出现在分析步骤列表中该步骤之后。

*description*

一个字符串，指定新步骤的描述。默认值为空字符串。

*fullyPlastic*

一个字符串，指定被监测完全塑性行为的区域名称。默认值为空字符串。

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定正在监测最终位移值的顶点。当 *nodeOn*=ON 时需要此参数。

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

### 49.24.4 对应的分析关键字

| [*STATIC](../key/key-link.md#usb-kws-hstatic) |
| --- |
| [*STEP](../key/key-link.md#usb-kws-hstep) |
