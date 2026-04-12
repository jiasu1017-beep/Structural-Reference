# 5.3 Arrow 对象





Arrow 对象存储箭头注释的视觉设置和位置。

Arrow 对象派生自 [Annotation](pt01ch05pyo01.md) 对象。

**访问**

```
import annotationToolset
mdb.annotations[*name*]
session.odbs[*name*].userData.annotations[*name*]
session.viewports[*name*].annotationsToPlot[*i*]
```

### 5.3.1 Arrow(...)

此方法创建一个 Arrow 对象。

**路径**

```
mdb.Arrow
```

```
session.odbs[*name*].userData.Arrow
```

**必需参数**

*name*

一个 String，指定注释仓库键。

**可选参数**

*startPoint*

一对 Float，指定起点 *X*- 和 *Y*- 相对于 *startAnchor* 的偏移量（以毫米为单位）。默认值为 (0, 0)。

*endPoint*

一对 Float，指定终点 *X*- 和 *Y*- 相对于 *endAnchor* 的偏移量（以毫米为单位）。默认值为 (0, 0)。

*startAnchor*

一个 SymbolicConstant 或 Float 序列，指定一个点。两个 Float 的序列将 *X*- 和 *Y*- 坐标指定为视口宽度和高度的百分比。三个 Float 的序列指定模型坐标系中点的 *X*-、*Y*- 和 *Z*- 坐标。A SymbolicConstant 表示相对位置。可能的值为：
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

*endAnchor*

一个 SymbolicConstant 或 Float 序列，指定一个点。两个 Float 的序列将 *X*- 和 *Y*- 坐标指定为视口宽度和高度的百分比。三个 Float 的序列指定模型坐标系中点的 *X*-、*Y*- 和 *Z*- 坐标。A SymbolicConstant 表示相对位置。可能的值为：
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

*startHeadStyle*

一个 SymbolicConstant，指定起始箭头的样式。可能的值为：
- ARROW
- FILLED_ARROW
- HOLLOW_CIRCLE
- FILLED_CIRCLE
- HOLLOW_DIAMOND
- FILLED_DIAMOND
- HOLLOW_SQUARE
- FILLED_SQUARE
- NONE

默认值为 NONE。

*endHeadStyle*

一个 SymbolicConstant，指定结束箭头的样式。可能的值为：
- ARROW
- FILLED_ARROW
- HOLLOW_ CIRCLE
- FILLED_CIRCLE
- HOLLOW_DIAMOND
- FILLED_DIAMOND
- HOLLOW_SQUARE
- FILLED_SQUARE
- NONE

默认值为 FILLED_ARROW。

*startGap*

一个 Float，指定箭头起点与箭头起始头部之间的距离（以毫米为单位）。默认值为 0.0。

*endGap*

一个 Float，指定箭头终点与箭头结束头部之间的距离（以毫米为单位）。默认值为 0.0。

*color*

一个 String，指定箭头的颜色。可能的字符串值为任何有效颜色。默认值为 "White"。

*lineStyle*

一个 SymbolicConstant，指定箭头的线条样式。可能的值为 SOLID、DASHED、DOTTED 和 DOT_DASH。默认值为 SOLID。

*lineThickness*

一个 SymbolicConstant，指定箭头的线条粗细。可能的值为 VERY_THIN、THIN、MEDIUM 和 THICK。默认值为 VERY_THIN。

**返回值**

一个 Arrow 对象。

**异常**

InvalidNameError。

### 5.3.2 translateStartPoint(...)

此方法在视口平面上平移 Arrow 对象的起点。

**必需参数**

无。

**可选参数**

*x*

一个 Float，指定 *X* 方向以毫米为单位的平移量。

*y*

一个 Float，指定 *Y* 方向以毫米为单位的平移量。

**返回值**

无

**异常**

无。

### 5.3.3 translateEndPoint(...)

此方法在视口平面上平移 Arrow 对象的终点。

**必需参数**

无。

**可选参数**

*x*

一个 Float，指定 *X* 方向以毫米为单位的平移量。

*y*

一个 Float，指定 *Y* 方向以毫米为单位的平移量。

**返回值**

无

**异常**

无。

### 5.3.4 setValues(...)

此方法修改 Arrow 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [Arrow](pt01ch05pyo03.md#ker-arrow-arrow-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 5.3.5 成员

Arrow 对象具有与 [Arrow](pt01ch05pyo03.md#ker-arrow-arrow-pyc) 方法参数相同名称和描述的成员。




