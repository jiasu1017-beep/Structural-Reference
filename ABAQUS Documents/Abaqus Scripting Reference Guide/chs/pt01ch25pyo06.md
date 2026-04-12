# 25.6 ActuatorSensorProp 对象

ActuatorSensorProp 对象是交互属性，定义由 [ActuatorSensor](pt01ch25pyo05.md) 对象引用的属性。

ActuatorSensorProp 对象派生自 [InteractionProperty](pt01ch25pyo48.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].interactionProperties[*name*]
```

### 25.6.1 ActuatorSensorProp(...)

此方法创建一个 ActuatorSensorProp 对象。

**路径**

```
mdb.models[*name*].ActuatorSensorProp
```

**必需参数**

*name*

字符串，指定交互属性存储库键。

**可选参数**

*realProperties*

浮点数序列，指定用户子程序 [`UEL`](../sub/sub-link.md#sub-xsl-uel) 使用的 `PROPS` 数组。默认值为空序列。

*integerProperties*

整数序列，指定用户子程序 [`UEL`](../sub/sub-link.md#sub-xsl-uel) 使用的 `JPROPS` 数组。默认值为空序列。

**返回值**

ActuatorSensorProp 对象。

**异常**

无。

### 25.6.2 setValues(...)

此方法修改 ActuatorSensorProp 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ActuatorSensorProp](pt01ch25pyo06.md#ker-actuatorsensorprop-actuatorsensorprop-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

无。

### 25.6.3 成员

ActuatorSensorProp 对象的成员与 [ActuatorSensorProp](pt01ch25pyo06.md#ker-actuatorsensorprop-actuatorsensorprop-pyc) 方法的参数具有相同的名称和描述。

### 25.6.4 对应的分析关键字

| [*UEL PROPERTY](../key/key-link.md#usb-kws-muelproperty) |
| --- |



