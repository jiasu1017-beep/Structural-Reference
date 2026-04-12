# 25.57 RadiationToAmbient 对象

RadiationToAmbient 对象定义表面与其环境之间的辐射热传递。

RadiationToAmbient 对象派生自 [Interaction](pt01ch25pyo01.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.57.1 RadiationToAmbient(...)

此方法创建一个 RadiationToAmbient 对象。

**路径**

```
mdb.models[*name*].RadiationToAmbient
```

**必需参数**

*name*

字符串，指定存储库键。

*createStepName*

字符串，指定创建 RadiationToAmbient 对象的步骤名称。

*surface*

[Region](pt01ch45pyo03.md) 对象，指定应用辐射交互的表面。

*emissivity*

浮点数，指定发射率，![](../graphics/ker_eqn00062.gif)。

**可选参数**

*field*

字符串，指定与此交互关联的 [AnalyticalField](pt01ch21pyo02.md) 对象的名称。*field* 参数仅在 *distributionType*=ANALYTICAL_FIELD 时适用。默认值为空字符串。

*distributionType*

 SymbolicConstant，指定辐射如何分布。此参数仅在 *radiationType*=AMBIENT 时适用。可能的值为 UNIFORM 和 ANALYTICAL_FIELD。默认值为 UNIFORM。

*radiationType*

 SymbolicConstant，指定是使用默认表面辐射行为还是腔体辐射近似。可能的值为 AMBIENT 和 CAVITY。默认值为 AMBIENT。

*ambientTemperature*

浮点数，指定参考环境温度，![](../graphics/ker_eqn00061.gif)。此参数仅在 *radiationType*=AMBIENT 时适用。默认值为 0.0。

*ambientTemperatureAmp*

字符串，指定给出环境温度随时间变化的 [Amplitude](pt01ch03pyo01.md) 对象的名称。

**注：**在 Abaqus/Standard 分析中使用 `None` 可以指定参考环境温度在步骤开始时立即应用或线性跨越步骤应用。在 Abaqus/Explicit 分析中使用 `None` 可以指定参考环境温度在整个步骤中应用。此参数仅在 *radiationType*=AMBIENT 时适用。

**返回值**

RadiationToAmbient 对象。

**异常**

无。

### 25.57.2 setValues(...)

此方法修改创建 RadiationToAmbient 对象的步骤中现有 RadiationToAmbient 对象的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [RadiationToAmbient](pt01ch25pyo57.md#ker-radiationtoambient-radiationtoambient-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 25.57.3 setValuesInStep(...)

此方法修改指定步骤中现有 RadiationToAmbient 对象的传播数据。

**必需参数**

*stepName*

字符串，指定修改交互的步骤名称。

**可选参数**

`setValuesInStep` 的可选参数与 [RadiationToAmbient](pt01ch25pyo57.md#ker-radiationtoambient-radiationtoambient-pyc) 方法的参数相同，但 *name*、*createStepName* 和 *surface* 参数除外。
无。

**返回值**

无。

**异常**

无。

### 25.57.4 成员

RadiationToAmbient 对象的成员与 [RadiationToAmbient](pt01ch25pyo57.md#ker-radiationtoambient-radiationtoambient-pyc) 方法的参数具有相同的名称和描述。





