# AFXDialogStep






该类在 GUI 过程中提供对话框步骤。
![](../graphics/gui-afxdialogstep.png)

### AFXDialogStep(owner, dialog, prompt)

使用提示区域提示的构造函数。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| owner | AFXProcedure |  | 创建该步骤的过程。 |
| dialog | AFXDataDialog |  | 将在此步骤中张贴的对话框。 |
| prompt | String |  |  |

### AFXDialogStep(owner, dialog)

为提示区域提供默认提示的构造函数。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| owner | AFXProcedure |  | 创建该步骤的过程。 |
| dialog | AFXDataDialog |  | 将在此步骤中张贴的对话框。 |

### onCancel()

当步骤被取消时调用。

从 AFXStep 重新实现。

### onExecute()

当执行 getFirstStep 和 getNextStep 返回的步骤时调用。

从 AFXStep 重新实现。

### onResume()

当步骤恢复时调用。

从 AFXStep 重新实现。

### onSuspend()

当步骤被挂起时调用。

从 AFXStep 重新实现。




