# 40.22 DGSuperimposeOptions 对象

DGSuperimposeOptions 对象存储与未变形形状关联的值和属性，当显示包含变形形状和未变形形状时。DGSuperimposeOptions 对象没有构造函数命令。创建显示组实例时，Abaqus 使用 *odbDisplay.superimposeOptions* 的值创建 *odbDisplayOptions.superimposeOptions* 成员。

**访问**

```
session.viewports[*name*].assemblyDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions.superimposeOptions
session.viewports[*name*].layers[*name*].assemblyDisplay\
.displayGroupInstances[*name*].odbDisplayOptions.superimposeOptions
session.viewports[*name*].layers[*name*].odbDisplay\
.displayGroupInstances[*name*].odbDisplayOptions.superimposeOptions
session.viewports[*name*].layers[*name*].partDisplay\
.displayGroupInstances[*name*].odbDisplayOptions.superimposeOptions
session.viewports[*name*].odbDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions.superimposeOptions
session.viewports[*name*].partDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions.superimposeOptions
```

### 40.22.1 成员

DGSuperimposeOptions 对象可以具有以下成员：

*renderStyle*

 SymbolicConstant，指定绘图的渲染样式。可选值为 WIREFRAME、FILLED、HIDDEN 和 SHADED。默认值为 WIREFRAME。

*visibleEdges*

 SymbolicConstant，指定要绘制的边缘。可选值为 ALL、EXTERIOR、FEATURE、FREE 和 NONE。默认值为 FEATURE。

 仅当 *renderStyle*=SHADED 时才能使用 NONE。

*edgeLineStyle*

 SymbolicConstant，指定边缘线型。可选值为 SOLID、DASHED、DOTTED 和 DOT_DASH。默认值为 SOLID。

*edgeLineThickness*

 SymbolicConstant，指定边缘线宽。可选值为 VERY_THIN、THIN、MEDIUM 和 THICK。默认值为 VERY_THIN。

*colorCodeOverride*

 Boolean，指定是否允许输出数据库中的颜色编码项覆盖边缘和填充颜色设置。默认值为 ON。

*elemLabels*

 Boolean，指定是否绘制单元标签。默认值为 OFF。

*faceLabels*

 Boolean，指定是否绘制面标签。默认值为 OFF。

*nodeLabels*

 Boolean，指定是否绘制节点标签。默认值为 OFF。

*nodeSymbols*

 Boolean，指定是否绘制节点符号。默认值为 OFF。

*nodeSymbolType*

 SymbolicConstant，指定节点符号类型。可选值为：
- FILLED_CIRCLE
- FILLED_SQUARE
- FILLED_DIAMOND
- FILLED_TRI
- HOLLOW_CIRCLE
- HOLLOW_SQUARE
- HOLLOW_DIAMOND
- HOLLOW_TRI
- CROSS
- XMARKER

默认值为 HOLLOW_CIRCLE。

*nodeSymbolSize*

 SymbolicConstant，指定节点符号大小。可选值为 SMALL、MEDIUM 和 LARGE。默认值为 SMALL。

*elementShrink*

 Boolean，指定单元是否以收缩格式显示。默认值为 OFF。

*elementShrinkFactor*

 Int，指定当 *elementShrink*=ON 时收缩单元的百分比。可能的值为 0![](../graphics/ker_eqn00013.gif) *elementShrinkPercentage* ![](../graphics/ker_eqn00013.gif) 90。默认值为 5。

*coordinateScale*

 Boolean，指定是否缩放坐标。默认值为 OFF。

*normals*

 Boolean，指定是否绘制表示单元和曲面法线方向的箭头。默认值为 OFF。

*normalDisplay*

 SymbolicConstant，指定绘制单元法线还是曲面法线。可选值为 ELEMENT 和 SURFACE。默认值为 ELEMENT。

*normalArrowLength*

 SymbolicConstant，指定法线箭头长度。可选值为 SHORT、MEDIUM 和 LONG。默认值为 MEDIUM。

*normalLineThickness*

 SymbolicConstant，指定法线箭头的粗细。可选值为 VERY_THIN、THIN、MEDIUM 和 THICK。默认值为 VERY_THIN。

*normalArrowheadStyle*

 SymbolicConstant，指定法线箭头的箭头样式。可选值为 NONE、FILLED 和 WIRE。默认值为 WIRE。

*translucency*

 Boolean，指定是否设置半透明度。默认值为 OFF。

*translucencyFactor*

 Float，指定当 *translucency*=ON 时的半透明因子。可能的值为 0.0![](../graphics/ker_eqn00013.gif) *translucencyFactor* ![](../graphics/ker_eqn00013.gif) 1.0。默认值为 0.3。

*edgeColorWireHide*

 String，指定当 *renderStyle*=WIREFRAME 或 HIDDEN 时绘制模型边缘的颜色。默认值为 "Green"。

*edgeColorFillShade*

 String，指定当 *renderStyle*=FILLED 或 SHADED 时绘制模型边缘的颜色。默认值为 "Black"。

*fillColor*

 String，指定当 *renderStyle*=FILLED 或 SHADED 时填充单元的颜色。默认值为 "Green"。

*labelFont*

 String，指定所有模型标签使用的标签字体。默认值为 "-*-courier-medium-r-normal-*-*-120-*-*-m-*-*-*"。

*elemLabelColor*

 String，指定绘制单元标签的颜色。默认值为 "Cyan"。

*faceLabelColor*

 String，指定绘制面标签的颜色。默认值为 "Red"。

*nodeLabelColor*

 String，指定绘制节点标签的颜色。默认值为 "Yellow"。

*nodeSymbolColor*

 String，指定绘制节点符号的颜色。默认值为 "Yellow"。

*faceNormalColor*

 String，指定绘制非梁单元或曲面的法线的颜色。默认值为 "Red"。

*beamN1Color*

 String，指定绘制沿梁 ![](../graphics/ker_eqn00408.gif) 方向的箭头的颜色。默认值为 "Blue"。

*beamN2Color*

 String，指定绘制沿梁 ![](../graphics/ker_eqn00409.gif) 方向的箭头的颜色。默认值为 "Red"。

*beamTangentColor*

 String，指定绘制沿梁切线的箭头的颜色。默认值为 "White"。

*coordinateScaleFactors*

三个 Float 的元组，指定当 *coordinateScale*=ON 时三个坐标方向中的坐标缩放。默认值为 (1, 1, 1)。

