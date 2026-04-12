# AFXEditSketchStep






该类用于在 GUI 过程中提供拾取步骤。
![](../graphics/gui-afxeditsketchstep.png)

### AFXEditSketchStep(owner, sketchName, prompt='Edit a sketch')

构造函数。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| owner | AFXProcedure |  | 创建该步骤的过程。 |
| sketchName | String |  | 要编辑的草图名称，如果为空则创建。 |
| prompt | String | 'Edit a sketch' | 步骤的提示文本，显示在提示区域。 |

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




