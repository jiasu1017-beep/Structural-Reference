# FXMenuButton







A menu button posts a popup menu when clicked. There are many ways to control the placement where the popup will appear; first, the popup may be placed on either of the four sides relative to the menu button; this is controlled by the flags MENUBUTTON_DOWN, etc. Next, there are several attachment modes; the popup's left/bottom edge may attach to the menu button's left/top edge, or the popup's right/top edge may attach to the menu button's right/bottom edge, or both. Also, the popup may apear centered relative to the menu button. Finally, a small offset may be specified to displace the location of the popup by a few pixels so as to account for borders and so on. Normally, the menu button shows an arrow pointing to the direction where the popup is set to appear; this can be turned off by passing the option MENUBUTTON_NOARROWS.
![](../graphics/gui-fxmenubutton.png)

### FXMenuButton(p, text, ic=None, pup=None, opts=JUSTIFY_NORMAL| ICON_BEFORE_TEXT| MENUBUTTON_DOWN, x=0, y=0, w=0, h=0, pl=DEFAULT_PAD, pr=DEFAULT_PAD, pt=DEFAULT_PAD, pb=DEFAULT_PAD)

Constructor.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| p | FXComposite |  |  |
| text | String |  |  |
| ic | FXIcon | None |  |
| pup | FXPopup | None |  |
| opts | Int | JUSTIFY_NORMAL| ICON_BEFORE_TEXT| MENUBUTTON_DOWN |  |
| x | Int | 0 |  |
| y | Int | 0 |  |
| w | Int | 0 |  |
| h | Int | 0 |  |
| pl | Int | DEFAULT_PAD |  |
| pr | Int | DEFAULT_PAD |  |
| pt | Int | DEFAULT_PAD |  |
| pb | Int | DEFAULT_PAD |  |

### canFocus()

Returns True because a menu button can receive focus.

Reimplemented from FXWindow.

### create()

Create server-side resources.

Reimplemented from FXLabel.

### detach()

Detach server-side resources.

Reimplemented from FXLabel.

### getAttachment()

Get attachment.

### getButtonStyle()

Get menu button style.

### getDefaultHeight()

Return default height.

Reimplemented from FXLabel.

Reimplemented in FXMDIWindowButton.

### getDefaultWidth()

Return default width.

Reimplemented from FXLabel.

Reimplemented in FXMDIWindowButton.

### getMenu()

Return current popup menu.

### getPopupStyle()

Get popup style.

### getXOffset()

Return current X offset.

### getYOffset()

Return current Y offset.

### setAttachment(att)

Change attachment.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| att | Int |  |  |

### setButtonStyle(style)

Change menu button style.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| style | Int |  |  |

### setMenu(pup)

Change the popup menu.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| pup | FXPopup |  |  |

### setPopupStyle(style)

Change popup style.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| style | Int |  |  |

### setXOffset(offx)

Set X offset where menu pops up relative to button.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| offx | Int |  |  |

### setYOffset(offy)

Set Y offset where menu pops up relative to button.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| offy | Int |  |  |

### Global flags

### **Menu button options**

| **MENUBUTTON_AUTOGRAY** | Automatically gray out when no target. |
| --- | --- |
| **MENUBUTTON_AUTOHIDE** | Automatically hide when no target. |
| **MENUBUTTON_TOOLBAR** | Toolbar style. |
| **MENUBUTTON_COMBOBOX** | CAE - Combobox style. |
| **MENUBUTTON_DOWN** | Popup window appears below menu button. |
| **MENUBUTTON_UP** | Popup window appears above menu button. |
| **MENUBUTTON_LEFT** | Popup window to the left of the menu button. |
| **MENUBUTTON_RIGHT** | Popup window to the right of the menu button. |
| **MENUBUTTON_NOARROWS** | Do not show arrows. |
| **MENUBUTTON_ATTACH_LEFT** | Popup attaches to the left side of the menu button. |
| **MENUBUTTON_ATTACH_TOP** | Popup attaches to the top of the menu button. |
| **MENUBUTTON_ATTACH_RIGHT** | Popup attaches to the right side of the menu button. |
| **MENUBUTTON_ATTACH_BOTTOM** | Popup attaches to the bottom of the menu button. |
| **MENUBUTTON_ATTACH_CENTER** | Popup attaches to the center of the menu button. |
| **MENUBUTTON_ATTACH_BOTH** | Popup attaches to both sides of the menu button. |




