# 25.37 FluidExchange 对象

FluidExchange 对象用于定义两个流体腔体之间或流体腔体与其环境之间的流体交换。

FluidExchange 对象派生自 [Interaction](pt01ch25pyo01.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.37.1 FluidExchange(...)

此方法创建一个 FluidExchange 对象。

**路径**

```
mdb.models[*name*].FluidExchange
```

**必需参数**

*name*

字符串，指定存储库键。

*createStepName*

字符串，指定创建 FluidExchange 对象的步骤名称。

*firstCavity*

字符串，指定与此交互关联的第一个 [FluidCavity](pt01ch25pyo34.md) 对象。如果 *definition*=TO_ENVIRONMENT，这是指定的唯一腔体。

*interactionProperty*

字符串，指定与此交互关联的 [FluidExchangeProperty](pt01ch25pyo38.md) 对象。

**可选参数**

*definition*

 SymbolicConstant，指定要定义的流体交换类型。可能的值为 TO_ENVIRONMENT 和 BETWEEN_CAVITIES。默认值为 TO_ENVIRONMENT。

*secondCavity*

字符串，指定与此交互关联的第二个 [FluidCavity](pt01ch25pyo34.md) 对象。此参数仅在 *definition*=BETWEEN_CAVITIES 时适用。

*exchangeArea*

浮点数，指定有效交换面积。默认值为 1.0。

**返回值**

FluidExchange 对象。

**异常**

无。

### 25.37.2 setValues(...)

此方法修改 FluidExchange 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [FluidExchange](pt01ch25pyo37.md#ker-fluidexchange-fluidexchange-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 25.37.3 成员

FluidExchange 对象的成员与 [FluidExchange](pt01ch25pyo37.md#ker-fluidexchange-fluidexchange-pyc) 方法的参数具有相同的名称和描述。

### 25.37.4 对应的分析关键字

| [*FLUID EXCHANGE](../key/key-link.md#usb-kws-mfluidexchange) |
| --- |



