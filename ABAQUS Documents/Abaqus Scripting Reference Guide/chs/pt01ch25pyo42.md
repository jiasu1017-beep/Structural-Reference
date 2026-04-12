# 25.42 GapHeatGeneration 对象

GapHeatGeneration 对象为接触交互属性指定热生成。

**访问**

```
import interaction
mdb.models[*name*].interactionProperties[*name*].heatGeneration
```

### 25.42.1 HeatGeneration(...)

此方法创建一个 GapHeatGeneration 对象。

**路径**

```
mdb.models[*name*].interactionProperties[*name*].HeatGeneration
```

**必需参数**

无。

**可选参数**

*conversionFraction*

浮点数，指定由摩擦或电流引起的耗散能转化为热量的比例。默认值为 1.0。

*slaveFraction*

浮点数，指定分配给从属表面的转化热量的比例。默认值为 0.5。

**返回值**

GapHeatGeneration 对象。

**异常**

无。

### 25.42.2 setValues(...)

此方法修改 GapHeatGeneration 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [GapHeatGeneration](pt01ch25pyo42.md#ker-gapheatgeneration-heatgeneration-pyc) 方法的参数相同。

**返回值**

无。

**异常**

无。

### 25.42.3 成员

GapHeatGeneration 对象具有以下成员：

*conversionFraction*

浮点数，指定由摩擦或电流引起的耗散能转化为热量的比例。默认值为 1.0。

*slaveFraction*

浮点数，指定分配给从属表面的转化热量的比例。默认值为 0.5。

### 25.42.4 对应的分析关键字

| [*GAP HEAT GENERATION](../key/key-link.md#usb-kws-mgapheatgener) |
| --- |



