# AFXForm






该类是表单的抽象基类。
![](../graphics/gui-afxform.png)

### AFXForm(owner)

构造函数。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| owner | AFXGuiObjectManager |  | 表单的所有者（模块或工具集）。 |

### activate()

执行表单被激活时所需的任务。

从 AFXGuiMode 重新实现。

### cancel(tgt=None, msg=0)

请求取消表单。当取消操作完成（无论成功与否）时，目标将收到指定消息。如果取消操作成功完成，则消息数据指针将非零；如果取消操作因某种原因被放弃，则为零。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| tgt | FXObject | None | 完成消息目标。 |
| msg | Int | 0 | 完成消息 ID。 |

### commit()

执行表单被提交时所需的任务。

实现 AFXGuiMode。

### continueMode()

用于获取模式中的下一个对话框。

实现 AFXGuiMode。

### deactivateIfNeeded()

如果用户按下了当前张贴对话框的"确定"按钮，则停用表单。此方法在命令成功处理后被调用。

### getFirstDialog()

返回第一个要张贴的对话框。

### getNextDialog(previousDialog)

返回下一个要张贴的对话框。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| previousDialog | AFXDialog |  | 上一个对话框。 |

### issueCommands(writeToReplay=True, writeToJournal=False)

根据当前状态生成命令，发送命令，并在必要时停用表单。如果命令未成功完成，将张贴带有错误消息的对话框。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| writeToReplay | Bool | True | 如果命令应写入回放文件，则为 True；否则为 False。 |
| writeToJournal | Bool | False | 如果命令应写入日志文件，则为 True；否则为 False。 |

### setModal(postModalDialogs)

设置模态状态；如果为 True，对话框将作为模态对话框张贴。默认情况下，表单将对话框作为非模态对话框张贴。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| postModalDialogs | Bool |  | 如果表单应将对话框作为模态对话框张贴，则为 True。 |




