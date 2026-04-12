# 49.16 ImplicitDynamicsStep 对象

ImplicitDynamicsStep 对象用于在 Abaqus/Standard 分析中提供动态应力/位移响应的直接积分，通常用于非线性情况。

ImplicitDynamicsStep 对象派生于 [AnalysisStep](pt01ch49pyo02.md) 对象。

**访问**

```
import step
mdb.models[*name*].steps[*name*]
```

### 49.16.1 ImplicitDynamicsStep(...)

此方法创建一个 ImplicitDynamicsStep 对象。

**路径**

```
mdb.models[*name*].ImplicitDynamicsStep
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

*nlgeom*

一个布尔值，指定是否在步骤期间考虑几何非线性。默认值为基于前一步的值。

*matrixStorage*

一个 SymbolicConstant，指定矩阵存储类型。可选值为 SYMMETRIC、UNSYMMETRIC 和 SOLVER_DEFAULT。默认值为 SOLVER_DEFAULT。

*application*

一个 SymbolicConstant，指定步骤的应用程序类型。可选值为 ANALYSIS_PRODUCT_DEFAULT、TRANSIENT_FIDELITY、MODERATE_DISSIPATION 和 QUASI_STATIC。默认值为 ANALYSIS_PRODUCT_DEFAULT。

*adiabatic*

一个布尔值，指定是否执行绝热应力分析。默认值为 OFF。

*timeIncrementationMethod*

一个 SymbolicConstant，指定要使用的时间增量方法。可选值为 FIXED 和 AUTOMATIC。默认值为 AUTOMATIC。

*maxNumInc*

一个 Int，指定步骤中的最大增量数。默认值为 100。

*initialInc*

一个 Float，指定初始时间增量。默认值为步骤的总时间周期。

*minInc*

一个 Float，指定允许的最小时间增量。默认值为建议的初始时间增量或总时间周期的 105 倍中的较小值。

*maxInc*

SymbolicConstant DEFAULT 或一个 Float，指定允许的最大时间增量。

*hafTolMethod*

一个 SymbolicConstant，指定使用自动时间增量方案指定半增量残差容差的方式。可选值为 ANALYSIS_PRODUCT_DEFAULT、VALUE 和 SCALE。默认值为 VALUE。

*haftol*

`None` 或一个 Float，指定与自动时间增量方案一起使用的半增量残差容差。默认值为 `None`。

*halfIncScaleFactor*

`None` 或一个 Float，指定与自动时间增量方案一起使用的半增量残差容差比例因子。默认值为 `None`。

*nohaf*

一个布尔值，指定是否抑制半增量残差的计算。默认值为 OFF。

*amplitude*

一个 SymbolicConstant，指定步骤中载荷幅值的变化。可选值为 STEP 和 RAMP。默认值为 STEP。

*alpha*

SymbolicConstant DEFAULT 或一个 Float，指定隐式算子中数值（人工）阻尼控制参数 ![](../graphics/ker_eqn00090.gif) 的非默认值。可选值为 .333 ![](../graphics/ker_eqn00422.gif) 0。默认值为 DEFAULT。

*initialConditions*

一个 SymbolicConstant，指定是否应在步骤开始时计算或重新计算加速度。可选值为 DEFAULT、BYPASS 和 ALLOW。默认值为 DEFAULT。

*extrapolation*

一个 SymbolicConstant，指定用于确定非线性分析的增量解的外推类型。可选值为 NONE、LINEAR、PARABOLIC、VELOCITY_PARABOLIC 和 ANALYSIS_PRODUCT_DEFAULT。默认值为 ANALYSIS_PRODUCT_DEFAULT。

*noStop*

一个布尔值，指定在完成允许的最大迭代次数后，即使未满足平衡容差，是否接受增量的解。默认值为 OFF。

**警告：**仅在您对如何解释结果有充分理解的特殊情况下，才应将 *noStop* 设置为 OFF。

*maintainAttributes*

一个布尔值，指定是否保留具有相同名称的现有步骤的属性。默认值为 False。

*solutionTechnique*

一个 SymbolicConstant，指定用于求解非线性方程的技术。可选值为 FULL_NEWTON 和 QUASI_NEWTON。默认值为 FULL_NEWTON。

*reformKernel*

一个 Int，指定在核矩阵重新形成之前允许的准牛顿迭代次数。默认值为 8。

*convertSDI*

一个 SymbolicConstant，指定在迭代期间发生严重不连续时是否强制进行新迭代。可选值为 PROPAGATED、CONVERT_SDI_OFF 和 CONVERT_SDI_ON。默认值为 PROPAGATED。

**返回值**

一个 ImplicitDynamicsStep 对象。

**异常**

RangeError。

### 49.16.2 setValues(...)

此方法修改 ImplicitDynamicsStep 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ImplicitDynamicsStep](pt01ch49pyo16.md#ker-implicitdynamicsstep-implicitdynamicsstep-pyc) 方法的参数相同，但 *name*、*previous* 和 *maintainAttributes* 参数除外。

**返回值**

无

**异常**

RangeError。

### 49.16.3 成员

ImplicitDynamicsStep 对象可以具有以下成员：

*name*

一个字符串，指定存储库键。

*timePeriod*

一个 Float，指定步骤的总时间周期。默认值为 1.0。

*nlgeom*

一个布尔值，指定是否在步骤期间考虑几何非线性。默认值为基于前一步的值。

*matrixStorage*

一个 SymbolicConstant，指定矩阵存储类型。可选值为 SYMMETRIC、UNSYMMETRIC 和 SOLVER_DEFAULT。默认值为 SOLVER_DEFAULT。

*application*

一个 SymbolicConstant，指定步骤的应用程序类型。可选值为 ANALYSIS_PRODUCT_DEFAULT、TRANSIENT_FIDELITY、MODERATE_DISSIPATION 和 QUASI_STATIC。默认值为 ANALYSIS_PRODUCT_DEFAULT。

*adiabatic*

一个布尔值，指定是否执行绝热应力分析。默认值为 OFF。

*timeIncrementationMethod*

一个 SymbolicConstant，指定要使用的时间增量方法。可选值为 FIXED 和 AUTOMATIC。默认值为 AUTOMATIC。

*maxNumInc*

一个 Int，指定步骤中的最大增量数。默认值为 100。

*initialInc*

一个 Float，指定初始时间增量。默认值为步骤的总时间周期。

*minInc*

一个 Float，指定允许的最小时间增量。默认值为建议的初始时间增量或总时间周期的 105 倍中的较小值。

*maxInc*

SymbolicConstant DEFAULT 或一个 Float，指定允许的最大时间增量。

*hafTolMethod*

一个 SymbolicConstant，指定使用自动时间增量方案指定半增量残差容差的方式。可选值为 ANALYSIS_PRODUCT_DEFAULT、VALUE 和 SCALE。默认值为 VALUE。

*haftol*

`None` 或一个 Float，指定与自动时间增量方案一起使用的半增量残差容差。默认值为 `None`。

*halfIncScaleFactor*

`None` 或一个 Float，指定与自动时间增量方案一起使用的半增量残差容差比例因子。默认值为 `None`。

*nohaf*

一个布尔值，指定是否抑制半增量残差的计算。默认值为 OFF。

*amplitude*

一个 SymbolicConstant，指定步骤中载荷幅值的变化。可选值为 STEP 和 RAMP。默认值为 STEP。

*alpha*

SymbolicConstant DEFAULT 或一个 Float，指定隐式算子中数值（人工）阻尼控制参数 ![](../graphics/ker_eqn00090.gif) 的非默认值。可选值为 .333 ![](../graphics/ker_eqn00422.gif) 0。默认值为 DEFAULT。

*initialConditions*

一个 SymbolicConstant，指定是否应在步骤开始时计算或重新计算加速度。可选值为 DEFAULT、BYPASS 和 ALLOW。默认值为 DEFAULT。

*extrapolation*

一个 SymbolicConstant，指定用于确定非线性分析的增量解的外推类型。可选值为 NONE、LINEAR、PARABOLIC、VELOCITY_PARABOLIC 和 ANALYSIS_PRODUCT_DEFAULT。默认值为 ANALYSIS_PRODUCT_DEFAULT。

*noStop*

一个布尔值，指定在完成允许的最大迭代次数后，即使未满足平衡容差，是否接受增量的解。默认值为 OFF。

**警告：**仅在您对如何解释结果有充分理解的特殊情况下，才应将 *noStop* 设置为 OFF。

*solutionTechnique*

一个 SymbolicConstant，指定用于求解非线性方程的技术。可选值为 FULL_NEWTON 和 QUASI_NEWTON。默认值为 FULL_NEWTON。

*reformKernel*

一个 Int，指定在核矩阵重新形成之前允许的准牛顿迭代次数。默认值为 8。

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

### 49.16.4 对应的分析关键字

| [*DYNAMIC](../key/key-link.md#usb-kws-hdynamic) |
| --- |
| [*STEP](../key/key-link.md#usb-kws-hstep) |
