# AFXDialog






该类是所有 Abaqus GUI Toolkit 对话框的基类。
![](../graphics/gui-afxdialog.png)

### AFXDialog(title, actionButtonIds=0, opts=DIALOG_NORMAL, x=0, y=0, w=0, h=0)

创建在与主窗口重叠时始终遮挡主窗口的对话框的构造函数。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| title | String |  | 标题字符串。 |
| actionButtonIds | Int | 0 | 要创建的操作按钮的 ID。 |
| opts | Int | DIALOG_NORMAL | 选项和提示。 |
| x | Int | 0 | 原点 X 坐标。 |
| y | Int | 0 | 原点 Y 坐标。 |
| w | Int | 0 | widget 的宽度。 |
| h | Int | 0 | widget 的高度。 |

### AFXDialog(owner, title, actionButtonIds=0, opts=DIALOG_NORMAL, x=0, y=0, w=0, h=0)

创建在与 widget 重叠时始终遮挡其所有者 widget 的对话框的构造函数。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| owner | FXWindow |  | 所有者 widget。 |
| title | String |  | 标题字符串。 |
| actionButtonIds | Int | 0 | 要创建的操作按钮的 ID。 |
| opts | Int | DIALOG_NORMAL | 选项和提示。 |
| x | Int | 0 | 原点 X 坐标。 |
| y | Int | 0 | 原点 Y 坐标。 |
| w | Int | 0 | widget 的宽度。 |
| h | Int | 0 | widget 的高度。 |

### AFXDialog(app, title, actionButtonIds=0, opts=DIALOG_NORMAL, x=0, y=0, w=0, h=0)

创建可被应用程序任何其他窗口遮挡的对话框的构造函数。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| app | FXApp |  | 应用程序。 |
| title | String |  | 标题字符串。 |
| actionButtonIds | Int | 0 | 要创建的操作按钮的 ID。 |
| opts | Int | DIALOG_NORMAL | 选项和提示。 |
| x | Int | 0 | 原点 X 坐标。 |
| y | Int | 0 | 原点 Y 坐标。 |
| w | Int | 0 | widget 的宽度。 |
| h | Int | 0 | widget 的高度。 |

### appendActionButton(text, tgt, sel)

在对话框的操作区域添加自定义操作按钮。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| text | String |  | 标签字符串。 |
| tgt | FXObject |  | 消息目标。 |
| sel | Int |  | 消息 ID。 |

### appendActionButton(buttonID)

在对话框的操作区域添加标准操作按钮。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| buttonID | ButtonID |  | 按钮 ID。 |

### bailout()

执行检查以确定是否可以取消对话框。此类的实现始终返回 True，派生类应重新实现此方法以执行特定检查。

在 AFXDataDialog 中重新实现。

### create()

创建对话框。

从 FXTopWindow 重新实现。

### createButton(parent, text, icon, tgt, sel, opts)

创建操作区域按钮。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| parent | FXComposite |  | 父 widget。 |
| text | String |  | 标签字符串。 |
| icon | FXIcon |  | 图标。 |
| tgt | FXObject |  | 消息目标。 |
| sel | Int |  | 消息 ID。 |
| opts | Int |  | 选项和提示。 |

### getActionButton(sel)

返回具有指定消息 ID 的操作按钮；如果没有任何操作按钮具有该消息 ID，则返回 0。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| sel | Int |  | 消息 ID。 |

### getInitialFocusWidget()

返回将接收初始焦点的 widget。

### getUnpostHints()

返回张贴者在对话框被取消张贴时应对此对话框执行的操作。可能的返回值有：DIALOG_UNPOST_DELETE - 删除 C++ 对话框对象及其关联窗口。（默认）DIALOG_UNPOST_DESTROY - 保留 C++ 对话框对象，但销毁关联窗口以释放资源。DIALOG_UNPOST_NOTHING - 不执行任何操作。

### hide()

取消张贴对话框。

从 FXTopWindow 重新实现。

在 AFXManagerMenuDB 和 AFXMessageDialog 中重新实现。

### onKeywordError(kwd)

处理给定关键字或目标包含无效内容时发生的错误。此方法将选择以该关键字或目标作为其消息目标的 widget 内容。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| kwd | FXObject |  | 包含无效内容的对象。 |

### onTableError(tableKwd, row, col)

