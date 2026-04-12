# 25.5 ActuatorSensor 对象

ActuatorSensor 对象定义单个点致动器，其中致动由用户子程序（[`UEL`](../sub/sub-link.md#sub-xsl-uel)）确定。子程序在同一位置感测致动器的数据。

ActuatorSensor 对象派生自 [Interaction](pt01ch25pyo01.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.5.1 ActuatorSensor(...)

此方法创建一个 ActuatorSensor 对象。

**路径**

```
mdb.models[*name*].ActuatorSensor
```

**必需参数**

*name*

字符串，指定存储库键。

*createStepName*

字符串，指定创建致动器/传感器交互的步骤名称。*createStepName* 必须设置为 'Initial'。

*point*

[Region](pt01ch45pyo03.md) 对象，指定应用约束的点。

*interactionProperty*

字符串，指定与此交互关联的 [ActuatorSensorProp](pt01ch25pyo06.md) 对象。

*noCoordComponents*

整数，指定传递给用户子程序（[`UEL`](../sub/sub-link.md#sub-xsl-uel)）的坐标分量数量。

*unsymm*

布尔值，指定单元矩阵是否对称（ON）或非对称（OFF）。默认值为 OFF。

*noSolutionDepVar*

整数，指定解相关变量的数量。默认值为 0。

*userSubUel*

字符串，指定定义用户元素的用户子程序（[`UEL`](../sub/sub-link.md#sub-xsl-uel)）的名称。

*dof*

字符串，指定自由度，用逗号分隔。

*solutionDepVars*

浮点数序列，指定解相关变量的初始值。

**可选参数**

无。

**返回值**

ActuatorSensor 对象。

**异常**

无。

### 25.5.2 setValues(...)

此方法修改 ActuatorSensor 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ActuatorSensor](pt01ch25pyo05.md#ker-actuatorsensor-actuatorsensor-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 25.5.3 成员

ActuatorSensor 对象的成员与 [ActuatorSensor](pt01ch25pyo05.md#ker-actuatorsensor-actuatorsensor-pyc) 方法的参数具有相同的名称和描述。

### 25.5.4 对应的分析关键字

| [*ELEMENT](../key/key-link.md#usb-kws-melement) |
| --- |
| [*USER ELEMENT](../key/key-link.md#usb-kws-muserelement) |
| [*INITIAL CONDITIONS](../key/key-link.md#usb-kws-minitialcond), TYPE=SOLUTION |



