# FXButton





按钮提供一个带有可选图标和/或文本标签的按钮。当按下时，按钮 widget 向其目标发送 SEL_COMMAND。
![](../graphics/gui-fxbutton.png)

### FXButton(p, text, ic=None, tgt=None, sel=0, opts=BUTTON_NORMAL, x=0, y=0, w=0, h=0, pl=DEFAULT_PAD, pr=DEFAULT_PAD, pt=DEFAULT_PAD, pb=DEFAULT_PAD)

构造带有文本和图标的按钮。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| p | FXComposite |  | |
| text | String |  | |
| ic | FXIcon | None | |
| tgt | FXObject | None | |
| sel | Int | 0 | |
| opts | Int | BUTTON_NORMAL | |
| x | Int | 0 | |
| y | Int | 0 | |
| w | Int | 0 | |
| h | Int | 0 | |
| pl | Int | DEFAULT_PAD | |
| pr | Int | DEFAULT_PAD | |
| pt | Int | DEFAULT_PAD | |
| pb | Int | DEFAULT_PAD | |

### canFocus()

因为按钮可以接收焦点，所以返回 True。

从 FXWindow 重新实现。

在 AFXFlyoutItem 中重新实现。

### getButtonStyle()

获取按钮样式标志。

### getState()

获取按钮状态。

### setButtonStyle(style)

设置按钮样式标志。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| style | Int |  | |

### setDefault(enable=True)

设置为默认按钮。

从 FXWindow 重新实现。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| enable | Bool | True | |

### setState(s)

设置按钮状态。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| s | Int |  | |

### 全局标志

### **按钮状态位**

| **STATE_UP** | 按钮弹起。 |
| --- | --- |
| **STATE_DOWN** | 按钮按下。 |
| **STATE_ENGAGED** | 按钮处于接合状态。 |
| **STATE_UNCHECKED** | 与 STATE_UP 相同（用于复选按钮或单选按钮）。 |
| **STATE_CHECKED** | 与 STATE_ENGAGED 相同（用于复选按钮或单选按钮）。 |

### **按钮标志**

| **BUTTON_AUTOGRAY** | 更新时自动变灰。 |
| --- | --- |
| **BUTTON_AUTOHIDE** | 更新时自动隐藏按钮。 |
| **BUTTON_TOOLBAR** | 工具栏样式按钮【平面外观】。 |
| **BUTTON_DEFAULT** | 接收焦点时可能成为默认按钮。 |
| **BUTTON_INITIAL** | 此按钮是初始默认按钮。 |
| **BUTTON_NORMAL** | 正常按钮样式。 |





