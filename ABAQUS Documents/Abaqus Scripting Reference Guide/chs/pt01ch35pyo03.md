# 35.3 ContourOptions 对象

ContourOptions 对象存储与等值线图关联的值和属性。ContourOptions 对象没有构造函数命令。当您导入 Visualization 模块时，Abaqus 会创建 *defaultOdbDisplay.contourOptions* 成员。当创建 [OdbDisplay](pt01ch35pyo01.md) 对象时，Abaqus 会创建 *contourOptions* 成员，使用 *defaultOdbDisplay.contourOptions* 的值。创建视口时，Abaqus 会创建 *odbDisplay* 成员，使用 *defaultOdbDisplay* 的值。

ContourOptions 对象通过两种方式之一访问：
- 默认等值线选项。创建其他 *contourOptions* 成员时使用这些设置作为默认值。可以设置这些值以自定义用户首选项。
- 与特定视口关联的等值线选项。

ContourOptions 对象派生自 [DGContourOptions](pt01ch40pyo03.md) 对象。

**访问**

```
import visualization
session.defaultOdbDisplay.contourOptions
session.viewports[*name*].assemblyDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions.contourOptions
session.viewports[*name*].layers[*name*].assemblyDisplay\
.displayGroupInstances[*name*].odbDisplayOptions.contourOptions
session.viewports[*name*].layers[*name*].odbDisplay.contourOptions
session.viewports[*name*].layers[*name*].odbDisplay\
.displayGroupInstances[*name*].odbDisplayOptions.contourOptions
session.viewports[*name*].layers[*name*].partDisplay\
.displayGroupInstances[*name*].odbDisplayOptions.contourOptions
session.viewports[*name*].odbDisplay.contourOptions
session.viewports[*name*].odbDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions.contourOptions
session.viewports[*name*].partDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions.contourOptions
```

### 35.3.1 setValues(...)

此方法修改 ContourOptions 对象。

**必要参数**

无。

**可选参数**

*options*

要从中复制值的 ContourOptions 对象。如果还向 `setValues` 提供其他参数，它们将覆盖 *options* 中的值。默认值为 `None`。

*contourType*

一个 SymbolicConstant，指定等值线类型。可能的值为 LINE、BANDED、QUILT 和 ISOSURFACE。默认值为 BANDED。

*contourMethod*

一个 SymbolicConstant，指定等值线渲染方法。可能的值为 TEXTURE_MAPPED 和 TESSELLATED。默认值为 TEXTURE_MAPPED。

*tickmarkPlots*

一个布尔值，指定是否在线型单元上显示刻度线图。如果 *tickmarkPlots*=ON，Abaqus 显示刻度线图。如果 *tickmarkPlots*=OFF，Abaqus 在单元面上显示等值线。默认值为 OFF。

*contourStyle*

一个 SymbolicConstant，指定等值线图的间隔样式。可能的值为 CONTINUOUS 和 UNIFORM。默认值为 UNIFORM。

*numIntervals*

一个整数，指定当 *contourStyle*=UNIFORM 时的间隔数。可能的值为 2 ![](../graphics/ker_eqn00013.gif) *numIntervals* ![](../graphics/ker_eqn00013.gif) 24。默认值为 12。

*intervalType*

一个 SymbolicConstant，指定等值线图的间隔类型。可能的值为 UNIFORM、LOG 和 USER_DEFINED。默认值为 UNIFORM。

*intervalValues*

浮点数序列，指定当 *intervalType*=USER_DEFINED 时的间隔值。

*maxAutoCompute*

一个布尔值，指定是否从要绘制等值线的输出数据计算等值线范围最大值。默认值为 ON。

*maxValue*

一个 Float，指定当 *maxAutoCompute*=ON 时在图中使用的等值线范围最大值。默认值为 *autoMaxValue*。

*minAutoCompute*

一个布尔值，指定是否从要绘制等值线的输出数据计算等值线范围最小值。默认值为 ON。

*minValue*

一个 Float，指定当 *maxAutoCompute*=ON 时在图中使用的等值线范围最小值。默认值为 *minAutoValue*。

*animationAutoLimits*

一个 SymbolicConstant，指定自动计算动画等值线限制时使用的方法。当 *minAutoCompute* 和/或 *maxAutoCompute*=True 时，*animationAutoLimits* 将仅影响最小限制和/或最大限制。可能的值为 FIRST_AND_LAST、CURRENT_FRAME、RECOMPUTE_EACH_FRAME 和 ALL_FRAMES。默认值为 ALL_FRAMES。

*edgeColorLine*

一个字符串，指定当 *contourType*=LINE 时使用的边颜色。默认值为 "White"。

*edgeColorBandedQuilt*

一个字符串，指定当 *contourType*=BANDED 或 QUILT 时使用的边颜色。默认值为 "Black"。

*spectrum*

一个字符串，指定等值线图中使用的颜色光谱名称。默认值为 "Rainbow"。

