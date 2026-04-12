# 17.19 ViewportAnnotationOptions 对象









ViewportAnnotationOptions 对象存储控制如何在特定视口中渲染标注的设置。ViewportAnnotationOptions 对象通过以下两种方式之一访问：
- 默认视口标注。这些设置在创建其他 *viewportAnnotationOptions* 成员时使用，可以设置以自定义用户首选项。
- 与特定视口关联的视口标注。

ViewportAnnotationOptions 对象没有构造函数；Abaqus 在启动会话时创建 *defaultViewportAnnotationOptions* 成员。创建新视口时，设置从当前视口复制。

**访问**

```
session.defaultViewportAnnotationOptions
session.viewports[*name*].viewportAnnotationOptions
```

### 17.19.1 setValues(...)

此方法修改 ViewportAnnotationOptions 对象。

**必需参数**

无。

**可选参数**

*triad*

一个 Boolean，指定是否显示视图方向三角轴。默认值为 ON。

*triadPosition*

一对 Int，指定视图方向三角轴的位置，作为视口大小的百分比。可能的值为 (0, 0) ≤ *triadPosition* ≤ (100, 100)。默认值为 (6, 12)。

*triadColor*

一个 String，指定视图方向三角轴的颜色。可能的值为任何有效颜色。默认值为 "White"。

*triadLabels*

一个 SymbolicConstant，指定视图方向三角轴的标签方式。可能的值为：
- NUMBERS，指定标签轴 1、2、3。
- LETTERS，指定标签轴 X、Y、Z。

默认值为 NUMBERS。

*triadFont*

一个 String，指定视图方向三角轴标签的字体。可能的值为任何有效字体。默认值为 "-*-helvetica-bold-r-normal--12-*"。

*triadSize*

一个 Int，指定每个三角轴的长度，作为视口大小的百分比。可能的值为 1 ≤ *legendDecimalPlaces* ≤ 50。默认值为 4。

*legend*

一个 Boolean，指定是否显示图例。默认值为 ON。

*legendMinMax*

一个 Boolean，指定是否显示 *X–Y* 和等值线图的最小和最大值。默认值为 OFF。

*legendBox*

一个 Boolean，指定是否显示图例外框。默认值为 ON。

*legendDecimalPlaces*

一个 Int，指定图例中显示的小数位数。可能的值为 0 ≤ *legendDecimalPlaces* ≤ 9。默认值为 3。

*legendPosition*

一对 Int，指定图例的位置，作为视口大小的百分比。可能的值为 (0, 0) ≤ *legendPosition* ≤ (100, 100)。默认值为 (2, 98)。

*legendFont*

一个 String，指定图例标签的字体。可能的值为任何有效字体。默认值为 "-*-courier-medium-r-*-*-*-80-*-*-*-*-iso8859-1"。

*legendTextColor*

一个 String，指定图例的颜色。可能的值为任何有效颜色。默认值为 "White"。

*legendBackgroundStyle*

一个 SymbolicConstant，指定图例背景样式。可能的值为 MATCH、TRANSPARENT 和 OTHER。默认值为 TRANSPARENT。

当指定 OTHER 时的默认颜色为背景色（黑色）。

*legendBackgroundColor*

一个 String，指定图例背景的颜色。可能的值为任何有效颜色。初始值与视口背景匹配。

*title*

一个 Boolean，指定是否显示标题块。默认值为 ON。

*titleBox*

一个 Boolean，指定是否显示标题块外框。默认值为 OFF。

*titlePosition*

一对 Int，指定标题块的位置，作为视口大小的百分比。可能的值为 (0, 0) ≤ *titlePosition* ≤ (100, 100)。默认值为 (13, 20)。

*titleFont*

一个 String，指定标题的字体。可能的值为任何有效字体。默认值为 "-*-courier-medium-r-*-*-*-80-*-*-*-*-iso8859-1"。

*titleTextColor*

一个 String，指定标题的颜色。可能的值为任何有效颜色。默认值为 "White"。

*titleBackgroundStyle*

一个 SymbolicConstant，指定标题块背景样式。可能的值为 MATCH、TRANSPARENT 和 OTHER。默认值为 TRANSPARENT。

当指定 OTHER 时的默认颜色为背景色（黑色）。

*titleBackgroundColor*

一个 String，指定标题块背景的颜色。可能的值为任何有效颜色。初始值与视口背景匹配。

*state*

一个 Boolean，指定是否显示状态块。默认值为 ON。

*stateBox*

一个 Boolean，指定是否显示状态块外框。默认值为 OFF。

*statePosition*

一对 Int，指定状态块的位置，作为视口大小的百分比。可能的值为 (0, 0) ≤ *statePosition* ≤ (100, 100)。默认值为 (13, 12)。

*stateFont*

一个 String，指定状态标签的字体。可能的值为任何有效字体。默认值为 "-*-courier-medium-r-*-*-*-80-*-*-*-*-iso8859-1"。

*stateTextColor*

一个 String，指定状态块标签的颜色。可能的值为任何有效颜色。默认值为 "White"。

*stateBackgroundStyle*

一个 SymbolicConstant，指定状态块背景样式。可能的值为 MATCH、TRANSPARENT 和 OTHER。默认值为 TRANSPARENT。

当指定 OTHER 时的默认颜色为背景色（黑色）。

*stateBackgroundColor*

一个 String，指定状态块背景的颜色。可能的值为任何有效颜色。初始值与视口背景匹配。

*compass*

一个 Boolean，指定是否显示 3D 罗盘。默认值为 ON。

*compassScale*

一个 Float，指定视口中 3D 罗盘的相对大小。可能的值为 0.5 ≤ *compassScale* ≤ 2.0。默认值为 0.8。

*compassPrivilegedPlane*

一个 SymbolicConstant，指定将用于 3D 罗盘底座的平面。可能的值为 XYPLANE、XZPLANE 和 YZPLANE。默认值为 XZPLANE。

**返回值**

无

**异常**

RangeError。

### 17.19.2 成员

ViewportAnnotationOptions 对象的成员与 [setValues](pt01ch17pyo19.md#ker-viewportannotationoptions-setvalues-pyc) 方法的参数具有相同的名称和描述。





