# 49.19 ModalDynamicsStep 对象

ModalDynamicsStep 对象用于使用模态叠加作为线性扰动过程提供动态时程响应。

ModalDynamicsStep 对象派生于 [AnalysisStep](pt01ch49pyo02.md) 对象。

**访问**

```
import step
mdb.models[*name*].steps[*name*]
```

### 49.19.1 ModalDynamicsStep(...)

此方法创建一个 ModalDynamicsStep 对象。

**路径**

```
mdb.models[*name*].ModalDynamicsStep
```

**必需参数**

*name*

一个字符串，指定存储库键。

*previous*

一个字符串，指定前一步的名称。新步骤将出现在分析步骤列表中该步骤之后。

**可选参数**

*description*

一个字符串，指定新步骤的描述。默认值为空字符串。

*continueAnalysis*

一个布尔值，指定该步骤从零初始条件开始。默认值为 OFF。

*timePeriod*

一个 Float，指定总时间周期。默认值为 1.0。

*incSize*

一个 Float，指定要使用的时间增量。默认值为 1.0。

*directDamping*

一个 [DirectDamping](pt01ch50pyo04.md) 对象。

*compositeDamping*

一个 [CompositeDamping](pt01ch50pyo01.md) 对象。

*rayleighDamping*

一个 [RayleighDamping](pt01ch50pyo11.md) 对象。

*amplitude*

一个 SymbolicConstant，指定步骤中载荷幅值的变化。可选值为 STEP 和 RAMP。默认值为 STEP。

*maintainAttributes*

一个布尔值，指定是否保留具有相同名称的现有步骤的属性。默认值为 False。

*directDampingByFrequency*

一个 [DirectDampingByFrequency](pt01ch50pyo05.md) 对象。

*rayleighDampingByFrequency*

一个 [RayleighDampingByFrequency](pt01ch50pyo12.md) 对象。

**返回值**

一个 ModalDynamicsStep 对象。

**异常**

RangeError。

### 49.19.2 setValues(...)

此方法修改 ModalDynamicsStep 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ModalDynamicsStep](pt01ch49pyo19.md#ker-modaldynamicsstep-modaldynamicsstep-pyc) 方法的参数相同，但 *name*、*previous* 和 *maintainAttributes* 参数除外。

**返回值**

无

**异常**

RangeError。

### 49.19.3 成员

ModalDynamicsStep 对象可以具有以下成员：

*name*

一个字符串，指定存储库键。

*continueAnalysis*

一个布尔值，指定该步骤从零初始条件开始。默认值为 OFF。

*timePeriod*

一个 Float，指定总时间周期。默认值为 1.0。

*incSize*

一个 Float，指定要使用的时间增量。默认值为 1.0。

*amplitude*

一个 SymbolicConstant，指定步骤中载荷幅值的变化。可选值为 STEP 和 RAMP。默认值为 STEP。

*previous*

一个字符串，指定前一步的名称。新步骤将出现在分析步骤列表中该步骤之后。

*description*

一个字符串，指定新步骤的描述。默认值为空字符串。

*directDamping*

一个 [DirectDamping](pt01ch50pyo04.md) 对象。

*compositeDamping*

一个 [CompositeDamping](pt01ch50pyo01.md) 对象。

*rayleighDamping*

一个 [RayleighDamping](pt01ch50pyo11.md) 对象。

*directDampingByFrequency*

一个 [DirectDampingByFrequency](pt01ch50pyo05.md) 对象。

*rayleighDampingByFrequency*

一个 [RayleighDampingByFrequency](pt01ch50pyo12.md) 对象。

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

### 49.19.4 对应的分析关键字

| [*DAMPING](../key/key-link.md#usb-kws-mdamping) |
| --- |
| [*MODAL DAMPING](../key/key-link.md#usb-kws-hmodaldamp) |
| [*MODAL DYNAMIC](../key/key-link.md#usb-kws-hmodaldyn) |
| [*STEP](../key/key-link.md#usb-kws-hstep) |
