# 11.5 ImageOptions 对象

ImageOptions 对象存储控制如何在特定视口中渲染图像的设置。ImageOptions 对象从与特定视口关联的图像选项访问。

ImageOptions 对象没有构造函数；Abaqus 在创建视口时使用当前视口的 *imageOptions* 成员中的值创建视口的 *imageOptions* 成员。

**访问**

```
session.viewports[*name*].imageOptions
```

### 11.5.1 setValues(...)

此方法修改 ImageOptions 对象。

**必需参数**

无。

**可选参数**

*imageName*

String，指定图像的名称。有效图像名称列表在 *session* 对象的 *images* 存储库中。

*showImage*

Boolean，指定是否应在视口背景中显示图像。默认值为 OFF。

*positionMethod*

SymbolicConstant，指定使用哪种定位方法来确定图像如何在视口中缩放和定位。可能的值为：
- FIT_TO_VIEWPORT，指定一种显示模式，其中图像使用指定的 *fitMethod* 缩放以适应视口。
- AUTO_ALIGN，指定一种显示模式，其中图像按 *xScale* 和 *yScale* 指定进行缩放，然后使用指定的 *alignment* 在视口中定位。
- MANUAL，指定一种显示模式，其中图像按 *xScale* 和 *yScale* 指定进行缩放，然后使用指定的 *origin* 在视口中定位。

默认值为 FIT_TO_VIEWPORT。

*fitMethod*

SymbolicConstant，指定当 *positionMethod* =FIT_TO_VIEWPORT 时执行哪种类型的适配来缩放和定位视口中的图像。可能的值为：
- BEST_FIT，指定一种模式，其中图像被缩放以完全适应视口。
- FIT_WIDTH，指定一种模式，其中图像宽度被缩放以匹配视口宽度。
- FIT_HEIGHT，指定一种模式，其中图像高度被缩放以匹配视口高度。

默认值为 BEST_FIT。

*alignment*

SymbolicConstant，指定当 *positionMethod* =AUTO_ALIGN 时图像在视口中的相对位置。可能的值为：
- BOTTOM_LEFT
- BOTTOM_CENTER
- BOTTOM_RIGHT
- CENTER_LEFT
- CENTER
- CENTER_RIGHT
- TOP_LEFT
- TOP_CENTER
- TOP_RIGHT

默认值为 CENTER。

*xScale*

Float，指定应用于图像宽度的缩放比例。当 *positionMethod* =FIT_TO_VIEWPORT 时，*xScale* 参数被忽略。默认值为 1.0。

当 *xScale* 为负时，图像围绕其 y 轴镜像，但其位置不受影响。

*yScale*

Float，指定应用于图像高度的缩放比例。当 *positionMethod* =FIT_TO_VIEWPORT 时，*yScale* 参数被忽略。默认值为 1.0。

当 *yScale* 为负时，图像围绕其 x 轴镜像，但其位置不受影响。

*origin*

Float 对，指定从视口左下角的 X 和 Y 偏移量（毫米）。除非 *positionMethod* =MANUAL，否则 *origin* 参数被忽略。默认值为 (0, 0)。

*translucency*

Float，指定显示图像时使用的半透明因子。可能的值为 0.0 ![](../graphics/ker_eqn00013.gif) *translucency* ![](../graphics/ker_eqn00013.gif) 1.0，其中 0.0 不可见，1.0 不透明。默认值为 1.0。

*options*

`None` 或 ImageOptions 对象，指定要从中复制值的对象。如果还向 `setValues` 提供了其他参数，它们将覆盖 *options* 成员中的值。默认值为 `None`。

**返回值**

无。

**异常**

RangeError。

### 11.5.2 成员

ImageOptions 对象的成员与 [setValues](pt01ch11pyo05.md#ker-imageoptions-setvalues-pyc) 方法的参数具有相同的名称和描述。