*outsideLimitsMode*

一个 SymbolicConstant，指定超出图的限制的等值线值的颜色。可能的值为 SPECTRUM 和 SPECIFY。

当 *outsideLimitsMode*=SPECTRUM 时，超出图的限制的值使用最大和最小等值线光谱颜色。当 *outsideLimitsMode*=SPECIFY 时，超出图的限制的值使用 *outsideLimitsAboveColor* 和 *outsideLimitsBelowColor* 的值。

*outsideLimitsAboveColor*

一个字符串，指定当 *outsideLimitsMode*=SPECIFY 时超出图的限制的值使用的颜色。默认值为 "Grey80"。

*outsideLimitsBelowColor*

一个字符串，指定当 *outsideLimitsMode*=SPECIFY 时超出图的限制的值使用的颜色。默认值为 "Grey20"。

*intervalLineAttributes*

SymbolicConstant 元组的序列，指定当 *contourType*=LINE 时图中每个间隔的线样式和线厚度。外层序列的大小必须等于 *numIntervals*-1。内层序列由两个 SymbolicConstant 组成，指定线样式和线厚度。可能的值，请参阅 [DGCommonOptions](pt01ch40pyo02.md) 对象的 *edgeLineStyle* 和 *edgeLineThickness* 成员。默认值为 ((SOLID, VERY_THIN), )。

*contourEdges*

一个布尔值，指定当 *contourType*=BANDED 或 ISOSURFACE 时是否绘制每个等值线间隔的边。默认值为 OFF。

*contourEdgeColor*

一个字符串，指定当 *contourType*=BANDED 或 ISOSURFACE 时用于绘制等值线边的颜色。默认值为 "Grey60"。

*contourEdgeStyle*

一个 SymbolicConstant，指定当 *contourType*=BANDED 或 ISOSURFACE 时用于绘制等值线边的边线样式。可能的值为 SOLID、DASHED、DOTTED 和 DOT_DASH。默认值为 SOLID。

*contourEdgeThickness*

一个 SymbolicConstant，指定当 *contourType*=BANDED 或 ISOSURFACE 时用于绘制等值线间隔边的边线厚度。可能的值为 VERY_THIN、THIN、MEDIUM 和 THICK。默认值为 VERY_THIN。

*tickmarkAxisLength*

一个 SymbolicConstant，指定刻度线图轴的长度。可能的值为 SHORT、MEDIUM 和 LONG。默认值为 MEDIUM。

*tickmarkBaseValue*

一个 Float，定义与单元相交的刻度线轴等值线值的基准等值线值。可能的值为 *autoMinValue* ![](../graphics/ker_eqn00013.gif) *tickmarkBaseValue* ![](../graphics/ker_eqn00013.gif) *autoMaxValue*。默认值为 0.0。

*tickmarkOrientation*

一个 SymbolicConstant，指定刻度线图的方向。可能的值为 N1 和 N2。默认值为 N2。

*tickmarkCurveColor*

一个字符串，指定用于绘制刻度曲线的颜色。默认值为 "Cyan"。

*averagedOrientationDisplay*

一个布尔值，指定平均节点坐标系的显示，用于平均元素向量或张量数据。默认值为 OFF。

*extrapolatedAveraging*

一个布尔值，指定是仅使用外推值还是使用平均的外推值自动计算等值线限制。默认值为 OFF。

*showMaxLocation*

一个布尔值，指定是否显示最大值位置。默认值为 OFF。

*showMinLocation*

一个布尔值，指定是否显示最小值位置。默认值为 OFF。

**返回值**

无

**异常**

RangeError。

### 35.3.2 成员

ContourOptions 对象可以具有以下成员：

*contourType*

一个 SymbolicConstant，指定等值线类型。可能的值为 LINE、BANDED、QUILT 和 ISOSURFACE。默认值为 BANDED。

*numIntervals*

一个整数，指定当 *contourStyle*=UNIFORM 时的间隔数。可能的值为 2 ![](../graphics/ker_eqn00013.gif) *numIntervals* ![](../graphics/ker_eqn00013.gif) 24。默认值为 12。

*intervalType*

一个 SymbolicConstant，指定等值线图的间隔类型。可能的值为 UNIFORM、LOG 和 USER_DEFINED。默认值为 UNIFORM。

*maxAutoCompute*

一个布尔值，指定是否从要绘制等值线的输出数据计算等值线范围最大值。默认值为 ON。

*maxValue*

一个 Float，指定当 *maxAutoCompute*=ON 时在图中使用的等值线范围最大值。默认值为 *autoMaxValue*。

*minAutoCompute*

一个布尔值，指定是否从要绘制等值线的输出数据计算等值线范围最小值。默认值为 ON。

*minValue*

一个 Float，指定当 *maxAutoCompute*=ON 时在图中使用的等值线范围最小值。默认值为 *minAutoValue*。

*animationAutoLimits*

