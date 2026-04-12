# 40.5 DGDisplayBodyOptions 对象

DGDisplayBodyOptions 对象存储应用于显示体的值和属性。DGDisplayBodyOptions 对象没有构造函数命令。创建显示组实例时，Abaqus 使用 *odbDisplay.displayBodyOptions* 的值创建 *odbDisplayOptions.displayBodyOptions* 成员。

**访问**

```
session.viewports[*name*].assemblyDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions.displayBodyOptions
session.viewports[*name*].layers[*name*].assemblyDisplay\
.displayGroupInstances[*name*].odbDisplayOptions.displayBodyOptions
session.viewports[*name*].layers[*name*].odbDisplay\
.displayGroupInstances[*name*].odbDisplayOptions.displayBodyOptions
session.viewports[*name*].layers[*name*].partDisplay\
.displayGroupInstances[*name*].odbDisplayOptions.displayBodyOptions
session.viewports[*name*].odbDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions.displayBodyOptions
session.viewports[*name*].partDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions.displayBodyOptions
```

### 40.5.1 成员

DGDisplayBodyOptions 对象可以具有以下成员：

*visibleEdges*

 SymbolicConstant，指定要绘制的边缘。可选值为 ALL、EXTERIOR、FEATURE、FREE 和 NONE。默认值为 EXTERIOR。

 仅当 *renderStyle*=SHADED 时才能使用 NONE。

*edgeLineStyle*

 SymbolicConstant，指定边缘线型。可选值为 SOLID、DASHED、DOTTED 和 DOT_DASH。默认值为 SOLID。

*edgeLineThickness*

 SymbolicConstant，指定边缘线宽。可选值为 VERY_THIN、THIN、MEDIUM 和 THICK。默认值为 VERY_THIN。

*colorCodeOverride*

 Boolean，指定是否允许输出数据库中的颜色编码项覆盖边缘和填充颜色设置。默认值为 ON。

*elementShrink*

 Boolean，指定单元是否以收缩格式显示。默认值为 OFF。

*elementShrinkFactor*

 Int，指定当 *elementShrink*=ON 时收缩单元的百分比。可能的值为 0![](../graphics/ker_eqn00013.gif) *elementShrinkPercentage* ![](../graphics/ker_eqn00013.gif) 90。默认值为 5。

*coordinateScale*

 Boolean，指定是否缩放坐标。默认值为 OFF。

*translucency*

 Boolean，指定是否设置半透明度。默认值为 OFF。

*translucencyFactor*

 Float，指定当 *translucency*=ON 时的半透明因子。可能的值为 0.0![](../graphics/ker_eqn00013.gif) *translucencyFactor* ![](../graphics/ker_eqn00013.gif) 1.0。默认值为 0.3。

*edgeColorWireHide*

 String，指定当 *renderStyle*=WIREFRAME 或 HIDDEN 时绘制模型边缘的颜色。默认值为 "White"。

*edgeColorFillShade*

 String，指定当 *renderStyle*=FILLED 或 SHADED 时绘制模型边缘的颜色。默认值为 "Black"。

*fillColor*

 String，指定当 *renderStyle*=FILLED 或 SHADED 时填充单元的颜色。默认值为 "White"。

*coordinateScaleFactors*

三个 Float 的元组，指定当 *coordinateScale*=ON 时三个坐标方向中的坐标缩放。默认值为 (1, 1, 1)。

