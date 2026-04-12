# 49.9 DirectCyclicStep 对象

DirectCyclicStep 对象用于提供非线性、非等温准静态分析的直接循环过程。它也可用于预测延性体材料的渐进损伤和失效，和/或预测层合复合材料中界面处的分层/脱粘在低循环疲劳分析中的扩展。

DirectCyclicStep 对象派生于 [AnalysisStep](pt01ch49pyo02.md) 对象。

**访问**

```
import step
mdb.models[*name*].steps[*name*]
```

### 49.9.1 DirectCyclicStep(...)

此方法创建一个 DirectCyclicStep 对象。

**路径**

```
mdb.models[*name*].DirectCyclicStep
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

一个 Float，指定单个加载循环的时间。默认值为 1.0。

*timeIncrementationMethod*

一个 SymbolicConstant，指定要使用的时间增量方法。可选值为 FIXED 和 AUTOMATIC。默认值为 AUTOMATIC。

*maxNumInc*

一个 Int，指定步骤中的最大增量数。默认值为 100。

*initialInc*

一个 Float，指定初始时间增量。默认值为步骤的总时间周期。

*minInc*

一个 Float，指定允许的最小时间增量。默认值为建议的初始时间增量或总时间周期的 105 倍中的较小值。

*maxInc*

一个 Float，指定允许的最大时间增量。默认值为步骤的总时间周期。

*maxNumIterations*

一个 Int，指定步骤中的最大迭代次数。默认值为 200。

*initialTerms*

一个 Int，指定傅里叶级数中的初始项数。默认值为 11。

*maxTerms*

一个 Int，指定傅里叶级数中的最大项数。默认值为 25。

*termsIncrement*

一个 Int，指定傅里叶级数项数的增量。默认值为 5。

*deltmx*

一个 Float，指定允许的增量中的最大温度变化。默认值为 0.0。

*cetol*

一个 Float，指定从增量的开始和结束时的蠕变应变率计算的蠕变应变增量之间的最大差异。默认值为 0.0。

*timePoints*

`None` 或一个字符串，指定一个字符串，指定用于确定结构响应将在哪些时间进行评估的时间点对象名称。默认值为 NONE。

*fatigue*

一个布尔值，指定是否包含低循环疲劳分析。默认值为 OFF。

*continueAnalysis*

一个布尔值，指定是否使用在前一个直接循环步骤中获得的傅里叶级数中的位移解作为当前步骤的起始值。默认值为 OFF。

*minCycleInc*

一个 Int，指定向前外推损伤的最小循环数。默认值为 100。

*maxCycleInc*

一个 Int，指定向前外推损伤的最大循环数。默认值为 1000。

*maxNumCycles*

SymbolicConstant DEFAULT 或一个 Int，指定步骤中允许的最大循环数或 DEFAULT。如果指定 DEFAULT，则将使用 1 加上最大循环数一半的值。默认值为 DEFAULT。

*damageExtrapolationTolerance*

一个 Float，指定最大外推损伤增量。默认值为 1.0。

*matrixStorage*

一个 SymbolicConstant，指定矩阵存储类型。可选值为 SYMMETRIC、UNSYMMETRIC 和 SOLVER_DEFAULT。默认值为 SOLVER_DEFAULT。

*extrapolation*

一个 SymbolicConstant，指定用于确定非线性分析的增量解的外推类型。可选值为 NONE、LINEAR 和 PARABOLIC。默认值为 LINEAR。

*maintainAttributes*

一个布尔值，指定是否保留具有相同名称的现有步骤的属性。默认值为 False。

*convertSDI*

一个 SymbolicConstant，指定在迭代期间发生严重不连续时是否强制进行新迭代。可选值为 PROPAGATED、CONVERT_SDI_OFF 和 CONVERT_SDI_ON。默认值为 PROPAGATED。

**返回值**

一个 DirectCyclicStep 对象。

**异常**

RangeError。

### 49.9.2 setValues(...)

此方法修改 DirectCyclicStep 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [DirectCyclicStep](pt01ch49pyo09.md#ker-directcyclicstep-directcyclicstep-pyc) 方法的参数相同，但 *name*、*previous* 和 *maintainAttributes* 参数除外。

**返回值**

无

**异常**

RangeError。

### 49.9.3 成员

DirectCyclicStep 对象可以具有以下成员：

*name*

一个字符串，指定存储库键。

*timePeriod*

一个 Float，指定单个加载循环的时间。默认值为 1.0。

*timeIncrementationMethod*

一个 SymbolicConstant，指定要使用的时间增量方法。可选值为 FIXED 和 AUTOMATIC。默认值为 AUTOMATIC。

*maxNumInc*

一个 Int，指定步骤中的最大增量数。默认值为 100。

*initialInc*

一个 Float，指定初始时间增量。默认值为步骤的总时间周期。

*minInc*

一个 Float，指定允许的最小时间增量。默认值为建议的初始时间增量或总时间周期的 105 倍中的较小值。

*maxInc*

一个 Float，指定允许的最大时间增量。默认值为步骤的总时间周期。

*maxNumIterations*

一个 Int，指定步骤中的最大迭代次数。默认值为 200。

*initialTerms*

一个 Int，指定傅里叶级数中的初始项数。默认值为 11。

*maxTerms*

一个 Int，指定傅里叶级数中的最大项数。默认值为 25。

*termsIncrement*

一个 Int，指定傅里叶级数项数的增量。默认值为 5。

*deltmx*

一个 Float，指定允许的增量中的最大温度变化。默认值为 0.0。

*cetol*

一个 Float，指定从增量的开始和结束时的蠕变应变率计算的蠕变应变增量之间的最大差异。默认值为 0.0。

*fatigue*

一个布尔值，指定是否包含低循环疲劳分析。默认值为 OFF。

*continueAnalysis*

一个布尔值，指定是否使用在前一个直接循环步骤中获得的傅里叶级数中的位移解作为当前步骤的起始值。默认值为 OFF。

*minCycleInc*

一个 Int，指定向前外推损伤的最小循环数。默认值为 100。

*maxCycleInc*

一个 Int，指定向前外推损伤的最大循环数。默认值为 1000。

*maxNumCycles*

SymbolicConstant DEFAULT 或一个 Int，指定步骤中允许的最大循环数或 DEFAULT。如果指定 DEFAULT，则将使用 1 加上最大循环数一半的值。默认值为 DEFAULT。

*damageExtrapolationTolerance*

一个 Float，指定最大外推损伤增量。默认值为 1.0。

*matrixStorage*

一个 SymbolicConstant，指定矩阵存储类型。可选值为 SYMMETRIC、UNSYMMETRIC 和 SOLVER_DEFAULT。默认值为 SOLVER_DEFAULT。

*extrapolation*

一个 SymbolicConstant，指定用于确定非线性分析的增量解的外推类型。可选值为 NONE、LINEAR 和 PARABOLIC。默认值为 LINEAR。

*convertSDI*

一个 SymbolicConstant，指定在迭代期间发生严重不连续时是否强制进行新迭代。可选值为 PROPAGATED、CONVERT_SDI_OFF 和 CONVERT_SDI_ON。默认值为 PROPAGATED。

*previous*

一个字符串，指定前一步的名称。新步骤将出现在分析步骤列表中该步骤之后。

*description*

一个字符串，指定新步骤的描述。默认值为空字符串。

*timePoints*

`None` 或一个字符串，指定一个字符串，指定用于确定结构响应将在哪些时间进行评估的时间点对象名称。默认值为 NONE。

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

### 49.9.4 对应的分析关键字

| [*DIRECT CYCLIC](../key/key-link.md#usb-kws-hdirectcyclic) |
| --- |
| [*STEP](../key/key-link.md#usb-kws-hstep) |
