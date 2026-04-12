# 25.21 ContactProperty 对象

ContactProperty 对象定义接触交互属性。

ContactProperty 对象派生自 [InteractionProperty](pt01ch25pyo48.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].interactionProperties[*name*]
```

### 25.21.1 ContactProperty(...)

此方法创建一个 ContactProperty 对象。

**路径**

```
mdb.models[*name*].ContactProperty
```

**必需参数**

*name*

字符串，指定交互属性存储库键。

**可选参数**

无。

**返回值**

ContactProperty 对象。

**异常**

无。

### 25.21.2 成员

ContactProperty 对象可以具有以下成员：

*tangentialBehavior*

[ContactTangentialBehavior](pt01ch25pyo25.md) 对象。

*normalBehavior*

[NormalBehavior](pt01ch25pyo53.md) 对象。

*damping*

[ContactDamping](pt01ch25pyo18.md) 对象。

*damage*

[ContactDamage](pt01ch25pyo17.md) 对象。

*fractureCriterion*

[FractureCriterion](pt01ch25pyo40.md) 对象。

*cohesiveBehavior*

[CohesiveBehavior](pt01ch25pyo11.md) 对象。

*thermalConductance*

[ThermalConductance](pt01ch25pyo78.md) 对象。

*heatGeneration*

[GapHeatGeneration](pt01ch25pyo42.md) 对象。

*radiation*

[Radiation](pt01ch25pyo56.md) 对象。

*geometricProperties*

[GeometricProperties](pt01ch25pyo43.md) 对象。

*electricalConductance*

[GapElectricalConductance](pt01ch25pyo41.md) 对象。

### 25.21.3 对应的分析关键字

| [*SURFACE INTERACTION](../key/key-link.md#usb-kws-hsurfaceinteraction) |
| --- |



