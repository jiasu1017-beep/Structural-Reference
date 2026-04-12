# AFXFlyoutButton






该类包含一个按钮，当快速按下和释放时表现得像常规 FXButton，但当按下并保持一小段时间时会显示弹出菜单。
![](../graphics/gui-afxflyoutbutton.png)

### AFXFlyoutButton(p, pup=None, act=0, opts=AFXFLYOUT_NORMAL, x=0, y=0, w=0, h=0, pl=0, pr=0, pt=0, pb=0)

构造函数。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| p | FXComposite |  | 父 widget。 |
| pup | FXPopup | None | 包含飞出条目的弹出菜单。 |
| act | Int | 0 | 当前按钮索引（从零开始）。 |
| opts | Int | AFXFLYOUT_NORMAL | 选项和提示。 |
| x | Int | 0 | 原点 X 坐标。 |
| y | Int | 0 | 原点 Y 坐标。 |
| w | Int | 0 | widget 的宽度。 |
| h | Int | 0 | widget 的高度。 |
| pl | Int | 0 | 左边距。 |
| pr | Int | 0 | 右边距。 |
| pt | Int | 0 | 顶边距。 |
| pb | Int | 0 | 底边距。 |

### canFocus()

返回 True（因为飞出按钮可以接收焦点）。

从 FXWindow 重新实现。

### create()

创建飞出按钮。

从 FXLabel 重新实现。

### detach()

分离飞出按钮的服务器端资源。

从 FXLabel 重新实现。

### disable()

禁用飞出按钮。

从 FXLabel 重新实现。

### enable()

启用飞出按钮。

从 FXLabel 重新实现。

### getButtonStyle()

返回飞出按钮样式。

### getCurrentItem()

返回当前条目。

### getPane()

返回弹出菜单。

### getState()

返回飞出按钮状态。

### setButtonStyle(style)

设置飞出按钮样式。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| style | Int |  | 按钮样式（请参阅"飞出按钮选项的标志"）。 |

### setCurrentItem(item)

设置当前条目。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| item | AFXFlyoutItem |  | 条目。 |

### setCurrentItem(index, setCheck=False)

设置当前条目，如果 setCheck 为 True 则按下按钮。指定的条目索引从零开始计数，仅计算有效条目（分隔符等不计）。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| index | Int |  | 索引。 |
| setCheck | Bool | False | 复选按钮的值。 |

### setPane(pup)

设置弹出菜单。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| pup | FXPopup |  | 弹出菜单。 |

### setState(state)

设置飞出按钮状态。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| state | Int |  | 状态（请参阅 FXButton 的按钮状态位）。 |

### 类标志

### **消息 ID。**

| **ID_AFXFLYOUT_TIMER** | 弹出计时器的 ID。 |
| --- | --- |
| **ID_HIDE_ITEM** | 隐藏飞出条目时使用的 ID。 |

### 全局标志

### **飞出按钮选项的标志。**

| **AFXFLYOUT_AUTOGRAY** | 当没有目标时自动变灰。 |
| --- | --- |
| **AFXFLYOUT_AUTOHIDE** | 当没有目标时自动隐藏。 |
| **AFXFLYOUT_TOOLBAR** | 工具栏样式按钮。 |
| **AFXFLYOUT_HORIZONTAL** | 弹出水平。 |
| **AFXFLYOUT_VERTICAL** | 弹出垂直。 |
| **AFXFLYOUT_RADIO** | 当前条目始终处于活动状态。 |




