# 55.10 LineStyle 对象







LineStyle 对象用于定义绘制 XY 绘图对象时要使用的线条样式。

LineStyle 对象可以使用下面描述的方法创建。

**访问**

```
import visualization
session.charts[*name*].area.border
session.charts[*name*].axes1[*i*].axisData.curves[*i*].lineStyle
session.charts[*name*].axes1[*i*].lineStyle
session.charts[*name*].axes1[*i*].tickStyle
session.charts[*name*].axes2[*i*].axisData.curves[*i*].lineStyle
session.charts[*name*].axes2[*i*].lineStyle
session.charts[*name*].axes2[*i*].tickStyle
session.charts[*name*].curves[*name*].lineStyle
session.charts[*name*].gridArea.border
session.charts[*name*].legend.area.border
session.charts[*name*].majorAxis1GridStyle
session.charts[*name*].majorAxis2GridStyle
session.charts[*name*].minorAxis1GridStyle
session.charts[*name*].minorAxis2GridStyle
session.charts[*name*].tagBorder
session.curves[*name*].lineStyle
session.defaultChartOptions.defaultAxis1Options.axisData.curves[*i*]\
.lineStyle
session.defaultChartOptions.defaultAxis1Options.lineStyle
session.defaultChartOptions.defaultAxis1Options.tickStyle
session.defaultChartOptions.defaultAxis2Options.axisData.curves[*i*]\
.lineStyle
session.defaultChartOptions.defaultAxis2Options.lineStyle
session.defaultChartOptions.defaultAxis2Options.tickStyle
session.defaultChartOptions.gridArea.border
session.defaultChartOptions.legend.area.border
session.defaultChartOptions.majorAxis1GridStyle
session.defaultChartOptions.majorAxis2GridStyle
session.defaultChartOptions.minorAxis1GridStyle
session.defaultChartOptions.minorAxis2GridStyle
session.defaultChartOptions.tagBorder
session.defaultPlot.area.border
session.defaultPlot.title.area.border
session.xyPlots[*name*].area.border
session.xyPlots[*name*].charts[*name*].area.border
session.xyPlots[*name*].charts[*name*].axes1[*i*].axisData.curves[*i*]\
.lineStyle
session.xyPlots[*name*].charts[*name*].axes1[*i*].lineStyle
session.xyPlots[*name*].charts[*name*].axes1[*i*].tickStyle
session.xyPlots[*name*].charts[*name*].axes2[*i*].axisData.curves[*i*]\
.lineStyle
session.xyPlots[*name*].charts[*name*].axes2[*i*].lineStyle
session.xyPlots[*name*].charts[*name*].axes2[*i*].tickStyle
session.xyPlots[*name*].charts[*name*].curves[*name*].lineStyle
session.xyPlots[*name*].charts[*name*].gridArea.border
session.xyPlots[*name*].charts[*name*].legend.area.border
session.xyPlots[*name*].charts[*name*].majorAxis1GridStyle
session.xyPlots[*name*].charts[*name*].majorAxis2GridStyle
session.xyPlots[*name*].charts[*name*].minorAxis1GridStyle
session.xyPlots[*name*].charts[*name*].minorAxis2GridStyle
session.xyPlots[*name*].charts[*name*].tagBorder
session.xyPlots[*name*].curves[*name*].lineStyle
session.xyPlots[*name*].title.area.border
```

### 55.10.1 LineStyle(...)

此方法创建 LineStyle。

**路径**

```
session.LineStyle
```

```
xyPlot.LineStyle
```

**必需参数**

None。

**可选参数**

*color*

一个 String，指定使用此 LineStyle 对象绘制线条时要使用的颜色。默认值为 "White"。

*show*

一个 Boolean，指定使用此 LineStyle 时是否绘制线条。默认值为 ON。

*style*

一个 SymbolicConstant，指定使用此 LineStyle 绘制线条时要使用的线条样式。可能的值为 SOLID、DASHED、DOTTED 和 DOT_DASH。默认值为 SOLID。

*thickness*

一个 Float，指定使用此 LineStyle 绘制线条时要使用的线条厚度（毫米）。默认值为 0.2。

**返回值**

LineStyle 对象。

**异常**

ColorError

### 55.10.2 setValues(...)

此方法修改 LineStyle 对象。

**必需参数**

None。

**可选参数**

*color*

一个 String，指定使用此 LineStyle 对象绘制线条时要使用的颜色。默认值为 "White"。

*show*

一个 Boolean，指定使用此 LineStyle 时是否绘制线条。默认值为 ON。

*style*

一个 SymbolicConstant，指定使用此 LineStyle 绘制线条时要使用的线条样式。可能的值为 SOLID、DASHED、DOTTED 和 DOT_DASH。默认值为 SOLID。

*thickness*

一个 Float，指定使用此 LineStyle 绘制线条时要使用的线条厚度（毫米）。默认值为 0.2。

**返回值**

None

**异常**

None。

### 55.10.3 成员

LineStyle 对象具有与 [setValues](pt01ch55pyo10.md#ker-linestyle-setvalues-pyc) 方法的参数具有相同名称和描述的成员。

