# 11.6 MovieOptions 对象

MovieOptions 对象存储控制如何在特定视口中渲染动画电影背景的设置。MovieOptions 对象从与特定视口关联的电影选项访问。

MovieOptions 对象没有构造函数；Abaqus 在创建视口时使用当前视口的 *movieOptions* 成员中的值创建视口的 *movieOptions* 成员。

**访问**

```
session.viewports[*name*].movieOptions
```

### 11.6.1 setValues(...)

此方法修改 MovieOptions 对象。

**必需参数**

无。

**可选参数**

*movieName*

String，指定电影的名称。有效电影名称列表在 *session* 对象的 *movies* 存储库中。

*showMovie*

Boolean，指定在动画过程中是否应在视口中显示电影。默认值为 OFF。

*positionMethod*

SymbolicConstant，指定使用哪种定位方法来确定电影帧如何在视口中缩放和定位。可能的值为：
- FIT_TO_VIEWPORT，指定一种显示模式，其中电影帧使用指定的 *fitMethod* 缩放以适应视口。
- AUTO_ALIGN，指定一种显示模式，其中电影帧按 *xScale* 和 *yScale* 指定进行缩放，然后使用指定的 *alignment* 在视口中定位。
- MANUAL，指定一种显示模式，其中电影帧按 *xScale* 和 *yScale* 指定进行缩放，然后使用指定的 *origin* 在视口中定位。

默认值为 FIT_TO_VIEWPORT。

*fitMethod*

SymbolicConstant，指定当 *positionMethod* =FIT_TO_VIEWPORT 时执行哪种类型的适配来缩放和定位视口中的电影帧。可能的值为：
- BEST_FIT，指定一种模式，其中电影帧被缩放以完全适应视口。
- FIT_WIDTH，指定一种模式，其中电影帧宽度被缩放以匹配视口宽度。
- FIT_HEIGHT，指定一种模式，其中电影帧高度被缩放以匹配视口高度。

默认值为 BEST_FIT。

*alignment*

SymbolicConstant，指定当 *positionMethod* =AUTO_ALIGN 时电影帧在视口中的相对位置。可能的值为：
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

Float，指定应用于电影帧宽度的缩放比例。当 *positionMethod* =FIT_TO_VIEWPORT 时，*xScale* 参数被忽略。默认值为 1.0。

当 *xScale* 为负时，电影帧围绕其 y 轴镜像，但其位置不受影响。

*yScale*

Float，指定应用于电影帧高度的缩放比例。当 *positionMethod* =FIT_TO_VIEWPORT 时，*yScale* 参数被忽略。默认值为 1.0。

当 *yScale* 为负时，电影帧围绕其 x 轴镜像，但其位置不受影响。

*origin*

Float 对，指定从视口左下角的 X 和 Y 偏移量（毫米）。除非 *positionMethod* =MANUAL，否则 *origin* 参数被忽略。默认值为 (0, 0)。

*translucency*

Float，指定显示电影帧时使用的半透明因子。可能的值为 0.0 ![](../graphics/ker_eqn00013.gif) *translucency* ![](../graphics/ker_eqn00013.gif) 1.0，其中 0.0 不可见，1.0 不透明。默认值为 1.0。

*options*

`None` 或 MovieOptions 对象，指定要从中复制值的对象。如果还向 `setValues` 提供了其他参数，它们将覆盖 *options* 成员中的值。默认值为 `None`。

**返回值**

无。

**异常**

RangeError。

### 11.6.2 成员

MovieOptions 对象的成员与 [setValues](pt01ch11pyo06.md#ker-movieoptions-setvalues-pyc) 方法的参数具有相同的名称和描述。
