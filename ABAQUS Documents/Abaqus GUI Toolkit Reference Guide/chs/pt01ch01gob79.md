# FXGroupBox





组框 widget 在一组 widget 周围提供一个美观的凸起或凹陷边框，提供视觉分隔。通常，在边框上放置一个标题以提供一些说明。在组框内放置的单选按钮自动假定为互斥行为，即在任何给定时间最多只有一个单选按钮被选中。
![](../graphics/gui-fxgroupbox.png)

### FXGroupBox(p, text, opts=GROUPBOX_NORMAL, x=0, y=0, w=0, h=0, pl=DEFAULT_SPACING, pr=DEFAULT_SPACING, pt=DEFAULT_SPACING, pb=DEFAULT_SPACING, hs=DEFAULT_SPACING, vs=DEFAULT_SPACING)

构造组框布局管理器。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| p | FXComposite |  | |
| text | String |  | |
| opts | Int | GROUPBOX_NORMAL | |
| x | Int | 0 | |
| y | Int | 0 | |
| w | Int | 0 | |
| h | Int | 0 | |
| pl | Int | DEFAULT_SPACING | |
| pr | Int | DEFAULT_SPACING | |
| pt | Int | DEFAULT_SPACING | |
| pb | Int | DEFAULT_SPACING | |
| hs | Int | DEFAULT_SPACING | |
| vs | Int | DEFAULT_SPACING | |

### create()

创建服务器端资源。

从 FXComposite 重新实现。

### detach()

分离服务器端资源。

从 FXComposite 重新实现。

### disable()

禁用窗口。

从 FXWindow 重新实现。

### enable()

启用窗口。

从 FXWindow 重新实现。

### getDefaultHeight()

返回默认高度。

从 FXPacker 重新实现。

### getDefaultWidth()

返回默认宽度。

从 FXPacker 重新实现。

### getText()

返回当前组框标题文本。

### setText(text)

更改组框标题文本。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| text | String |  | |

### 全局标志

### **组框选项**

| **GROUPBOX_TITLE_LEFT** | 标题左对齐。 |
| --- | --- |
| **GROUPBOX_TITLE_CENTER** | 标题居中。 |
| **GROUPBOX_TITLE_RIGHT** | 标题右对齐。 |





