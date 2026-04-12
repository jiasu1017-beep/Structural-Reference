# AFXGuiCommand







This class is designed for the GUI commands processed by modes. 
![](../graphics/gui-afxguicommand.png)

### AFXGuiCommand(mode, method, objectName='', registerQuery=False)

Constructor.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| mode | AFXGuiMode |  | Host mode. |
| method | String |  | Method. |
| objectName | String | '' | Object name. |
| registerQuery | Bool | False | True if a query should be registered so that the command's keyword values can be updated based on the kernel state. |

### getMode()

Retrieves the command's mode.




