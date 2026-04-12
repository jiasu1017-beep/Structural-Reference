# 55.6 Chart 对象

Chart 对象用于显示 [XYCurve](pt01ch55pyo15.md) 对象。创建 [XYPlot](pt01ch55pyo16.md) 对象时会自动创建 Chart 对象。

**访问**

```
import visualization
session.charts[*name*]
session.xyPlots[*name*].charts[*name*]
```

### 55.6.1 autoColor(...)

此方法使用 xyColors 对象定义的调色板分配图表中所有曲线的颜色。

**必需参数**

无。

**可选参数**

*lines*

一个 Boolean，定义颜色分配是否影响曲线线条。

*symbols*

一个 Boolean，定义颜色分配是否影响曲线符号。

**返回值**

无。

**异常**

无。

### 55.6.2 autoSymbol()

此方法分配图表中所有曲线的符号。

**参数**

无。

**返回值**

无。

**异常**

无。

### 55.6.3 fitCurves()

此方法重置图表的变换。它取消任何缩放或平移操作。

**参数**

无。

**返回值**

无。

**异常**

无。

### 55.6.4 getAxis1(...)

此方法返回用于显示由名称或对象指定的 [XYCurve](pt01ch55pyo15.md) 的 Axis1 的 [Axis](pt01ch55pyo04.md) 对象，或用于给定 [QuantityType](pt01ch55pyo11.md) 对象。

**必需参数**

*curve*

与 [Axis](pt01ch55pyo04.md) 对象关联的 [XYCurve](pt01ch55pyo15.md) 的名称或对象。

*quantityType*

与 [Axis](pt01ch55pyo04.md) 对象关联的 [QuantityType](pt01ch55pyo11.md) 对象。

**可选参数**

无。

**返回值**

一个 [Axis](pt01ch55pyo04.md) 对象。

**异常**

如果给定的 [XYCurve](pt01ch55pyo15.md) 未在 Chart 中使用。

XypError: Curve not found:

如果指定了两个参数。

```
TypeError: Specify curve or quantityType; too many arguments; expected 1, got 2.
```

如果给定的 [QuantityType](pt01ch55pyo11.md) 未在 Chart 中使用。

```
ValueError: QuantityType not found
```

### 55.6.5 getAxis2(...)

此方法返回用于显示由名称或对象指定的 [XYCurve](pt01ch55pyo15.md) 的 Axis2 的 [Axis](pt01ch55pyo04.md) 对象，或用于给定 [QuantityType](pt01ch55pyo11.md) 对象。

**必需参数**

*curve*

与 [Axis](pt01ch55pyo04.md) 对象关联的 [XYCurve](pt01ch55pyo15.md) 的名称或对象。

*quantityType*

与 [Axis](pt01ch55pyo04.md) 对象关联的 [QuantityType](pt01ch55pyo11.md) 对象。

**可选参数**

无。

**返回值**

一个 [Axis](pt01ch55pyo04.md) 对象。

**异常**

如果给定的 [XYCurve](pt01ch55pyo15.md) 未在 Chart 中使用。

XypError: Curve not found:

如果指定了两个参数。

```
TypeError: Specify curve or quantityType; too many arguments; expected 1, got 2.
```

如果给定的 [QuantityType](pt01ch55pyo11.md) 未在 Chart 中使用。

```
ValueError: QuantityType not found
```

### 55.6.6 moveAxisUp(...)

此方法在 Chart 的轴序列中向上移动给定 [Axis](pt01ch55pyo04.md) 对象的相对位置。

**必需参数**

*axis*

要移动的 [Axis](pt01ch55pyo04.md) 对象。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 55.6.7 moveAxisDown(...)

此方法在 Chart 的轴序列中向下移动给定 [Axis](pt01ch55pyo04.md) 对象的相对位置。

**必需参数**

*axis*

要移动的 [Axis](pt01ch55pyo04.md) 对象。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 55.6.8 removeCurve(...)

