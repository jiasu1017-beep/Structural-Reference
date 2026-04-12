# FXLabel









标签窗口部件可用于放置文本和/或图标以进行说明。文本标签可以有可选的工具提示和/或帮助字符串。
![](../graphics/gui-fxlabel.png)

### FXLabel(p, text, ic=None, opts=LABEL_NORMAL, x=0, y=0, w=0, h=0, pl=DEFAULT_PAD, pr=DEFAULT_PAD, pt=DEFAULT_PAD, pb=DEFAULT_PAD)

使用给定文本和图标构造标签。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| p | FXComposite |  |  |
| text | String |  |  |
| ic | FXIcon | None |  |
| opts | Int | LABEL_NORMAL |  |
| x | Int | 0 |  |
| y | Int | 0 |  |
| w | Int | 0 |  |
| h | Int | 0 |  |
| pl | Int | DEFAULT_PAD |  |
| pr | Int | DEFAULT_PAD |  |
| pt | Int | DEFAULT_PAD |  |
| pb | Int | DEFAULT_PAD |  |

### create()

创建服务器端资源。

从 FXWindow 重新实现。

在 FXMenuButton、FXOptionMenu、FXToggleButton 和 AFXFlyoutButton 中重新实现。

### detach()

分离服务器端资源。

从 FXWindow 重新实现。

在 FXMenuButton、FXOptionMenu、FXToggleButton 和 AFXFlyoutButton 中重新实现。

### disable()

禁用窗口。

从 FXWindow 重新实现。

在 AFXFlyoutButton 中重新实现。

### enable()

启用窗口。

从 FXWindow 重新实现。

在 AFXFlyoutButton 中重新实现。

### getDefaultHeight()

返回默认高度。

从 FXFrame 重新实现。

在 FXCheckButton、FXMDIDeleteButton、FXMDIRestoreButton、FXMDIMaximizeButton、FXMDIMinimizeButton、FXMDIWindowButton、FXMenuButton、FXOption、FXOptionMenu、FXRadioButton 和 FXToggleButton 中重新实现。

### getDefaultWidth()

返回默认宽度。

从 FXFrame 重新实现。

在 FXCheckButton、FXMDIDeleteButton、FXMDIRestoreButton、FXMDIMaximizeButton、FXMDIMinimizeButton、FXMDIWindowButton、FXMenuButton、FXOption、FXOptionMenu、FXRadioButton 和 FXToggleButton 中重新实现。

### getFont()

获取文本字体。

### getHelpText()

获取此标签的状态栏帮助文本。

### getIcon()

获取此标签的图标。

### getIconPosition()

获取当前图标位置。

### getJustify()

获取当前文本对齐模式。

### getText()

获取此标签的文本。

### getTextColor()

获取当前文本颜色。

### getTipText()

获取此标签的工具提示消息。

### setFont(fnt)

设置文本字体。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| fnt | FXFont |  |  |

### setHelpText(text)

设置此标签的状态栏帮助文本。

在 AFXFlyoutItem 中重新实现。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| text | String |  |  |

### setIcon(ic)

设置此标签的图标。

在 AFXFlyoutItem 中重新实现。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| ic | FXIcon |  |  |

### setIconPosition(mode)

设置当前图标位置。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| mode | Int |  |  |

### setJustify(mode)

设置当前文本对齐模式。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| mode | Int |  |  |

### setText(text)

设置此标签的文本。

在 AFXFlyoutItem 中重新实现。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| text | String |  |  |

### setTextColor(clr)

设置当前文本颜色。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| clr | FXColor |  |  |

### setTipText(text)

设置此标签的工具提示消息。

在 AFXFlyoutItem 中重新实现。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| text | String |  |  |

### 全局标志

### **图标标签的关系选项**

| **ICON_UNDER_TEXT** | 图标显示在文本下方。 |
| --- | --- |
| **ICON_AFTER_TEXT** | 图标显示在文本之后（右侧）。 |
| **ICON_BEFORE_TEXT** | 图标显示在文本之前（左侧）。 |
| **ICON_ABOVE_TEXT** | 图标显示在文本上方。 |
| **ICON_BELOW_TEXT** | 图标显示在文本下方。 |
| **TEXT_OVER_ICON** | 与 ICON_UNDER_TEXT 相同。 |
| **TEXT_AFTER_ICON** | 与 ICON_BEFORE_TEXT 相同。 |
| **TEXT_BEFORE_ICON** | 与 ICON_AFTER_TEXT 相同。 |
| **TEXT_ABOVE_ICON** | 与 ICON_BELOW_TEXT 相同。 |
| **TEXT_BELOW_ICON** | 与 ICON_ABOVE_TEXT 相同。 |

### **显示标签的正常方式**

| **LABEL_NORMAL** | JUSTIFY_NORMAL 和 ICON_BEFORE_TEXT 的组合。 |
| --- | --- |





