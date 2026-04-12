# 49.8 CoupledThermalElectricStep 对象

CoupledThermalElectricStep 对象用于分析必须同时求解电势和温度场的问题。

CoupledThermalElectricStep 对象派生于 [AnalysisStep](pt01ch49pyo02.md) 对象。

**访问**

```
import step
mdb.models[*name*].steps[*name*]
```

### 49.8.1 CoupledThermalElectricStep(...)

此方法创建一个 CoupledThermalElectricStep 对象。

**路径**

```
mdb.models[*name*].CoupledThermalElectricStep
```

**必需参数**

*name*

一个字符串，指定存储库键。

*previous*

一个字符串，指定前一步的名称。新步骤将出现在分析步骤列表中该步骤之后。

**可选参数**

*description*

一个字符串，指定新步骤的描述。默认值为空字符串。

*response*

一个 SymbolicConstant，指定分析类型。可选值为 STEADY_STATE 和 TRANSIENT。默认值为 TRANSIENT。

*timePeriod*

一个 Float，指定步骤的总时间周期。默认值为 1.0。

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

*end*

一个 SymbolicConstant，指定瞬态分析中要分析的时间周期。可选值为 PERIOD 和 SS。默认值为 PERIOD。

*deltmx*

一个 Float，指定瞬态分析中允许的增量中的最大温度变化。默认值为 0.0。

*mxdem*

一个 Float，指定增量过程中允许的发射率随温度和场变量的最大变化。默认值为 0.1。

*solutionTechnique*

一个 SymbolicConstant，指定解技术类型。可选值为 FULL_NEWTON 和 SEPARATED。默认值为 FULL_NEWTON。

*matrixStorage*

一个 SymbolicConstant，指定矩阵存储类型。可选值为 SYMMETRIC、UNSYMMETRIC 和 SOLVER_DEFAULT。默认值为 SOLVER_DEFAULT。

*amplitude*

一个 SymbolicConstant，指定步骤中载荷幅值的变化。默认值为 STEP。可选值为 STEP 和 RAMP。

*extrapolation*

一个 SymbolicConstant，指定用于确定非线性分析的增量解的外推类型。可选值为 NONE、LINEAR 和 PARABOLIC。默认值为 LINEAR。

*maintainAttributes*

一个布尔值，指定是否保留具有相同名称的现有步骤的属性。默认值为 False。

*convertSDI*

一个 SymbolicConstant，指定在迭代期间发生严重不连续时是否强制进行新迭代。可选值为 PROPAGATED、CONVERT_SDI_OFF 和 CONVERT_SDI_ON。默认值为 PROPAGATED。

**返回值**

一个 CoupledThermalElectricStep 对象。

**异常**

RangeError。

### 49.8.2 setValues(...)

此方法修改 CoupledThermalElectricStep 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [CoupledThermalElectricStep](pt01ch49pyo08.md#ker-coupledthermalelectricstep-coupledthermalelectricste-pyc) 方法的参数相同，但 *name*、*previous* 和 *maintainAttributes* 参数除外。

**返回值**

无

**异常**

RangeError。

### 49.8.3 成员

CoupledThermalElectricStep 对象可以具有以下成员：

*name*

一个字符串，指定存储库键。

*response*

一个 SymbolicConstant，指定分析类型。可选值为 STEADY_STATE 和 TRANSIENT。默认值为 TRANSIENT。

*timePeriod*

一个 Float，指定步骤的总时间周期。默认值为 1.0。

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

*end*

一个 SymbolicConstant，指定瞬态分析中要分析的时间周期。可选值为 PERIOD 和 SS。默认值为 PERIOD。

*deltmx*

一个 Float，指定瞬态分析中允许的增量中的最大温度变化。默认值为 0.0。

*mxdem*

一个 Float，指定增量过程中允许的发射率随温度和场变量的最大变化。默认值为 0.1。

*solutionTechnique*

一个 SymbolicConstant，指定解技术类型。可选值为 FULL_NEWTON 和 SEPARATED。默认值为 FULL_NEWTON。

*matrixStorage*

一个 SymbolicConstant，指定矩阵存储类型。可选值为 SYMMETRIC、UNSYMMETRIC 和 SOLVER_DEFAULT。默认值为 SOLVER_DEFAULT。

*amplitude*

一个 SymbolicConstant，指定步骤中载荷幅值的变化。默认值为 STEP。可选值为 STEP 和 RAMP。

*extrapolation*

一个 SymbolicConstant，指定用于确定非线性分析的增量解的外推类型。可选值为 NONE、LINEAR 和 PARABOLIC。默认值为 LINEAR。

*convertSDI*

一个 SymbolicConstant，指定在迭代期间发生严重不连续时是否强制进行新迭代。可选值为 PROPAGATED、CONVERT_SDI_OFF 和 CONVERT_SDI_ON。默认值为 PROPAGATED。

*previous*

一个字符串，指定前一步的名称。新步骤将出现在分析步骤列表中该步骤之后。

*description*

一个字符串，指定新步骤的描述。默认值为空字符串。

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

### 49.8.4 对应的分析关键字

| [*COUPLED THERMAL-ELECTRICAL](../key/key-link.md#usb-kws-hthermalelectric) |
| --- |
| [*SOLUTION TECHNIQUE](../key/key-link.md#usb-kws-hsolutiontech) |
| [*STEP](../key/key-link.md#usb-kws-hstep) |