此方法从 Chart 中移除给定的 [XYCurve](pt01ch55pyo15.md)。

**必需参数**

*curve*

要从 Chart 中移除的 XYCurve 名称或 [XYCurve](pt01ch55pyo15.md) 对象或 [XYCurve](pt01ch55pyo15.md) 对象序列。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 55.6.9 setValues(...)

此方法修改 Chart 对象。

**必需参数**

无。

**可选参数**

*chart*

一个 Chart 对象，从中复制属性。

*curvesToPlot*

一个 String 序列，指定要绘制的曲线名称。除此之外，参数也可以是以下之一：
- 一个 String，指定要绘制的曲线名称。
- 一个 [XYCurve](pt01ch55pyo15.md) 对象，指定要绘制的曲线。
- 一个 [XYCurve](pt01ch55pyo15.md) 对象序列，指定要绘制的曲线（如 `curveSet` 方法所返回）。

*aspectRatio*

一个 Float，指定网格区域的纵横比。值为 -1 指定 gridArea 将占用所有可用空间。默认值为 1。

*transform*

一个 Float 序列，指定用于沿 Chart 轴缩放或平移的变换矩阵。

*view*

一个 [View](pt01ch54pyo01.md) 对象。

*useQuantityType*

一个 Boolean，指定是否使用 [QuantityType](pt01ch55pyo11.md) 将曲线与轴关联。默认值为 ON。

**返回值**

无。

**异常**

RangeError。

### 55.6.10 成员

Chart 对象可以具有以下成员：

*name*

一个 String，指定 Chart 对象的名称。

*useQuantityType*

一个 Boolean，指定是否使用 [QuantityType](pt01ch55pyo11.md) 将曲线与轴关联。默认值为 ON。

*aspectRatio*

一个 Float，指定网格区域的纵横比。值为 -1 指定 gridArea 将占用所有可用空间。默认值为 1。

*curves*

一个 [XYCurve](pt01ch55pyo15.md) 对象 repository，指定要在 Chart 中显示的 [XYCurve](pt01ch55pyo15.md) 对象 repository。

*axes1*

一个 [AxisArray](pt01ch55pyo04.md) 对象，指定显示为 axes1 的轴对象的只读序列——对于 Cartesian 图表为横坐标。

*axes2*

一个 [AxisArray](pt01ch55pyo04.md) 对象，指定显示为 axes2 的轴对象的只读序列——对于 Cartesian 图表为纵坐标。

*area*

一个 [Area](pt01ch55pyo02.md) 对象，指定图表的位置、填充、背景和边框。

*gridArea*

一个 [Area](pt01ch55pyo02.md) 对象，指定如何显示网格区域。

*legend*

一个 [Legend](pt01ch55pyo09.md) 对象，指定图表图例的属性。

*majorAxis1GridStyle*

一个 [LineStyle](pt01ch55pyo10.md) 对象，指定绘制轴 1 方向主网格线时要使用的线条属性。

*majorAxis2GridStyle*

一个 [LineStyle](pt01ch55pyo10.md) 对象，指定绘制轴 2 方向主网格线时要使用的线条属性。

*minorAxis1GridStyle*

一个 [LineStyle](pt01ch55pyo10.md) 对象，指定绘制轴 1 方向次网格线时要使用的线条属性。

*minorAxis2GridStyle*

一个 [LineStyle](pt01ch55pyo10.md) 对象，指定绘制轴 2 方向次网格线时要使用的线条属性。

*tagTextStyle*

一个 [TextStyle](pt01ch55pyo13.md) 对象，指定创建标签时要使用的文本属性。

*tagAreaStyle*

一个 [AreaStyle](pt01ch55pyo03.md) 对象，指定创建标签时要使用的区域属性。

*tagBorder*

一个 [LineStyle](pt01ch55pyo10.md) 对象，指定创建标签时要使用的标签区域边框属性。

*transform*

一个 Float 元组，指定用于沿 Chart 轴缩放或平移的变换矩阵。
