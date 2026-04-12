# 17.9 GraphicsOptions 对象









GraphicsOptions 对象存储控制所有视口中对象渲染方式的设置。GraphicsOptions 对象通过以下两种方式之一访问：
- 默认图形选项。这些设置在您启动会话时使用，也由"图形选项"对话框上的"默认"按钮使用。
- 当前图形选项。

GraphicsOptions 对象没有构造函数；Abaqus 在启动会话时创建 *defaultGraphicsOptions* 和 *graphicsOptions* 成员。

启动会话时，Abaqus 会检测系统上安装的图形硬件，并使用环境文件 (`abaqus_v6.env`) 中的 `setValues` 方法来修改 GraphicsOptions 对象的成员。如果您的图形硬件不受 Abaqus/CAE 支持，或者您希望覆盖默认图形选项，可以修改环境文件中的设置。有关更多信息，请参阅《Abaqus 安装和许可指南》第 5.3 节"调整图形卡"。

**访问**

```
session.defaultGraphicsOptions
session.graphicsOptions
```

### 17.9.1 setValues(...)

此方法修改 GraphicsOptions 对象。

**必需参数**

无。

**可选参数**

*graphicsDriver*

一个 SymbolicConstant，指定要使用的图形驱动程序。Abaqus/CAE 目前仅使用 OpenGL，所以唯一的可能值是 OPEN_GL。OPEN_GL 利用图形适配器硬件加速。

*doubleBuffering*

一个 Boolean，指定是否使用双缓冲。默认值为 ON。

双缓冲控制 Abaqus/CAE 绘制图形的位置。当 *doubleBuffering*=OFF 时，所有内容直接绘制到屏幕上，在许多系统上您可以看到绘制操作的进度。大多数用户觉得这很分散注意力，尤其是在视图操作或结果动画等动态情况下。当 *doubleBuffering*=ON 时，绘制发生在单独的图形缓冲区中，在所有绘制操作完成时显示。这会在视图更改或动画期间产生更平滑的显示。建议将双缓冲设置为 ON。

*displayLists*

一个 Boolean，指定是否将使用显示列表来加速图形性能。默认值为 ON。

当 *displayLists*=ON 时，绘制操作被记录在一个可以快速重放的列表中。这在大多数系统上会产生更快的绘制，但需要额外的内存来记录绘制操作。在可视化模块中，显示列表仅在视图操作期间使用，然后它们的使用取决于 *viewManipDisplayListThreshold* 的设置。

*highlightMethodHint*

一个 SymbolicConstants 序列，指定用于修改高亮方法的提示。可能的值为：
- HARDWARE_OVERLAY，指定硬件覆盖的提示。最佳图形性能通过硬件覆盖实现，但并非所有系统和图形适配器都支持硬件覆盖。
- XOR，指定 XOR 技术的提示。XOR 技术使用布尔像素操作来模拟绘制操作，但可以根据底层像素的颜色产生不同的颜色。
- SOFTWARE_OVERLAY，指定软件覆盖的提示。软件覆盖方法模拟硬件覆盖的效果。
- BLEND，指定混合方法的提示。混合方法将底层像素的颜色与期望颜色组合，产生瞬态图形的近似值。

默认值为 (HARDWARE_OVERLAY, XOR, SOFTWARE_OVERLAY, BLEND)。

Abaqus 在启动会话时按从先到后的顺序应用此序列的值。第一个成功的值成为默认高亮方法。并非所有图形适配器都支持 HARDWARE_OVERLAY 值，您必须使用 *highlightMethodHint* 参数提供替代方案。

您可以使用单个值来设置列表的第一个元素，也可以使用包含一到四个唯一值的元组。Abaqus 会根据默认顺序将元组的任何剩余元素设置为唯一值。

*dragMode*

一个 SymbolicConstant，指定在视图动态旋转期间使用哪种渲染。可能的值为：
- FAST，指定以线框形式渲染图像的渲染模式。
- AS_IS，指定按原样渲染图像的渲染模式。

默认值为 AS_IS。

当设置为 *dragMode*=FAST 时，在旋转、平移或缩放等视图更改期间绘制线框轮廓。当 *dragMode*=AS_IS 时，窗口中显示的所有内容将在视图更改期间绘制；但是，当模型复杂时，尤其是在使用较旧或较慢的系统时，显示可能会滞后于鼠标移动。对于具有图形硬件加速的较新系统，可以在不显著降低性能的情况下实现 AS_IS 设置。

*antiAlias*

