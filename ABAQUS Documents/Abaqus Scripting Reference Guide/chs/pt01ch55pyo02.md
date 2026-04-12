# 55.2 Area 对象







Area 对象用于在 XYPlot 中显示矩形区域。Area 对象没有构造函数。每当创建 [XYPlot](pt01ch55pyo16.md)、[Chart](pt01ch55pyo06.md)、PlotTitle 或 Legend 对象时，都会自动创建 Area 对象。

**访问**

```
import visualization
session.charts[*name*].area
session.charts[*name*].gridArea
session.charts[*name*].legend.area
session.defaultChartOptions.gridArea
session.defaultChartOptions.legend.area
session.defaultPlot.area
session.defaultPlot.title.area
session.xyPlots[*name*].area
session.xyPlots[*name*].charts[*name*].area
session.xyPlots[*name*].charts[*name*].gridArea
session.xyPlots[*name*].charts[*name*].legend.area
session.xyPlots[*name*].title.area
```

### 55.2.1 setValues(...)

此方法修改 Area 对象。

**必需参数**

None。

**可选参数**

*area*

一个 Area 对象，从中复制属性。

*style*

一个 [AreaStyle](pt01ch55pyo03.md) 对象。

*border*

一个 [LineStyle](pt01ch55pyo10.md) 对象。

*positionMethod*

一个 SymbolicConstant，指定区域的位置方式。可能的值为 AUTO_ALIGN 和 MANUAL。默认值为 AUTO_ALIGN。

*alignment*

一个 SymbolicConstant，指定当 *positionMethod*=AUTO_ALIGN 时区域在其父区域中的相对位置。可能的值为：
- BOTTOM_LEFT
- BOTTOM_CENTER
- BOTTOM_RIGHT
- CENTER_LEFT
- CENTER
- CENTER_RIGHT
- TOP_LEFT
- TOP_CENTER
- TOP_RIGHT

默认值为 BOTTOM_LEFT。

*sizeMethod*

一个 SymbolicConstant，指定区域大小定义方式。可能的值为 AUTOMATIC 和 MANUAL。默认值为 AUTOMATIC。

*originOffset*

一对 Float，指定原点相对于可用区域的 X 和 Y 偏移量。除非 *positionMethod*=MANUAL，否则忽略 *originOffset* 参数。默认值为 (-1, 0)。每个 float 的有效范围为 (0, 1)。

*widthScale*

一个 Float，指定当 sizeMethod=MANUAL 时相对于可用区域宽度的比例。有效范围为 (0, 1)。默认值为 1.0。

*heightScale*

一个 Float，指定当 *sizeMethod*=MANUAL 时相对于可用区域高度的比例。有效范围为 (0, 1)。默认值为 1.0。

*inset*

一个 Boolean，指定区域是嵌入的还是占用保留区域。默认值为 OFF。

*pl*

一个 Float，指定区域左侧的填充（毫米）。默认值为 1.0。

*pr*

一个 Float，指定区域右侧的填充（毫米）。默认值为 1.0。

*pt*

一个 Float，指定区域顶部的填充（毫米）。默认值为 1.0。

*pb*

一个 Float，指定区域底部的填充（毫米）。默认值为 1.0。

**返回值**

None

**异常**

RangeError。

### 55.2.2 成员

Area 对象可以具有以下成员：

*inset*

一个 Boolean，指定区域是嵌入的还是占用保留区域。默认值为 OFF。

*positionMethod*

一个 SymbolicConstant，指定区域的位置方式。可能的值为 AUTO_ALIGN 和 MANUAL。默认值为 AUTO_ALIGN。

*alignment*

一个 SymbolicConstant，指定当 *positionMethod*=AUTO_ALIGN 时区域在其父区域中的相对位置。可能的值为：
- BOTTOM_LEFT
- BOTTOM_CENTER
- BOTTOM_RIGHT
- CENTER_LEFT
- CENTER
- CENTER_RIGHT
- TOP_LEFT
- TOP_CENTER
- TOP_RIGHT

默认值为 BOTTOM_LEFT。

*sizeMethod*

一个 SymbolicConstant，指定区域大小定义方式。可能的值为 AUTOMATIC 和 MANUAL。默认值为 AUTOMATIC。

*width*

一个 Float，指定区域的宽度（毫米）。默认值为 1.0。

*height*

一个 Float，指定区域的高度（毫米）。默认值为 1.0。

*widthScale*

一个 Float，指定当 sizeMethod=MANUAL 时相对于可用区域宽度的比例。有效范围为 (0, 1)。默认值为 1.0。

*heightScale*

一个 Float，指定当 *sizeMethod*=MANUAL 时相对于可用区域高度的比例。有效范围为 (0, 1)。默认值为 1.0。

*pl*

一个 Float，指定区域左侧的填充（毫米）。默认值为 1.0。

*pr*

一个 Float，指定区域右侧的填充（毫米）。默认值为 1.0。

*pt*

一个 Float，指定区域顶部的填充（毫米）。默认值为 1.0。

*pb*

一个 Float，指定区域底部的填充（毫米）。默认值为 1.0。

*style*

一个 [AreaStyle](pt01ch55pyo03.md) 对象，指定是否以及如何填充区域。

*border*

一个 [LineStyle](pt01ch55pyo10.md) 对象，指定是否以及如何绘制区域的边框。

*origin*

一对 Float，指定相对于 XYPlot 左下角的 X 和 Y 偏移量（毫米）。

*originOffset*

一对 Float，指定原点相对于可用区域的 X 和 Y 偏移量。除非 *positionMethod*=MANUAL，否则忽略 *originOffset* 参数。默认值为 (-1, 0)。每个 float 的有效范围为 (0, 1)。

