# 25.14 ConcentratedRadiationToAmbient 对象

ConcentratedRadiationToAmbient 对象定义点与其非反射环境之间的辐射热传递。

ConcentratedRadiationToAmbient 对象派生自 [Interaction](pt01ch25pyo01.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.14.1 ConcentratedRadiationToAmbient(...)

此方法创建一个 ConcentratedRadiationToAmbient 对象。

**路径**

```
mdb.models[*name*].ConcentratedRadiationToAmbient
```

**必需参数**

*name*

字符串，指定存储库键。

*createStepName*

字符串，指定创建 ConcentratedRadiationToAmbient 对象的步骤名称。

*region*

[Region](pt01ch45pyo03.md) 对象，指定应用集中辐射交互的区域。交互应用于区域中的每个节点。

*ambientTemperature*

浮点数，指定参考环境温度，![](../graphics/ker_eqn00061.gif)。

*ambientTemperatureAmp*

字符串，指定给出环境温度随时间变化的 [Amplitude](pt01ch03pyo01.md) 对象的名称。

**注：**在 Abaqus/Standard 分析中使用 `None` 可以指定参考环境温度在步骤开始时立即应用或线性跨越步骤应用。在 Abaqus/Explicit 分析中使用 `None` 可以指定参考环境温度在整个步骤中应用。

*emissivity*

浮点数，指定发射率，![](../graphics/ker_eqn00062.gif)。

**可选参数**

*nodalArea*

浮点数，指定应用集中辐射交互的节点关联的面积。默认值为 1.0。

*explicitRegionType*

 SymbolicConstant，指定如何将集中辐射应用于自适应网格域的边界。可能的值为 LAGRANGIAN、SLIDING 和 EULERIAN。默认值为 LAGRANGIAN。

**注：** *explicitRegionType* 仅在 Abaqus/Explicit 分析期间适用。

*field*

字符串，指定与此交互关联的 [AnalyticalField](pt01ch21pyo02.md) 对象的名称。*field* 参数仅在 *distributionType*=ANALYTICAL_FIELD 时适用。默认值为空字符串。

*distributionType*

 SymbolicConstant，指定如何定义辐射。可能的值为 UNIFORM 和 ANALYTICAL_FIELD。默认值为 UNIFORM。

**返回值**

ConcentratedRadiationToAmbient 对象。

**异常**

无。

### 25.14.2 setValues(...)

此方法修改创建 ConcentratedRadiationToAmbient 对象的步骤中现有 ConcentratedRadiationToAmbient 对象的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ConcentratedRadiationToAmbient](pt01ch25pyo14.md#ker-concentratedradiationtoambient-concentratedradiation-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无