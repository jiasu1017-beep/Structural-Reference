# 55.14 Title 对象







Title 对象用于存储 XYPlot 标题的显示属性。创建 [XYPlot](pt01ch55pyo16.md) 对象时会自动创建 Title 对象。

**访问**

```
import visualization
session.defaultPlot.title
session.xyPlots[*name*].title
```

### 55.14.1 setValues(...)

此方法修改 Title 对象。

**必需参数**

None。

**可选参数**

*title*

一个 Title 对象，从中复制属性。

*text*

一个 String，指定作为标题显示的文本。默认情况下，标题设置为 [XYPlot](pt01ch55pyo16.md) 对象名称。默认值为空字符串。

*area*

一个 [Area](pt01ch55pyo02.md) 对象，指定标题的区域。

*useDefault*

一个 Boolean，指定是否显示默认标题。默认值为 OFF。

*titleStyle*

一个 [TextStyle](pt01ch55pyo13.md) 对象，指定用于显示图例标题的文本属性。

**返回值**

None

**异常**

None。

### 55.14.2 成员

Title 对象可以具有以下成员：

*useDefault*

一个 Boolean，指定是否显示默认标题。默认值为 OFF。

*area*

一个 [Area](pt01ch55pyo02.md) 对象，指定标题的区域。

*text*

一个 String，指定作为标题显示的文本。默认情况下，标题设置为 [XYPlot](pt01ch55pyo16.md) 对象名称。默认值为空字符串。

*titleStyle*

一个 [TextStyle](pt01ch55pyo13.md) 对象，指定用于显示图例标题的文本属性。

