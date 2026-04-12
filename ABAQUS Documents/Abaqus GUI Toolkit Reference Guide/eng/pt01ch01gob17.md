# AFXFloatSpinner







Convenience class for creating a labeled spinner. The label field can be a label or check button (AFXFLOATSPINNER_CHECKBUTTON option).
![](../graphics/gui-afxfloatspinner.png)

### AFXFloatSpinner(p, ncols, labelText, tgt=None, sel=0, opts=0, x=0, y=0, w=0, h=0, pl=DEFAULT_PAD, pr=DEFAULT_PAD, pt=DEFAULT_PAD, pb=DEFAULT_PAD)

Constructor.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| p | FXComposite |  | Parent widget. |
| ncols | Int |  | Number of columns in the spinner. |
| labelText | String |  | Label preceeding spinner. |
| tgt | FXObject | None | Message target. |
| sel | Int | 0 | Message ID. |
| opts | Int | 0 | Options and hints. |
| x | Int | 0 | X coordinate of origin. |
| y | Int | 0 | Y coordinate of origin. |
| w | Int | 0 | Width of the widget. |
| h | Int | 0 | Height of the widget. |
| pl | Int | DEFAULT_PAD | Left padding. |
| pr | Int | DEFAULT_PAD | Right padding. |
| pt | Int | DEFAULT_PAD | Top padding. |
| pb | Int | DEFAULT_PAD | Bottom padding. |

### canFocus()

Returns True if the spinner can recieve focus.

Reimplemented from FXWindow.

### create()

Creates the spinner.

Reimplemented from FXComposite.

### disable()

Disables the spinner.

Reimplemented from FXWindow.

### enable()

Enables the spinner.

Reimplemented from FXWindow.

### getCheck()

Returns the state of the check button or the radio button.

### getHelpText()

Returns the status line help text.

### getIncrement()

Returns the spinner increment.

### getLabelFont()

Returns the label font.

### getLabelText()

Returns the label string.

### getRange()

Returns a sequence of floats (low, high) representing the widget's allowable minimum and maximum values.

### getTipText()

Returns the tool tip message.

### getValue()

Returns the spinner value.

### isCheckStateChanged()

Returns True if the state of the check button or the radio button has changed by the user since it was programmatically set last time.

### isEditable()

Returns True if the input field of spinner may be edited.

### isReadOnlyState()

Returns True if the spinner is set to the read-only state.

### setCheck(state)

Sets the state of the check button or the radio button.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| state | Bool |  | Button state. |

### setCheckButtonSelector(sel)

Sets the message ID of the check button or the radio button.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| sel | Int |  | Selector. |

### setCheckButtonTarget(tgt)

Sets the message target of the check button or the radio button.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| tgt | FXObject |  | Target. |

### setEditable(edit=True)

Sets the editable state for the input field of spinner.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| edit | Bool | True | Editable state. |

### setHelpText(text)

Sets the status line help text.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| text | String |  | Help text. |

### setIncrement(incr)

Sets the spinner increment.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| incr | Float |  | Increment. |

### setLabelFont(fnt)

Sets the label font.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| fnt | FXFont |  | Label font. |

### setLabelText(txt)

Sets the label string.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| txt | String |  | Label text. |

### setRange(low, high)

Sets the spinner range.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| low | Float |  | Minimum value. |
| high | Float |  | Maximum value. |

### setReadOnlyState(edit=True)

Sets the read-only state of the spinner.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| edit | Bool | True | Read-only state. |

### setTipText(text)

Sets the tool tip message.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| text | String |  | Tooltip text. |

### setValue(val, notify=False)

Sets the spinner value.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| val | Float |  | Value. |
| notify | Bool | False | Notification flag. |

### Class flags

### ** **

| **ID_BUTTON** | ID for the check or radio button. |
| --- | --- |
| **ID_SPINNER** | ID for the spinner. |

### Global flags

### **Flags for AFX float spinner options.**

| **AFXFLOATSPINNER_CHECKBUTTON** | Use a check button instead of a label. |
| --- | --- |
| **AFXFLOATSPINNER_RADIOBUTTON** | Use a radio button instead of a label. |
| **AFXFLOATSPINNER_VERTICAL** | Orient label or button above spinner. |
| **AFXFLOATSPINNER_READONLY** | Configure spinner to the read-only state. |




