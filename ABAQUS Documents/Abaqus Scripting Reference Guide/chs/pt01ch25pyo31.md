# 25.31 FilmCondition 对象

FilmCondition 对象为耦合温度-位移分析定义膜系数和相关的汇温度。

FilmCondition 对象派生自 [Interaction](pt01ch25pyo01.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.31.1 FilmCondition(...)

此方法创建一个 FilmCondition 对象。

**路径**

```
mdb.models[*name*].FilmCondition
```

**必需参数**

*name*

字符串，指定存储库键。

*createStepName*

字符串，指定创建 FilmCondition 对象的步骤名称。

*surface*

[Region](pt01ch45pyo03.md) 对象，指定应用膜条件交互的表面名称。

*definition*

 SymbolicConstant，指定如何定义膜条件。可能的值为 EMBEDDED_COEFF、PROPERTY_REF、USER_SUB 和 FIELD。

**可选参数**

*interactionProperty*

字符串，指定与此交互关联的 [FilmConditionProp](pt01ch25pyo32.md) 对象的名称。*interactionProperty* 参数仅在 *definition*=PROPERTY_REF 时适用。默认值为空字符串。

*sinkTemperature*

浮点数，指定参考汇温度，![](../graphics/ker_eqn00061.gif)。默认值为 0.0。

*sinkAmplitude*

字符串，指定给出汇温度 ![](../graphics/ker_eqn00061.gif) 随时间变化的 [Amplitude](pt01ch03pyo01.md) 对象的名称。默认值为空字符串。

**注：**在 Abaqus/Standard 分析中使用空字符串可以指定参考汇温度在步骤开始时立即应用或线性跨越步骤应用。在 Abaqus/Explicit 分析中使用空字符串可以指定参考汇温度在整个步骤中应用。

*filmCoeff*

浮点数，指定参考膜系数值，![](../graphics/ker_eqn00069.gif)。*filmCoeff* 参数适用于 *definition*=EMBEDDED_COEFF、*definition*=USER_SUB 或 *definition*=FIELD 时。默认值为 0.0。

*filmCoeffAmplitude*

字符串，指定给出膜系数 ![](../graphics/ker_eqn00069.gif) 随时间变化的 [Amplitude](pt01ch03pyo01.md) 对象的名称。默认值为空字符串。

**注：**在 Abaqus/Standard 分析中使用空字符串可以指定参考膜系数在步骤开始时立即应用或线性跨越步骤应用。在 Abaqus/Explicit 分析中使用空字符串可以指定参考膜系数在整个步骤中应用。

*field*

字符串，指定与此交互关联的 [AnalyticalField](pt01ch21pyo02.md) 对象的名称。*field* 参数仅在 *definition*=FIELD 时适用。默认值为空字符串。

*sinkFieldName*

字符串，指定与汇温度关联的 [AnalyticalField](pt01ch21pyo02.md) 或 [DiscreteField](pt01ch21pyo04.md) 对象的名称。*sinkFieldName* 参数仅在 *sinkDistributionType*=ANALYTICAL_FIELD 或 *sinkDistributionType*=DISCRETE_FIELD 时适用。默认值为空字符串。

*sinkDistributionType*

 SymbolicConstant，指定如何分布汇温度。可能的值为 UNIFORM、ANALYTICAL_FIELD 和 DISCRETE_FIELD。默认值为 UNIFORM。

**返回值**

FilmCondition 对象。

**异常**

无。

### 25.31.2 setValues(...)

此方法修改创建 FilmCondition 对象的步骤中现有 FilmCondition 对象的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [FilmCondition](pt01ch25pyo31.md#ker-filmcondition-filmcondition-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 25.31.3 setValuesInStep(...)

此方法修改指定步骤中现有 FilmCondition 对象的传播数据。

**必需参数**

*stepName*

字符串，指定修改交互的步骤名称。

**可选参数**

`setValuesInStep` 的可选参数与 [FilmCondition](pt01ch25pyo31.md#ker-filmcondition-filmcondition-pyc) 方法的可选参数相同。
无。

**返回值**

无。

**异常**

无。

### 25.31.4 成员

FilmCondition 对象的成员与 [FilmCondition](pt01ch25pyo31.md#ker-filmcondition-filmcondition-pyc) 方法的参数具有相同的名称和描述。





