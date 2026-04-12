# FXMenuTitle







A menu title is a child of a menu bar which is responsible for popping up a pulldown menu. 
![](../graphics/gui-fxmenutitle.png)

### FXMenuTitle(p, text, ic=None, pup=None, opts=0)

Constructor.
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

### detach()

Detach server-side resources.

Reimplemented from FXMenuCaption.

### getDefaultHeight()

Return default height.

Reimplemented from FXMenuCaption.

### getDefaultWidth()

Return default width.

Reimplemented from FXMenuCaption.

### getMenu()

Return popup menu.

### setMenu(menu)

Set popup menu to pop up.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| menu | FXPopup |  |  |




