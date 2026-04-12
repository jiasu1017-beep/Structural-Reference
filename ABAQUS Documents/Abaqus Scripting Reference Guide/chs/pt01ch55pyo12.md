# 55.12 SymbolStyle 对象

SymbolStyle 对象用于定义绘制曲线时要使用的标记属性。

SymbolStyle 对象可以使用下面描述的方法创建。

**访问**

```
import visualization
session.charts[*name*].axes1[*i*].axisData.curves[*i*].symbolStyle
session.charts[*name*].axes2[*i*].axisData.curves[*i*].symbolStyle
session.charts[*name*].curves[*name*].symbolStyle
session.curves[*name*].symbolStyle
session.defaultChartOptions.defaultAxis1Options.axisData.curves[*i*]\
.symbolStyle
session.defaultChartOptions.defaultAxis2Options.axisData.curves[*i*]\
.symbolStyle
session.xyPlots[*name*].charts[*name*].axes1[*i*].axisData.curves[*i*]\
.symbolStyle
session.xyPlots[*name*].charts[*name*].axes2[*i*].axisData.curves[*i*]\
.symbolStyle
session.xyPlots[*name*].charts[*name*].curves[*name*].symbolStyle
session.xyPlots[*name*].curves[*name*].symbolStyle
```

### 55.12.1 SymbolStyle(...)

此方法创建 SymbolStyle 对象。

**路径**

```
session.SymbolStyle
```

```
xyPlot.SymbolStyle
```

**必需参数**

无。

**可选参数**

*color*

一个 String，指定使用此 SymbolStyle 对象绘制标记时要使用的颜色。默认值为 "White"。

*show*

一个 Boolean，指定使用此 SymbolStyle 对象时是否绘制标记。默认值为 ON。

*marker*

一个 SymbolicConstant，指定使用此 SymbolStyle 绘制符号时要使用的标记类型。可能的值为：
- FILLED_CIRCLE
- FILLED_SQUARE
- FILLED_DIAMOND
- FILLED_TRI
- HOLLOW_CIRCLE
- HOLLOW_SQUARE
- HOLLOW_DIAMOND
- HOLLOW_TRI
- CROSS
- XMARKER
- POINT

默认值为 FILLED_CIRCLE。

*size*

一个 Float，指定使用此 SymbolStyle 对象绘制标记时要使用的标记大小。默认值为 2.0。

**返回值**

SymbolStyle 对象。

**异常**

ColorError

### 55.12.2 setValues(...)

此方法修改 SymbolStyle 对象。

**必需参数**

无。

**可选参数**

*color*

一个 String，指定使用此 SymbolStyle 对象绘制标记时要使用的颜色。默认值为 "White"。

*show*

一个 Boolean，指定使用此 SymbolStyle 对象时是否绘制标记。默认值为 ON。

*marker*

一个 SymbolicConstant，指定使用此 SymbolStyle 绘制符号时要使用的标记类型。可能的值为：
- FILLED_CIRCLE
- FILLED_SQUARE
- FILLED_DIAMOND
- FILLED_TRI
- HOLLOW_CIRCLE
- HOLLOW_SQUARE
- HOLLOW_DIAMOND
- HOLLOW_TRI
- CROSS
- XMARKER
- POINT

默认值为 FILLED_CIRCLE。

*size*

一个 Float，指定使用此 SymbolStyle 对象绘制标记时要使用的标记大小。默认值为 2.0。

**返回值**

无。

**异常**

无。

### 55.12.3 成员

SymbolStyle 对象具有与 [setValues](pt01ch55pyo12.md#ker-symbolstyle-setvalues-pyc) 方法的参数具有相同名称和描述的成员。
