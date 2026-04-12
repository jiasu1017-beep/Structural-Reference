# AFXMode







This class is the base class for modes. 
![](../graphics/gui-afxmode.png)

### AFXMode()

Constructor.

### getCommand(index)

Returns the command at the given index (returns 0 if the index is out-of-bounds).
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  | Command index (0-based). |

### getNumCommands()

Returns the number of commands associated with the mode.

### isActive()

Returns True if the mode is active.

### Class flags

### **Message ID's.**

| **ID_ACTIVATE** | Activates the mode. |
| --- | --- |
| **ID_COMMIT** | Commits the mode. |
| **ID_CANCEL** | Cancels the mode. |
| **ID_DEACTIVATE** | Deactivates the mode. |
| **ID_GET_NEXT** | Gets the next step/dialog box. |
| **ID_RESUME** | Resumes the mode. |
| **ID_SET_DEFAULTS** | Sets defaults. |
| **ID_SUSPEND** | Suspends the mode. |
| **ID_CMD_ACTIVATED** | Indicates that a command is activated. |
| **ID_CMD_DEACTIVATED** | Indicates that a command is deactivated. |
| **ID_CMD_MODIFIED** | Indicates that a command is modified. |




