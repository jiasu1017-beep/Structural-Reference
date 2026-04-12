# 49.30 SubstructureGenerateStep 对象

SubstructureGenerateStep 对象用于生成子结构。

SubstructureGenerateStep 对象派生于 [AnalysisStep](pt01ch49pyo02.md) 对象。

**访问**

```
import step
mdb.models[*name*].steps[*name*]
```

### 49.30.1 SubstructureGenerateStep(...)

此方法创建一个 SubstructureGenerateStep 对象。

**路径**

```
mdb.models[*name*].SubstructureGenerateStep
```

**必需参数**

*name*

一个字符串，指定存储库键。

*previous*

一个字符串，指定前一步的名称。新步骤将出现在分析步骤列表中该步骤之后。

*substructureIdentifier*

一个字符串，指定子结构的唯一标识符。默认值为空字符串。

**可选参数**

*description*

一个字符串，指定新步骤的描述。默认值为空字符串。

*recoveryMatrix*

一个 SymbolicConstant，指定要计算的子结构恢复。可选值为 WHOLE_MODEL、REGION 和 NONE。默认值为 WHOLE_MODEL。

*recoveryRegion*

一个 [Region](pt01ch45pyo03.md) 对象，指定子结构恢复的区域。当 *recoveryMatrix*=REGION 时需要此参数。

*computeGravityLoadVectors*

一个布尔值，指定是否计算重力载荷向量。默认值为 False。

*computeReducedMassMatrix*

一个布尔值，指定是否计算缩减质量矩阵。默认值为 False。

*computeReducedStructuralDampingMatrix*

一个布尔值，指定是否计算缩减结构阻尼矩阵。默认值为 False。

*computeReducedViscousDampingMatrix*

一个布尔值，指定是否计算缩减粘性阻尼矩阵。默认值为 False。

*evaluateFrequencyDependentProperties*

一个布尔值，指定是否评估频率相关属性。默认值为 False。

*frequency*

一个 Float，指定评估频率相关属性的频率。默认值为 0.0。

*retainedEigenmodesMethod*

一个 SymbolicConstant，指定要保留的特征模态。可选值为 MODE_RANGE、FREQUENCY_RANGE 和 NONE。默认值为 NONE。

*modeRange*

一个 [SubstructureGenerateModesArray](pt01ch50pyo25.md) 对象。

*frequencyRange*

一个 [SubstructureGenerateFrequencyArray](pt01ch50pyo24.md) 对象。

*globalDampingField*

一个 SymbolicConstant，指定应应用全局阻尼因子的场。可选值为 ALL、ACOUSTIC、MECHANICAL 和 NONE。默认值为 NONE。

*alphaDampingRatio*

一个 Float，指定创建全局 Rayleigh 质量比例阻尼的因子。默认值为 0.0。

*betaDampingRatio*

一个 Float，指定创建全局 Rayleigh 刚度比例阻尼的因子。默认值为 0.0。

*structuralDampingRatio*

一个 Float，指定创建与频率无关的刚度比例结构阻尼的因子。默认值为 0.0。

*viscousDampingControl*

一个 SymbolicConstant，指定包含粘性阻尼矩阵的阻尼控制。可选值为 ELEMENT、FACTOR、COMBINED 和 NONE。默认值为 NONE。

*structuralDampingControl*

一个 SymbolicConstant，指定包含结构阻尼矩阵的阻尼控制。可选值为 ELEMENT、FACTOR、COMBINED 和 NONE。默认值为 NONE。

**返回值**

一个 SubstructureGenerateStep 对象。

**异常**

RangeError。

### 49.30.2 setValues(...)

此方法修改 SubstructureGenerateStep 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [SubstructureGenerateStep](pt01ch49pyo30.md#ker-substructuregeneratestep-substructuregeneratestep-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

RangeError。

### 49.30.3 成员

SubstructureGenerateStep 对象可以具有以下成员：

*name*

一个字符串，指定存储库键。

*recoveryMatrix*

一个 SymbolicConstant，指定要计算的子结构恢复。可选值为 WHOLE_MODEL、REGION 和 NONE。默认值为 WHOLE_MODEL。

*frequency*

一个 Float，指定评估频率相关属性的频率。默认值为 0.0。

*retainedEigenmodesMethod*

一个 SymbolicConstant，指定要保留的特征模态。可选值为 MODE_RANGE、FREQUENCY_RANGE 和 NONE。默认值为 NONE。

*globalDampingField*

一个 SymbolicConstant，指定应应用全局阻尼因子的场。可选值为 ALL、ACOUSTIC、MECHANICAL 和 NONE。默认值为 NONE。

*alphaDampingRatio*

一个 Float，指定创建全局 Rayleigh 质量比例阻尼的因子。默认值为 0.0。

*betaDampingRatio*

一个 Float，指定创建全局 Rayleigh 刚度比例阻尼的因子。默认值为 0.0。

*structuralDampingRatio*

一个 Float，指定创建与频率无关的刚度比例结构阻尼的因子。默认值为 0.0。

*viscousDampingControl*

一个 SymbolicConstant，指定包含粘性阻尼矩阵的阻尼控制。可选值为 ELEMENT、FACTOR、COMBINED 和 NONE。默认值为 NONE。

*structuralDampingControl*

一个 SymbolicConstant，指定包含结构阻尼矩阵的阻尼控制。可选值为 ELEMENT、FACTOR、COMBINED 和 NONE。默认值为 NONE。

*previous*

一个字符串，指定前一步的名称。新步骤将出现在分析步骤列表中该步骤之后。

*description*

一个字符串，指定新步骤的描述。默认值为空字符串。

*substructureIdentifier*

一个字符串，指定子结构的唯一标识符。默认值为空字符串。

*recoveryRegion*

一个 [Region](pt01ch45pyo03.md) 对象，指定子结构恢复的区域。当 *recoveryMatrix*=REGION 时需要此参数。

*frequencyRange*

一个 [SubstructureGenerateFrequencyArray](pt01ch50pyo24.md) 对象。

*modeRange*

一个 [SubstructureGenerateModesArray](pt01ch50pyo25.md) 对象。

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

### 49.30.4 对应的分析关键字

| [*SUBSTRUCTURE GENERATE](../key/key-link.md#usb-kws-ssubgenerate) |
| --- |
| [*STEP](../key/key-link.md#usb-kws-hstep) |
