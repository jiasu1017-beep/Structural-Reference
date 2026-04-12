# AFXListBox





此类包含一个标签和列表框，允许用户从下拉列表中选择条目。
![](../graphics/gui-afxlistbox.png)

### AFXListBox(p, nvis, labelText, tgt=None, sel=0, opts=0, x=0, y=0, w=0, h=0, pl=DEFAULT_PAD, pr=DEFAULT_PAD, pt=DEFAULT_PAD, pb=DEFAULT_PAD)

构造函数。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| p | FXComposite |  | 父窗口部件。 |
| nvis | Int |  | 可见项目数。 |
| labelText | String |  | 标签字符串。 |
| tgt | FXObject | None | 消息目标。 |
| sel | Int | 0 | 消息 ID。 |
| opts | Int | 0 | 选项和提示。 |
| x | Int | 0 | 原点的 X 坐标。 |
| y | Int | 0 | 原点的 Y 坐标。 |
| w | Int | 0 | 窗口部件的宽度。 |
| h | Int | 0 | 窗口部件的高度。 |
| pl | Int | DEFAULT_PAD | 左边距（填充）。 |
| pr | Int | DEFAULT_PAD | 右边距（填充）。 |
| pt | Int | DEFAULT_PAD | 顶部边距（填充）。 |
| pb | Int | DEFAULT_PAD | 底部边距（填充）。 |

### appendItem(text, icon=None, sel=0)

在列表末尾添加一个项目。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| text | String |  |  |
| icon | FXIcon | None |  |
| sel | Int | 0 |  |

### clearItems()

从列表中移除所有项目。

### create()

创建列表框。

从 FXComposite 重新实现。

### disable()

禁用列表框。

从 FXWindow 重新实现。

### enable()

启用列表框。

从 FXWindow 重新实现。

### getCurrentItem()

返回当前项目的索引。

### getHelpText()

返回状态栏帮助文本。

### getItemData(index)

返回指定项目的数据。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  |  |

### getItemIndexForData(data)

返回具有关联数据的第一个项目的索引，如果未找到则返回 -1。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| data |  |  |  |

### getLabelFont()

返回标签字体。

### getLabelText()

返回标签字符串。

### getNumItems()

返回列表中的项目数。

### getNumVisible()

返回可见项目数。

### getTipText()

返回工具提示消息。

### insertItem(index, text, icon=None, sel=0)

在指定索引位置插入一个新项目。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  |  |
| text | String |  |  |
| icon | FXIcon | None |  |
| sel | Int | 0 |  |

### isItemCurrent(index)

如果指定索引位置的项目是当前项目，则返回 True。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  |  |

### isReadOnlyState()

如果列表框设置为只读状态，则返回 True。

### removeItem(index)

从列表中移除指定索引位置的项目。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  |  |

### replaceItem(index, text, icon=None, sel=0)

替换指定索引位置的项目。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  |  |
| text | String |  |  |
| icon | FXIcon | None |  |
| sel | Int | 0 |  |

### setCurrentItem(index, notify=False)

设置当前项目。（索引从零开始）。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  |  |
| notify | Bool | False |  |

### setHelpText(text)

设置状态栏帮助文本。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| text | String |  |  |

### setItemData(index, ptr)

设置指定项目的数据。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  |  |
| ptr | String |  |  |

### setLabelFont(fnt)

设置标签字体。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| fnt | FXFont |  |  |

### setLabelText(txt)

设置标签字符串。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| txt | String |  |  |

### setNumVisible(nvis)

设置可见项目数。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| nvis | Int |  |  |

### setReadOnlyState(readonly=True)

设置列表框的只读状态。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| readonly | Bool | True |  |

### setTipText(text)

设置工具提示消息。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| text | String |  |  |

### 类标志

### **消息 ID。**

| **ID_LIST** | 列表框的 ID。 |
| --- | --- |
| **ID_FIELD** | 文本字段的 ID。 |

### 全局标志

### **AFX 列表框选项的标志。**

| **AFXLISTBOX_VERTICAL** | 将标签定向在列表框上方。 |
| --- | --- |
| **AFXLISTBOX_READONLY** | 将列表框配置为只读状态。 |