处理给定表格关键字或目标包含无效元素时发生的错误。此方法将选择以该关键字或目标作为其消息目标的 widget 内容。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| tableKwd | FXObject |  | 包含无效元素的对象。 |
| row | Int |  | 行索引。 |
| col | Int |  | 列索引。 |

### onTupleError(tupleKwd, index)

处理给定元组关键字或目标包含无效元素时发生的错误。此方法将选择以该关键字或目标作为其消息目标的 widget 内容。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| tupleKwd | FXObject |  | 包含无效元素的对象。 |
| index | Int |  | 元素索引。 |

### selectContents(widget)

选择给定 widget 的内容。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| widget | FXWindow |  | 要选择的 widget。 |

### selectTableElement(widget, row, col)

选择给定 widget 显示的二维元素数组中的给定（row,col）元素。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| widget | FXWindow |  | 要选择的 widget。 |
| row | Int |  | 行索引。 |
| col | Int |  | 列索引。 |

### selectTupleElement(widget, index)

选择给定 widget 显示的元素序列中给定索引处的元素。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| widget | FXWindow |  | 要选择的 widget。 |
| index | Int |  | 元素索引。 |

### setInitialFocusWidget(w)

设置将接收初始焦点的 widget。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| w | FXWindow |  | 将接收初始焦点的 widget。 |

### setOnPopdownTarget(target)

设置在对话框被取消张贴时将被通知的对象。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| target | FXObject |  | 在对话框被取消张贴时将被通知的对象。 |

### setUnpostHints(hints)

设置张贴者在对话框被取消张贴时应对此对话框执行的操作。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| hints | Int |  |  |

### show()

张贴对话框。

从 FXTopWindow 重新实现。

在 AFXFileDialog 和 AFXMessageDialog 中重新实现。

### showModal(occludedWindow=None)

将对话框作为模态对话框张贴。对话框相对于给定 widget 或其所有者 widget（如果给出 0）居中。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| occludedWindow | FXWindow | None | 要被遮挡的 widget（0 表示所有者 widget）。 |

### 类标志

### **消息 ID。**

| **ID_CLICKED_OK** | 确定按钮 ID。 |
| --- | --- |
| **ID_CLICKED_CONTINUE** | 继续按钮 ID。 |
| **ID_CLICKED_YES** | 是按钮 ID。 |
| **ID_CLICKED_YES_TO_ALL** | 全是按钮 ID。 |
| **ID_CLICKED_APPLY** | 应用按钮 ID。 |
| **ID_CLICKED_DEFAULTS** | 默认按钮 ID。 |
| **ID_CLICKED_NO** | 否按钮 ID。 |
| **ID_CLICKED_CANCEL** | 取消按钮 ID。 |
| **ID_CLICKED_DISMISS** | 关闭按钮 ID。 |

### **标准操作按钮 ID。**

| **APPLY** | 在操作区域添加"应用"按钮。 |
| --- | --- |
| **CANCEL** | 在操作区域添加"取消"按钮。 |
| **CONTINUE** | 在操作区域添加"继续"按钮。 |
| **DEFAULTS** | 在操作区域添加"默认"按钮。 |
| **DISMISS** | 在操作区域添加"关闭"按钮。 |
| **NO** | 在操作区域添加"否"按钮。 |
| **OK** | 在操作区域添加"确定"按钮。 |
| **YES** | 在操作区域添加"是"按钮。 |
| **YES_TO_ALL** | 在操作区域添加"全部是"按钮。 |

### 全局标志

### **对话框选项的标志。**

| **DIALOG_ACTIONS_BOTTOM** | 在对话框底部水平创建操作区域。 |
| --- | --- |
| **DIALOG_ACTIONS_RIGHT** | 在对话框右侧垂直创建操作区域。 |
| **DIALOG_ACTIONS_NONE** | 不创建操作区域。 |
| **DIALOG_ACTIONS_SEPARATOR** | 在操作区域创建分隔线。 |
| **DIALOG_UNPOST_DELETE** | 取消张贴时删除对话框。 |
| **DIALOG_UNPOST_DESTROY** | 取消张贴时销毁对话框。 |
| **DIALOG_UNPOST_NOTHING** | 取消张贴时不执行任何操作。 |
| **DIALOG_NORMAL** | 默认对话框选项。 |




