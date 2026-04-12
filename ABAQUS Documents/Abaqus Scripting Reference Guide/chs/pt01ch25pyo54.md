# 25.54 PressurePenetration 对象

PressurePenetration 对象定义使用表面到表面接触模拟的压力渗透载荷。

PressurePenetration 对象派生自 [Interaction](pt01ch25pyo01.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.54.1 PressurePenetration(...)

此方法创建一个 PressurePenetration 对象。

**路径**

```
mdb.models[*name*].PressurePenetration
```

**必需参数**

*name*

字符串，指定存储库键。

*createStepName*

字符串，指定创建 PressurePenetration 对象的步骤名称。

*contactInteraction*

字符串，指定表面到表面接触（Standard）交互的名称。

*masterPoints*

[RegionArray](pt01ch45pyo03.md) 对象，指定暴露于流体的主表面上的点。

*slavePoints*

[RegionArray](pt01ch45pyo03.md) 对象，指定暴露于流体的从属表面上的点。

*penetrationPressure*

浮点数元组，指定流体压力大小。对于稳态动态分析，指定流体压力大小的复数元组。

*criticalPressure*

浮点数元组，指定开始发生流体渗透的临界接触压力。

**可选参数**

*amplitude*

字符串或 SymbolicConstant UNSET，指定幅值引用的名称。如果载荷没有幅值引用，则应使用 UNSET。默认值为 UNSET。您应该仅在指定步骤有效时提供 *amplitude* 参数。

*penetrationTime*

浮点数，指定流体压力在当前步骤时间上斜升到当前大小的比例。默认值为 0.001。

**返回值**

PressurePenetration 对象。

**异常**

无。

### 25.54.2 setValues(...)

此方法修改创建 PressurePenetration 对象的步骤中现有 PressurePenetration 对象的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [PressurePenetration](pt01ch25pyo54.md#ker-pressurepenetration-pressurepenetration-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 25.54.3 setValuesInStep(...)

此方法修改指定步骤中现有 PressurePenetration 对象的传播数据。

**必需参数**

*stepName*

字符串，指定修改交互的步骤名称。

**可选参数**

*penetrationPressure*

浮点数元组，指定流体压力大小。对于稳态动态分析，指定流体压力大小的复数元组。

*criticalPressure*

浮点数元组，指定开始发生流体渗透的临界接触压力。

*amplitude*

字符串或 SymbolicConstant，指定幅值引用的名称。 SymbolicConstants 的可能值为 UNCHANGED 和 FREED。UNCHANGED 应在幅值从前一个分析步骤传播时使用。FREED 应在载荷更改为没有幅值引用时使用。您应该仅在指定步骤有效时提供 *amplitude* 参数。

*penetrationTime*

浮点数，指定流体压力在当前步骤时间上斜升到当前大小的比例。默认值为 0.001。

**返回值**

无。

**异常**

无。

### 25.54.4 成员

PressurePenetration 对象具有以下成员：

*name*

字符串，指定存储库键。

*createStepName*

字符串，指定创建 PressurePenetration 对象的步骤名称。

*contactInteraction*

字符串，指定表面到表面接触（Standard）交互的名称。

*masterPoints*

[RegionArray](pt01ch45pyo03.md) 对象，指定暴露于流体的主表面上的点。

*slavePoints*

[RegionArray](pt01ch45pyo03.md) 对象，指定暴露于流体的从属表面上的点。

### 25.54.5 对应的分析关键字

| [*PRESSURE PENETRATION](../key/key-link.md#usb-kws-hpressurepenetration) |
| --- |



