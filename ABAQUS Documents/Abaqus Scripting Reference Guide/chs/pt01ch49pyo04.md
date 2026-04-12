# 49.4 BuckleStep 对象

BuckleStep 对象控制特征值屈曲估计。

BuckleStep 对象派生于 [AnalysisStep](pt01ch49pyo02.md) 对象。

**访问**

```
import step
mdb.models[*name*].steps[*name*]
```

### 49.4.1 BuckleStep(...)

此方法创建一个 BuckleStep 对象。

**路径**

```
mdb.models[*name*].BuckleStep
```

**必需参数**

*name*

一个字符串，指定存储库键。

*previous*

一个字符串，指定前一步的名称。新步骤将出现在分析步骤列表中该步骤之后。

*numEigen*

一个 Int，指定要估计的特征值数量。

**可选参数**

*description*

一个字符串，指定新步骤的描述。默认值为空字符串。

*eigensolver*

一个 SymbolicConstant，指定特征值求解器。可选值为 SUBSPACE 和 LANCZOS。默认值为 SUBSPACE。

*minEigen*

`None` 或一个 Float，指定感兴趣的最小特征值。默认值为 `None`。

*maxEigen*

`None` 或一个 Float，指定感兴趣的最大特征值。默认值为 `None`。

*vectors*

一个 Int，指定迭代中使用的向量数。默认值为 (2*n*, *n* + 8) 中的最小值，其中 *n* 是请求的特征值数量。

*maxIterations*

一个 Int，指定最大迭代次数。默认值为 30。

*blockSize*

SymbolicConstant DEFAULT 或一个 Int，指定 Lanczos 块步骤的大小。默认值为 DEFAULT。

*maxBlocks*

SymbolicConstant DEFAULT 或一个 Int，指定每个 Lanczos 运行中 Lanczos 块步骤的最大数量。默认值为 DEFAULT。

**注意：**除非 *eigensolver*=LANCZOS，否则忽略 *minEigen*、*blockSize* 和 *maxBlocks*。

*matrixStorage*

一个 SymbolicConstant，指定矩阵存储类型。可选值为 SYMMETRIC、UNSYMMETRIC 和 SOLVER_DEFAULT。默认值为 SOLVER_DEFAULT。

*maintainAttributes*

一个布尔值，指定是否保留具有相同名称的现有步骤的属性。默认值为 False。

**返回值**

一个 BuckleStep 对象。

**异常**

RangeError。

### 49.4.2 setValues(...)

此方法修改 BuckleStep 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [BuckleStep](pt01ch49pyo04.md#ker-bucklestep-bucklestep-pyc) 方法的参数相同，但 *name*、*previous* 和 *maintainAttributes* 参数除外。

**返回值**

无

**异常**

RangeError。

### 49.4.3 成员

BuckleStep 对象可以具有以下成员：

*name*

一个字符串，指定存储库键。

*numEigen*

一个 Int，指定要估计的特征值数量。

*eigensolver*

一个 SymbolicConstant，指定特征值求解器。可选值为 SUBSPACE 和 LANCZOS。默认值为 SUBSPACE。

*minEigen*

`None` 或一个 Float，指定感兴趣的最小特征值。默认值为 `None`。

*maxEigen*

`None` 或一个 Float，指定感兴趣的最大特征值。默认值为 `None`。

*vectors*

一个 Int，指定迭代中使用的向量数。默认值为 (2*n*, *n* + 8) 中的最小值，其中 *n* 是请求的特征值数量。

*maxIterations*

一个 Int，指定最大迭代次数。默认值为 30。

*blockSize*

SymbolicConstant DEFAULT 或一个 Int，指定 Lanczos 块步骤的大小。默认值为 DEFAULT。

*maxBlocks*

SymbolicConstant DEFAULT 或一个 Int，指定每个 Lanczos 运行中 Lanczos 块步骤的最大数量。默认值为 DEFAULT。

**注意：**除非 *eigensolver*=LANCZOS，否则忽略 *minEigen*、*blockSize* 和 *maxBlocks*。

*matrixStorage*

一个 SymbolicConstant，指定矩阵存储类型。可选值为 SYMMETRIC、UNSYMMETRIC 和 SOLVER_DEFAULT。默认值为 SOLVER_DEFAULT。

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

### 49.4.4 对应的分析关键字

| [*BUCKLE](../key/key-link.md#usb-kws-hbuckle) |
| --- |
| [*STEP](../key/key-link.md#usb-kws-hstep) |
