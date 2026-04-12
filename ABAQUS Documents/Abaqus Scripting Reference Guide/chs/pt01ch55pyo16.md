# 55.16 XYPlot 对象







XYPlot 对象用于显示 [Chart](pt01ch55pyo06.md) 对象。

**访问**

```
import visualization
session.xyPlots[*name*]
```

### 55.16.1 XYPlot(...)

此方法创建空 XYPlot 对象。

**路径**

```
session.XYPlot
```

**必需参数**

*name*

一个 String，指定 XYPlot 对象的名称。

**可选参数**

None。

**返回值**

XYPlot 对象。

**异常**

InvalidNameError。

### 55.16.2 autoColor(...)

此方法使用 xyColors [AutoColors](pt01ch47pyo02.md) 对象定义的调色板分配 XYPlot 中所有曲线的颜色。

**必需参数**

None。

**可选参数**

*lines*

一个 Boolean，定义颜色分配是否影响曲线线条。

*symbols*

一个 Boolean，定义颜色分配是否影响曲线符号。

**返回值**

None

**异常**

None。

### 55.16.3 autoSymbol()

此方法分配 XYPlot 中所有曲线的符号。

**参数**

None。

**返回值**

None

**异常**

None。

### 55.16.4 fitCurves()

此方法重置 XYPlot 对象所有图表的变换。它取消任何缩放或平移操作。

**参数**

None。

**返回值**

None

**异常**

None。

### 55.16.5 next(...)

此方法将活动 [Chart](pt01ch55pyo06.md) 对象的 *transform* 成员恢复到变换列表中的下一个设置。（每个图表存储八个变换的列表。）如果没有下一个变换，则不执行任何操作。

**必需参数**

None。

**可选参数**

*drawImmediately*

一个 Boolean，指定在处理命令后立即刷新视口。这通常仅在编写脚本时使用，期望在脚本完成前显示中间结果。默认值为 False。

**返回值**

None

**异常**

None。

### 55.16.6 previous(...)

此方法将活动 [Chart](pt01ch55pyo06.md) 对象的 *transform* 成员恢复到变换列表中的上一个设置。（每个图表存储八个变换的列表。）如果没有下一个变换，则不执行任何操作。

**必需参数**

None。

**可选参数**

*drawImmediately*

一个 Boolean，指定在处理命令后立即刷新视口。这通常仅在编写脚本时使用，期望在脚本完成前显示中间结果。默认值为 False。

**返回值**

None

**异常**

None。

### 55.16.7 setValues(...)

此方法修改 XYPlot 对象。

**必需参数**

None。

**可选参数**

*title*

一个 [Title](pt01ch55pyo14.md) 对象，指定 XYPlot 对象的标题。

*transform*

一个 Float 序列，指定用于沿 XYPlot 活动 [Chart](pt01ch55pyo06.md) 对象的轴缩放或平移的变换矩阵。

**返回值**

None

**异常**

None。

### 55.16.8 成员

XYPlot 对象具有与 [XYPlot](pt01ch55pyo16.md#ker-xyplot-xyplot-pyc) 方法的参数具有相同名称和描述的成员。

此外，XYPlot 对象可以具有以下成员：

*area*

一个 [Area](pt01ch55pyo02.md) 对象，指定 XYPlot 对象的位置、填充、背景和边框。

*title*

一个 [Title](pt01ch55pyo14.md) 对象，指定 XYPlot 对象的标题。

*charts*

一个 [Chart](pt01ch55pyo06.md) 对象 repository。

*curves*

一个 [XYCurve](pt01ch55pyo15.md) 对象 repository。

*transform*

一个 Float 元组，指定用于沿 XYPlot 活动 [Chart](pt01ch55pyo06.md) 对象的轴缩放或平移的变换矩阵。