一个 Boolean，指定是否平滑线条以减少光栅化的锯齿效果。默认值为 ON。

*autoFitAfterRotate*

一个 Boolean，指定是否在每次视图旋转后自动调整模型大小以适应视口。默认值为 OFF。

*polygonOffsetConstant*

一个 Float，指定在绘制多边形面时添加的偏移量。*polygonOffsetConstant* 参数仅影响 OpenGL 驱动程序的行为。可能的值为 0.0 ≤ *polygonOffsetConstant* ≤ 100.0。默认值为平台相关，通常在 0.0 和 2.0 之间。

*polygonOffsetSlope*

一个 Float，指定在将线条添加到多边形面的顶点之前乘以每条线条斜率的因子。*polygonOffsetSlope* 参数仅影响 OpenGL 驱动程序的行为。可能的值为 0.0 ≤ *polygonOffsetSlope* ≤ 100.0。默认值为平台相关，通常在 0.0 和 2.0 之间。

*printPolygonOffsetConstant*

一个 Float，指定在绘制多边形面时添加的偏移量。*printPolygonOffsetConstant* 类似于 *polygonOffsetConstant*；但是，*printPolygonOffsetConstant* 用于打印，而 *polygonOffsetConstant* 用于显示。某些系统（尤其是 Windows）使用不同的 OpenGL 驱动程序进行打印和显示，您可能需要为每个驱动程序使用不同的偏移值。

*printPolygonOffsetSlope*

一个 Float，指定在将线条添加到多边形面的顶点之前乘以每条线条斜率的因子。*printPolygonOffsetSlope* 类似于 *polygonOffsetSlope*；但是，*printPolygonOffsetSlope* 用于打印，而 *polygonOffsetSlope* 用于显示。某些系统（尤其是 Windows）使用不同的 OpenGL 驱动程序进行打印和显示，您可能需要为每个驱动程序使用不同的偏移值。

*vertexArrays*

一个 Boolean，指定如何处理模型的三维顶点。当 *vertexArrays*=OFF 时，模型的每个顶点单独处理。当 *vertexArrays*=ON 时，顶点以大块处理，从而加快显示速度。并非所有图形适配器都正确支持此功能。图形适配器未正确处理三维顶点的标志之一是在"橡皮筋"操作期间缺少图形。例如，在 Sketcher 中动态拖动圆的半径时，圆应该可见。默认值为 ON。

*vertexArraysInDisplayLists*

一个 Boolean，指定在构建显示列表时 *vertexArrays* 设置是否应暂时设置为 OFF。默认值为 ON。

某些图形适配器在显示列表内正确使用顶点数组支持方面存在问题。将 *vertexArraysInDisplayLists* 设置为 OFF 对图形性能的影响比将 *vertexArrays* 或 *displayLists* 设置为 OFF 要小。

*viewManipDisplayListThreshold*

一个 Int，指定可创建以加速视图操作操作的显示列表的最大大小。在查看大型模型时增加此值将增加视图操作操作开始之前的延迟，以在视图操作期间获得更好的图形性能。如果对大型模型设置过高，延迟可能是数秒。在过多的情况下，图形内存可能会超出，结果可能是视图操作的空显示列表（模型不可见）。如果 *displayLists*=OFF，则此设置视为 0。可能的值为 0 ≤ *viewManipDisplayListThreshold* ≤ 20000。默认值为 40。

*directRendering*

一个 Boolean，指定 Abaqus 如何渲染 X11 图形操作。当 *directRendering*=OFF 时，图形通过 X 服务器渲染。当 *directRendering*=ON 时，图形操作直接发送到图形适配器，产生更快的显示。为了获得最佳性能，初始值为 ON。此参数仅在您首次启动 Abaqus/CAE 时使用；您无法在会话期间配置 *directRendering*。

*hardwareAcceleration*

一个 Boolean，指定是否将在 Windows 平台上使用硬件加速的 OpenGL 图形驱动程序。默认值为 ON。

当 *hardwareAcceleration*=OFF 时，图形驱动程序使用操作系统附带的 OpenGL 软件实现。这在大多数系统上会导致更慢的绘制；但是，如果硬件图形驱动程序与 Abaqus/CAE 不兼容，您可能必须使用 OpenGL 的软件实现。

*hardwareAcceleration* 仅在您首次在 Windows 平台上启动 Abaqus/CAE 时使用；您无法在会话期间配置 *hardwareAcceleration*。当您在 X-Windows 平台上启动 Abaqus/CAE 并显示到运行 Exceed 或任何其他 X-Windows 服务器的 Windows 平台时，不使用 *hardwareAcceleration*。

