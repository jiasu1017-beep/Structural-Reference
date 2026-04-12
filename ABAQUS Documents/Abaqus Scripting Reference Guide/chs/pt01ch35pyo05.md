# 35.5 DisplayBodyOptions 对象

DisplayBodyOptions 对象存储与所有绘图状态通用的值和属性。DisplayBodyOptions 对象没有构造函数命令。当您导入 Visualization 模块时，Abaqus 会创建 *defaultOdbDisplay.displayBodyOptions* 成员。当创建 [OdbDisplay](pt01ch35pyo01.md) 对象时，Abaqus 会创建 *displayBodyOptions* 成员，使用 *defaultOdbDisplay.displayBodyOptions* 的值。创建视口时，Abaqus 会创建 *odbDisplay* 成员，使用 *defaultOdbDisplay* 的值。

DisplayBodyOptions 对象通过两种方式之一访问：
- 默认显示体选项。创建其他 *displayBodyOptions* 成员时使用这些设置作为默认值。可以设置这些值以自定义用户首选项。
- 与特定视口关联的显示体选项。

DisplayBodyOptions 对象派生自 [DGDisplayBodyOptions](pt01ch40pyo05.md) 对象。

**访问**

```
import visualization
session.defaultOdbDisplay.displayBodyOptions
session.viewports[*name*].assemblyDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions.displayBodyOptions
session.viewports[*name*].layers[*name*].assemblyDisplay\
.displayGroupInstances[*name*].odbDisplayOptions.displayBodyOptions
session.viewports[*name*].layers[*name*].odbDisplay.displayBodyOptions
session.viewports[*name*].layers[*name*].odbDisplay\
.displayGroupInstances[*name*].odbDisplayOptions.displayBodyOptions
session.viewports[*name*].layers[*name*].partDisplay\
.displayGroupInstances[*name*].odbDisplayOptions.displayBodyOptions
session.viewports[*name*].odbDisplay.displayBodyOptions
session.viewports[*name*].odbDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions.displayBodyOptions
session.viewports[*name*].partDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions.displayBodyOptions
```

### 35.5.1 setValues(...)

此方法修改 DisplayBodyOptions 对象。

**必要参数**

无。

**可选参数**

*options*

要从中复制值的 DisplayBodyOptions 对象。如果还向 `setValues` 提供其他参数，它们将覆盖 *options* 中的值。默认值为 `None`。

*visibleEdges*

一个 SymbolicConstant，指定要绘制的边。可能的值为 ALL、EXTERIOR、FEATURE、FREE 和 NONE。默认值为 EXTERIOR。

NONE 仅在 *renderStyle*=SHADED 时可用。

*edgeColorWireHide*

一个字符串，指定当 *renderStyle*=WIREFRAME 或 HIDDEN 时用于绘制模型边的颜色。默认值为 "White"。

*edgeColorFillShade*

一个字符串，指定当 *renderStyle*=FILLED 或 SHADED 时用于绘制模型边的颜色。默认值为 "Black"。

*edgeLineStyle*

一个 SymbolicConstant，指定边线样式。可能的值为 SOLID、DASHED、DOTTED 和 DOT_DASH。默认值为 SOLID。

*edgeLineThickness*

一个 SymbolicConstant，指定边线厚度。可能的值为 VERY_THIN、THIN、MEDIUM 和 THICK。默认值为 VERY_THIN。

*fillColor*

一个字符串，指定当 *renderStyle*=FILLED 或 SHADED 时用于填充单元的颜色。默认值为 "White"。

*colorCodeOverride*

一个布尔值，指定是否允许输出数据库中的颜色编码项目覆盖边和填充颜色设置。默认值为 ON。

*elementShrink*

一个布尔值，指定是否以收缩格式显示单元。默认值为 OFF。

*elementShrinkFactor*

一个整数，指定当 *elementShrink*=ON 时收缩单元的百分比。可能的值为 0![](../graphics/ker_eqn00013.gif) *elementShrinkPercentage* ![](../graphics/ker_eqn00013.gif) 90。默认值为 5。

*coordinateScale*

一个布尔值，指定是否缩放坐标。默认值为 OFF。

*coordinateScaleFactors*

三个浮点数序列，指定当 *coordinateScale*=ON 时在三个坐标方向中的坐标缩放。默认值为 (1, 1, 1)。

*translucency*

一个布尔值，指定是否设置透明度。默认值为 OFF。

*translucencyFactor*

一个 Float，指定当 *translucency*=ON 时的透明度因子。可能的值为 0.0![](../graphics/ker_eqn00013.gif) *translucencyFactor* ![](../graphics/ker_eqn00013.gif) 1.0。默认值为 0.3。

**返回值**

无

**异常**

RangeError。

### 35.5.2 成员

DisplayBodyOptions 对象可以具有以下成员：

*visibleEdges*

一个 SymbolicConstant，指定要绘制的边。可能的值为 ALL、EXTERIOR、FEATURE、FREE 和 NONE。默认值为 EXTERIOR。

NONE 仅在 *renderStyle*=SHADED 时可用。

*edgeLineStyle*

一个 SymbolicConstant，指定边线样式。可能的值为 SOLID、DASHED、DOTTED 和 DOT_DASH。默认值为 SOLID。

*edgeLineThickness*

一个 SymbolicConstant，指定边线厚度。可能的值为 VERY_THIN、THIN、MEDIUM 和 THICK。默认值为 VERY_THIN。

*colorCodeOverride*

一个布尔值，指定是否允许输出数据库中的颜色编码项目覆盖边和填充颜色设置。默认值为 ON。

*elementShrink*

一个布尔值，指定是否以收缩格式显示单元。默认值为 OFF。

*elementShrinkFactor*

一个整数，指定当 *elementShrink*=ON 时收缩单元的百分比。可能的值为 0![](../graphics/ker_eqn00013.gif) *elementShrinkPercentage* ![](../graphics/ker_eqn00013.gif) 90。默认值为 5。

*coordinateScale*

一个布尔值，指定是否缩放坐标。默认值为 OFF。

*translucency*

一个布尔值，指定是否设置透明度。默认值为 OFF。

*translucencyFactor*

一个 Float，指定当 *translucency*=ON 时的透明度因子。可能的值为 0.0![](../graphics/ker_eqn00013.gif) *translucencyFactor* ![](../graphics/ker_eqn00013.gif) 1.0。默认值为 0.3。

*edgeColorWireHide*

一个字符串，指定当 *renderStyle*=WIREFRAME 或 HIDDEN 时用于绘制模型边的颜色。默认值为 "White"。

*edgeColorFillShade*

一个字符串，指定当 *renderStyle*=FILLED 或 SHADED 时用于绘制模型边的颜色。默认值为 "Black"。

*fillColor*

一个字符串，指定当 *renderStyle*=FILLED 或 SHADED 时用于填充单元的颜色。默认值为 "White"。

*coordinateScaleFactors*

三个浮点数元组，指定当 *coordinateScale*=ON 时在三个坐标方向中的坐标缩放。默认值为 (1, 1, 1)。
