# AFXMenuCascade





此类提供创建 FXMenuCascade 并对其进行各种管理活动的接口。它将使用实用方法，以便正确管理模块和工具集的菜单级联。
![](../graphics/gui-afxmenucascade.png)

### AFXMenuCascade(owner, p, label, ic=None, popup=None)

构造函数。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| owner | AFXGuiObjectManager |  | 菜单级联的创建者。 |
| p | FXComposite |  | 父窗口部件。 |
| label | String |  | 菜单按钮的标签。 |
| ic | FXIcon | None | 菜单按钮图标。 |
| popup | FXPopup | None | 菜单级联的拉右键窗格。 |

### getOwner()

返回菜单级联的所有者。

从 FXWindow 重新实现。




