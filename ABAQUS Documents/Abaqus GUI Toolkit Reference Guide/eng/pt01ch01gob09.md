# AFXCreateSketchStep







This class is used to provide pick steps in GUI procedures. 
![](../graphics/gui-afxcreatesketchstep.png)

### AFXCreateSketchStep(owner, keyword, sheetSize, prompt='Create a sketch')

Constructor.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| owner | AFXProcedure |  | Procedure creating the step. |
| keyword | AFXObjectKeyword |  | Object kwd containing pick variable. Part of AFXGuiCommand. |
| sheetSize | float |  | Sketch sheet size when creating. |
| prompt | String | 'Create a sketch' | Step's prompt displayed in prompt area. |

### onCancel()

Called when the step is cancelled.

Reimplemented from AFXStep.

### onExecute()

Called to execute the steps returned by getFirstStep and getNextStep.

Reimplemented from AFXStep.

### onResume()

Called when the step is resumed.

Reimplemented from AFXStep.

### onSuspend()

Called when the step is suspended.

Reimplemented from AFXStep.




