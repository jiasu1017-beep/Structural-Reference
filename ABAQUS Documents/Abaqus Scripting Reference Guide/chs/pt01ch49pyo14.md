# 49.13 FrequencyStep 对象

FrequencyStep 对象用于执行特征值提取，以计算系统的固有频率和相应的振型。

FrequencyStep 对象派生于 [AnalysisStep](pt01ch49pyo02.md) 对象。

**访问**

```
import step
mdb.models[*name*].steps[*name*]
```

### 49.13.1 FrequencyStep(...)

此方法创建一个 FrequencyStep 对象。

**路径**

```
mdb.models[*name*].FrequencyStep
```

**必需参数**

*name*

一个字符串，指定存储库键。

*previous*

一个字符串，指定前一步的名称。新步骤将出现在分析步骤列表中该步骤之后。

*eigensolver*

一个 SymbolicConstant，指定特征值求解器。可选值为 LANCZOS、SUBSPACE 和 AMS。

除非 *eigensolver*=LANCZOS，否则忽略以下可选参数：*blockSize*、*maxBlocks*、*normalization*、*propertyEvaluationFrequency*。

除非 *eigensolver*=LANCZOS 或 AMS，否则忽略以下可选参数：*minEigen*、*maxEigen* 和 *acousticCoupling*。

除非 *eigensolver*=AMS，否则忽略以下可选参数：*projectDamping*、*acousticRangeFactor*、*substructureCutoffMultiplier*、*firstCutoffMultiplier*、*secondCutoffMultiplier*、*residualModeRegion*、*regionalModeDof* 和 *limitSavedEigenvectorRegion*。

**可选参数**

*numEigen*

SymbolicConstant ALL 或一个 Int，指定要计算的特征值数量或 ALL。默认值为 ALL。

*description*

一个字符串，指定新步骤的描述。默认值为空字符串。

*shift*

一个 Float，指定以每时间周期计的位移点。默认值为 0.0。

*minEigen*

`None` 或一个 Float，指定感兴趣的最小频率（以每时间周期计）。默认值为 `None`。

*maxEigen*

`None` 或一个 Float，指定感兴趣的最大频率（以每时间周期计）。默认值为 `None`。

*vectors*

`None` 或一个 Int，指定迭代中使用的向量数。默认值为 (2*n*, *n* + 8) 中的最小值，其中 *n* 是请求的特征值数量。默认值为 `None`。

*maxIterations*

一个 Int，指定最大迭代次数。默认值为 30。

*blockSize*

一个 SymbolicConstant，指定 Lanczos 块步骤的大小。默认值为 DEFAULT。

*maxBlocks*

一个 SymbolicConstant，指定每个 Lanczos 运行中 Lanczos 块步骤的最大数量。默认值为 DEFAULT。

*normalization*

一个 SymbolicConstant，指定特征向量归一化的方法。可选值为 DISPLACEMENT 和 MASS。默认值为 DISPLACEMENT。

DISPLACEMENT 值表示将特征向量归一化，使每个向量中的最大位移条目为 1。MASS 值表示相对于结构质量矩阵对特征向量进行归一化，这导致缩放特征向量，使每个向量的广义质量为 1。

*propertyEvaluationFrequency*

`None` 或一个 Float，指定在特征值提取过程中评估粘弹性、弹簧和阻尼器频率相关属性的频率。如果值为 `None`，分析产品将在零频率下评估与频率相关弹簧和阻尼器相关的刚度，并且不会考虑步骤中频域粘弹性的刚度贡献。默认值为 `None`。

*projectDamping*

一个布尔值，指定在 *AMS* 特征值提取期间是否包含粘性和结构阻尼算子的投影。仅在 *eigenSolver*=AMS 时有效。默认值为 ON。

*acousticCoupling*

