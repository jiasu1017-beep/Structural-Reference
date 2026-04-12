# 55.5 AxisData 对象







AxisData 对象用于存储轴的数据属性。创建 [Axis](pt01ch55pyo04.md) 对象时，会自动创建 AxisData 对象。

**访问**

```
import visualization
session.charts[*name*].axes1[*i*].axisData
session.charts[*name*].axes2[*i*].axisData
session.defaultChartOptions.defaultAxis1Options.axisData
session.defaultChartOptions.defaultAxis2Options.axisData
session.xyPlots[*name*].charts[*name*].axes1[*i*].axisData
session.xyPlots[*name*].charts[*name*].axes2[*i*].axisData
```

### 55.5.1 setValues(...)

此方法修改 AxisData 对象。

**必需参数**

None。

**可选参数**

*axisData*

一个 AxisData 对象，从中复制属性。

*labelFormat*

一个 SymbolicConstant，指定刻度标签的格式。可能的值为 AUTOMATIC、DECIMAL、SCIENTIFIC 和 ENGINEERING。默认值为 AUTOMATIC。

*labelNumDigits*

一个 Int，指定显示标签的有效数字位数。可能的值为 1 到 7。默认值为 2。

*scale*

一个 SymbolicConstant，指定轴使用的刻度类型。可能的值为：
- LINEAR，指定刻度线和标签线性分布。
- LOG，指定刻度线和标签对数分布。
- DB，指定刻度线和标签按分贝刻度分布。
- DB2，指定刻度线和标签按 2*分贝刻度分布。

默认值为 LINEAR。

*dbReference*

一个 Float，指定分贝计算的参考值。默认值为 1.0。

*minAutoCompute*

一个 Boolean，指定是否使用轴的自动计算最小值。默认值为 ON。

*minValue*

一个 Float，指定当 *minAutoCompute* 为 false 时的最小值。默认情况下，*minValue* 设置为 *minAutoValue*。

*maxAutoCompute*

一个 Boolean，指定是否使用轴的自动计算最大值。默认值为 ON。

*maxValue*

一个 Float，指定当 *maxAutoCompute* 为 false 时的最大值。默认情况下，*maxValue* 设置为 *maxAutoValue*。

*tickMode*

一个 SymbolicConstant，指定轴使用的刻度类型。可能的值为：
- AUTOCOMPUTE，指定自动计算刻度线和标签。
- INCREMENT，指定刻度线和标签由给定增量定义。
- TOTAL_NUMBER，指定刻度线和标签由总刻度数定义。

默认值为 AUTOCOMPUTE。

*tickIncrement*

一个 Float，指定当 *tickMode* = INCREMENT 时轴上主刻度线的增量。有效值为 0 ![](../graphics/ker_eqn00048.gif) *tickIncrement*。默认基于自动方法和所绘制范围的结果计算。当 *scale* 设置为 LOG 时，tickIncrement 被解释为每十年的值，应在 0.05 到 1 之间。

*tickCount*

一个 Int，指定当 *tickMode* =TOTAL_NUMBER 时轴上的主刻度线数。可能的值为 0 ![](../graphics/ker_eqn00013.gif) *tickCount* ![](../graphics/ker_eqn00013.gif) 30。默认基于轴的范围计算。当 *scale* 设置为 LOG 时，tickCount 被解释为每十年的刻度数，可接受的值为 1、4、8 和 17。

*minorTickCount*

一个 Int，指定主刻度线之间的次刻度线数。可能的值为 0 ![](../graphics/ker_eqn00013.gif) *minorTickCount* ![](../graphics/ker_eqn00013.gif) 20。当 *scale* 设置为 LOG 时，minorTickCount 被解释为每十年的刻度数，限制为 0、1、4、8 和 17。默认值为 1。

*title*

一个 String，指定轴的标题。默认情况下，标题设置为 *systemTitle*。

*useSystemTitle*

一个 Boolean，指定用于轴标题的标题是由系统定义还是由用户定义。默认值为 ON。

**返回值**

None

**异常**

RangeError。

### 55.5.2 成员

AxisData 对象可以具有以下成员：

*dbReference*

一个 Float，指定分贝计算的参考值。默认值为 1.0。

*direction*

一个 SymbolicConstant，指定轴的方向。可能的值为 ABSCISSA 和 ORDINATE。

*labelFormat*