*hardwareOverlay*

一个 Boolean，指定是否使用硬件覆盖平面（如果可用）。默认值为与 *hardwareOverlayAvailable* 成员相同的值。

当 *hardwareOverlayAvailable*=OFF 时，无法将 *hardwareOverlay* 设置为 ON，并且 HIGHLIGHT_METHOD  高亮方法将不可用。如果视口显示纯色且不显示模型，则需要在启动 Abaqus/CAE 之前将 ABAQUS_EMULATE_OVERLAYS 环境变量（设置为任何值）完全抑制硬件覆盖。

*hardwareOverlay* 仅在您首次启动 Abaqus/CAE 时使用；您无法在会话期间配置 *hardwareOverlay*。

*textureMapping*

一个 Boolean，指定是否使用纹理来显示等值线图。默认值为 ON。

仅当视口无法正确显示模型的等值线图时，才需要关闭纹理映射。

*printTextureMapping*

一个 Boolean，指定是否使用纹理来显示等值线图。默认值为 ON。

仅当打印输出无法正确显示模型的等值线图时，才需要关闭打印纹理映射。*printTextureMapping* 类似于 *textureMapping*；但是，*printTextureMapping* 用于打印，而 *textureMapping* 用于显示。某些系统（尤其是 Windows）使用不同的 OpenGL 驱动程序进行打印和显示，您可能需要为每个驱动程序使用不同的设置。

*backgroundStyle*

一个 SymbolicConstant，指定所有视口窗口使用的背景样式。可能的值为 SOLID 和 GRADIENT。默认值为 SOLID。

如果 *backgroundStyle*=SOLID，则视口背景将显示为 *backgroundColor* 指定的纯色。如果 *backgroundStyle*=GRADIENT，则视口背景将从视口顶部的 *backgroundColor* 开始逐渐混合到视口底部的 *backgroundBottomColor*。

*backgroundColor*

一个 String，指定所有视口窗口的两个背景颜色之一。初始颜色为黑色。有效颜色字符串列表在 [Session](pt01ch47pyo01.md) 对象的 *colors* 映射中。

*backgroundBottomColor*

一个 String，指定所有视口窗口的两个背景颜色之一。仅在 *backgroundStyle*=GRADIENT 时使用此颜色。初始颜色为黑色。有效颜色字符串列表在 [Session](pt01ch47pyo01.md) 对象的 *colors* 映射中。

*backgroundOverride*

一个 Boolean，指定当显示某些对象（如草图或 XY 绘图）时是否可以覆盖 GRADIENT 的视口背景样式。被覆盖时，背景将是渐变背景的顶部颜色。

*backfaceCulling*

一个 Boolean，指定是否绘制被确定为远离观看者的面。默认值为 ON。backfaceCulling 在显示元素前面遮挡后面的实心元素时提供性能增强。如果您似乎看到元素的背面而前面缺失，也应设置 *backfaceCulling*=OFF。如果您认为显示不完整，也应设置 *backfaceCulling*=OFF。

*accelerateOffScreen*

一个 Boolean，指定是否将硬件加速图形驱动程序用于屏幕外渲染。如果图形硬件加速可用且未被 hardwareAcceleration 选项禁用，并且图形驱动程序支持底层技术，则默认值为 ON。设置为 OFF 时，将使用替代（较慢）技术来创建屏幕外图像。屏幕外渲染用于打印、探针和后备存储（视口刷新）。将此值设置为 OFF 将强制打印图像不使用硬件加速。这在编写自动化测试以生成跨多台可能具有不同图形环境的机器进行比较的光栅图像时很有用。

*backingStore*

一个 Boolean，指定是否使用后备存储来在遮挡视口的窗口被移动或关闭后刷新视口。默认值为 ON。

*shadersAvailable*

一个 Boolean，指定图形硬件是否支持 OpenGL 着色语言 (GLSL)。

*translucencyMode*

一个 Int，指定在绘制半透明对象时速度或准确性更重要。较低的值针对速度优化，而较高的值针对准确性优化。每个设置的实际含义取决于 *shadersAvailable* 和图形硬件及驱动程序的能力。可能的值为 1 ≤ *translucencyMode* ≤ 6。默认值为 4。

*options*

`None` 或一个 GraphicsOptions 对象，指定要从中复制值的对象。如果其他参数也提供给 `setValues`，它们将覆盖 *options* 成员中的值。默认值为 `None`。

