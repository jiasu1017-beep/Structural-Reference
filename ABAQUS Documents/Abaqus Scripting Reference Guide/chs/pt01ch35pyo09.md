# 35.9 ViewCut 对象

ViewCut 对象用于存储与 ViewCut 类型对象关联的值和属性。可以使用以下方法创建 ViewCut 对象。通过 [OdbDisplay](pt01ch35pyo01.md) 对象访问的方法会将 ViewCut 对象添加到 session.viewports[name].odbDisplay.viewCuts 仓库。

**访问**

```
import visualization
session.viewports[*name*].layers[*name*].odbDisplay.viewCuts[*name*]
session.viewports[*name*].odbDisplay.viewCuts[*name*]
```

### 35.9.1 ViewCut(...)

此方法创建 ViewCut 对象。

**路径**

```
session.viewports[*name*].layers[*name*].odbDisplay.ViewCut
session.viewports[*name*].odbDisplay.ViewCut
```

**必要参数**

*name*

一个字符串，指定仓库键。

*shape*

一个 SymbolicConstant，指定 ViewCut 对象的形状。可能的值为 PLANE、CYLINDER、SPHERE 和 ISOSURFACE。

*origin*

三个浮点数序列，指定平面、圆柱或球体切割的原点 X、Y 和 Z 坐标。如果切割形状为 ISOSURFACE 或切割由 *csysName* 参数定义，则不需要此原点。

*normal*

当使用 *origin* 参数定义平面时，指定定义切割的平面的法线轴的 X、Y 和 Z 坐标序列；或当切割由 *csysName* 参数定义时，指定定义此法线轴的 SymbolicConstant。可能的值为 AXIS_1、AXIS_2、AXIS_3。如果切割 *shape* 为 CYLINDER、SPHERE 或 ISOSURFACE，则不需要此轴。

*axis2*

当使用 *origin* 参数定义平面时，指定定义切割的平面第二轴的 X、Y 和 Z 坐标序列；或当切割由 *csysName* 参数定义时，指定定义此第二轴的 SymbolicConstant。可能的值为 AXIS_1、AXIS_2、AXIS_3。此轴用于旋转平面切割。如果切割 *shape* 为 CYLINDER、SPHERE 或 ISOSURFACE，则不需要此轴。

*csysName*

一个字符串，指定用于定义切割的 [DatumCsys](pt01ch15pyo03.md) 对象的名称。如果切割 *shape* 为 ISOSURFACE 或切割由 *origin* 参数定义，则不需要此名称。

*cylinderAxis*

当使用 *origin* 参数定义切割时，指定定义切割的圆柱轴的 X、Y 和 Z 坐标序列；或当切割由 *csysName* 参数定义时，指定定义此圆柱轴的 SymbolicConstant。可能的值为 AXIS_1、AXIS_2、AXIS_3。如果切割 *shape* 为 PLANE、SPHERE 或 ISOSURFACE，则不需要此轴。

**可选参数**

*followDeformation*

一个布尔值，指定切割是否跟随变形或保持静态。默认值为 OFF。

*overrideAveraging*

一个布尔值，指定当为真时，与等值面切割关联的基于元素的场的平均将设置为以 100% 阈值计算平均值。当为假时，将使用当前场的选项。默认值为 ON。

*referenceFrame*

一个 SymbolicConstant，指定当切割跟随变形时使用哪个参考帧。可能的值为 FIRST_FRAME、LAST_FRAME 和 CURRENT_FRAME。默认值为 FIRST_FRAME。

**返回值**

ViewCut 对象。

**异常**

无。

### 35.9.2 setValues(...)

此方法修改 ViewCut 对象。

**必要参数**

无。

**可选参数**

必须提供以下至少一个参数：

*angle*

一个 Float，指定当 *shape* 设置为 PLANE 时定义的切割的旋转角度。

*motion*

一个 SymbolicConstant，指定当 *shape* 设置为 PLANE 时定义的切割的运动类型。可能的值为 TRANSLATE 和 ROTATE。默认值为 TRANSLATE。

*position*

一个 Float，指定当 *shape* 设置为 PLANE 时定义的切割的位置。

*radius*

一个 Float，指定当 *shape* 设置为 CYLINDER 或 SPHERE 时定义的切割的半径。

*rotationAxis*

一个 SymbolicConstant，指定当 *shape* 设置为 PLANE 时定义的切割的旋转轴。可能的值为 AXIS_1、AXIS_2 和 AXIS_3。默认值为 AXIS_2。

*value*

一个 Float，指定当 *shape* 设置为 ISOSURFACE 时定义的切割的值。

