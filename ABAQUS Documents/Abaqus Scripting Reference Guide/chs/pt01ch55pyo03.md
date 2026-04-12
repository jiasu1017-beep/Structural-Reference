# 55.3 AreaStyle 对象

AreaStyle 对象用于定义绘制 XY 绘图对象时区域的填充方式。

每当创建 [Area](pt01ch55pyo02.md) 对象时，都会自动创建 AreaStyle 对象。AreaStyle 对象可以使用下面描述的方法创建。

**访问**

```
import visualization
session.charts[*name*].area.style
session.charts[*name*].gridArea.style
session.charts[*name*].legend.area.style
session.charts[*name*].tagAreaStyle
session.defaultChartOptions.areaStyle
session.defaultChartOptions.gridArea.style
session.defaultChartOptions.legend.area.style
session.defaultChartOptions.tagAreaStyle
session.defaultPlot.area.style
session.defaultPlot.title.area.style
session.xyPlots[*name*].area.style
session.xyPlots[*name*].charts[*name*].area.style
session.xyPlots[*name*].charts[*name*].gridArea.style
session.xyPlots[*name*].charts[*name*].legend.area.style
session.xyPlots[*name*].charts[*name*].tagAreaStyle
session.xyPlots[*name*].title.area.style
```

### 55.3.1 AreaStyle(...)

此方法创建 AreaStyle。

**路径**

```
session.AreaStyle
```

```
xyPlot.AreaStyle
```

**必需参数**

无。

**可选参数**

*color*

一个 String，指定使用此 AreaStyle 对象填充区域时要使用的颜色。默认值为 "White"。

*fill*

一个 Boolean，指定使用此 AreaStyle 时是否填充区域。默认值为 ON。

*style*

一个 SymbolicConstant，指定使用此 AreaStyle 填充区域时要使用的区域图案样式。默认值为 SOLID。

**返回值**

AreaStyle 对象。

**异常**

ColorError

### 55.3.2 setValues(...)

此方法修改 AreaStyle 对象。

**必需参数**

无。

**可选参数**

*color*

一个 String，指定使用此 AreaStyle 对象填充区域时要使用的颜色。默认值为 "White"。

*fill*

一个 Boolean，指定使用此 AreaStyle 时是否填充区域。默认值为 ON。

*style*

一个 SymbolicConstant，指定使用此 AreaStyle 填充区域时要使用的区域图案样式。默认值为 SOLID。

**返回值**

无。

**异常**

无。

### 55.3.3 成员

AreaStyle 对象具有与 [setValues](pt01ch55pyo03.md#ker-areastyle-setvalues-pyc) 方法的参数具有相同名称和描述的成员。
