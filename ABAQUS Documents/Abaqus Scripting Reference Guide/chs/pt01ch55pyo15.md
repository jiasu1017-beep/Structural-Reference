# 55.13 TextStyle 对象







TextStyle 对象用于存储绘制 XY 绘图文本对象时要使用的文本属性。

创建图表时会自动创建 TextStyle 对象，也可以使用下面描述的方法创建。

**访问**

```
import visualization
session.charts[*name*].axes1[*i*].labelStyle
session.charts[*name*].axes1[*i*].titleStyle
session.charts[*name*].axes2[*i*].labelStyle
session.charts[*name*].axes2[*i*].titleStyle
session.charts[*name*].legend.textStyle
session.charts[*name*].legend.titleStyle
session.charts[*name*].tagTextStyle
session.defaultChartOptions.defaultAxis1Options.labelStyle
session.defaultChartOptions.defaultAxis1Options.titleStyle
session.defaultChartOptions.defaultAxis2Options.labelStyle
session.defaultChartOptions.defaultAxis2Options.titleStyle
session.defaultChartOptions.legend.textStyle
session.defaultChartOptions.legend.titleStyle
session.defaultChartOptions.tagTextStyle
session.defaultPlot.title.titleStyle
session.xyPlots[*name*].charts[*name*].axes1[*i*].labelStyle
session.xyPlots[*name*].charts[*name*].axes1[*i*].titleStyle
session.xyPlots[*name*].charts[*name*].axes2[*i*].labelStyle
session.xyPlots[*name*].charts[*name*].axes2[*i*].titleStyle
session.xyPlots[*name*].charts[*name*].legend.textStyle
session.xyPlots[*name*].charts[*name*].legend.titleStyle
session.xyPlots[*name*].charts[*name*].tagTextStyle
session.xyPlots[*name*].title.titleStyle
```

### 55.13.1 TextStyle(...)

此方法创建 TextStyle。

**路径**

```
session.TextStyle
```

```
xyPlot.TextStyle
```

**必需参数**

None。

**可选参数**

*color*

一个 String，指定使用此 TextStyle 对象绘制文本时要使用的颜色。默认值为 "White"。

*show*

一个 Boolean，指定使用此 TextStyle 对象时是否绘制文本。默认值为 ON。

*font*

一个 String，指定使用此 TextStyle 对象绘制文本时要使用的字体名称。默认值为 "-*-arial-medium-r-normal-*-*-140-*-*-p-*-*-*"。

*rotationAngle*

一个 Float，指定用于显示文本的角度（度）。默认值为 0.0。

**返回值**

TextStyle 对象。

**异常**

ColorError

### 55.13.2 setValues(...)

此方法修改 TextStyle 对象。

**必需参数**

None。

**可选参数**

*color*

一个 String，指定使用此 TextStyle 对象绘制文本时要使用的颜色。默认值为 "White"。

*show*

一个 Boolean，指定使用此 TextStyle 对象时是否绘制文本。默认值为 ON。

*font*

一个 String，指定使用此 TextStyle 对象绘制文本时要使用的字体名称。默认值为 "-*-arial-medium-r-normal-*-*-140-*-*-p-*-*-*"。

*rotationAngle*

一个 Float，指定用于显示文本的角度（度）。默认值为 0.0。

**返回值**

None

**异常**

None。

### 55.13.3 成员

TextStyle 对象具有与 [setValues](pt01ch55pyo13.md#ker-textstyle-setvalues-pyc) 方法的参数具有相同名称和描述的成员。

