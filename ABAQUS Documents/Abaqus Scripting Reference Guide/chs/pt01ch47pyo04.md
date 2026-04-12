# 47.4 Drawing 对象





Drawing 是几何对象的容器。Drawing 对象存储顶点数据和各种决定如何显示绘制的设置。

**访问**

```
session.drawings[*name*]
```

### 47.4.1 Drawing(...)

此方法创建一个空的 Drawing 对象。

**路径**

```
session.Drawing
```

**必要参数**

*name*

String，指定存储库键。

**可选参数**

无。

**返回值**

Drawing 对象。

**异常**

ValueError。

如果用户尝试使用现有 Drawing 的名称创建新 Drawing：

```
ValueError: There is already a drawing with this name
```

### 47.4.2 setVertices(...)

此方法接受定义 Drawing 对象的顶点数据。它在数组中定义顶点，长度等于 *vertexData* 序列的长度除以 *vertexDimension*。

**必要参数**

*vertexDimension*

Integer，范围为 2 到 4，指定组成单个顶点所需的 Float 值数量。

*vertexData*

Float 值序列，用于组成顶点。每个顶点必须有 *vertexDimension* 个值。

**可选参数**

无。

**返回值**

描述的顶点数量。

**异常**

RangeError。

ValueError。

如果指定了无效的 *vertexDimension*：

```
RangeError: *vertexDimension* must be in the range 2 <= value <= 4
```

如果 *vertexData* 是空序列：

```
ValueError: *vertexData* cannot be empty.
```

如果已调用 `setVertices` 且此次调用发送的顶点较少：

```
ValueError: *vertexData* cannot be reduced
```

### 47.4.3 setNormals(...)

此方法接受每个顶点的法线数据。它在数组中定义法向量，长度等于 *normalData* 序列的长度除以 3。

**必要参数**

*normalData*

Float 值序列，用于组成法线。每个法线必须有 3 个值。

如果只指定一个法线，所有顶点将使用该法线值。

**可选参数**

无。

**返回值**

描述的法线数量。

**异常**

RangeError。

ValueError。

如果 *normalData* 是少于 3 个值的序列：

```
ValueError: *normalData* must have at least three values.
```

如果已调用 `setNormals` 且此次调用发送的值较少：

```
ValueError: *normalData* cannot be reduced.
```

### 47.4.4 setColors(...)

此方法接受每个顶点的颜色数据。它在数组中定义颜色，长度等于 *colorData* 序列的长度除以 *colorDimension*。

**必要参数**

*colorDimension*

Integer，范围为 3 到 4，指定组成单个颜色所需的 Float 值数量。

*colorData*

Float 值序列，范围为 0.0 到 1.0，用于组成颜色。每个颜色必须有 *colorDimension* 个值。第一个颜色将与第一个顶点关联，依此类推。

第一个 Float 将是第一个颜色的红色值。第二个 Float 将是绿色值，第三个将是蓝色值。当 *colorDimension* 为 4 时，第四个 Float 将是第一个颜色的 Alpha 值，但会被忽略。

如果只指定一个颜色，所有顶点将使用该颜色值。

**可选参数**

无。

**返回值**

描述的颜色数量。

**异常**

RangeError。

ValueError。

如果指定了无效的 *colorDimension*：

```
RangeError: *colorDimension* must be in the range 3 <= value <= 4
```

如果 *colorData* 是空序列：

```
ValueError: *colorData* cannot be empty.
```

如果已调用 `setColors` 且此次调用发送的颜色较少：

```
ValueError: *colorData* cannot be reduced
```

### 47.4.5 setEdgeColor(...)

此方法允许在渲染绘制边缘时使用单独的单一颜色。调用后，边缘将使用指定颜色渲染，但面将继续使用 `setColors` 方法中指定的颜色。可以指定空序列以恢复使用颜色数组进行边缘渲染。

**必要参数**

*edgeColor*

0 或 3 个 Float 值的序列，范围为 0.0 到 1.0，用于组成边缘颜色。

如果第一个 Float 值为 -1，则视口背景颜色将用作边缘颜色。

**可选参数**

无。

**返回值**

无

**异常**

ValueError。

如果 *edgeColor* 不是 0 或 3 个 Float 的序列：

```
ValueError: *edgeColor* must be a tuple with 3 values
```

### 47.4.6 setPointColor(...)

此方法允许在渲染绘制点时使用单独的单一颜色。调用后，点将使用指定颜色渲染，但面将继续使用 `setColors` 方法中指定的颜色。可以指定空序列以恢复使用颜色数组进行点渲染。

**必要参数**

*pointColor*

0 或 3 个 Float 值的序列，范围为 0.0 到 1.0，用于组成点颜色。

如果第一个 Float 值为 -1，则视口背景颜色将用作边缘颜色。

**可选参数**

无。

**返回值**

无

**异常**

ValueError。