*showModelAboveCut*

一个布尔值，指定是否显示切割上方的模型。默认值为 OFF。

*showModelOnCut*

一个布尔值，指定是否显示切割上的模型。默认值为 ON。

*showModelBelowCut*

一个布尔值，指定是否显示切割下方的模型。默认值为 ON。

*showFreeBodyCut*

一个布尔值，指定是否显示自由体切割。默认值为 OFF。

*csysName*

一个字符串，指定用于定义切割的 [DatumCsys](pt01ch15pyo03.md) 对象的名称。如果切割 *shape* 为 ISOSURFACE 或切割由 *origin* 参数定义，则不需要此名称。

*origin*

三个浮点数序列，指定平面、圆柱或球体切割的原点 X、Y 和 Z 坐标。如果切割形状为 ISOSURFACE 或切割由 *csysName* 参数定义，则不需要此原点。

*normal*

当使用 *origin* 参数定义平面时，指定定义切割的平面的法线轴的 X、Y 和 Z 坐标序列；或当切割由 *csysName* 参数定义时，指定定义此法线轴的 SymbolicConstant。可能的值为 AXIS_1、AXIS_2、AXIS_3。如果切割 *shape* 为 CYLINDER、SPHERE 或 ISOSURFACE，则不需要此轴。

*axis2*

当使用 *origin* 参数定义平面时，指定定义切割的平面第二轴的 X、Y 和 Z 坐标序列；或当切割由 *csysName* 参数定义时，指定定义此第二轴的 SymbolicConstant。可能的值为 AXIS_1、AXIS_2、AXIS_3。此轴用于旋转平面切割。如果切割 *shape* 为 CYLINDER、SPHERE 或 ISOSURFACE，则不需要此轴。

*cylinderAxis*

当使用 *origin* 参数定义切割时，指定定义切割的圆柱轴的 X、Y 和 Z 坐标序列；或当切割由 *csysName* 参数定义时，指定定义此圆柱轴的 SymbolicConstant。可能的值为 AXIS_1、AXIS_2、AXIS_3。如果切割 *shape* 为 PLANE、SPHERE 或 ISOSURFACE，则不需要此轴。

*followDeformation*

一个布尔值，指定切割是否跟随变形或保持静态。默认值为 OFF。

*overrideAveraging*

一个布尔值，指定当为真时，与等值面切割关联的基于元素的场的平均将设置为以 100% 阈值计算平均值。当为假时，将使用当前场的选项。默认值为 ON。

*referenceFrame*

一个 SymbolicConstant，指定当切割跟随变形时使用哪个参考帧。可能的值为 FIRST_FRAME、LAST_FRAME 和 CURRENT_FRAME。默认值为 FIRST_FRAME。

**返回值**

无

**异常**

无。

### 35.9.3 updateVariable()

此方法更新与等值面切割关联的场，以与当前主要变量保持一致。

**参数**

无。

**返回值**

无

**异常**

无。

### 35.9.4 成员

ViewCut 对象具有与 [ViewCut](pt01ch35pyo09.md#ker-viewcut-viewcut-pyc) 方法的参数名称和描述相同的成员。

此外，ViewCut 对象具有以下成员：

*angle*

一个 Float，指定当 *shape* 设置为 PLANE 时定义的切割的旋转角度。

*motion*

一个 SymbolicConstant，指定当 *shape* 设置为 PLANE 时定义的切割的运动类型。可能的值为 TRANSLATE 和 ROTATE。默认值为 TRANSLATE。

*position*

一个 Float，指定当 *shape* 设置为 PLANE 时定义的切割的位置。

*radius*

一个 Float，指定当 *shape* 设置为 CYLINDER 或 SPHERE 时定义的切割的半径。

*rotationAxis*

一个 SymbolicConstant，指定当 *shape* 设置为 PLANE 时定义的切割的旋转轴。可能的值为 AXIS_1、AXIS_2 和 AXIS_3。默认值为 AXIS_2。

*value*

一个 Float，指定当 *shape* 设置为 ISOSURFACE 时定义的切割的值。

*showModelAboveCut*

一个布尔值，指定是否显示切割上方的模型。默认值为 OFF。

*showModelOnCut*

一个布尔值，指定是否显示切割上的模型。默认值为 ON。

*showModelBelowCut*

一个布尔值，指定是否显示切割下方的模型。默认值为 ON。

*showFreeBodyCut*

一个布尔值，指定是否显示自由体切割。默认值为 OFF。

*active*

一个布尔值，指定是否显示切割。

*cutRange*

一对浮点数，指定定位切割的可接受范围。
