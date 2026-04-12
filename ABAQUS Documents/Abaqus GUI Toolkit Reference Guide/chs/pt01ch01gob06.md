# AFXComboBox






该类包含一个标签和组合框，允许用户从下拉列表中选择条目。
![](../graphics/gui-afxcombobox.png)

### AFXComboBox(p, ncols, nvis, text, tgt=None, sel=0, opts=0, x=0, y=0, w=0, h=0, pl=DEFAULT_PAD, pr=DEFAULT_PAD, pt=DEFAULT_PAD, pb=DEFAULT_PAD)

构造函数。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| p | FXComposite |  | 父 widget。 |
| ncols | Int |  | 组合框中的列数（使用 0 自动调整大小）。 |
| nvis | Int |  | 组合框下拉列表中可见的条目数。 |
| text | String |  | 标签字符串。 |
| tgt | FXObject | None | 消息目标。 |
| sel | Int | 0 | 消息 ID。 |
| opts | Int | 0 | 选项和提示。 |
| x | Int | 0 | 原点 X 坐标。 |
| y | Int | 0 | 原点 Y 坐标。 |
| w | Int | 0 | widget 的宽度。 |
| h | Int | 0 | widget 的高度。 |
| pl | Int | DEFAULT_PAD | 左边距。 |
| pr | Int | DEFAULT_PAD | 右边距。 |
| pt | Int | DEFAULT_PAD | 顶边距。 |
| pb | Int | DEFAULT_PAD | 底边距。 |

### appendItem(text, sel=0)

将条目添加到列表末尾。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| text | String |  | 文本。 |
| sel | Int | 0 | 选择器。 |

### clearItems()

从列表中移除所有条目。

### create()

创建组合框。

从 FXComposite 重新实现。

### disable()

禁用组合框。

从 FXWindow 重新实现。

### enable()

启用组合框。

从 FXWindow 重新实现。

### getCheck()

返回复选按钮或单选按钮的状态。

### getCurrentItem()

返回当前条目的索引。

### getHelpText()

返回状态栏帮助文本。

### getItemData(index)

返回指定条目的数据。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| index | Int |  | 索引。 |

### getItemIndexForData(data)

返回具有关联数据的第一个条目的索引，如果未找到则返回 -1。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| data |  |  |  |

### getItemIndexForFloat(val)

返回文本计算为给定值的第一个条目的索引。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| val | Float |  |  |

### getItemProvider()

返回组合框条目的提供者。

### getItemText(index)

返回指定条目的文本。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| index | Int |  | 索引。 |

### getLabelFont()

返回标签字体。

### getLabelText()

返回标签字符串。

### getNumColumns()

返回列数。

### getNumItems()

返回列表中的条目数。

### getNumVisible()

返回可见条目数。

### getText()

返回输入字段中显示的文本。

### getTipText()

返回工具提示消息。

### insertItem(index, text, sel=0)

在指定索引位置插入新条目。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| index | Int |  | 索引。 |
| text | String |  | 文本。 |
| sel | Int | 0 | 选择器。 |

### isEditable()

如果输入字段中的文本可以编辑，则返回 True。

### isItemCurrent(index)

如果指定索引位置的条目是当前条目，则返回 True。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| index | Int |  | 索引。 |

### isReadOnlyState()

如果组合框处于只读状态，则返回 True。

### removeItem(index)

从列表中移除指定索引位置的条目。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| index | Int |  | 索引。 |

### replaceItem(index, text, sel=0)

替换指定索引位置的条目。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| index | Int |  | 索引。 |
| text | String |  | 文本。 |
| sel | Int | 0 | 选择器。 |

### setCheck(state)

设置复选按钮或单选按钮的状态。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| state | Bool |  | 按钮状态。 |

### setCheckButtonSelector(sel)

设置复选按钮或单选按钮的消息 ID。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| sel | Int |  | 选择器。 |

### setCheckButtonTarget(tgt, checkVal=False)

设置复选按钮或单选按钮的消息目标。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| tgt | FXObject |  | 目标。 |
| checkVal | Bool | False | 复选按钮的值。 |

### setCurrentItem(index)

设置当前条目（索引从零开始）。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| index | Int |  | 索引。 |

### setEditable(edit=True)

设置输入字段的可编辑状态。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| edit | Bool | True | 可编辑状态。 |

### setFocusAndSelection()

将焦点移到输入字段，如果组合框可编辑则选择其内容。

### setFocusToCheckButton()

将焦点移到 widget 的复选按钮或单选按钮（如果存在）。

### setFocusToComboBox()

将焦点移到 widget 的输入字段。

### setHelpText(text)

设置状态栏帮助文本。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| text | String |  | 帮助文本。 |

### setItemData(index, ptr)

设置指定条目的数据。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| index | Int |  | 索引。 |
| ptr | String |  | 数据。 |

### setItemProvider(cp)

设置此对象条目的提供者。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| cp | FXObject |  | 条目提供者。 |

### setItemText(index, text)

设置指定条目的文本。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| index | Int |  | 索引。 |
| text | String |  | 文本。 |

### setLabelFont(fnt)

设置标签字体。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| fnt | FXFont |  | 标签字体。 |

### setLabelText(txt)

设置标签字符串。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| txt | String |  | 标签文本。 |

### setMaxVisible(maxVis)

设置可见条目的最大数量。组合框将在其列表中显示最多给定最大数量的条目。如果组合框有更多条目，其列表将显示滚动条。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| maxVis | Int |  | 可见条目的最大数量。 |

### setNumColumns(cols)

设置组合框中的列数；传递零将导致组合框始终具有等于最大条目长度的列数。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| cols | Int |  | 列数。 |

### setNumVisible(nvis)

设置可见条目数。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| nvis | Int |  | 可见条目数。 |

### setReadOnlyState(readonly=True)

设置组合框的只读状态。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| readonly | Bool | True | 只读状态。 |

### setText(txt)

设置输入字段中显示的文本。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| txt | String |  | 输入字段文本。 |

### setTipText(text)

设置工具提示消息。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| text | String |  | 工具提示文本。 |

### 类标志

### **消息 ID。**

| **ID_BUTTON** | 标签或按钮 ID。 |
| --- | --- |
| **ID_COMBO** | 组合框 ID。 |
| **ID_INCREMENT** | 向上箭头按钮 ID。 |
| **ID_DECREMENT** | 向下箭头按钮 ID。 |

### 全局标志

### **AFX 组合框选项的标志。**

| **AFXCOMBOBOX_CHECKBUTTON** | 使用复选按钮而不是标签。 |
| --- | --- |
| **AFXCOMBOBOX_RADIOBUTTON** | 使用单选按钮而不是标签。 |
| **AFXCOMBOBOX_VERTICAL** | 将标签或按钮置于组合框上方。 |
| **AFXCOMBOBOX_FLOAT** | 允许与浮点关键字交互。 |
| **AFXCOMBOBOX_READONLY** | 将组合框配置为只读状态。 |
| **AFXCOMBOBOX_SPINNER** | 包含微调按钮。 |




