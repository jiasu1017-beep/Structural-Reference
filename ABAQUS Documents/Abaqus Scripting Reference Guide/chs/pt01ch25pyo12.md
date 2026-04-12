# 25.12 ConcentratedFilmCondition 对象

ConcentratedFilmCondition 对象定义集中膜系数和相关的汇温度。

ConcentratedFilmCondition 对象派生自 [Interaction](pt01ch25pyo01.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.12.1 ConcentratedFilmCondition(...)

此方法创建一个 ConcentratedFilmCondition 对象。

**路径**

```
mdb.models[*name*].ConcentratedFilmCondition
```

**必需参数**

*name*

字符串，指定存储库键。

*createStepName*

字符串，指定创建 ConcentratedFilmCondition 对象的步骤名称。

*region*

[Region](pt01ch45pyo03.md) 对象，指定应用集中膜条件交互的区域。交互应用于区域中的每个节点。

*definition*

 SymbolicConstant，指定如何定义集中膜条件。可能的值为 EMBEDDED_COEFF、PROPERTY_REF、USER_SUB 和 FIELD。

**可选参数**

*nodalArea*

浮点数，指定应用集中膜条件的节点关联的面积。默认值为 1.0。

*explicitRegionType*

 SymbolicConstant，指定如何将集中膜条件应用于自适应网格域的边界。可能的值为 LAGRANGIAN、SLIDING 和 EULERIAN。默认值为 LAGRANGIAN。

此参数仅在 Abaqus/Explicit 分析期间适用。

*interactionProperty*

字符串，指定与此交互关联的 [FilmConditionProp](pt01ch25pyo32.md) 对象的名称。*interactionProperty* 参数仅在 *definition*=PROPERTY_REF 时适用。默认值为空字符串。

*field*

字符串，指定与此交互关联的 [AnalyticalField](pt01ch21pyo02.md) 对象的名称。*field* 参数仅在 *definition*=FIELD 时适用。默认值为空字符串。

*sinkTemperature*

浮点数，指定参考汇温度，![](../graphics/ker_eqn00061.gif)。默认值为 0.0。

*sinkAmplitude*

字符串，指定给出汇温度 ![](../graphics/ker_eqn00061.gif) 随时间变化的 [Amplitude](pt01ch03pyo01.md) 对象的名称。默认值为空字符串。

**注：**在 Abaqus/Standard 分析中使用 `None` 可以指定参考汇温度在步骤开始时立即应用或在线性跨越步骤应用。在 Abaqus/Explicit 分析中使用 `None` 可以指定参考汇温度在整个步骤中应用。

*filmCoeff*

浮点数，指定参考膜系数值，![](../graphics/ker_eqn00069.gif)。*filmCoeff* 参数适用于 *definition*=EMBEDDED_COEFF、*definition*=USER_SUB 或 *definition*=FIELD 时。默认值为 0.0。

*filmCoeffAmplitude*

字符串，指定给出膜系数 ![](../graphics/ker_eqn00069.gif) 随时间变化的 [Amplitude](pt01ch03pyo01.md) 对象的名称。默认值为空字符串。

**注：**在 Abaqus/Standard 分析中使用 `None` 可以指定参考膜系数在步骤开始时立即应用或线性跨越步骤应用。在 Abaqus/Explicit 分析中使用 `None` 可以指定参考膜系数在整个步骤中应用。

*sinkFieldName*

字符串，指定与汇温度关联的 [AnalyticalField](pt01ch21pyo02.md) 或 [DiscreteField](pt01ch21pyo04.md) 对象的名称。*sinkFieldName* 参数仅在 *sinkDistributionType*=ANALYTICAL_FIELD 或 *sinkDistributionType*=DISCRETE_FIELD 时适用。默认值为空字符串。

*sinkDistributionType*

 SymbolicConstant，指定如何分布汇温度。可能的值为 UNIFORM、ANALYTICAL_FIELD 和 DISCRETE_FIELD。默认值为 UNIFORM。

**返回值**

ConcentratedFilmCondition 对象。

**异常**

无。

### 25.12.2 setValues(...)

此方法修改创建 ConcentratedFilmCondition 对象的步骤中现有 ConcentratedFilmCondition 对象的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ConcentratedFilmCondition](pt01ch25pyo12.md#ker-concentratedfilmcondition-concentratedfilmcondition-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 25.12.3 setValuesInStep(...)

此方法修改指定步骤中现有 ConcentratedFilmCondition 对象的传播数据。

**必需参数**

*stepName*

字符串，指定修改交互的步骤名称。

**可选参数**

`setValuesInStep` 的可选参数与 [ConcentratedFilmCondition](pt01ch25pyo12.md#ker-concentratedfilmcondition-concentratedfilmcondition-pyc) 方法的可选参数相同，但 *explicitRegionType* 参数除外。
无。

**返回值**

无。

**异常**

无。

### 25.12.4 成员

ConcentratedFilmCondition 对象的成员与 [ConcentratedFilmCondition](pt01ch25pyo12.md#ker-concentratedfilmcondition-concentratedfilmcondition-pyc) 方法的参数具有相同的名称和描述。





