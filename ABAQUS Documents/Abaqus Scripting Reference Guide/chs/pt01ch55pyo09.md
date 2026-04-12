# 55.9 Legend 对象







Legend 对象用于存储图表图例的显示属性。创建 [Chart](pt01ch55pyo06.md) 对象时会自动创建 Legend 对象。

**访问**

```
import visualization
session.charts[*name*].legend
session.defaultChartOptions.legend
session.xyPlots[*name*].charts[*name*].legend
```

### 55.9.1 setValues(...)

此方法修改 Legend 对象。

**必需参数**

None。

**可选参数**

*legend*

一个 Legend 对象，从中复制属性。

*show*

一个 Boolean，指定是否显示图例。默认值为 ON。

*showMinMax*

一个 Boolean，指定是否显示最小值和最大值。默认值为 OFF。

*title*

一个 String，指定显示在图例上的标题。默认值为空字符串。

*numberFormat*

一个 SymbolicConstant，指定最小值和最大值的格式。可能的值为 AUTOMATIC、DECIMAL、SCIENTIFIC 和 ENGINEERING。默认值为 AUTOMATIC。

*numDigits*

一个 Int，指定显示最小值和最大值有效数字位数。可能的值为 1 到 7。默认值为 2。

*textStyle*

一个 [TextStyle](pt01ch55pyo13.md) 对象，指定用于显示图例文本的文本属性。

*titleStyle*

一个 [TextStyle](pt01ch55pyo13.md) 对象，指定用于显示图例标题的文本属性。

**返回值**

None

**异常**

None。

### 55.9.2 成员

Legend 对象可以具有以下成员：

*numberFormat*

一个 SymbolicConstant，指定最小值和最大值的格式。可能的值为 AUTOMATIC、DECIMAL、SCIENTIFIC 和 ENGINEERING。默认值为 AUTOMATIC。

*numDigits*

一个 Int，指定显示最小值和最大值有效数字位数。可能的值为 1 到 7。默认值为 2。

*show*

一个 Boolean，指定是否显示图例。默认值为 ON。

*showMinMax*

一个 Boolean，指定是否显示最小值和最大值。默认值为 OFF。

*area*

一个 [Area](pt01ch55pyo02.md) 对象，指定图例的区域。

*textStyle*

一个 [TextStyle](pt01ch55pyo13.md) 对象，指定用于显示图例文本的文本属性。

*title*

一个 String，指定显示在图例上的标题。默认值为空字符串。

*titleStyle*

一个 [TextStyle](pt01ch55pyo13.md) 对象，指定用于显示图例标题的文本属性。

