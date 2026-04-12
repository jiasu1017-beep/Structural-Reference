# 40.3 DGContourOptions 对象

DGContourOptions 对象存储与轮廓图关联的值和属性。DGContourOptions 对象没有构造函数命令。创建显示组实例时，Abaqus 使用 *odbDisplay.contourOptions* 的值创建 *odbDisplayOptions.contourOptions* 成员。

**访问**

```
session.viewports[*name*].assemblyDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions.contourOptions
session.viewports[*name*].layers[*name*].assemblyDisplay\
.displayGroupInstances[*name*].odbDisplayOptions.contourOptions
session.viewports[*name*].layers[*name*].odbDisplay\
.displayGroupInstances[*name*].odbDisplayOptions.contourOptions
session.viewports[*name*].layers[*name*].partDisplay\
.displayGroupInstances[*name*].odbDisplayOptions.contourOptions
session.viewports[*name*].odbDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions.contourOptions
session.viewports[*name*].partDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions.contourOptions
```

### 40.3.1 成员

DGContourOptions 对象可以具有以下成员：

*contourMethod*

 SymbolicConstant，指定轮廓渲染方法。可选值为 TEXTURE_MAPPED 和 TESSELLATED。默认值为 TEXTURE_MAPPED。

*tickmarkPlots*

 Boolean，指定是否在线型单元上显示刻度线图。如果 *tickmarkPlots*=ON，Abaqus 显示刻度线图。如果 *tickmarkPlots*=OFF，Abaqus 在单元面上显示轮廓。默认值为 OFF。

*contourStyle*

 SymbolicConstant，指定轮廓图的间隔样式。可选值为 CONTINUOUS 和 UNIFORM。默认值为 UNIFORM。

*contourEdges*

 Boolean，指定当 *contourType*=BANDED 或 ISOSURFACE 时是否绘制每个轮廓间隔的边缘。默认值为 OFF。

*contourEdgeStyle*

 SymbolicConstant，指定当 *contourType*=BANDED 或 ISOSURFACE 时绘制轮廓边缘使用的边缘线型。可选值为 SOLID、DASHED、DOTTED 和 DOT_DASH。默认值为 SOLID。

*contourEdgeThickness*

 SymbolicConstant，指定当 *contourType*=BANDED 或 ISOSURFACE 时绘制轮廓间隔边缘使用的边缘线宽。可选值为 VERY_THIN、THIN、MEDIUM 和 THICK。默认值为 VERY_THIN。

*averagedOrientationDisplay*

 Boolean，指定平均节点坐标系（用于平均元素向量或张量数据）的显示。默认值为 OFF。

*matchingPlyLabels*

 Boolean，指定匹配层的标签是否显示在视口中。默认值为 OFF。

*colorByMatchingPlies*

 Boolean，指定轮廓颜色是否由匹配层决定。默认值为 OFF。

*tickmarkAxisLength*

 SymbolicConstant，指定刻度线图轴的长度。可选值为 SHORT、MEDIUM 和 LONG。默认值为 MEDIUM。

*tickmarkBaseValue*

 Float，定义刻度线图轴轮廓值的基准轮廓值，该值与单元相交。可能的值为 *autoMinValue* ![](../graphics/ker_eqn00013.gif) *tickmarkBaseValue* ![](../graphics/ker_eqn00013.gif) *autoMaxValue*。默认值为 0.0。

*tickmarkOrientation*

 SymbolicConstant，指定刻度线图的取向。可选值为 N1 和 N2。默认值为 N2。

*edgeColorLine*

 String，指定当 *contourType*=LINE 时使用的边缘颜色。默认值为 "White"。

*edgeColorBandedQuilt*

 String，指定当 *contourType*=BANDED 或 QUILT 时使用的边缘颜色。默认值为 "Black"。

*contourEdgeColor*

 String，指定当 *contourType*=BANDED 或 ISOSURFACE 时绘制轮廓边缘的颜色。默认值为 "Grey60"。

*tickmarkCurveColor*

 String，指定绘制刻度线曲线的颜色。默认值为 "Cyan"。

*intervalLineAttributes*

 SymbolicConstant 元组的元组，指定当 *contourType*=LINE 时图中每个间隔的线型和线宽。外层序列的大小必须等于 *numIntervals*-1。内部序列由两个 SymbolicConstant 组成，指定线型和线宽。可选值请参阅 [DGCommonOptions](pt01ch40pyo02.md) 对象的 *edgeLineStyle* 和 *edgeLineThickness* 成员。默认值为 ((SOLID, VERY_THIN), )。

