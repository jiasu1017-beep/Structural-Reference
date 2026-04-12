# 49.31 TempDisplacementDynamicsStep 对象

TempDisplacementDynamicsStep 对象用于使用显式积分执行动态耦合热应力分析。

TempDisplacementDynamicsStep 对象派生于 [AnalysisStep](pt01ch49pyo02.md) 对象。

**访问**

```
import step
mdb.models[*name*].steps[*name*]
```

### 49.31.1 TempDisplacementDynamicsStep(...)

此方法创建一个 TempDisplacementDynamicsStep 对象。

**路径**

```
mdb.models[*name*].TempDisplacementDynamicsStep
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

一个 Float，指定步骤的时间周期。默认值为 1.0。

*nlgeom*

一个布尔值，指定是否在步骤期间考虑几何非线性。默认值为 OFF。

*timeIncrementationMethod*

一个 SymbolicConstant，指定要使用的时间增量方法。可选值为 AUTOMATIC_GLOBAL、AUTOMATIC_EBE、FIXED_USER_DEFINED_INC 和 FIXED_EBE。默认值为 AUTOMATIC_GLOBAL。

*maxIncrement*

`None` 或一个 Float，指定允许的最大时间增量。如果没有上限，则 *maxIncrement*=`None`。默认值为 `None`。

*scaleFactor*

一个 Float，指定用于缩放时间增量的因子。此参数仅在 *timeIncrementationMethod*=AUTOMATIC_GLOBAL、AUTOMATIC_EBE 或 FIXED_EBE 时需要。默认值为 1.0。

*userDefinedInc*

`None` 或一个 Float，指定用户定义的时间增量。默认值为 `None`。

*massScaling*

一个 [MassScalingArray](pt01ch50pyo09.md) 对象，指定质量缩放控制。默认值为 PREVIOUS_STEP。

*linearBulkViscosity*

一个 Float，指定线性体积粘度参数 ![](../graphics/ker_eqn00420.gif)。默认值为 0.06。

*quadBulkViscosity*

一个 Float，指定二次体积粘度参数 ![](../graphics/ker_eqn00421.gif)。默认值为 1.2。

*maintainAttributes*

一个布尔值，指定是否保留具有相同名称的现有步骤的属性。默认值为 False。

**返回值**

一个 TempDisplacementDynamicsStep 对象。

**异常**

RangeError。

### 49.31.2 setValues(...)

此方法修改 TempDisplacementDynamicsStep 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [TempDisplacementDynamicsStep](pt01ch49pyo31.md#ker-tempdisplacementdynamicsstep-tempdisplacementdynamic-pyc) 方法的参数相同，但 *name*、*previous* 和 *maintainAttributes* 参数除外。

**返回值**

无

**异常**

RangeError。

### 49.31.3 成员

TempDisplacementDynamicsStep 对象可以具有以下成员：

*name*

一个字符串，指定存储库键。

*timePeriod*

一个 Float，指定步骤的时间周期。默认值为 1.0。

*nlgeom*

一个布尔值，指定是否在步骤期间考虑几何非线性。默认值为 OFF。

*timeIncrementationMethod*

一个 SymbolicConstant，指定要使用的时间增量方法。可选值为 AUTOMATIC_GLOBAL、AUTOMATIC_EBE、FIXED_USER_DEFINED_INC 和 FIXED_EBE。默认值为 AUTOMATIC_GLOBAL。

*maxIncrement*

`None` 或一个 Float，指定允许的最大时间增量。如果没有上限，则 *maxIncrement*=`None`。默认值为 `None`。

*scaleFactor*

一个 Float，指定用于缩放时间增量的因子。此参数仅在 *timeIncrementationMethod*=AUTOMATIC_GLOBAL、AUTOMATIC_EBE 或 FIXED_EBE 时需要。默认值为 1.0。

*userDefinedInc*

`None` 或一个 Float，指定用户定义的时间增量。默认值为 `None`。

*linearBulkViscosity*

一个 Float，指定线性体积粘度参数 ![](../graphics/ker_eqn00420.gif)。默认值为 0.06。

*quadBulkViscosity*

一个 Float，指定二次体积粘度参数 ![](../graphics/ker_eqn00421.gif)。默认值为 1.2。

*previous*

一个字符串，指定前一步的名称。新步骤将出现在分析步骤列表中该步骤之后。

*description*

一个字符串，指定新步骤的描述。默认值为空字符串。

*massScaling*

一个 [MassScalingArray](pt01ch50pyo09.md) 对象，指定质量缩放控制。默认值为 PREVIOUS_STEP。

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

### 49.31.4 对应的分析关键字

| [*BULK VISCOSITY](../key/key-link.md#usb-kws-hbulkvisco) |
| --- |
| [*DYNAMIC](../key/key-link.md#usb-kws-hdynamic) |
| [*FIXED MASS SCALING](../key/key-link.md#usb-kws-hfixedmassscaling) |
| [*STEP](../key/key-link.md#usb-kws-hstep) |
| [*VARIABLE MASS SCALING](../key/key-link.md#usb-kws-hvariablemassscaling) |
