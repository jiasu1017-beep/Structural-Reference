# 54.1 View 对象

[Session](pt01ch47pyo01.md) 和 [Viewport](pt01ch11pyo04.md) View 对象存储自定义视图（预定义和用户定义）的视图设置。用于定义视图的范式基于相机类比。
与使用相机拍照类似，指定相机位置、视图方向、方向、景深和投影等特征，以将三维视图转换到屏幕。

[Layer](pt01ch11pyo03.md) View 对象存储用于在视口内定位 [Layer](pt01ch11pyo03.md) 内容的变换矩阵。

**访问**

```
session.viewports[*name*].layers[*name*].view
session.viewports[*name*].view
session.views[*name*]
```

### 54.1.1 View(...)

此方法创建一个 View 对象。

**注意：**所有尺寸和坐标都在模型坐标系中指定。

**注意：**此方法不能用于为 [Layer](pt01ch11pyo03.md) 对象创建 View。

**路径**

```
session.View
```

**必需参数**

*name*

一个 String，指定视图的名称（也用作 repository 键）。可能的值为 'Front'、'Back'、'Top'、'Bottom'、'Left'、`Right'、'Iso'、'User-1'、'User-2'、'User-3' 和 'User-4'。与此参数关联的对象成员是一个 SymbolicConstant。*name* 成员的可能值为：FRONT、BACK、TOP、BOTTOM、LEFT、RIGHT、ISO、USER1、USER2、USER3 和 USER4。

*fieldOfViewAngle*

一个 Float，指定相机的视角。可能的值为 0.0  ![](../graphics/ker_eqn00048.gif) *fieldOfViewAngle*  ![](../graphics/ker_eqn00048.gif) 180.0。

*nearPlane*

一个 Float，指定从相机到近裁剪平面的距离。可能的值为 *nearPlane*  ![](../graphics/ker_eqn00060.gif) 0.0。

*farPlaneMode*

一个 SymbolicConstant，指定如何设置从相机到远裁剪平面的距离。可能的值为 AUTO_COMPUTE 和 SPECIFY。

*farPlane*

当 *farPlaneMode*=SPECIFY 时，一个 Float，指定从相机到远裁剪平面的距离。可能的值为 *farPlane*  ![](../graphics/ker_eqn00060.gif) *nearPlane*。

*width*

一个 Float，指定前裁剪平面的宽度。可能的值为 *width*  ![](../graphics/ker_eqn00060.gif) 0.0。

*height*

一个 Float，指定前裁剪平面的高度。可能的值为 *height*  ![](../graphics/ker_eqn00060.gif) 0.0。

*projection*

一个 SymbolicConstant，指定投影模式。可能的值为 PERSPECTIVE 和 PARALLEL。

*cameraPosition*

一个三个 Float 的序列，指定相机位置。

*cameraUpVector*

一个三个 Float 的序列，指定相机的向上向量（屏幕的正 *Y* 轴）。初始值为 (0, 0, 0)。

*cameraTarget*

一个三个 Float 的序列，指定场景的中心。

*viewOffsetX*

一个 Float，指定在屏幕 *X* 方向上平移模型的比例（相对于视口宽度）。正值将模型向右平移。负值将模型向左平移。

*viewOffsetX* 和 *viewOffsetY* 参数允许您在不更改相机或目标位置（`View` 方法的 *cameraPosition* 和 *cameraTarget* 参数）的情况下平移视图。由此产生的视图更改允许您平移透视显示而不会产生明显的模型旋转效果。

*viewOffsetY*

一个 Float，指定在屏幕 *Y* 方向上平移模型的比例（相对于视口高度）。正值将模型向上平移。负值将模型向下平移。

*autoFit*

一个 Boolean，指定应用视图时是否自动拟合。

**可选参数**

*movieMode*

一个 Boolean，指定相机是否处于电影模式。默认值为 OFF。

**返回值**

一个 View 对象。

**异常**

RangeError。

### 54.1.2 fitView(...)

此方法缩放可显示对象（如零件、装配或 *X–Y* 绘图）以适应视口。

**必需参数**

无。

**可选参数**

*drawImmediately*

一个 Boolean，指定在处理命令后立即刷新视口。这通常仅在编写脚本时使用，期望在脚本完成前显示中间结果。默认值为 False。

**返回值**

无。

**异常**

无。

### 54.1.3 next(...)

此方法将视口中的视图恢复到列表中的下一个视图设置。（每个视口存储八个视图的列表。）如果没有下一个视图，则不执行任何操作。

**注意：**此方法不适用于 [Layer](pt01ch11pyo03.md) View。

**必需参数**

无。

**可选参数**

*drawImmediately*

一个 Boolean，指定在处理命令后立即刷新视口。这通常仅在编写脚本时使用，期望在脚本完成前显示中间结果。默认值为 False。

**返回值**

无。

**异常**

无。

### 54.1.4 pan(...)

此方法在视口中平移视图，使用绝对模式而非相对模式。

**必需参数**

无。

**可选参数**

*xFraction*

一个 Float，指定在屏幕 *X* 方向上平移模型的比例（相对于视口宽度）。正值将模型向右平移。负值将模型向左平移。默认值为 0.0。

*yFraction*

一个 Float，指定在屏幕 *Y* 方向上平移模型的比例（相对于视口高度）。正值将模型向上平移。负值将模型向下平移。默认值为 0.0。

*asMovie*

一个 Boolean，指定是否使用 `pan` 视图操作的替代模式。默认值为 OFF。此参数不适用于 [Layer](pt01ch11pyo03.md) View。

*drawImmediately*

一个 Boolean，指定在处理命令后立即刷新视口。此参数通常仅在编写脚本时使用，期望在脚本完成前显示中间结果。默认值为 False。

**返回值**

无。

**异常**

无。

### 54.1.5 previous(...)

此方法将视口中的视图恢复到列表中的上一个视图设置。（每个视口存储八个视图的列表。）如果没有上一个视图，则不执行任何操作。

**注意：**此方法不适用于 [Layer](pt01ch11pyo03.md) View。

**必需参数**

无。

**可选参数**

*drawImmediately*

一个 Boolean，指定在处理命令后立即刷新视口。此参数通常仅在编写脚本时使用，期望在脚本完成前显示中间结果。默认值为 False。

**返回值**

无。

**异常**

无。

### 54.1.6 rotate(...)

此方法在视口中旋转视图。如果之前已指定旋转中心且 *asMovie* 为 OFF，则此方法将遵循该旋转中心。

**必需参数**

无。

**可选参数**

*xAngle*

一个 Float，指定绕 *X* 轴旋转的角度（度）。默认值为 0.0。

*yAngle*

一个 Float，指定绕 *Y* 轴旋转的角度（度）。默认值为 0.0。

*zAngle*

一个 Float，指定绕 *Z* 轴旋转的角度（度）。默认值为 0.0。

*mode*

一个 SymbolicConstant，指定旋转模式。可能的值为：
- TOTAL：将视图设置为 (0, 0, 1)，然后绕屏幕轴旋转（绝对旋转）。
- SCREEN：绕屏幕轴增量旋转（相对旋转）。
- MODEL：绕模型轴增量旋转（相对旋转）。

默认值为 MODEL。

*asMovie*

一个 Boolean，指定是否使用 `rotate` 视图操作的替代模式。默认值为 OFF。

*drawImmediately*

一个 Boolean，指定在处理命令后立即刷新视口。此参数通常仅在编写脚本时使用，期望在脚本完成前显示中间结果。默认值为 False。

**返回值**

无。

**异常**

无。

### 54.1.7 setLayerTransform(...)

此方法修改用于定位 [Layer](pt01ch11pyo03.md) 的变换。

**注意：**此方法不适用于 [Session](pt01ch47pyo01.md) 和 [Viewport](pt01ch11pyo04.md) View。

**必需参数**

无。

**可选参数**

*layerTransform*

一个 16 个 Float 的序列，指定变换矩阵。

*options*

一个 View 对象，从中复制视图设置。如果也向 `setLayerTransform` 提供了 *layerTransform* 参数，它将覆盖由 *view* 指定的 View 对象中的值。

*drawImmediately*

一个 Boolean，指定在处理命令后立即刷新视口。此参数通常仅在编写脚本时使用，期望在脚本完成前显示中间结果。默认值为 False。

**返回值**

无。

**异常**

无。

### 54.1.8 setProjection(...)

此方法修改视口中三维模型的外观。选择 PERSPECTIVE 使模型显得更真实，通过减小离视点更远的特征的明显尺寸。

**注意：**此方法不适用于 [Layer](pt01ch11pyo03.md) View。

**必需参数**

*projection*

一个 SymbolicConstant，指定投影模式。可能的值为 PERSPECTIVE 和 PARALLEL。

**可选参数**

*drawImmediately*

一个 Boolean，指定在处理命令后立即刷新视口。此参数通常仅在编写脚本时使用，期望在脚本完成前显示中间结果。默认值为 False。

**返回值**

无。

**异常**

RangeError。

### 54.1.9 setRotationCenter(...)

此方法将旋转中心设置为指定位置。

**必需参数**

*rotationCenter*

一个 String 和 Int 的序列，指定零件实例名称和节点标签，或三个 Float 的序列，指定一个点。

**可选参数**

无。

**返回值**

无。

**异常**

TypeError: 除非显示的对象是 ODB，否则不能使用零件实例和节点标签设置旋转中心。

### 54.1.10 setValues(...)

此方法修改 View 对象。

**注意：**此方法不适用于 [Layer](pt01ch11pyo03.md) View。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [View](pt01ch54pyo01.md#ker-view-view-pyc) 方法的参数相同，但 *name* 和 *autoFit* 参数除外。此外，`setValues` 具有以下可选参数：

*options*

一个 View 对象，从中复制视图设置。如果也向 `setValues` 提供了其他参数，它们将覆盖由 *view* 指定的 View 对象中的值。

*drawImmediately*

一个 Boolean，指定在处理命令后立即刷新视口。此参数通常仅在编写脚本时使用，期望在脚本完成前显示中间结果。默认值为 False。

**返回值**

无。

**异常**

RangeError。

### 54.1.11 setViewpoint(...)

此方法设置视口中相机的位置。

**注意：**此方法不适用于 [Layer](pt01ch11pyo03.md) View。

**必需参数**

*viewVector*

三个 Float 的序列，指定视图向量（从相机到模型原点的方向）。

**可选参数**

*cameraUpVector*

三个 Float 的序列，指定相机的向上向量（屏幕的正 *Y* 轴）。初始值为 (0, 0, 0)。

*drawImmediately*

一个 Boolean，指定在处理命令后立即刷新视口。此参数通常仅在编写脚本时使用，期望在脚本完成前显示中间结果。默认值为 False。

**返回值**

无。

**异常**

无。

### 54.1.12 zoom(...)

此方法在视口中放大视图。

**必需参数**

*zoomFactor*

一个 Float，指定缩放数量。可能的值为 0.000001  ![](../graphics/ker_eqn00013.gif) *zoomFactor*  ![](../graphics/ker_eqn00013.gif) 1000000。小于 1 的 *zoomFactor* 会缩小图像。大于 1 的 *zoomFactor* 会放大图像。

**可选参数**

*mode*

一个 SymbolicConstant，指定缩放的执行方式。可能的值为：
- ABSOLUTE：执行 `fitView`，然后缩放。
- RELATIVE：从当前相机设置缩放。

默认值为 ABSOLUTE。

*asMovie*

一个 Boolean，指定是否使用 `zoom` 视图操作的替代模式。默认值为 OFF。此参数不适用于 [Layer](pt01ch11pyo03.md) View。

*drawImmediately*

一个 Boolean，指定在处理命令后立即刷新视口。此参数通常仅在编写脚本时使用，期望在脚本完成前显示中间结果。默认值为 False。

**返回值**

无。

**异常**

RangeError。

### 54.1.13 zoomRectangle(...)

此方法用给定矩形内的图形填充视口。

**必需参数**

*point1*

一对 Float，指定矩形一角的 *X* 和 *Y* 坐标（相对于视口宽度和高度的分数）。

*point2*

一对 Float，指定矩形另一角的 *X* 和 *Y* 坐标（相对于视口宽度和高度的分数）。

**可选参数**

*drawImmediately*

一个 Boolean，指定在处理命令后立即刷新视口。此参数通常仅在编写脚本时使用，期望在脚本完成前显示中间结果。默认值为 False。

**返回值**

无。

**异常**

无。

### 54.1.14 成员

View 对象具有与 [View](pt01ch54pyo01.md#ker-view-view-pyc) 方法的参数具有相同名称和描述的成员。

此外，View 对象具有以下成员：

*displayedObjectScreenWidth*

一个 Float，指定视口内容周围边界矩形的视口毫米宽度。此值不包括注释或符号，也不会裁剪到视口窗口的大小。

*displayedObjectScreenHeight*

一个 Float，指定视口内容周围边界矩形的视口毫米高度。此值不包括注释或符号，也不会裁剪到视口窗口的大小。

*layerTransform*

一个 Float 元组，指定用于在视口内定位 [Layer](pt01ch11pyo03.md) 内容的变换矩阵。
