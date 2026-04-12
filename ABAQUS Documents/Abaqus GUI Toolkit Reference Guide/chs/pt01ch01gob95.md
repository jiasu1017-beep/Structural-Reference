# FXMenuCascade









层叠菜单窗口部件用于从下拉菜单中弹出子菜单。
![](../graphics/gui-fxmenucascade.png)

### FXMenuCascade(p, text, ic=None, pup=None, opts=0)

构造一个负责给定弹出菜单的菜单层叠。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| p | FXComposite |  |  |
| text | String |  |  |
| ic | FXIcon | None |  |
| pup | FXPopup | None |  |
| opts | Int | 0 |  |

### canFocus()

是的，它可以接收焦点。

从 FXWindow 重新实现。

### create()

创建服务器端资源。

从 FXMenuCaption 重新实现。

### destroy()

销毁服务器端资源。

从 FXWindow 重新实现。

在 AFXManagerMenuCascade 中重新实现。

### detach()

分离服务器端资源。

从 FXMenuCaption 重新实现。

### getMenu()

返回弹出菜单。

### setMenu(pup)

设置要弹出的弹出菜单。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| pup | FXPopup |  |  |