如果 *pointColor* 不是 0 或 3 个 Float 的序列：

```
ValueError: *pointColor* must be a tuple with 3 values
```

### 47.4.7 addArrayDraw(...)

此方法向绘制添加渲染命令，可以多次调用以添加其他渲染命令。当绘制被 [Viewport](pt01ch11pyo04.md) 引用时，绘制命令用于渲染 Drawing。

渲染命令使用从元素索引 *startIndex* 开始的 *numVertices* 个数组元素构造指定类型的几何图元。

**必要参数**

*type*

SymbolicConstant，指定此命令渲染的几何图元类型。可能的值为 POINTS、LINES、LINE_LOOP、LINE_STRIP、TRIANGLES、TRIANGLE_STRIP、TRIANGLE_FAN、QUADS 和 QUAD_STRIP。

*startIndex*

Integer，指定要渲染的第一个顶点的索引。

*numVertices*

Integer，指定要渲染的顶点总数。

**可选参数**

*polygonMode*

SymbolicConstant，指定此命令渲染多边形几何图元的方式。可能的值为 FILL、EDGES 和 POINTS。默认值为 FILL。

**返回值**

已指定的渲染命令总数。

**异常**

ValueError。

如果 (*startIndex* + *numVertices* - 1) 大于顶点数组的长度：

```
ValueError: Drawing request extends past array size of vertices.
```

如果 (*startIndex* + *numVertices* - 1) 大于法线数组的长度且几何图元需要法线：

```
Drawing request extends past array size of normals.
```

如果 (*startIndex* + *numVertices* - 1) 大于颜色数组的长度且几何图元需要顶点颜色：

```
Drawing request extends past array size of colors.
```

### 47.4.8 addIndexDraw(...)

此方法向绘制添加渲染命令，可以多次调用以添加其他渲染命令。当绘制被 [Viewport](pt01ch11pyo04.md) 引用时，绘制命令用于渲染 Drawing。

渲染命令使用从元素索引 *startIndex* 开始的 *numVertices* 个数组元素构造指定类型的几何图元。

**必要参数**

*type*

SymbolicConstant，指定此命令渲染的几何图元类型。可能的值为 POINTS、LINES、LINE_LOOP、LINE_STRIP、TRIANGLES、TRIANGLE_STRIP、TRIANGLE_FAN、QUADS 和 QUAD_STRIP。

*indices*

Integer 值序列，指定每个要渲染的顶点的索引。

**可选参数**

*polygonMode*

SymbolicConstant，指定此命令渲染多边形几何图元的方式。可能的值为 FILL、EDGES 和 POINTS。默认值为 FILL。

**返回值**

已指定的渲染命令总数。

**异常**

ValueError。

如果 *indices* 序列中的任何值为负数：

```
ValueError: Index values must be positive.
```

如果 *indices* 序列中的任何值大于顶点数组的长度：

```
ValueError: Drawing request extends past array size of vertices.
```

如果 *indices* 序列中的任何值大于法线数组的长度且几何图元需要法线：

```
Drawing request extends past array size of normals.
```

如果 *indices* 序列中的任何值大于颜色数组的长度且几何图元需要顶点颜色：

```
Drawing request extends past array size of colors.
```

### 47.4.9 setValues(...)

此方法修改 Drawing 对象的渲染。

**必要参数**

无。

**可选参数**

*show*

Boolean，指定绘制对象被引用时是否被渲染。默认值为 OFF。

*cullBackfaces*

Boolean，指定是否剔除（不渲染）远离观察者的多边形几何图元。默认值为 OFF。

几何图元的缠绕顺序（而非法线）用于确定其朝向。

*frontFaceOrder*

SymbolicConstant，指定面向观察者的多边形几何图元的缠绕顺序。可能的值为：
- CCW，指定正面缠绕顺序为逆时针。
- CW，指定正面缠绕顺序为顺时针。

默认值为 CCW。

*smoothShade*

Boolean，指定多边形几何图元的光照是针对每个面一致计算还是针对每个显示的像素计算。默认值为 ON。

当为 False 时，每个面只有最后一个法线将用于光照计算。

*edgesInShaded*

Boolean，指定在 FILLED 或 SHADED 显示中是否发出边缘和点绘制命令。默认值为 ON。

如果没有定义边缘或点绘制命令，则多边形绘制命令将以 WIREFRAME 和 HIDDEN_LINE 显示发出，*polygonMode* 设置为 EDGES。如果只定义了边缘和点绘制命令，则 Drawing 不会在 FILLED 或 SHADED 显示中渲染。

*translucency*

Float，指定多边形几何图元的不透明度。可能的值为 0.0 ![](../graphics/ker_eqn00013.gif) *translucency* ![](../graphics/ker_eqn00013.gif) 1.0，其中 0.0 表示完全透明（不可见），1.0 表示不透明。默认值为 1.0。