*contourRangeTexturePrecision*

一个 Float，指定在计算将结果（等值线）值转换为纹理值的适当比例时使用的容差。当设置过低时，接近范围限制的值可能会错误显示"超出范围"颜色。默认值为 0.5×10⁻⁵。

**返回值**

无

**异常**

RangeError。

### 17.9.2 成员

GraphicsOptions 对象可具有以下成员：

*backgroundOverride*

一个 Boolean，指定当显示某些对象（如草图或 XY 绘图）时是否可以覆盖 GRADIENT 的视口背景样式。被覆盖时，背景将是渐变背景的顶部颜色。

*backfaceCulling*

一个 Boolean，指定是否绘制被确定为远离观看者的面。默认值为 ON。backfaceCulling 在显示元素前面遮挡后面的实心元素时提供性能增强。如果您似乎看到元素的背面而前面缺失，也应设置 *backfaceCulling*=OFF。如果您认为显示不完整，也应设置 *backfaceCulling*=OFF。

*graphicsDriver*

一个 SymbolicConstant，指定要使用的图形驱动程序。Abaqus/CAE 目前仅使用 OpenGL，所以唯一的可能值是 OPEN_GL。OPEN_GL 利用图形适配器硬件加速。

*doubleBuffering*

一个 Boolean，指定是否使用双缓冲。默认值为 ON。

双缓冲控制 Abaqus/CAE 绘制图形的位置。当 *doubleBuffering*=OFF 时，所有内容直接绘制到屏幕上，在许多系统上您可以看到绘制操作的进度。大多数用户觉得这很分散注意力，尤其是在视图操作或结果动画等动态情况下。当 *doubleBuffering*=ON 时，绘制发生在单独的图形缓冲区中，在所有绘制操作完成时显示。这会在视图更改或动画期间产生更平滑的显示。建议将双缓冲设置为 ON。

*displayLists*

一个 Boolean，指定是否将使用显示列表来加速图形性能。默认值为 ON。

当 *displayLists*=ON 时，绘制操作被记录在一个可以快速重放的列表中。这在大多数系统上会产生更快的绘制，但需要额外的内存来记录绘制操作。在可视化模块中，显示列表仅在视图操作期间使用，然后它们的使用取决于 *viewManipDisplayListThreshold* 的设置。

*dragMode*

一个 SymbolicConstant，指定在视图动态旋转期间使用哪种渲染。可能的值为：
- FAST，指定以线框形式渲染图像的渲染模式。
- AS_IS，指定按原样渲染图像的渲染模式。

默认值为 AS_IS。

当设置为 *dragMode*=FAST 时，在旋转、平移或缩放等视图更改期间绘制线框轮廓。当 *dragMode*=AS_IS 时，窗口中显示的所有内容将在视图更改期间绘制；但是，当模型复杂时，尤其是在使用较旧或较慢的系统时，显示可能会滞后于鼠标移动。对于具有图形硬件加速的较新系统，可以在不显著降低性能的情况下实现 AS_IS 设置。

*antiAlias*

一个 Boolean，指定是否平滑线条以减少光栅化的锯齿效果。默认值为 ON。

*autoFitAfterRotate*

一个 Boolean，指定是否在每次视图旋转后自动调整模型大小以适应视口。默认值为 OFF。

*polygonOffsetConstant*

一个 Float，指定在绘制多边形面时添加的偏移量。*polygonOffsetConstant* 参数仅影响 OpenGL 驱动程序的行为。可能的值为 0.0 ≤ *polygonOffsetConstant* ≤ 100.0。默认值为平台相关，通常在 0.0 和 2.0 之间。

*polygonOffsetSlope*

一个 Float，指定在将线条添加到多边形面的顶点之前乘以每条线条斜率的因子。*polygonOffsetSlope* 参数仅影响 OpenGL 驱动程序的行为。可能的值为 0.0 ≤ *polygonOffsetSlope* ≤ 100.0。默认值为平台相关，通常在 0.0 和 2.0 之间。

*printPolygonOffsetConstant*

一个 Float，指定在绘制多边形面时添加的偏移量。*printPolygonOffsetConstant* 类似于 *polygonOffsetConstant*；但是，*printPolygonOffsetConstant* 用于打印，而 *polygonOffsetConstant* 用于显示。某些系统（尤其是 Windows）使用不同的 OpenGL 驱动程序进行打印和显示，您可能需要为每个驱动程序使用不同的偏移值。

