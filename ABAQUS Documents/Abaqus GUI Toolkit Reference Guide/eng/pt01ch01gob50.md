# AFXStep







This class is the base class for steps used in a GUI procedure. 
![](../graphics/gui-afxstep.png)

### AFXStep(prompt, owner)

Constructor.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| prompt | String |  | Prompt. |
| owner | AFXProcedure |  | Owner. |

### onCancel()

Called when the step is cancelled.

Reimplemented in AFXCreateSketchStep, AFXDialogStep, AFXEditSketchStep, AFXOrderedPickStep, and AFXPickStep.

### onDone()

Called when the step completes.

### onExecute()

Called to execute the steps returned by getFirstStep and getNextStep.

Reimplemented in AFXCreateSketchStep, AFXDialogStep, AFXEditSketchStep, AFXOrderedPickStep, and AFXPickStep.

### onResume()

Called when the step is resumed.

Reimplemented in AFXCreateSketchStep, AFXDialogStep, AFXEditSketchStep, and AFXPickStep.

### onSuspend()

Called when the step is suspended.

Reimplemented in AFXCreateSketchStep, AFXDialogStep, AFXEditSketchStep, and AFXPickStep.

### onValueChanged()

Called when the step's value changes.

### reset()

Allows a step to reset any of its data (if needed) when looping.

Reimplemented in AFXOrderedPickStep, and AFXPickStep.