一个 SymbolicConstant，指定自动计算动画等值线限制时使用的方法。可能的值为 FIRST_AND_LAST、CURRENT_FRAME、RECOMPUTE_EACH_FRAME 和 ALL_FRAMES。默认值为 ALL_FRAMES。

*outsideLimitsMode*

一个 SymbolicConstant，指定超出图的限制的等值线值的颜色。可能的值为 SPECTRUM 和 SPECIFY。

*extrapolatedAveraging*

一个布尔值，指定是仅使用外推值还是使用平均的外推值自动计算等值线限制。默认值为 OFF。

*showMaxLocation*

一个布尔值，指定是否显示最大值位置。默认值为 OFF。

*showMinLocation*

一个布尔值，指定是否显示最小值位置。默认值为 OFF。

*autoMaxValue*

一个 Float，指定在图中使用的最大值。该值从要绘制等值线的输出数据计算。此值是只读的。

*autoMinValue*

一个 Float，指定在图中使用的最小值。该值从要绘制等值线的输出数据计算。此值是只读的。

*outsideLimitsAboveColor*

一个字符串，指定当 *outsideLimitsMode*=SPECIFY 时超出图的限制的值使用的颜色。默认值为 "Grey80"。

*outsideLimitsBelowColor*

一个字符串，指定当 *outsideLimitsMode*=SPECIFY 时超出图的限制的值使用的颜色。默认值为 "Grey20"。

*spectrum*

一个字符串，指定等值线图中使用的颜色光谱名称。默认值为 "Rainbow"。

*intervalValues*

浮点数元组，指定当 *intervalType*=USER_DEFINED 时的间隔值。

*contourMethod*

一个 SymbolicConstant，指定等值线渲染方法。可能的值为 TEXTURE_MAPPED 和 TESSELLATED。默认值为 TEXTURE_MAPPED。

*tickmarkPlots*

一个布尔值，指定是否在线型单元上显示刻度线图。默认值为 OFF。

*contourStyle*

一个 SymbolicConstant，指定等值线图的间隔样式。可能的值为 CONTINUOUS 和 UNIFORM。默认值为 UNIFORM。

*contourEdges*

一个布尔值，指定当 *contourType*=BANDED 或 ISOSURFACE 时是否绘制每个等值线间隔的边。默认值为 OFF。

*contourEdgeStyle*

一个 SymbolicConstant，指定当 *contourType*=BANDED 或 ISOSURFACE 时用于绘制等值线边的边线样式。可能的值为 SOLID、DASHED、DOTTED 和 DOT_DASH。默认值为 SOLID。

*contourEdgeThickness*

一个 SymbolicConstant，指定当 *contourType*=BANDED 或 ISOSURFACE 时用于绘制等值线间隔边的边线厚度。可能的值为 VERY_THIN、THIN、MEDIUM 和 THICK。默认值为 VERY_THIN。

*averagedOrientationDisplay*

一个布尔值，指定平均节点坐标系的显示，用于平均元素向量或张量数据。默认值为 OFF。

*matchingPlyLabels*

一个布尔值，指定匹配层的标签是否显示在视口中。默认值为 OFF。

*colorByMatchingPlies*

一个布尔值，指定等值线颜色是否由匹配层驱动。默认值为 OFF。

*tickmarkAxisLength*

一个 SymbolicConstant，指定刻度线图轴的长度。可能的值为 SHORT、MEDIUM 和 LONG。默认值为 MEDIUM。

*tickmarkBaseValue*

一个 Float，定义与单元相交的刻度线轴等值线值的基准等值线值。可能的值为 *autoMinValue* ![](../graphics/ker_eqn00013.gif) *tickmarkBaseValue* ![](../graphics/ker_eqn00013.gif) *autoMaxValue*。默认值为 0.0。

*tickmarkOrientation*

一个 SymbolicConstant，指定刻度线图的方向。可能的值为 N1 和 N2。默认值为 N2。

*edgeColorLine*

一个字符串，指定当 *contourType*=LINE 时使用的边颜色。默认值为 "White"。

*edgeColorBandedQuilt*

一个字符串，指定当 *contourType*=BANDED 或 QUILT 时使用的边颜色。默认值为 "Black"。

*contourEdgeColor*

一个字符串，指定当 *contourType*=BANDED 或 ISOSURFACE 时用于绘制等值线边的颜色。默认值为 "Grey60"。

*tickmarkCurveColor*

一个字符串，指定用于绘制刻度曲线的颜色。默认值为 "Cyan"。

*intervalLineAttributes*

SymbolicConstant 元组的元组，指定当 *contourType*=LINE 时图中每个间隔的线样式和线厚度。外层序列的大小必须等于 *numIntervals*-1。内层序列由两个 SymbolicConstant 组成，指定线样式和线厚度。可能的值，请参阅 [DGCommonOptions](pt01ch40pyo02.md) 对象的 *edgeLineStyle* 和 *edgeLineThickness* 成员。默认值为 ((SOLID, VERY_THIN), )。
