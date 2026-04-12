# 11.4 Viewport 对象

视口是应用程序生成的图形的容器。Viewport 对象存储各种设置，这些设置决定如何在该视口中显示对象。

**访问**

```
session.viewports[*name*]
```

### 11.4.1 Viewport(...)

此方法创建具有指定原点和尺寸的 Viewport 对象。

**路径**

```
session.Viewport
```

**必需参数**

*name*

String，指定存储库密钥。

**可选参数**

*origin*

Float 对，指定视口左下角在画布坐标系中的 X 和 Y 坐标（毫米）。默认原点为 (0, 0)。

*width*

Float，指定视口的宽度（毫米）。可能值为 30 ![](../graphics/ker_eqn00013.gif) *width* ![](../graphics/ker_eqn00013.gif) (*maxWidth*)。默认值为 120.0。

**注意：**width 的最大值 (*maxWidth*) 是屏幕宽度（毫米）。

*height*

Float，指定视口的高度（毫米）。此高度包括标题栏。可能值为 30 ![](../graphics/ker_eqn00013.gif) *height* ![](../graphics/ker_eqn00013.gif) (*maxHeight*)。默认值为 80.0。

**注意：**height 的最大值 (*maxHeight*) 是屏幕高度（毫米）。

*border*

Boolean，指定视口边框在打印图像中是否可见。默认值为 ON。

*titleBar*

Boolean，指定视口标题是否应在打印图像中显示。默认值为 ON。

如果 *border* = OFF，则即使 *titleBar* =ON，标题也将不可见。

*titleStyle*

SymbolicConstant，指定要用于视口标题的标题。可能的值为 CUSTOM 和 SYSTEM。默认值为 SYSTEM。

如果 *titleStyle* = CUSTOM，则将使用 *customTitleString*。如果 *titleStyle* = SYSTEM，则将使用系统生成的字符串。

*customTitleString*

String，当 *titleStyle* = CUSTOM 时指定视口标题。默认值为空字符串。

**返回值**

Viewport 对象。

**异常**

RangeError。

如果用户尝试删除唯一视口：

```
SystemError: the current viewport may not be deleted.
```

如果 *width* 超出范围：

```
RangeError: width must be a Float in the range: 30 <= width <= *maxWidth*
```

如果 *height* 超出范围：

```
RangeError: height must be a Float in the range: 30 <= width <= *maxHeight*
```

### 11.4.2 bringToFront()

此方法将 Viewport 对象移到前面。

**参数**

无。

**返回值**

无。

**异常**

无。

### 11.4.3 disableMultipleColors()

此方法禁用使用 `enableMultipleColors` 启用的多重颜色映射应用。

**参数**

无。

**返回值**

无。

**异常**

无。

### 11.4.4 disableRefresh()

此方法禁用 Viewport 刷新。某些需要 Viewport 是最新状态的方法将覆盖此设置。建议谨慎使用此方法。

**参数**

无。

**返回值**

无。

**异常**

无。

### 11.4.5 disableColorCodeUpdates()

此方法禁用由颜色编码引起的 Viewport 更新和内部计算。当颜色编码为 ON 且使用脚本执行需要颜色代码更新的重复操作时，性能提升将显著。当颜色编码为 OFF 时不会有好处。

**参数**

无。

**返回值**

无。

**异常**

无。

### 11.4.6 enableMultipleColors()

此方法启用可以同时应用的多重颜色映射。它还确保在设置 *initialColor* 时正确更新 Viewport。

**参数**

无。

**返回值**

无。

**异常**

无。

### 11.4.7 enableRefresh()

此方法启用使用 `disableRefresh` 禁用的 Viewport 刷新。

**参数**

无。

**返回值**

无。

**异常**

无。

### 11.4.8 enableColorCodeUpdates()

此方法启用使用 `disableColorCodeUpdates` 禁用的 Viewport 颜色代码更新。

**参数**

无。

**返回值**

无。

**异常**

无。

### 11.4.9 getActiveElementLabels(...)