大于 0.3 的值将导致半透明面在渲染前按深度排序，并具有禁用这些面的双面光照的副作用。

*lineSize*

Float，指定用于渲染边缘的线宽（以毫米为单位）。可能的值为 0.0 ![](../graphics/ker_eqn00013.gif) *lineSize* ![](../graphics/ker_eqn00013.gif) 5.0，其中 0.0 被解释为最细的线。默认值为 0.0。

0.0 值在输出设备上为一个像素。屏幕上一个像素通常可见，但 1200 DPI 打印机上的一个像素可能不清楚。

*pointSize*

Float，指定用于渲染点的点宽（以毫米为单位）。可能的值为 0.0 ![](../graphics/ker_eqn00013.gif) *lineSize* ![](../graphics/ker_eqn00013.gif) 5.0，其中 0.0 被解释为最小的点。默认值为 0.0。

0.0 值在输出设备上为一个像素。屏幕上一个像素通常可见，但 1200 DPI 打印机上的一个像素可能不清楚。

**返回值**

无

**异常**

RangeError。

如果指定了无效的 *translucency* 值：

```
RangeError: *translucency* must be in the range 0.0 <= value <= 1.0
```

如果指定了无效的 *lineSize* 值：

```
RangeError: *lineSize* must be in the range 0.0 <= value <= 5.0
```

如果指定了无效的 *pointSize* 值：

```
RangeError: *pointSize* must be in the range 0.0 <= value <= 5.0
```

### 47.4.10 成员

Drawing 对象的成员与 [Drawing](pt01ch47pyo04.md#ker-drawing-drawing-pyc) 方法的参数具有相同的名称和描述。

此外，Drawing 对象具有以下成员：

*vertexCount*

Int，指定调用 `setVertices` 方法后顶点数组中的顶点数量。默认值为 0。

*normalCount*

Int，指定调用 `setNormals` 方法后法线数组中的法线向量数量。默认值为 0。

*colorCount*

Int，指定调用 `setColors` 方法后颜色数组中的颜色数量。默认值为 0。

*show*

Boolean，指定绘制对象被引用时是否被渲染。默认值为 OFF。

*cullBackfaces*

Boolean，指定是否剔除（不渲染）远离观察者的多边形几何图元。默认值为 OFF。

几何图元的缠绕顺序（而非法线）用于确定其朝向。

*frontFaceOrder*

SymbolicConstant，指定面向观察者的多边形几何图元的缠绕顺序。可能的值为：
- CCW，指定正面缠绕顺序为逆时针。
- CW，指定正面缠绕顺序为顺时针。

默认值为 CCW。

*translucency*

Float，指定多边形几何图元的不透明度。可能的值为 0.0 ![](../graphics/ker_eqn00013.gif) *translucency* ![](../graphics/ker_eqn00013.gif) 1.0，其中 0.0 表示完全透明（不可见），1.0 表示不透明。默认值为 1.0。

大于 0.3 的值将导致半透明面在渲染前按深度排序，并具有禁用这些面的双面光照的副作用。

*lineSize*

Float，指定用于渲染边缘的线宽（以毫米为单位）。可能的值为 0.0 ![](../graphics/ker_eqn00013.gif) *lineSize* ![](../graphics/ker_eqn00013.gif) 5.0，其中 0.0 被解释为最细的线。默认值为 0.0。

0.0 值在输出设备上为一个像素。屏幕上一个像素通常可见，但 1200 DPI 打印机上的一个像素可能不清楚。

*pointSize*

Float，指定用于渲染点的点宽（以毫米为单位）。可能的值为 0.0 ![](../graphics/ker_eqn00013.gif) *lineSize* ![](../graphics/ker_eqn00013.gif) 5.0，其中 0.0 被解释为最小的点。默认值为 0.0。

0.0 值在输出设备上为一个像素。屏幕上一个像素通常可见，但 1200 DPI 打印机上的一个像素可能不清楚。

*smoothShade*

Boolean，指定多边形几何图元的光照是针对每个面一致计算还是针对每个显示的像素计算。默认值为 ON。

当为 False 时，每个面只有最后一个法线将用于光照计算。

*edgesInShaded*

Boolean，指定在 FILLED 或 SHADED 显示中是否发出边缘和点绘制命令。默认值为 ON。

如果没有定义边缘或点绘制命令，则多边形绘制命令将以 WIREFRAME 和 HIDDEN_LINE 显示发出，*polygonMode* 设置为 EDGES。如果只定义了边缘和点绘制命令，则 Drawing 不会在 FILLED 或 SHADED 显示中渲染。

*edgeColor*

三个 Float 的元组，指定边缘颜色的红色、绿色和蓝色分量值。每个分量的可能值在 0.0 到 1.0 之间。

*pointColor*

三个 Float 的元组，指定点颜色的红色、绿色和蓝色分量值。每个分量的可能值在 0.0 到 1.0 之间。


