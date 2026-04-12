# 55.8 DefaultPlot 对象







DefaultPlot 对象用于保存默认绘图属性。DefaultPlot 对象属性在创建 [XYPlot](pt01ch55pyo16.md) 对象时使用。打开会话时自动创建 DefaultPlot 对象。

**访问**

```
import visualization
session.defaultPlot
```

### 55.8.1 成员

DefaultPlot 对象可以具有以下成员：

*area*

一个 [Area](pt01ch55pyo02.md) 对象，指定用于保存绘图区域默认显示属性的 [Area](pt01ch55pyo02.md)。

*title*

一个 [Title](pt01ch55pyo14.md) 对象，指定用于保存 XY 绘图标题默认属性的 [Title](pt01ch55pyo14.md) 对象。

