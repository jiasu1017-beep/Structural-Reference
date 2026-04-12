# 40.19 OptionArg 对象

OptionArg 对象用作与 viewCutOptions 对象关联的临时对象的值和属性存储。OptionArg 对象只有一个构造函数命令。

**访问**

```
import visualization
session.defaultOdbDisplay.viewCutOptions.aboveOptions
session.defaultOdbDisplay.viewCutOptions.belowOptions
session.defaultOdbDisplay.viewCutOptions.onOptions
session.viewports[*name*].layers[*name*].odbDisplay.viewCutOptions\
.aboveOptions
session.viewports[*name*].layers[*name*].odbDisplay.viewCutOptions\
.belowOptions
session.viewports[*name*].layers[*name*].odbDisplay.viewCutOptions\
.onOptions
session.viewports[*name*].odbDisplay.viewCutOptions.aboveOptions
session.viewports[*name*].odbDisplay.viewCutOptions.belowOptions
session.viewports[*name*].odbDisplay.viewCutOptions.onOptions
```

### 40.19.1 OptionArg(...)

此方法创建 OptionArg 对象。

**Path**

```
visualization.OptionArg
```

**必需参数**

无。

**可选参数**

*renderStyle*

 SymbolicConstant，指定绘图的渲染样式。可选值为 WIREFRAME、FILLED、HIDDEN 和 SHADED。默认值为 WIREFRAME。

*visibleEdges*

 SymbolicConstant，指定要绘制的边缘。可选值为 ALL、EXTERIOR、FEATURE、FREE 和 NONE。默认值为 FEATURE。

 仅当 *renderStyle*=SHADED 时才能使用 NONE。

*edgeColorWireHide*

 String，指定当 *renderStyle*=WIREFRAME 或 HIDDEN 时绘制未变形图形边缘的颜色。默认值为 "Green"。

*edgeColorFillShade*

 String，指定当 *renderStyle*=FILLED 或 SHADED 时绘制未变形图形边缘的颜色。默认值为 "Black"。

*edgeLineStyle*

 SymbolicConstant，指定边缘线型。可选值为 SOLID、DASHED、DOTTED 和 DOT_DASH。默认值为 SOLID。

*edgeLineThickness*

 SymbolicConstant，指定边缘线宽。可选值为 VERY_THIN、THIN、MEDIUM 和 THICK。默认值为 VERY_THIN。

*colorCodeOverride*

 Boolean，指定是否允许输出数据库中的颜色编码项覆盖边缘和填充颜色设置。默认值为 ON。

*fillColor*

 String，指定当 *renderStyle*=FILLED 或 SHADED 时填充单元的颜色。默认值为 "Green"。

*translucency*

 Boolean，指定是否设置半透明度。默认值为 OFF。

*translucencyFactor*

 Float，指定当 *translucency* = ON 时的半透明因子。可能的值为 0.0 ![](../graphics/ker_eqn00013.gif) *translucencyFactor* ![](../graphics/ker_eqn00013.gif) 1.0。默认值为 0.3。

**返回值**

OptionArg 对象。

**异常**

RangeError。

### 40.19.2 成员

OptionArg 对象的成员与 [OptionArg](pt01ch40pyo19.md#ker-optionarg-optionarg-pyc) 方法的参数具有相同的名称和描述。

