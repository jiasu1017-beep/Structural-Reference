# 55.7 DefaultChartOptions 对象

DefaultChartOptions 对象用于保存默认图表和轴属性。DefaultChartOptions 对象属性在创建 Chart 或 Axis 时使用。打开会话时自动创建 DefaultChartOptions 对象。

**访问**

```
import visualization
session.defaultChartOptions
```

### 55.7.1 setValues(...)

此方法修改 DefaultChartOptions 对象。

**必需参数**

无。

**可选参数**

*areaStyle*

一个 [AreaStyle](pt01ch55pyo03.md) 对象，指定用于保存图表区域默认显示属性的 [AreaStyle](pt01ch55pyo03.md)。

*aspectRatio*

一个 Float，指定网格区域的默认纵横比。值为 -1 指定 gridArea 将占用所有可用空间。默认值为 1。

*defaultAxis1Options*

一个 [Axis](pt01ch55pyo04.md) 对象，指定用于保存方向 1 轴默认属性的 [Axis](pt01ch55pyo04.md) 对象——对于 Cartesian 图表为横坐标。

*defaultAxis2Options*

一个 [Axis](pt01ch55pyo04.md) 对象，指定用于保存方向 2 轴默认属性的 [Axis](pt01ch55pyo04.md) 对象——对于 Cartesian 图表为纵坐标。

*gridArea*

一个 [Area](pt01ch55pyo02.md) 对象，指定默认显示网格区域的方式。

*legend*

一个 [Legend](pt01ch55pyo09.md) 对象，指定图表图例的默认属性。

*majorAxis1GridStyle*

一个 [LineStyle](pt01ch55pyo10.md) 对象，指定绘制轴 1 方向主网格线时要使用的默认线条属性。

*majorAxis2GridStyle*

一个 [LineStyle](pt01ch55pyo10.md) 对象，指定绘制轴 2 方向主网格线时要使用的默认线条属性。

*minorAxis1GridStyle*

一个 [LineStyle](pt01ch55pyo10.md) 对象，指定绘制轴 1 方向次网格线时要使用的默认线条属性。

*minorAxis2GridStyle*

一个 [LineStyle](pt01ch55pyo10.md) 对象，指定绘制轴 2 方向次网格线时要使用的默认线条属性。

*tagAreaStyle*

一个 [AreaStyle](pt01ch55pyo03.md) 对象，指定创建标签时要使用的默认区域属性。

*tagBorder*

一个 [LineStyle](pt01ch55pyo10.md) 对象，指定创建标签时要使用的默认标签区域边框属性。

*tagTextStyle*

一个 [TextStyle](pt01ch55pyo13.md) 对象，指定创建标签时要使用的默认文本属性。

*useQuantityType*

一个 Boolean，指定是否使用 [QuantityType](pt01ch55pyo11.md) 将曲线与轴关联。默认值为 ON。

**返回值**

无。

**异常**

无。

### 55.7.2 成员

DefaultChartOptions 对象具有与 [setValues](pt01ch55pyo07.md#ker-defaultchartoptions-setvalues-pyc) 方法的参数具有相同名称和描述的成员。