此方法返回基于当前显示组且可选地基于任何活动切割（如果 *useCut* 为 True）当前在视口中活动的元素标签。如果 *printResults* 为 True，标签将可选地打印到回放文件。`getActiveElementLabels` 方法具有以下参数：

**必需参数**

无。

**可选参数**

*useCut*

Boolean，指定是否应考虑任何活动切割平面来确定活动元素。

*printResults*

Boolean，指定是否将活动元素标签打印到回放文件。

**返回值**

每个活动部件实例的标签的 Dictionary 对象。

**异常**

无。

### 11.4.10 getActiveNodeLabels(...)

此方法返回基于当前显示组且可选地基于任何活动切割（如果 *useCut* 为 True）当前在视口中活动的节点标签。如果 *printResults* 为 True，标签将可选地打印到回放文件。`getActiveNodeLabels` 方法具有以下参数：

**必需参数**

无。

**可选参数**

*useCut*

Boolean，指定是否应考虑任何活动切割平面来确定活动节点。

*printResults*

Boolean，指定是否将活动节点标签打印到回放文件。

**返回值**

每个活动部件实例的标签的 Dictionary 对象。

**异常**

无。

### 11.4.11 getPrimVarMinMaxLoc()

此方法返回包含当前主变量的最小值、最大值及其位置的字典。应在当前视口中显示云图，否则该方法将返回 *None*。

**参数**

无。

**返回值**

具有键 'minPartInstanceName'、'minElementLabel'、'minNodeLabel'、'minPosition'、'maxPartInstanceName'、'maxElementLabel'、'maxNodeLabel'、'maxPosition' 的字典。

**异常**

无。

### 11.4.12 makeCurrent()

此方法使 Viewport 对象成为当前视口。

**参数**

无。

**返回值**

无。

**异常**

无。

### 11.4.13 maximize()

此方法将 Viewport 对象最大化以填充绘图区域。

**参数**

无。

**返回值**

无。

**异常**

无。

### 11.4.14 minimize()

此方法将 Viewport 对象最小化以显示为简化的标题栏。

**参数**

无。

**返回值**

无。

**异常**

无。

### 11.4.15 offset(...)

此方法通过指定距离修改视口的当前 X-Y 位置。

**必需参数**

无。

**可选参数**

*deltaX*

Float，指定视口原点的 X 分量的偏移量（毫米）。默认值为 0。

*deltaY*

Float，指定视口原点的 Y 分量的偏移量（毫米）。默认值为 0。

**返回值**

无。

**异常**

无。

### 11.4.16 restore()

此方法将最大化或最小化的 Viewport 对象恢复为其先前的大小和位置。

**参数**

无。

**返回值**

无。

**异常**

无。

### 11.4.17 sendToBack()

此方法将 Viewport 对象移到最后。

**参数**

无。

**返回值**

无。

**异常**

无。

### 11.4.18 setColor(...)

此方法使用 *initialColor* 和 *translucency* 指定颜色分配。如果 *initialColor* 的值为 'As is'，则 *translucency* 不起作用。`setColor` 方法具有以下参数：

**必需参数**

*initialColor*

指定要应用于对象的初始颜色的字符串。

**可选参数**

*translucency*

0.0 到 1.0 范围内的浮点数，指定使用 *initialColor* 绘制的对象的半透明度。

**返回值**

无。

**异常**

无。

### 11.4.19 setColor(...)

此方法使用 [AttributeColorMap](pt01ch11pyo01.md) 对象指定的属性指定颜色分配。`setColor` 方法具有以下参数：

**必需参数**

*colorMapping*

[AttributeColorMap](pt01ch11pyo01.md) 对象。可能的值为任何 AttributeColorMap 对象。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 11.4.20 setColor(...)

此方法指定 [Leaf](pt01ch16pyo04.md) 对象的颜色。

**必需参数**

*leaf*

[Leaf](pt01ch16pyo04.md) 对象。可能的值为任何 Leaf 对象。

**可选参数**

必须至少提供以下之一：

*edgeColorWireHide*

String，指定当渲染样式为线框或隐藏时用于绘制 *leaf* 中包含的元素的边的颜色。

*edgeColorFillShade*