一个 SymbolicConstant，指定使用 [*TIE](../key/key-link.md#usb-kws-mtie) 选项耦合的声学元件和结构元件的模型中，或使用 ASI 型元件的模型中的声-结构耦合类型。可选值为 AC_ON、AC_OFF 和 AC_PROJECTION。默认值为 AC_ON。

*acousticRangeFactor*

一个 Float，指定最大声频与最大结构频率的比率。默认值为 1.0。

*frictionDamping*

一个布尔值，指定是否向阻尼矩阵添加摩擦效应引起的贡献。默认值为 OFF。

*matrixStorage*

一个 SymbolicConstant，指定矩阵存储类型。可选值为 SYMMETRIC、UNSYMMETRIC 和 SOLVER_DEFAULT。默认值为 SOLVER_DEFAULT。

*maintainAttributes*

一个布尔值，指定是否保留具有相同名称的现有步骤的属性。默认值为 False。

*simLinearDynamics*

一个布尔值，指定是否激活基于 SIM 的线性动力学过程。默认值为 OFF。

*residualModes*

一个布尔值，指定是否包含紧邻前一个 Static、Linear Perturbation 步骤的残差模态。默认值为 OFF。

*substructureCutoffMultiplier*

一个 Float，指定子结构特征问题的截止频率，定义为感兴趣最大频率的乘数。默认值为 5.0。

*firstCutoffMultiplier*

一个 Float，指定简化特征问题的第一个截止频率，定义为感兴趣最大频率的乘数。默认值为 1.7。

*secondCutoffMultiplier*

一个 Float，指定简化特征问题的第二个截止频率，定义为感兴趣最大频率的乘数。默认值为 1.1。

*residualModeRegion*

`None` 或一个字符串序列，指定请求残差模态的区域名称。默认值为 `None`。

*residualModeDof*

`None` 或一个 Int 序列，指定请求残差模态的自由度。默认值为 `None`。

*limitSavedEigenvectorRegion*

`None` 或一个 [Region](pt01ch45pyo03.md) 对象，指定要保存特征向量的区域，或代表整个模型的 SymbolicConstant None。默认值为 `None`。

**返回值**

一个 FrequencyStep 对象。

**异常**

RangeError。

### 49.13.2 setValues(...)

此方法修改 FrequencyStep 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [FrequencyStep](pt01ch49pyo13.md#ker-frequencystep-frequencystep-pyc) 方法的参数相同，但 *name*、*previous* 和 *maintainAttributes* 参数除外。

**返回值**

无

**异常**

RangeError。

### 49.13.3 成员

FrequencyStep 对象可以具有以下成员：

*name*

一个字符串，指定存储库键。

*eigensolver*

一个 SymbolicConstant，指定特征值求解器。可选值为 LANCZOS、SUBSPACE 和 AMS。

除非 *eigensolver*=LANCZOS，否则忽略以下可选参数：*blockSize*、*maxBlocks*、*normalization*、*propertyEvaluationFrequency*。

除非 *eigensolver*=LANCZOS 或 AMS，否则忽略以下可选参数：*minEigen*、*maxEigen* 和 *acousticCoupling*。

除非 *eigensolver*=AMS，否则忽略以下可选参数：*projectDamping*、*acousticRangeFactor*、*substructureCutoffMultiplier*、*firstCutoffMultiplier*、*secondCutoffMultiplier*、*residualModeRegion*、*regionalModeDof* 和 *limitSavedEigenvectorRegion*。

*numEigen*

SymbolicConstant ALL 或一个 Int，指定要计算的特征值数量或 ALL。默认值为 ALL。

*shift*

一个 Float，指定以每时间周期计的位移点。默认值为 0.0。

*minEigen*

`None` 或一个 Float，指定感兴趣的最小频率（以每时间周期计）。默认值为 `None`。

*maxEigen*

`None` 或一个 Float，指定感兴趣的最大频率（以每时间周期计）。默认值为 `None`。

*vectors*

`None` 或一个 Int，指定迭代中使用的向量数。默认值为 (2*n*, *n* + 8) 中的最小值，其中 *n* 是请求的特征值数量。默认值为 `None`。

*maxIterations*

一个 Int，指定最大迭代次数。默认值为 30。

*blockSize*

一个 SymbolicConstant，指定 Lanczos 块步骤的大小。默认值为 DEFAULT。

*maxBlocks*

一个 SymbolicConstant，指定每个 Lanczos 运行中 Lanczos 块步骤的最大数量。默认值为 DEFAULT。

*normalization*

一个 SymbolicConstant，指定特征向量归一化的方法。可选值为 DISPLACEMENT 和 MASS。默认值为 DISPLACEMENT。

DISPLACEMENT 值表示将特征向量归一化，使每个向量中的最大位移条目为 1。MASS 值表示相对于结构质量矩阵对特征向量进行归一化，这导致缩放特征向量，使每个向量的广义质量为 1。

*propertyEvaluationFrequency*

`None` 或一个 Float，指定在特征值提取过程中评估粘弹性、弹簧和阻尼器频率相关属性的频率。如果值为 `None`，分析产品将在零频率下评估与频率相关弹簧和阻尼器相关的刚度，并且不会考虑步骤中频域粘弹性的刚度贡献。默认值为 `None`。

*projectDamping*

一个布尔值，指定在 *AMS* 特征值提取期间是否包含粘性和结构阻尼算子的投影。仅在 *eigenSolver*=AMS 时有效。默认值为 ON。

*acousticCoupling*

一个 SymbolicConstant，指定声-结构耦合类型。可选值为 AC_ON、AC_OFF 和 AC_PROJECTION。默认值为 AC_ON。

*acousticRangeFactor*

一个 Float，指定最大声频与最大结构频率的比率。默认值为 1.0。

*frictionDamping*

一个布尔值，指定是否向阻尼矩阵添加摩擦效应引起的贡献。默认值为 OFF。

*matrixStorage*

一个 SymbolicConstant，指定矩阵存储类型。可选值为 SYMMETRIC、UNSYMMETRIC 和 SOLVER_DEFAULT。默认值为 SOLVER_DEFAULT。

*simLinearDynamics*

一个布尔值，指定是否激活基于 SIM 的线性动力学过程。默认值为 OFF。

*residualModes*

一个布尔值，指定是否包含紧邻前一个 Static、Linear Perturbation 步骤的残差模态。默认值为 OFF。

*substructureCutoffMultiplier*

一个 Float，指定子结构特征问题的截止频率，定义为感兴趣最大频率的乘数。默认值为 5.0。

*firstCutoffMultiplier*

一个 Float，指定简化特征问题的第一个截止频率，定义为感兴趣最大频率的乘数。默认值为 1.7。

*secondCutoffMultiplier*

一个 Float，指定简化特征问题的第二个截止频率，定义为感兴趣最大频率的乘数。默认值为 1.1。

*previous*

一个字符串，指定前一步的名称。新步骤将出现在分析步骤列表中该步骤之后。

*description*

一个字符串，指定新步骤的描述。默认值为空字符串。

*residualModeRegion*

`None` 或一个字符串元组，指定请求残差模态的区域名称。默认值为 `None`。

*residualModeDof*

`None` 或一个 Int 元组，指定请求残差模态的自由度。默认值为 `None`。

*limitSavedEigenvectorRegion*

`None` 或一个 [Region](pt01ch45pyo03.md) 对象，指定要保存特征向量的区域，或代表整个模型的 SymbolicConstant None。默认值为 `None`。

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

### 49.13.4 对应的分析关键字

| [*FREQUENCY](../key/key-link.md#usb-kws-hfrequency) |
| --- |
| [*STEP](../key/key-link.md#usb-kws-hstep) |
