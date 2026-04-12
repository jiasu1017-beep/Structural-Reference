# AFXToolbarGroup





此类创建一个用作工具栏中组的容器。它在组之后创建一个垂直分隔符。它将使用实用方法，以便正确管理组。
![](../graphics/gui-afxtoolbargroup.png)

### AFXToolbarGroup(owner, name='', title='')

构造函数。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| owner | AFXGuiObjectManager |  | 组的创建者。 |
| name | String | '' | 英文工具集名称。 |
| title | String | '' | 组浮动时显示在标题栏中的名称。 |

### getDefaultHeight()

返回默认高度。

从 FXToolbar 重新实现。

### getDefaultWidth()

返回默认宽度。

从 FXToolbar 重新实现。

### getName()

返回组的英文标识符。

### getOwner()

返回组的创建者。

从 FXWindow 重新实现。

### getTitle()

返回组浮动时显示在标题栏中的名称。

### hide()

隐藏此窗口。

从 FXWindow 重新实现。

在 AFXToolbarGroupRender 和 AFXToolbarGroupVisibility 中重新实现。

### isActive()

如果窗口处于活动状态，则返回 True。

从 FXWindow 重新实现。

### layout()

计算布局。

从 FXToolbar 重新实现。

### setName(name)

设置组的英文标识符。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| name | String |  | |

### setTitle(title)

设置组浮动时显示在标题栏中的名称。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| title | String |  | |

### show()

显示此窗口。

从 FXWindow 重新实现。

在 AFXToolbarGroupRender 和 AFXToolbarGroupVisibility 中重新实现。





