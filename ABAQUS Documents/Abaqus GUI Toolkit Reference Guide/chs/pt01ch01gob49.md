# AFXSpinner





此类包含一个标签和微调框，允许用户通过单击其箭头按钮来指定值。
![](../graphics/gui-afxspinner.png)

### AFXSpinner(p, ncols, labelText, tgt=None, sel=0, opts=0, x=0, y=0, w=0, h=0, pl=DEFAULT_PAD, pr=DEFAULT_PAD, pt=DEFAULT_PAD, pb=DEFAULT_PAD)

构造函数。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| p | FXComposite |  | 父窗口部件。 |
| ncols | Int |  | 列数。 |
| labelText | String |  | 标签字符串。 |
| tgt | FXObject | None | 消息目标。 |
| sel | Int | 0 | 消息 ID |
| opts | Int | 0 | 选项和提示。 |
| x | Int | 0 | 原点的 X 坐标。 |
| y | Int | 0 | 原点的 Y 坐标。 |
| w | Int | 0 | 窗口部件的宽度。 |
| h | Int | 0 | 窗口部件的高度。 |
| pl | Int | DEFAULT_PAD | 左边距（填充）。 |
| pr | Int | DEFAULT_PAD | 右边距（填充）。 |
| pt | Int | DEFAULT_PAD | 顶部边距（填充）。 |
| pb | Int | DEFAULT_PAD | 底部边距（填充）。 |

### create()

创建微调框。

从 FXComposite 重新实现。

### disable()

禁用微调框。

从 FXWindow 重新实现。

### enable()

启用微调框。

从 FXWindow 重新实现。

### getCheck()

返回复选按钮或单选按钮的状态。

### getHelpText()

返回状态栏帮助文本。

### getIncrement()

返回微调框增量。

### getLabelFont()

返回标签字体。

### getLabelText()

返回标签字符串。

### getRange()

返回表示窗口部件允许的最小和最大值的整数序列（low, high）。

### getTipText()

返回工具提示消息。

### getValue()

返回微调框值。

### isEditable()

如果文本字段中的文本可以被编辑，则返回 True。

### isReadOnlyState()

如果微调框显示为只读状态，则返回 True。

### setCheck(state)

设置复选按钮或单选按钮的状态。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| state | Bool |  | 状态。 |

### setCheckButtonSelector(sel)

设置复选按钮或单选按钮的消息 ID。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| sel | Int |  | 选择器。 |

### setCheckButtonTarget(tgt)

设置复选按钮或单选按钮的消息目标。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| tgt | FXObject |  | 目标。 |

### setEditable(edit=True)

设置输入字段的可编辑状态。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| edit | Bool | True | 如果为 True，则输入字段可编辑。 |

### setHelpText(text)

设置状态栏帮助文本。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| text | String |  | 帮助文本。 |

### setIncrement(incr)

设置微调框增量。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| incr | Int |  | 增量。 |

### setLabelFont(fnt)

设置标签字体。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| fnt | FXFont |  | 标签字体。 |

### setLabelText(txt)

设置标签字符串。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| txt | String |  | 标签文本。 |

### setRange(low, high)

设置微调框范围。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| low | Int |  | 最小值。 |
| high | Int |  | 最大值。 |

### setReadOnlyState(readonly=True)

设置微调框的只读状态。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| readonly | Bool | True | 状态。 |

### setTipText(text)

设置工具提示消息。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| text | String |  | 工具提示文本。 |

### setValue(val, notify=False)

设置微调框的值。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| val | Int |  | 值。 |
| notify | Bool | False | 通知标志。 |

### 类标志

### ** **

| **ID_BUTTON** | 复选或单选按钮的 ID。 |
| --- | --- |
| **ID_SPINNER** | 微调框的 ID。 |

### 全局标志

### **AFX 微调框选项的标志。**

| **AFXSPINNER_CHECKBUTTON** | 使用复选按钮代替标签。 |
| --- | --- |
| **AFXSPINNER_RADIOBUTTON** | 使用单选按钮代替标签。 |
| **AFXSPINNER_VERTICAL** | 将标签或按钮定向在微调框上方。 |
| **AFXSPINNER_READONLY** | 将微调框配置为只读状态。 |



