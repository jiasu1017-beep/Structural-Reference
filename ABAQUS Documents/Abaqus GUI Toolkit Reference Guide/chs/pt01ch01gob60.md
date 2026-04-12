# AFXToolsetGui





这是工具集 GUI 的基类，提供管理工具集 GUI 项的接口。它提供了一种机制来添加菜单栏、工具栏和工具箱 GUI 项。
![](../graphics/gui-afxtoolsetgui.png)

### AFXToolsetGui(toolsetName)

构造函数。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| toolsetName | String |  | 从派生工具集传入的工具集名称。 |

### activate()

激活工具集（如果没有模式工厂，则不需要重新定义此方法）。

### deactivate()

停用工具集（如果没有模式工厂，则不需要重新定义此方法）。

### getToolsetName()

返回构造时给定的工具集名称。

### hide(location)

隐藏菜单栏、工具栏和工具箱中的 GUI 组件。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| location | Int |  | 指示 GUI 组件放置位置的标志。可能的值为 GUI_IN_NONE、GUI_IN_MENUBAR、GUI_IN_TOOL_PANE、GUI_IN_TOOLBAR 和 GUI_IN_TOOLBOX。 |

### show(location)

显示菜单栏、工具栏和工具箱中的 GUI 组件。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| location | Int |  | 指示 GUI 组件放置位置的标志。可能的值为 GUI_IN_NONE、GUI_IN_MENUBAR、GUI_IN_TOOL_PANE、GUI_IN_TOOLBAR 和 GUI_IN_TOOLBOX。 |





