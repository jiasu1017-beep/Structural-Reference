# FXMenuCaption









菜单标题是一个窗口部件，可用作为菜单中多个菜单命令上方的标题。
![](../graphics/gui-fxmenucaption.png)

### FXMenuCaption(p, text, ic=None, opts=0)

构造菜单标题。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| p | FXComposite |  |  |
| text | String |  |  |
| ic | FXIcon | None |  |
| opts | Int | 0 |  |

### create()

创建服务器端资源。

从 FXWindow 重新实现。

在 FXMenuCascade 和 FXMenuTitle 中重新实现。

### detach()

分离服务器端资源。

从 FXWindow 重新实现。

在 FXMenuCascade 和 FXMenuTitle 中重新实现。

### disable()

禁用菜单。

从 FXWindow 重新实现。

### enable()

启用菜单。

从 FXWindow 重新实现。

### getDefaultHeight()

返回默认高度。

从 FXWindow 重新实现。

在 FXMenuCommand 和 FXMenuTitle 中重新实现。

### getDefaultWidth()

返回默认宽度。

从 FXWindow 重新实现。

在 FXMenuCommand 和 FXMenuTitle 中重新实现。

### getFont()

返回文本字体。

### getIcon()

获取此菜单的图标。

### getText()

获取此菜单的文本。

### getTextColor()

获取当前文本颜色。

### setFont(fnt)

设置文本字体。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| fnt | FXFont |  |  |

### setIcon(ic)

设置此菜单的图标。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| ic | FXIcon |  |  |

### setText(text)

设置此菜单的文本。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| text | String |  |  |

### setTextColor(clr)

返回当前文本颜色。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| clr | FXColor |  |  |

### 全局标志

### **菜单标题选项**

| **MENU_AUTOGRAY** | 当未更新时自动变灰。 |
| --- | --- |
| **MENU_AUTOHIDE** | 当未更新时自动隐藏按钮。 |



