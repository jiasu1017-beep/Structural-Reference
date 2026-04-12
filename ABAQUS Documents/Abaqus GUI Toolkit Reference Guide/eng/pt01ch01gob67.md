# FXArrowButton







Button with an arrow; the arrow can point in any direction. When clicked, the arrow button sends a SEL_COMMAND to its target. When ARROW_REPEAT is passed, the arrow button sends a SEL_COMMAND repeatedly while the button is pressed.
![](../graphics/gui-fxarrowbutton.png)

### FXArrowButton(p, tgt=None, sel=0, opts=ARROW_NORMAL, x=0, y=0, w=0, h=0, pl=DEFAULT_PAD, pr=DEFAULT_PAD, pt=DEFAULT_PAD, pb=DEFAULT_PAD)

Construct arrow button.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| p | FXComposite |  |  |
| tgt | FXObject | None |  |
| sel | Int | 0 |  |
| opts | Int | ARROW_NORMAL |  |
| x | Int | 0 |  |
| y | Int | 0 |  |
| w | Int | 0 |  |
| h | Int | 0 |  |
| pl | Int | DEFAULT_PAD |  |
| pr | Int | DEFAULT_PAD |  |
| pt | Int | DEFAULT_PAD |  |
| pb | Int | DEFAULT_PAD |  |

### canFocus()

Returns True because a button can receive focus.

Reimplemented from FXWindow.

### disable()

Disable the button.

Reimplemented from FXWindow.

### enable()

Enable the button.

Reimplemented from FXWindow.

### getArrowColor()

Get the fill color for the arrow.

### getArrowSize()

Get the default arrow size.

### getArrowStyle()

Get the arrow style flags.

### getDefaultHeight()

Get default height.

Reimplemented from FXFrame.

### getDefaultWidth()

Get default width.

Reimplemented from FXFrame.

### getJustify()

Get the current justification mode.

### getState()

Get the button state (where True means the button is down).

### getTipText()

Get tool tip message for this arrow button.

### setArrowColor(clr)

Set the fill color for the arrow.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| clr | FXColor |  |  |

### setArrowSize(size)

Set the default arrow size.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| size | Int |  |  |

### setArrowStyle(style)

Set the arrow style flags.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| style | Int |  |  |

### setJustify(mode)

Set the current justification mode.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| mode | Int |  |  |

### setState(s)

Set the button state (where True means the button is down).
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| s | Bool |  |  |

### setTipText(text)

Set tool tip message for this arrow button.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| text | String |  |  |

### Global flags

### **Arrow style options**

| **ARROW_NONE** | No arrow. |
| --- | --- |
| **ARROW_UP** | Arrow points up. |
| **ARROW_DOWN** | Arrow points down. |
| **ARROW_LEFT** | Arrow points left. |
| **ARROW_RIGHT** | Arrow points right. |
| **ARROW_REPEAT** | Button repeats if held down. |
| **ARROW_AUTOGRAY** | Automatically gray out when not updated. |
| **ARROW_AUTOHIDE** | Automatically hide button when not updated. |
| **ARROW_TOOLBAR** | Button is toolbar-style. |
| **ARROW_SPINNER** | Button is spinner-style. |




