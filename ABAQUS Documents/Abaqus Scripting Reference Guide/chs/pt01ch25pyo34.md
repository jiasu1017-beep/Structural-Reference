# 25.34 FluidCavity 对象

FluidCavity 对象定义基于表面的腔体。

FluidCavity 对象派生自 [Interaction](pt01ch25pyo01.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.34.1 FluidCavity(...)

此方法创建一个 FluidCavity 对象。

**路径**

```
mdb.models[*name*].FluidCavity
```

**必需参数**

*name*

字符串，指定存储库键。

*createStepName*

字符串，指定创建 FluidCavity 对象的步骤名称。

*cavityPoint*

[Region](pt01ch45pyo03.md) 对象，指定流体腔体参考点。

*cavitySurface*

[Region](pt01ch45pyo03.md) 对象，指定形成流体腔体边界的表面。

*interactionProperty*

字符串，指定与此交互关联的 [FluidCavityProperty](pt01ch25pyo35.md) 对象。

**可选参数**

*ambientPressure*

浮点数，指定环境压力的大小。默认值为 0.0。

*thickness*

浮点数，指定二维模型的表面平面外厚度。此参数仅在使用二维模型时有效。默认值为 1.0。

*useAdiabatic*

布尔值，指定是否假设理想气体的绝热行为。此参数仅在 *interactionProperty* 指定气动定义时有效。默认值为 OFF。

*checkNormals*

布尔值，指定分析是否检查表面法线的一致性。默认值为 ON。

**返回值**

FluidCavity 对象。

**异常**

无。

### 25.34.2 setValues(...)

此方法修改 FluidCavity 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [FluidCavity](pt01ch25pyo34.md#ker-fluidcavity-fluidcavity-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 25.34.3 成员

FluidCavity 对象的成员与 [FluidCavity](pt01ch25pyo34.md#ker-fluidcavity-fluidcavity-pyc) 方法的参数具有相同的名称和描述。

### 25.34.4 对应的分析关键字

| [*FLUID CAVITY](../key/key-link.md#usb-kws-mfluidcavity) |
| --- |



