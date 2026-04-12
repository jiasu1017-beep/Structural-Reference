# AFXProcedureToolsetGui







This is the base class for toolset GUIs used in procedure steps (e.g. the Sketch toolset) and provides an interface for managing the toolset's GUI items. In conjuction with the AFXProcedureToolsetGuiData class, it provides a mechanism to overlay menubar, toolbar, and toolbox GUI items while the step executes. 
![](../graphics/gui-afxproceduretoolsetgui.png)

### AFXProcedureToolsetGui()

Deserialization.

### AFXProcedureToolsetGui(toolsetName)

Constructor.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| toolsetName | String |  | Toolset name passed in from derived toolsets. |

### swapInToolsetItems()

Swaps in the toolset's GUI items.

### swapOutToolsetItems()

Swaps out the toolset's GUI items.

### Class flags

### ** **

| **ID_LAST** | Do not use, do not delete; for use by derived classes. |
| --- | --- |




