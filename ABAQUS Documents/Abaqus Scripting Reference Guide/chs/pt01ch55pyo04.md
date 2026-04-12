# 55.4 Axis 对象

Axis 对象用于存储轴的显示属性。将 [XYCurve](pt01ch55pyo15.md) 对象添加到 [Chart](pt01ch55pyo06.md) 对象时，会自动创建 Axis 对象。

**访问**

```
import visualization
session.charts[*name*].axes1[*i*]
session.charts[*name*].axes2[*i*]
session.defaultChartOptions.defaultAxis1Options
session.defaultChartOptions.defaultAxis2Options
session.xyPlots[*name*].charts[*name*].axes1[*i*]
session.xyPlots[*name*].charts[*name*].axes2[*i*]
```

### 55.4.1 setValues(...)

此方法修改 Axis 对象。

**必需参数**

无。

**可选参数**

*axis*

一个 Axis 对象，从中复制属性。

*labelFrequency*

一个 Int，指定标签相对于刻度线的频率。默认值为 1。

*labelPlacement*

一个 SymbolicConstant，指定标签在轴上的放置方式。可能的值为：
- NONE，指定不显示标签。
- INSIDE，指定标签放置在轴的内侧。
- OUTSIDE，指定标签放置在轴的外侧。

默认值为 INSIDE。

*labelStyle*

一个 [TextStyle](pt01ch55pyo13.md) 对象，指定显示轴标签时要使用的文本属性。

*lineStyle*

一个 [LineStyle](pt01ch55pyo10.md) 对象，指定显示轴时要使用的线条属性。

*placement*

一个 SymbolicConstant，指定轴在网格上的放置方式。可能的值为：
- MIN_EDGE，指定轴放置在最小边缘——对于横坐标在底部，对于纵坐标在左侧。
- MAX_EDGE，指定轴放置在最大边缘——对于横坐标在顶部，对于纵坐标在右侧。
- MIN_MAX_EDGE，指定轴放置在最小边缘——对于横坐标在底部，对于纵坐标在左侧——并在最大边缘重复，不带标签和标题。
- CENTER，指定轴放置在网格中心。

默认值为 MIN_MAX_EDGE。

*tickLength*

一个 Float，指定刻度线的长度（毫米）。默认值为 2.0。

*tickPlacement*

一个 SymbolicConstant，指定刻度线在轴上的放置方式。可能的值为：
- NONE，指定不显示刻度线。
- INSIDE，指定刻度线放置在轴的内侧。
- OUTSIDE，指定刻度线放置在轴的外侧。
- ACROSS，指定刻度线穿过轴。

默认值为 INSIDE。

*tickStyle*

一个 [LineStyle](pt01ch55pyo10.md) 对象，指定显示轴刻度线时要使用的线条属性。

*titleStyle*

一个 [TextStyle](pt01ch55pyo13.md) 对象，指定显示轴标题时要使用的文本属性。

**返回值**

无。

**异常**

无。

### 55.4.2 成员

Axis 对象可以具有以下成员：

*labelFrequency*

一个 Int，指定标签相对于刻度线的频率。默认值为 1。

*tickLength*

一个 Float，指定刻度线的长度（毫米）。默认值为 2.0。

*placement*

一个 SymbolicConstant，指定轴在网格上的放置方式。可能的值为：
- MIN_EDGE，指定轴放置在最小边缘——对于横坐标在底部，对于纵坐标在左侧。
- MAX_EDGE，指定轴放置在最大边缘——对于横坐标在顶部，对于纵坐标在右侧。
- MIN_MAX_EDGE，指定轴放置在最小边缘——对于横坐标在底部，对于纵坐标在左侧——并在最大边缘重复，不带标签和标题。
- CENTER，指定轴放置在网格中心。

默认值为 MIN_MAX_EDGE。

*tickPlacement*

一个 SymbolicConstant，指定刻度线在轴上的放置方式。可能的值为：
- NONE，指定不显示刻度线。
- INSIDE，指定刻度线放置在轴的内侧。
- OUTSIDE，指定刻度线放置在轴的外侧。
- ACROSS，指定刻度线穿过轴。

默认值为 INSIDE。

*labelPlacement*

一个 SymbolicConstant，指定标签在轴上的放置方式。可能的值为：
- NONE，指定不显示标签。
- INSIDE，指定标签放置在轴的内侧。
- OUTSIDE，指定标签放置在轴的外侧。

默认值为 INSIDE。

*axisData*

一个 [AxisData](pt01ch55pyo05.md) 对象，指定轴的数值数据。

*lineStyle*

一个 [LineStyle](pt01ch55pyo10.md) 对象，指定显示轴时要使用的线条属性。

*labelStyle*

一个 [TextStyle](pt01ch55pyo13.md) 对象，指定显示轴标签时要使用的文本属性。

*titleStyle*

一个 [TextStyle](pt01ch55pyo13.md) 对象，指定显示轴标题时要使用的文本属性。

*tickStyle*

一个 [LineStyle](pt01ch55pyo10.md) 对象，指定显示轴刻度线时要使用的线条属性。
