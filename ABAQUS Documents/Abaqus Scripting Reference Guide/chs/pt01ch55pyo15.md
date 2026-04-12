# 55.15 XYCurve 对象

XYCurve 对象用于绘制 *X–Y* 数据并存储其显示属性。

**访问**

```
import visualization
session.charts[*name*].axes1[*i*].axisData.curves[*i*]
session.charts[*name*].axes2[*i*].axisData.curves[*i*]
session.charts[*name*].curves[*name*]
session.curves[*name*]
session.defaultChartOptions.defaultAxis1Options.axisData.curves[*i*]
session.defaultChartOptions.defaultAxis2Options.axisData.curves[*i*]
session.xyPlots[*name*].charts[*name*].axes1[*i*].axisData.curves[*i*]
session.xyPlots[*name*].charts[*name*].axes2[*i*].axisData.curves[*i*]
session.xyPlots[*name*].charts[*name*].curves[*name*]
session.xyPlots[*name*].curves[*name*]
```

### 55.15.1 Curve(...)

此方法从 [XYData](pt01ch55pyo01.md) 对象创建 XYCurve 对象。

**路径**

```
session.Curve
```

**必需参数**

*name*

一个 String，指定 repository 键。

*data*

一个 [XYData](pt01ch55pyo01.md) 对象，指定曲线的数据。

**可选参数**

无。

**返回值**

XYCurve 对象。

**异常**

InvalidNameError。

### 55.15.2 setValues(...)

此方法修改 XYCurve 对象。

**必需参数**

无。

**可选参数**

*displayTypes*

一个 SymbolicConstants 序列，指定如何显示曲线。可能的值为 LINE 和 SYMBOL。默认值为 (LINE)。

*legendLabel*

一个 String，指定在图例中显示的标签。默认情况下，标签是系统定义的。

*symbolFrequency*

一个 Int，指定绘制标记的频率。可能的值为 *symbolFrequency*  ![](../graphics/ker_eqn00060.gif) 0。如果 *symbolFrequency*=1，则在每个点绘制标记。默认值为 1。

*useDefault*

一个 Boolean，指定是否使用系统提供的图例标签。默认值为 ON。

**返回值**

无。

**异常**

无。

### 55.15.3 成员

XYCurve 对象可以具有以下成员：

*name*

一个 String，指定 repository 键。

*symbolFrequency*

一个 Int，指定绘制标记的频率。可能的值为 *symbolFrequency*  ![](../graphics/ker_eqn00060.gif) 0。如果 *symbolFrequency*=1，则在每个点绘制标记。默认值为 1。

*useDefault*

一个 Boolean，指定是否使用系统提供的图例标签。默认值为 ON。

*legendSource*

一个 SymbolicConstant，指定系统提供的默认图例标签的生成方式。可能的值为 CURVE_LEGEND、CURVE_NAME 和 CURVE_NAME_LEGEND。默认值为 CURVE_LEGEND。

*data*

一个 [XYData](pt01ch55pyo01.md) 对象，指定曲线的数据。

*lineStyle*

一个 [LineStyle](pt01ch55pyo10.md) 对象，指定显示曲线时要使用的线条属性。

*symbolStyle*

一个 [SymbolStyle](pt01ch55pyo12.md) 对象，指定显示曲线时要使用的符号属性。

*legendLabel*

一个 String，指定在图例中显示的标签。默认情况下，标签是系统定义的。

*displayTypes*

一个 SymbolicConstants 元组，指定如何显示曲线。可能的值为 LINE 和 SYMBOL。默认值为 (LINE)。
