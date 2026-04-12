# FXMenuCommand









菜单命令窗口部件用于从菜单中调用应用程序中的命令。菜单命令可以通过变灰、隐藏或通过复选标记或项目符号来反映应用程序的状态。
![](../graphics/gui-fxmenucommand.png)

### FXMenuCommand(p, text, ic=None, tgt=None, sel=0, opts=0)

构造菜单命令。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| p | FXComposite |  |  |
| text | String |  |  |
| ic | FXIcon | None |  |
| tgt | FXObject | None |  |
| sel | Int | 0 |  |
| opts | Int | 0 |  |

### canFocus()

是的，它可以接收焦点。

从 FXWindow 重新实现。

### check()

在文本旁放置复选标记。

### checkRadio()

在文本旁放置单选项目符号。

### getAccelText()

返回加速器文本。

### getDefaultHeight()

返回默认高度。

从 FXMenuCaption 重新实现。

### getDefaultWidth()

返回默认宽度。

从 FXMenuCaption 重新实现。

### isChecked()

如果已选中则返回 True。

### isRadioChecked()

如果已单选选中则返回 True。

### setAccelText(text)

设置加速器文本。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| text | String |  |  |

### uncheck()

取消选中该项。

### uncheckRadio()

取消单选项目符号。

### 全局标志

### **菜单命令可以处于的状态**

| **MENUSTATE_NORMAL** | 正常、未选中状态。 |
| --- | --- |
| **MENUSTATE_CHECKED** | 用复选标记选中。 |
| **MENUSTATE_RCHECKED** | 用项目符号选中。 |



