# 49.28 SteadyStateSubspaceStep 对象

SteadyStateSubspaceStep 对象用于基于子空间投影方法计算系统对谐波激励的线性化稳态响应。

SteadyStateSubspaceStep 对象派生于 [AnalysisStep](pt01ch49pyo02.md) 对象。

**访问**

```
import step
mdb.models[*name*].steps[*name*]
```

### 49.28.1 SteadyStateSubspaceStep(...)

此方法创建一个 SteadyStateSubspaceStep 对象。

**路径**

```
mdb.models[*name*].SteadyStateSubspaceStep
```

**必需参数**

*name*

一个字符串，指定存储库键。

*previous*

一个字符串，指定前一步的名称。新步骤将出现在分析步骤列表中该步骤之后。

*frequencyRange*

一个 [SteadyStateSubspaceFrequencyArray](pt01ch50pyo19.md) 对象。

**可选参数**

*description*

一个字符串，指定新步骤的描述。默认值为空字符串。

*factorization*

一个 SymbolicConstant，指定是否忽略阻尼项以便对实数（而非复数）系统矩阵进行分解。可选值为 REAL_ONLY 和 COMPLEX。默认值为 COMPLEX。

*scale*

一个 SymbolicConstant，指定输出使用的是对数标度还是线性标度。可选值为 LOGARITHMIC 和 LINEAR。默认值为 LOGARITHMIC。

*matrixStorage*

一个 SymbolicConstant，指定矩阵存储类型。可选值为 SYMMETRIC、UNSYMMETRIC 和 SOLVER_DEFAULT。默认值为 SOLVER_DEFAULT。

*maintainAttributes*

一个布尔值，指定是否保留具有相同名称的现有步骤的属性。默认值为 False。

*subdivideUsingEigenfrequencies*

一个布尔值，指定是否使用系统的特征频率细分每个频率范围。默认值为 ON。

*projection*

一个 SymbolicConstant，指定执行子空间投影到模态子空间的频率。可选值为 ALL_FREQUENCIES、CONSTANT、EIGENFREQUENCY、PROPERTY_CHANGE 和 RANGE。默认值为 ALL_FREQUENCIES。

*maxDampingChange*

一个 Float，指定在执行新投影之前阻尼材料属性的最大相对变化。默认值为 0.1。

*maxStiffnessChange*

一个 Float，指定在执行新投影之前刚度材料属性的最大相对变化。默认值为 0.1。

*frictionDamping*

一个布尔值，指定是否向阻尼矩阵添加摩擦效应引起的贡献。默认值为 OFF。

**返回值**

一个 SteadyStateSubspaceStep 对象。

**异常**

RangeError。

### 49.28.2 setValues(...)

此方法修改 SteadyStateSubspaceStep 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [SteadyStateSubspaceStep](pt01ch49pyo28.md#ker-steadystatesubspacestep-steadystatesubspacestep-pyc) 方法的参数相同，但 *name*、*previous* 和 *maintainAttributes* 参数除外。

**返回值**

无

**异常**

RangeError。

### 49.28.3 成员

SteadyStateSubspaceStep 对象可以具有以下成员：

*name*

一个字符串，指定存储库键。

*factorization*

一个 SymbolicConstant，指定是否忽略阻尼项以便对实数（而非复数）系统矩阵进行分解。可选值为 REAL_ONLY 和 COMPLEX。默认值为 COMPLEX。

*scale*

一个 SymbolicConstant，指定输出使用的是对数标度还是线性标度。可选值为 LOGARITHMIC 和 LINEAR。默认值为 LOGARITHMIC。

*matrixStorage*

一个 SymbolicConstant，指定矩阵存储类型。可选值为 SYMMETRIC、UNSYMMETRIC 和 SOLVER_DEFAULT。默认值为 SOLVER_DEFAULT。

*subdivideUsingEigenfrequencies*

一个布尔值，指定是否使用系统的特征频率细分每个频率范围。默认值为 ON。

*projection*

一个 SymbolicConstant，指定执行子空间投影到模态子空间的频率。可选值为 ALL_FREQUENCIES、CONSTANT、EIGENFREQUENCY、PROPERTY_CHANGE 和 RANGE。默认值为 ALL_FREQUENCIES。

*maxDampingChange*

一个 Float，指定在执行新投影之前阻尼材料属性的最大相对变化。默认值为 0.1。

*maxStiffnessChange*

一个 Float，指定在执行新投影之前刚度材料属性的最大相对变化。默认值为 0.1。

*frictionDamping*

一个布尔值，指定是否向阻尼矩阵添加摩擦效应引起的贡献。默认值为 OFF。

*previous*

一个字符串，指定前一步的名称。新步骤将出现在分析步骤列表中该步骤之后。

*description*

一个字符串，指定新步骤的描述。默认值为空字符串。

*frequencyRange*

一个 [SteadyStateSubspaceFrequencyArray](pt01ch50pyo19.md) 对象。

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

### 49.28.4 对应的分析关键字

| [*STEADY STATE DYNAMICS](../key/key-link.md#usb-kws-hsteadystdyn) |
| --- |
| [*STEP](../key/key-link.md#usb-kws-hstep) |
