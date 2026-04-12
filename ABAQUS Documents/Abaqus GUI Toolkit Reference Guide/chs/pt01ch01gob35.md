# AFXMenuTitle





此类提供创建 FXMenuTitle 并对其进行各种管理活动的接口。它将使用实用方法，以便正确管理模块和过程工具集的菜单标题。
![](../graphics/gui-afxmenutitle.png)

### AFXMenuTitle(owner, label, ic=None, popup=None)

接受所有者的构造函数。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| owner | AFXGuiObjectManager |  | 所有者（模块或工具集 GUI）。 |
| label | String |  | 标签字符串。 |
| ic | FXIcon | None | 图标。 |
| popup | FXPopup | None | 下拉菜单。 |

### AFXMenuTitle(parent, label, ic=None, popup=None)

接受父窗口部件的构造函数。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| parent | FXComposite |  | 父窗口部件。 |
| label | String |  | 标签字符串。 |
| ic | FXIcon | None | 图标。 |
| popup | FXPopup | None | 下拉菜单。 |

### getOwner()

返回菜单标题的所有者。

从 FXWindow 重新实现。

### hide()

隐藏窗口部件。

从 FXWindow 重新实现。

### show()

显示窗口部件。

从 FXWindow 重新实现。




