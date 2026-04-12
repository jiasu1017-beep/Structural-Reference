# AFXProcedure







This class provides the basis for writing procedures. 
![](../graphics/gui-afxprocedure.png)

### AFXProcedure(owner, type=NORMAL)

Constructor.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| owner | AFXGuiObjectManager |  | Owner (a module or a toolset) of the procedure. |
| type | typeEnum | NORMAL |  |

### activate()

Activates the mode.

Reimplemented from AFXGuiMode.

### cancel(tgt=None, msg=0)

Tries to cancel the procedure depending on checkCancel results.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| tgt | FXObject | None | Completion message target. |
| msg | Int | 0 | Completion message ID. |

### checkBackup()

Returns 1 if ok to backup else returns 0.

### checkCancel()

Returns BAILOUT_NOTOK, BAILOUT_OK, BAILOUT_WIP (writes to the message area), or BAILOUT_SAVE (use the 3 button save dialog box).

### commit()

Commits the procedure when the current dialog box calls either done or value changed.

Implements AFXGuiMode.

### continueMode()

Used to get the next step in the mode.

Implements AFXGuiMode.

### deactivate()

deactivates the mode.

Reimplemented from AFXGuiMode.

### getCurrentStep()

Returns the current step.

### getFirstStep()

Returns the first step to be executed in the procedure.

### getLoopStep()

Returns the step to which the procedure should loop back after processing its commands; if zero is returned (the default behavior) the procedure will not loop.

### getNextStep(previousStep)

Returns the next step to be executed; if zero is returned the procedure will process its commands.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| previousStep | AFXStep |  | Previous step. |

### getNumSteps()

Returns the number of steps in the step stack.

### handleException(exc)

This method is called if an error occurs while issueing commands. It can be reimplemented in derived classes to perform special error handling.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| exc | nex_Exception |  | Exception. |

### onBackup()

Called when a procedure backs up a step.

### onCancel()

Called when a procedure cancels.

### onCmdBackup(sender, sel, ptr)

Message handler for handling backup button activation.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| sender | FXObject |  | Sender. |
| sel | Int |  | Selector. |
| ptr | String |  | Data. |

### onCmdHandle2BtnBailout(sender, sel, ptr)

Message handler for handling the user 2 button bailout choice.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| sender | FXObject |  | Sender. |
| sel | Int |  | Selector. |
| ptr | String |  | Data. |

### onCmdHandleBailout(sender, sel, ptr)

Message handler for handling the user 3 button bailout choice.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| sender | FXObject |  | Sender. |
| sel | Int |  | Selector. |
| ptr | String |  | Data. |

### onResume()

Called when a procedure resumes.

### onSuspend()

Called when a procedure suspends.

### onValueChanged()

Called when a procedure's step changes in value.

### setCurrentDb(db)

Sets the current dialog box of the mode. Procedures will have this set by AFXDialogStep.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| db | AFXDialog |  | Dialog box. |

### setSelectionOptions(pickDepth=CLOSEST, pickScope=ALL, dragShape=RECTANGLE, dragScope=INSIDE_CROSSING, isoLines=True)

Sets the selection options to be used for picking.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| pickDepth | pickDepthEnum | CLOSEST | Depth into the screen of picking. |
| pickScope | pickScopeEnum | ALL | Entity type. |
| dragShape | dragShapeEnum | RECTANGLE | Drag-window shape. |
| dragScope | dragScopeEnum | INSIDE_CROSSING | Drag-window scope. |
| isoLines | Bool | True | If True, show isolines on surfaces. |

### verifyCurrentKeywordValues()

Checks whether keywords of active commands for the current dialog box contain valid data and, if not, posts a dialog box with an error message.

Reimplemented from AFXGuiMode.

### Class flags

### **Message ID's.**

| **ID_HANDLE_2BTN_BAILOUT** | ID for handling bailout. |
| --- | --- |
| **ID_BACKUP** | ID for the backup button. |

### **Flags for the drag scope.**

| **INSIDE** | Pick entities inside the drag shape only. |
| --- | --- |
| **INSIDE_CROSSING** | Pick entities inside and crossing the drag shape. |
| **CROSSING** | Pick entities crossing the drag shape only. |
| **OUTSIDE_CROSSING** | Pick entities outside and crossing the drag shape. |
| **OUTSIDE** | Pick entities outside the drag shape only. |

### **Flags for the drag shape.**

| **RECTANGLE** | Use rectangular drag shape. |
| --- | --- |
| **CIRCLE** | Use circular drag shape. |
| **POLYGON** | Use polygonal drag shape. |

### **Flags for the pick depth.**

| **CLOSEST** | Only pick the entity closest to the screen. |
| --- | --- |
| **INFINITE** | Pick entities at any depth. |

### **Flags for the pick scope.**

| **INTERIOR** | Pick only interior entities. |
| --- | --- |
| **EXTERIOR** | Pick only exterior entities. |
| **ALL** | Pick all entities. |

### **Flags for the activate action.**

| **NORMAL** | Cancel the currently running procedure (default). |
| --- | --- |
| **SUBPROCEDURE** | Suspend the currently running procedure. |