*printPolygonOffsetSlope*

一个 Float，指定在将线条添加到多边形面的顶点之前乘以每条线条斜率的因子。*printPolygonOffsetSlope* 类似于 *polygonOffsetSlope*；但是，*printPolygonOffsetSlope* 用于打印，而 *polygonOffsetSlope* 用于显示。某些系统（尤其是 Windows）使用不同的 OpenGL 驱动程序进行打印和显示，您可能需要为每个驱动程序使用不同的偏移值。

*vertexArrays*

一个 Boolean，指定如何处理模型的三维顶点。当 *vertexArrays*=OFF 时，模型的每个顶点单独处理。当 *vertexArrays*=ON 时，顶点以大块处理，从而加快显示速度。并非所有图形适配器都正确支持此功能。图形适配器未正确处理三维顶点的标志之一是在"橡皮筋"操作期间缺少图形。例如，在 Sketcher 中动态拖动圆的半径时，圆应该可见。默认值为 ON。

*vertexArraysInDisplayLists*

一个 Boolean，指定在构建显示列表时 *vertexArrays* 设置是否应暂时设置为 OFF。默认值为 ON。

某些图形适配器在显示列表内正确使用顶点数组支持方面存在问题。将 *vertexArraysInDisplayLists* 设置为 OFF 对图形性能的影响比将 *vertexArrays* 或 *displayLists* 设置为 OFF 要小。

*viewManipDisplayListThreshold*

一个 Int，指定可创建以加速视图操作操作的显示列表的最大大小。在查看大型模型时增加此值将增加视图操作操作开始之前的延迟，以在视图操作期间获得更好的图形性能。如果对大型模型设置过高，延迟可能是数秒。在过多的情况下，图形内存可能会超出，结果可能是视图操作的空显示列表（模型不可见）。如果 *displayLists*=OFF，则此设置视为 0。可能的值为 0 ≤ *viewManipDisplayListThreshold* ≤ 20000。默认值为 40。

*directRendering*

一个 Boolean，指定 Abaqus 如何渲染 X11 图形操作。当 *directRendering*=OFF 时，图形通过 X 服务器渲染。当 *directRendering*=ON 时，图形操作直接发送到图形适配器，产生更快的显示。为了获得最佳性能，初始值为 ON。此参数仅在您首次启动 Abaqus/CAE 时使用；您无法在会话期间配置 *directRendering*。

*hardwareAcceleration*

一个 Boolean，指定是否将在 Windows 平台上使用硬件加速的 OpenGL 图形驱动程序。默认值为 ON。

当 *hardwareAcceleration*=OFF 时，图形驱动程序使用操作系统附带的 OpenGL 软件实现。这在大多数系统上会导致更慢的绘制；但是，如果硬件图形驱动程序与 Abaqus/CAE 不兼容，您可能必须使用 OpenGL 的软件实现。

*hardwareAcceleration* 仅在您首次在 Windows 平台上启动 Abaqus/CAE 时使用；您无法在会话期间配置 *hardwareAcceleration*。当您在 X-Windows 平台上启动 Abaqus/CAE 并显示到运行 Exceed 或任何其他 X-Windows 服务器的 Windows 平台时，不使用 *hardwareAcceleration*。

*hardwareOverlay*

一个 Boolean，指定是否使用硬件覆盖平面（如果可用）。默认值为与 *hardwareOverlayAvailable* 成员相同的值。

当 *hardwareOverlayAvailable*=OFF 时，无法将 *hardwareOverlay* 设置为 ON，并且 HIGHLIGHT_METHOD  高亮方法将不可用。如果视口显示纯色且不显示模型，则需要在启动 Abaqus/CAE 之前将 ABAQUS_EMULATE_OVERLAYS 环境变量（设置为任何值）完全抑制硬件覆盖。

*hardwareOverlay* 仅在您首次启动 Abaqus/CAE 时使用；您无法在会话期间配置 *hardwareOverlay*。

*textureMapping*

一个 Boolean，指定是否使用纹理来显示等值线图。默认值为 ON。

仅当视口无法正确显示模型的等值线图时，才需要关闭纹理映射。

*printTextureMapping*

一个 Boolean，指定是否使用纹理来显示等值线图。默认值为 ON。

仅当打印输出无法正确显示模型的等值线图时，才需要关闭打印纹理映射。*printTextureMapping* 类似于 *textureMapping*；但是，*printTextureMapping* 用于打印，而 *textureMapping* 用于显示。某些系统（尤其是 Windows）使用不同的 OpenGL 驱动程序进行打印和显示，您可能需要为每个驱动程序使用不同的设置。