一个 SymbolicConstant，指定刻度标签的格式。可能的值为 AUTOMATIC、DECIMAL、SCIENTIFIC 和 ENGINEERING。默认值为 AUTOMATIC。

*labelNumDigits*

一个 Int，指定显示标签的有效数字位数。可能的值为 1 到 7。默认值为 2。

*maxAutoCompute*

一个 Boolean，指定是否使用轴的自动计算最大值。默认值为 ON。

*maxAutoValue*

一个 Float，指定当 *maxAutoCompute* 为 true 时的最大值。

*maxValue*

一个 Float，指定当 *maxAutoCompute* 为 false 时的最大值。默认情况下，*maxValue* 设置为 *maxAutoValue*。

*maxShownValue*

一个 Float，指定此轴当前显示的最大值。当轴正在被变换（缩放或平移）时，此值与 *maxAutoValue* 或 *maxValue* 不同。

*minAutoCompute*

一个 Boolean，指定是否使用轴的自动计算最小值。默认值为 ON。

*minAutoValue*

一个 Float，指定当 *minAutoCompute* 为 true 时的最小值。

*minValue*

一个 Float，指定当 *minAutoCompute* 为 false 时的最小值。默认情况下，*minValue* 设置为 *minAutoValue*。

*minShownValue*

一个 Float，指定此轴当前显示的最小值。当轴正在被变换（缩放或平移）时，此值与 *minAutoValue* 或 *minValue* 不同。

*minorTickCount*

一个 Int，指定主刻度线之间的次刻度线数。可能的值为 0 ![](../graphics/ker_eqn00013.gif) *minorTickCount* ![](../graphics/ker_eqn00013.gif) 20。当 *scale* 设置为 LOG 时，minorTickCount 被解释为每十年的刻度数，限制为 0、1、4、8 和 17。默认值为 1。

*scale*

一个 SymbolicConstant，指定轴使用的刻度类型。可能的值为：
- LINEAR，指定刻度线和标签线性分布。
- LOG，指定刻度线和标签对数分布。
- DB，指定刻度线和标签按分贝刻度分布。
- DB2，指定刻度线和标签按 2*分贝刻度分布。

默认值为 LINEAR。

*tickMode*

一个 SymbolicConstant，指定轴使用的刻度类型。可能的值为：
- AUTOCOMPUTE，指定自动计算刻度线和标签。
- INCREMENT，指定刻度线和标签由给定增量定义。
- TOTAL_NUMBER，指定刻度线和标签由总刻度数定义。

默认值为 AUTOCOMPUTE。

*tickCount*

一个 Int，指定当 *tickMode* =TOTAL_NUMBER 时轴上的主刻度线数。可能的值为 0 ![](../graphics/ker_eqn00013.gif) *tickCount* ![](../graphics/ker_eqn00013.gif) 30。默认基于轴的范围计算。当 *scale* 设置为 LOG 时，tickCount 被解释为每十年的刻度数，可接受的值为 1、4、8 和 17。

*tickCountShown*

一个 Int，指定有效显示的主刻度数。此值考虑缩放、平移和舍入。

*tickIncrement*

一个 Float，指定当 *tickMode* = INCREMENT 时轴上主刻度线的增量。有效值为 0 ![](../graphics/ker_eqn00048.gif) *tickIncrement*。默认基于自动方法和所绘制范围的结果计算。当 *scale* 设置为 LOG 时，tickIncrement 被解释为每十年的值，应在 0.05 到 1 之间。

*tickIncrementShown*

一个 Float，指定显示的主刻度线的增量。此值考虑缩放/平移。

*useSystemTitle*

一个 Boolean，指定用于轴标题的标题是由系统定义还是由用户定义。默认值为 ON。

*curves*

一个 [XYCurveArray](pt01ch55pyo15.md) 对象，指定与此轴关联的 Curve 对象的只读序列。

*quantityType*

一个 [QuantityType](pt01ch55pyo11.md) 对象，指定数量类型：即此轴所代表数据的物理维度和相关标签。

*tickValues*

一个 Float 元组，指定显示的主刻度值的只读元组。

*tickLabels*

一个 String 元组，指定显示的主刻度标签的只读元组。

*systemTitle*

一个 String，指定系统标题。系统标题基于轴和关联曲线的 *quantityType*。

*title*

一个 String，指定轴的标题。默认情况下，标题设置为 *systemTitle*。

