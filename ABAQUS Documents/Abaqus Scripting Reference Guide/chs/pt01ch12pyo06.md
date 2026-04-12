# 12.6 ConnectorFailure 对象

ConnectorFailure 对象为连接器相对运动的一个或多个分量定义失效准则。

ConnectorFailure 对象派生自 [ConnectorBehaviorOption](pt01ch12pyo01.md) 对象。

**访问**

```
import section
mdb.models[*name*].sections[*name*].behaviorOptions[*i*]
import odbSection
session.odbs[*name*].sections[*name*].behaviorOptions[*i*]
```

### 12.6.1 ConnectorFailure(...)

此方法为 [ConnectorSection](pt01ch46pyo08.md) 对象创建连接器失效行为选项。

**路径**

```
mdb.models[*name*].sections[*name*].ConnectorFailure
session.odbs[*name*].sections[*name*].ConnectorFailure
```

**必需参数**

无。

**可选参数**

*releaseComponent*

SymbolicConstant ALL 或 Int，指定发生失效的运动分量。如果指定 Int，则只有该运动分量在满足失效准则时失效。如果 *releaseComponent*=ALL，则所有运动分量都失效。默认值为 ALL。

*minMotion*

`None` 或 Float，指定连接器相对位置所有指定分量的下限，或无下限。默认值为 `None`。

*maxMotion*

`None` 或 Float，指定连接器相对位置所有指定分量的上限，或无上限。默认值为 `None`。

*minForce*

`None` 或 Float，指定发生锁定的指定分量方向上力或力矩的下限，或无下限。默认值为 `None`。

*maxForce*

`None` 或 Float，指定发生锁定的指定分量方向上力或力矩的上限，或无上限。默认值为 `None`。

*components*

Int 的序列，指定定义行为的相对运动分量。可能的值为 1 ![](../graphics/ker_eqn00013.gif) *components* ![](../graphics/ker_eqn00013.gif) 6。只能指定可用的分量。默认值为空序列。

**返回值**

ConnectorFailure 对象。

**异常**

ValueError 和 TextError。

### 12.6.2 setValues(...)

此方法修改 ConnectorFailure 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ConnectorFailure](pt01ch12pyo06.md#ker-connectorfailure-connectorfailure-pyc) 方法的参数相同。

**返回值**

无。

**异常**

ValueError。

### 12.6.3 成员

ConnectorFailure 对象的成员与 [ConnectorFailure](pt01ch12pyo06.md#ker-connectorfailure-connectorfailure-pyc) 方法的参数具有相同的名称和描述。

### 12.6.4 对应的分析关键字

| [*CONNECTOR FAILURE](../key/key-link.md#usb-kws-mconnectorfailure) |
| --- |