*backgroundStyle*

一个 SymbolicConstant，指定所有视口窗口使用的背景样式。可能的值为 SOLID 和 GRADIENT。默认值为 SOLID。

如果 *backgroundStyle*=SOLID，则视口背景将显示为 *backgroundColor* 指定的纯色。如果 *backgroundStyle*=GRADIENT，则视口背景将从视口顶部的 *backgroundColor* 开始逐渐混合到视口底部的 *backgroundBottomColor*。

*accelerateOffScreen*

一个 Boolean，指定是否将硬件加速图形驱动程序用于屏幕外渲染。如果图形硬件加速可用且未被 hardwareAcceleration 选项禁用，并且图形驱动程序支持底层技术，则默认值为 ON。设置为 OFF 时，将使用替代（较慢）技术来创建屏幕外图像。屏幕外渲染用于打印、探针和后备存储（视口刷新）。将此值设置为 OFF 将强制打印图像不使用硬件加速。这在编写自动化测试以生成跨多台可能具有不同图形环境的机器进行比较的光栅图像时很有用。

*backingStore*

一个 Boolean，指定是否使用后备存储来在遮挡视口的窗口被移动或关闭后刷新视口。默认值为 ON。

*highlightMethod*

一个 SymbolicConstant，指定高亮方法。对于 GraphicsOptions 对象，可能的值为 HARDWARE_OVERLAY、XOR、SOFTWARE_OVERLAY 和 BLEND。

*hardwareOverlayAvailable*

一个 Boolean，指定图形硬件是否支持硬件覆盖。

*shadersAvailable*

一个 Boolean，指定图形硬件是否支持 OpenGL 着色语言 (GLSL)。

*translucencyMode*

一个 Int，指定在绘制半透明对象时速度或准确性更重要。较低的值针对速度优化，而较高的值针对准确性优化。每个设置的实际含义取决于 *shadersAvailable* 和图形硬件及驱动程序的能力。可能的值为 1 ≤ *translucencyMode* ≤ 6。默认值为 4。

*contourRangeTexturePrecision*

一个 Float，指定在计算将结果（等值线）值转换为纹理值的适当比例时使用的容差。当设置过低时，接近范围限制的值可能会错误显示"超出范围"颜色。默认值为 0.5×10⁻⁵。

*options*

`None` 或一个 GraphicsOptions 对象，指定要从中复制值的对象。如果其他参数也提供给 `setValues`，它们将覆盖 *options* 成员中的值。默认值为 `None`。

*highlightMethodHint*

一个 SymbolicConstants 元组，指定用于修改高亮方法的提示。可能的值为：
- HARDWARE_OVERLAY，指定硬件覆盖的提示。最佳图形性能通过硬件覆盖实现，但并非所有系统和图形适配器都支持硬件覆盖。
- XOR，指定 XOR 技术的提示。XOR 技术使用布尔像素操作来模拟绘制操作，但可以根据底层像素的颜色产生不同的颜色。
- SOFTWARE_OVERLAY，指定软件覆盖的提示。软件覆盖方法模拟硬件覆盖的效果。
- BLEND，指定混合方法的提示。混合方法将底层像素的颜色与期望颜色组合，产生瞬态图形的近似值。

默认值为 (HARDWARE_OVERLAY, XOR, SOFTWARE_OVERLAY, BLEND)。

Abaqus 在启动会话时按从先到后的顺序应用此序列的值。第一个成功的值成为默认高亮方法。并非所有图形适配器都支持 HARDWARE_OVERLAY 值，您必须使用 *highlightMethodHint* 参数提供替代方案。

您可以使用单个值来设置列表的第一个元素，也可以使用包含一到四个唯一值的元组。Abaqus 会根据默认顺序将元组的任何剩余元素设置为唯一值。

*backgroundColor*

一个 String，指定所有视口窗口的两个背景颜色之一。初始颜色为黑色。有效颜色字符串列表在 [Session](pt01ch47pyo01.md) 对象的 *colors* 映射中。

*backgroundBottomColor*

一个 String，指定所有视口窗口的两个背景颜色之一。仅在 *backgroundStyle*=GRADIENT 时使用此颜色。初始颜色为黑色。有效颜色字符串列表在 [Session](pt01ch47pyo01.md) 对象的 *colors* 映射中。