String，指定当渲染样式为填充或着色时用于绘制 *leaf* 中包含的元素的边的颜色。

*fillColor*

String，指定当渲染样式为填充或着色时用于绘制 *leaf* 中包含的元素面的颜色。

*nodeSymbolColor*

String，指定用于绘制 *leaf* 中包含的节点的颜色。

*nodeSymbolType*

SymbolicConstant，指定 *leaf* 中包含的节点的节点符号类型。可能的值为 FILLED_CIRCLE、FILLED_SQUARE、FILLED_DIAMOND、FILLED_TRI、HOLLOW_CIRCLE、HOLLOW_SQUARE、HOLLOW_DIAMOND、HOLLOW_TRI、CROSS 和 XMARKER。默认值为 HOLLOW_CIRCLE。

*nodeSymbolSize*

SymbolicConstant，指定 *leaf* 中包含的节点的节点符号大小。可能的值为 SMALL、MEDIUM 和 LARGE。默认值为 SMALL。

**返回值**

无。

**异常**

无。

### 11.4.21 forceRefresh()

此方法导致 Viewport 立即刷新。它允许脚本在终止前刷新 Viewport。通常，在脚本完成后只会进行一次累积刷新。

**参数**

无。

**返回值**

无。

**异常**

无。

### 11.4.22 setValues(...)

