# 5.4 Text 对象





Text 对象存储文本注释的文本设置和位置。

Text 对象派生自 [Annotation](pt01ch05pyo01.md) 对象。

**访问**

```
import annotationToolset
mdb.annotations[*name*]
session.odbs[*name*].userData.annotations[*name*]
session.viewports[*name*].annotationsToPlot[*i*]
```

### 5.4.1 Text(...)

此方法创建一个 Text 对象。

**路径**

```
mdb.Text
```

```
session.odbs[*name*].userData.Text
```

**必需参数**

*name*

一个 String，指定注释仓库键。

**可选参数**

*text*

一个 String，指定 Text 对象的文本。默认值为空字符串。

*offset*

一对 Float，指定 Text 对象相对于 *anchor* 的 *X*- 和 *Y*- 偏移量（以毫米为单位）。默认值为 (0, 0)。

*anchor*

一个 SymbolicConstant 或 Float 序列，指定一个点。两个 Float 的序列将 *X*- 和 *Y* 坐标指定为视口宽度和高度的百分比。三个 Float 的序列指定模型坐标系中点的 *X*-、*Y*- 和 *Z*- 坐标。A SymbolicConstant 指定相对位置。可能的值为：
- BOTTOM_LEFT
- BOTTOM_CENTER
- BOTTOM_RIGHT
- CENTER_LEFT
- CENTER
- CENTER_RIGHT
- TOP_LEFT
- TOP_CENTER
- TOP_RIGHT

默认值为 BOTTOM_LEFT。

*referencePoint*

一个 SymbolicConstant 或 Float 序列，指定一个点。两个 Float 的序列将参考点的 *X*- 和 *Y*- 坐标指定为其宽度和高度的百分比。A SymbolicConstant 表示相对位置。可能的值为：
- BOTTOM_LEFT
- BOTTOM_CENTER
- BOTTOM_RIGHT
- CENTER_LEFT
- CENTER
- CENTER_RIGHT
- TOP_LEFT
- TOP_CENTER
- TOP_RIGHT

默认值为 BOTTOM_LEFT。

*rotationAngle*

一个 Float，指定围绕 *referencePoint* 旋转的角度（以度为单位）。默认值为 0.0。

*color*

一个 String，指定 Text 对象的颜色。可能的字符串值为任何有效颜色。默认值为 "White"。

*font*

一个 String，指定 Text 对象的字体。可能的字符串值为任何有效字体规格。默认值为 "-*-helvetica-medium-r-normal--12-*"。

*backgroundStyle*

一个 SymbolicConstant，指定 Text 对象背景样式。可能的值为 MATCH、TRANSPARENT 和 OTHER。默认值为 TRANSPARENT。

*backgroundColor*

一个 String，指定 Text 对象背景的颜色。可能的字符串值为任何有效颜色。默认值为与视口背景匹配。

*box*

一个 Boolean，指定是否显示文本周围的框。默认值为 OFF。

*justification*

一个 SymbolicConstant，指定多行文本的 Text 对象对齐方式。可能的值为 JUSTIFY_LEFT、JUSTIFY_CENTER 和 JUSTIFY_RIGHT。默认值为 JUSTIFY_LEFT。

**返回值**

一个 Text 对象。

**异常**

无。

### 5.4.2 setValues(...)

此方法修改 Text 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [Text](pt01ch05pyo04.md#ker-text-text-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 5.4.3 成员

Text 对象具有与 [Text](pt01ch05pyo04.md#ker-text-text-pyc) 方法参数相同名称和描述的成员。

此外，Text 对象可以具有以下成员：

*width*

一个 Float，指定 Text 对象的宽度（以毫米为单位）。

*height*

一个 Float，指定 Text 对象的高度（以毫米为单位）。




