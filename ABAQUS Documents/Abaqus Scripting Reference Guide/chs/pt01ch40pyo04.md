# 40.4 DisplayOptions 对象

DisplayOptions 对象存储绘图状态。

**访问**

```
import visualization
session.viewports[*name*].layers[*name*].odbDisplay.display
session.viewports[*name*].odbDisplay.display
```

### 40.4.1 setValues(...)

此方法修改 DisplayOptions 对象。

**必需参数**

无。

**可选参数**

*options*

 DisplayOptions 对象，指定要复制的值。如果还有其他参数提供给 `setValues`，它们将覆盖 *options* 中的值。默认值为 `None`。

*plotState*

 SymbolicConstant 序列，指定显示的绘图状态。可选值为 UNDEFORMED、DEFORMED、CONTOURS_ON_UNDEF、CONTOURS_ON_DEF、SYMBOLS_ON_UNDEF、SYMBOLS_ON_DEF、ORIENT_ON_UNDEF 和 ORIENT_ON_DEF。默认值为 (UNDEFORMED)。

**返回值**

无

**异常**

无。

### 40.4.2 成员

DisplayOptions 对象可以具有以下成员：

*plotState*

 SymbolicConstant 元组，指定显示的绘图状态。可选值为 UNDEFORMED、DEFORMED、CONTOURS_ON_UNDEF、CONTOURS_ON_DEF、SYMBOLS_ON_UNDEF、SYMBOLS_ON_DEF、ORIENT_ON_UNDEF 和 ORIENT_ON_DEF。默认值为 (UNDEFORMED)。

