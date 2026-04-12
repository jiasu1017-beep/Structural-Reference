# FXMDIChild







The MDI child window contains the application work area in a Multiple Document Interface application.
![](../graphics/gui-fxmdichild.png)

### FXMDIChild(p, name, ic=None, mn=None, opts=0, x=0, y=0, w=0, h=0)

Construct MDI Child window with given name and icon.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| p | FXMDIClient |  |  |
| name | String |  |  |
| ic | FXIcon | None |  |
| mn | FXMenuPane | None |  |
| opts | Int | 0 |  |
| x | Int | 0 |  |
| y | Int | 0 |  |
| w | Int | 0 |  |
| h | Int | 0 |  |

### canFocus()

MDI Child can receive focus.

Reimplemented from FXWindow.

### contentWindow()

Return content window.

### create()

Create window.

Reimplemented from FXComposite.

### detach()

Detach window.

Reimplemented from FXComposite.

### getDefaultHeight()

Return default height.

Reimplemented from FXComposite.

### getDefaultWidth()

Compute default size.

Reimplemented from FXComposite.

### getFont()

Get title font.

### getHiliteColor()

Get colors.

### getIconX()

Return iconified position.

### getMDINext()

Get next MDI Child.

### getMDIPrev()

Get previous MDI Child.

### getNormalX()

Return normal (restored) position.

### getTitle()

Get current title.

### getWindowIcon()

Get window icon.

### getWindowMenu()

Get window menu.

### isMaximized()

Return True if maximized.

### isMinimized()

Return True if minimized.

### maximize(notify=False)

Maximize MDI Child.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| notify | Bool | False |  |

### minimize(notify=False)

Minimize/iconify MDI Child.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| notify | Bool | False |  |

### move(x, y)

Move this window to the specified position in the parent's coordinates.

Reimplemented from FXWindow.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| x | Int |  |  |
| y | Int |  |  |

### position(x, y, w, h)

Move and resize this window in the parent's coordinates.

Reimplemented from FXWindow.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| x | Int |  |  |
| y | Int |  |  |
| w | Int |  |  |
| h | Int |  |  |

### resize(w, h)

Resize this window to the specified width and height.

Reimplemented from FXWindow.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| w | Int |  |  |
| h | Int |  |  |

### restore(notify=False)

Restore MDI Child to normal.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| notify | Bool | False |  |

### setFont(fnt)

Set title font.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| fnt | FXFont |  |  |

### setHiliteColor(clr)

Change colors.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| clr | FXColor |  |  |

### setIconX(x)

Change iconified position.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| x | Int |  |  |

### setNormalX(x)

Change normal (restored) position.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| x | Int |  |  |

### setTitle(name)

Change MDI Child's title.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| name | String |  |  |

### setWindowIcon(icon)

Set window icon.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| icon | FXIcon |  |  |

### setWindowMenu(menu)

Set window menu.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| menu | FXPopup |  |  |

### Global flags

### **MDI Child Window styles**

| **MDI_NORMAL** | Normal display mode. |
| --- | --- |
| **MDI_MAXIMIZED** | Window appears maximized. |
| **MDI_MINIMIZED** | Window is iconified or minimized. |




