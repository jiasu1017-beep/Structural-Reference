# FXMenuCascade







The cascade menu widget is used to bring up a sub menu from a pull down menu. 
![](../graphics/gui-fxmenucascade.png)

### FXMenuCascade(p, text, ic=None, pup=None, opts=0)

Construct a menu cascade responsible for the given popup menu.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| p | FXComposite |  |  |
| text | String |  |  |
| ic | FXIcon | None |  |
| pup | FXPopup | None |  |
| opts | Int | 0 |  |

### canFocus()

Yes it can receive the focus.

Reimplemented from FXWindow.

### create()

Create server-side resources.

Reimplemented from FXMenuCaption.

### destroy()

Destroy server-side resources.

Reimplemented from FXWindow.

Reimplemented in AFXManagerMenuCascade.

### detach()

Detach server-side resources.

Reimplemented from FXMenuCaption.

### getMenu()

Return popup menu.

### setMenu(pup)

Set popup menu to pop up.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| pup | FXPopup |  |  |