此方法修改 Viewport 对象。`setValues` 的参数与 [Viewport](pt01ch11pyo04.md#ker-viewport-viewport-pyc) 方法的参数相同，但 *name* 参数除外。此外，`setValues` 方法具有以下参数：

**必需参数**

无。

**可选参数**

*displayedObject*

[Displayable](#ker-displayable-pyc) 对象，指定要显示的对象。[Displayable](#ker-displayable-pyc) 类型是一个抽象概括。具体的可能类型为 [Part](pt01ch37pyo01.md)、[Assembly](pt01ch06pyo01.md)、[ConstrainedSketch](pt01ch48pyo01.md)、[Odb](pt01ch34pyo01.md)、[PlyStackPlot](pt01ch44pyo05.md) 或 [XYPlot](pt01ch55pyo16.md)。如果 *displayedObject*=`None`，Abaqus 显示空视口。

*displayMode*

SymbolicConstant，指定视口的显示模式。可能的值为：
- SINGLE，指定单个 *displayedObject*。
- OVERLAY，指定要同时显示的一个或多个图层——每个图层包含一个 *displayedObject*。

*visibleLayers*

String 序列，指定当 *displayMode* = OVERLAY 时将在视口中显示的图层名称。

*viewManipLayers*

SymbolicConstant，指定当 *displayMode*=OVERLAY 时哪些图层或哪些图层将受视图操作工具控制。可能的值为 ALL 和 CURRENT。

*currentLayer*

String，指定当 *displayMode* =OVERLAY 时哪些图层受选项设置影响。当前图层也是当 *viewManipLayers* =CURRENT 时受视图操作影响的唯一图层。

*layerOffset*

Float，指定用于在屏幕 Z 方向偏移图层的因子。可能值为 -1 到 1。负值会反转图层绘制的明显顺序。

**返回值**

无。

**异常**

RangeError。

### 11.4.23 addDrawings(...)

此方法识别要在 Viewport 中渲染的 [Drawing](pt01ch47pyo04.md) 对象的名称。

**必需参数**

无。

**可选参数**

*names*

String 值序列，标识 session.drawings 存储库中的键。

**返回值**

无。

**异常**

ValueError。

### 11.4.24 removeDrawings(...)

此方法识别不再在 Viewport 中渲染的 [Drawing](pt01ch47pyo04.md) 对象的名称。

**必需参数**

无。

**可选参数**

*names*

String 值序列，标识 Viewport 序列中的键。

**返回值**

无。

**异常**

ValueError。

### 11.4.25 timeDisplay(...)

此方法将 Viewport 显示刷新 *numFrames* 次，然后检查 *numSeconds* 秒是否已过。如果没有，它将继续刷新 Viewport 直到时间耗尽。完成时，将报告实际刷新的帧数（帧）和经过的时间以及计算的每秒帧数（fps）。

**必需参数**

无。

**可选参数**

*numFrames*

Int，指定最小刷新 Viewport 次数。默认值为 0。

*numSeconds*

Int，指定最小刷新 Viewport 秒数。默认值为 10。

*degreesPerFrame*

Float，指定在每次刷新前围绕其 Z 轴旋转模型视图的度数。默认值为 0.0。

**返回值**

无。

**异常**

无。

### 11.4.26 成员

Viewport 对象的成员与 [Viewport](pt01ch11pyo04.md#ker-viewport-viewport-pyc) 方法的参数具有相同的名称和描述。

此外，Viewport 对象可以具有以下成员：

*displayMode*

SymbolicConstant，指定视口的显示模式。可能的值为：
- SINGLE，指定单个 *displayedObject*。
- OVERLAY，指定要同时显示的一个或多个图层——每个图层包含一个 *displayedObject*。

*viewManipLayers*

SymbolicConstant，指定当 *displayMode*=OVERLAY 时哪些图层或哪些图层将受视图操作工具控制。可能的值为 ALL 和 CURRENT。

*layerOffset*

Float，指定用于在屏幕 Z 方向偏移图层的因子。可能值为 -1 到 1。负值会反转图层绘制的明显顺序。

*windowState*

SymbolicConstant，指定视口的当前状态。可能的值为 NORMAL、MAXIMIZED 和 MINIMIZED。

*currentWidth*

Float，指定当前视口的宽度（毫米），无论 *windowState* 的值如何。

*currentHeight*

Float，指定当前视口的高度（毫米），无论 *windowState* 的值如何，包括标题栏。

*applyLinkedCommands*

Boolean，指定视口是否链接以进行同步。默认值为 ON。

*activeColorModes*

SymbolicConstant，指定当前活动的颜色映射。可能的值为：
- DEFAULT_COLORS
- PART_GEOM_MAP_COLORS
- ASSEMBLY_MAP_COLORS
- PART_MAP_COLORS
- INSTANCE_MAP_COLORS
- INSTANCE_TYPE_MAP_COLORS
- SECTION_MAP_COLORS
- MATERIAL_MAP_COLORS
- LOAD_MAP_COLORS
- BC_MAP_COLORS
- INTERACTION_MAP_COLORS
- CONSTRAINT_MAP_COLORS
- SET_MAP_COLORS
- SURFACE_MAP_COLORS
- INTERNAL_SET_MAP_COLORS
- INTERNAL_SURFACE_MAP_COLORS
- DISPLAY_GRP_MAP_COLORS
- SELECTION_GRP_MAP_COLORS
- ELTYPE_MAP_COLORS
- PLOT_MAP_COLORS
- MESH_MAP_COLORS

默认值为 DEFAULT_COLORS。

*colorMode*

SymbolicConstant，指定最后应用的颜色映射。可能的值为：
- DEFAULT_COLORS
- PART_GEOM_MAP_COLORS
- ASSEMBLY_MAP_COLORS
- PART_MAP_COLORS
- INSTANCE_MAP_COLORS
- INSTANCE_TYPE_MAP_COLORS
- SECTION_MAP_COLORS
- MATERIAL_MAP_COLORS
- LOAD_MAP_COLORS
- BC_MAP_COLORS
- INTERACTION_MAP_COLORS
- CONSTRAINT_MAP_COLORS
- SET_MAP_COLORS
- SURFACE_MAP_COLORS
- INTERNAL_SET_MAP_COLORS
- INTERNAL_SURFACE_MAP_COLORS
- DISPLAY_GRP_MAP_COLORS
- SELECTION_GRP_MAP_COLORS
- ELTYPE_MAP_COLORS
- PLOT_MAP_COLORS
- MESH_MAP_COLORS

默认值为 DEFAULT_COLORS。

*translucency*

Float，指定将应用于使用 *initialColor* 着色的对象的半透明度，需要与 *initialColor* 一起设置。如果 *initialColor* 设置为 'As is'，则半透明度将不起作用。

*animationConnect*

Boolean，指定是否有动画连接到视口。

*colorMappings*

[AttributeColorMap](pt01ch11pyo01.md) 对象存储库，指定对象无法构造，但支持以下属性映射：
- "type"
- "Element set"
- "Material"
- "Section"
- "Default"
- "Part"
- "Part instance"
- "Element type"
- "Averaging region"
- "Assembly"
- "Property"
- "Set"
- "Surface"
- "Skin"
- "Profile"
- "Part shape"
- "Part status"
- "Part geometry"
- "Meshability"
- "Instance type"
- "Load"
- "Boundary condition"
- "Interaction"
- "Constraint"
- "Interaction type"
- "Constraint type"
- "Display group"
- "Selection group"
- "Interaction property"
- "Connector"
- "Connector type"
- "Connector property"
- "Internal set"
- "Internal surface"
- "mapColors"
- "autoColors"
- "overrides"
- "defaultAutoColors"
- "defaultOverrides"
- "objectToCopy"
- "colorMapping"
- "colorMappings"
- "colorMode"
- "attributeColors"
- "updateOverrides"
- "colorCodeOverride"
- "initialColor"
- "Layup"
- "Ply"

*initialColor*

String，指定在颜色编码开始时将应用于视口中所有对象的颜色。可能的值为 'As is'、'Default' 或带有颜色十六进制表示的字符串。

*currentLayer*

String，指定当 *displayMode* =OVERLAY 时哪些图层受选项设置影响。当前图层也是当 *viewManipLayers* =CURRENT 时受视图操作影响的唯一图层。

*displayedObject*

[Displayable](#ker-displayable-pyc) 对象，指定要显示的对象。[Displayable](#ker-displayable-pyc) 类型是一个抽象概括。具体的可能类型为 [Part](pt01ch37pyo01.md)、[Assembly](pt01ch06pyo01.md)、[ConstrainedSketch](pt01ch48pyo01.md)、[Odb](pt01ch34pyo01.md)、[PlyStackPlot](pt01ch44pyo05.md) 或 [XYPlot](pt01ch55pyo16.md)。如果 *displayedObject*=`None`，Abaqus 显示空视口。

*layers*

[Layer](pt01ch11pyo03.md) 对象存储库，指定存储库的键是 String，即图层的名称。

*view*

[View](pt01ch54pyo01.md) 对象，指定控制视口内容查看的对象。

*odbDisplay*

[OdbDisplay](pt01ch35pyo01.md) 对象，指定 [Odb](pt01ch34pyo01.md) 对象的显示选项。

*partDisplay*

[PartDisplayOptions](pt01ch17pyo16.md) 对象，指定 [Part](pt01ch37pyo01.md) 对象的显示选项。

*assemblyDisplay*

[AssemblyDisplayOptions](pt01ch17pyo01.md) 对象，指定 [Assembly](pt01ch06pyo01.md) 对象的显示选项。

*viewportAnnotationOptions*

[ViewportAnnotationOptions](pt01ch17pyo19.md) 对象。

*detailPlotOptions*

[DetailPlotOptions](pt01ch40pyo25.md) 对象。

*annotationsToPlot*

[AnnotationsToPlotArray](pt01ch05pyo02.md) 对象。

*visibleLayers*

String 元组，指定当 *displayMode* = OVERLAY 时将在视口中显示的图层名称。

*currentOrigin*

Float 对，指定当前视口左下角在画布坐标系中的 X 和 Y 坐标（毫米），无论 *windowState* 的值如何。

*iconOrigin*

Float 对，指定左下角在绘图区域左下角有原点的坐标系中当前视口的 X 和 Y 坐标（毫米）。此原点指的是当 *windowState* =MINIMIZED 时的视口位置。

*lightOptions*

[LightOptions](pt01ch17pyo12.md) 对象。

*imageOptions*

[ImageOptions](pt01ch11pyo05.md) 对象。

*movieOptions*

[MovieOptions](pt01ch11pyo06.md) 对象。

*drawings*

String 元组，指定 session.drawings 存储库的键。默认值为空序列。
