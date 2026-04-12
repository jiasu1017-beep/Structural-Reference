# AFXProgressBar







This class contains a progress bar, which can present work-in-progress in a number of different styles.
![](../graphics/gui-afxprogressbar.png)

### AFXProgressBar(p, tgt=None, sel=0, opts=FRAME_SUNKEN| FRAME_THICK, x=0, y=0, w=0, h=0, pl=DEFAULT_PAD, pr=DEFAULT_PAD, pt=DEFAULT_PAD, pb=DEFAULT_PAD)

Constructor.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| p | FXComposite |  | Parent widget. |
| tgt | FXObject | None | Message target. |
| sel | Int | 0 | Message ID. |
| opts | Int | FRAME_SUNKEN| FRAME_THICK | Options and hints. |
| x | Int | 0 | X coordinate of origin. |
| y | Int | 0 | Y coordinate of origin. |
| w | Int | 0 | Width of the widget. |
| h | Int | 0 | Height of the widget. |
| pl | Int | DEFAULT_PAD | Left padding (margin). |
| pr | Int | DEFAULT_PAD | Right padding (margin). |
| pt | Int | DEFAULT_PAD | Top padding (margin). |
| pb | Int | DEFAULT_PAD | Bottom padding (margin). |

### create()

Creates the progress bar.

Reimplemented from FXProgressBar.

### getBarStyle()

Returns the progress bar style.

Reimplemented from FXProgressBar.

### getDefaultHeight()

Returns the default height.

Reimplemented from FXProgressBar.

### getDefaultWidth()

Returns the default width.

Reimplemented from FXProgressBar.

### getNumCursorBoxes()

Returns the number of cursor boxes displayed.

### getProgress()

Returns the current progress amount.

Reimplemented from FXProgressBar.

### getTotal()

Returns the total progress amount.

Reimplemented from FXProgressBar.

### hide()

Hides the progress bar.

Reimplemented from FXWindow.

### hideNumber()

Hides the progress bar iteration or percentage text.

Reimplemented from FXProgressBar.

### setBarStyle(style)

Sets the progress bar style.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| style | Int |  | Style flag. |

### setNumCursorBoxes(nb)

Sets the number of cursor boxes to display.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| nb | Int |  | Number of boxes. |

### setProgress(value)

Sets the current progress amount that is used by a progress bar in either iteration or percentage mode; the progress amount is ingored by a progress bar in scanner mode.

Reimplemented from FXProgressBar.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| value | Int |  |  |

### setTotal(value)

Sets the total progress amount that is used by a progress bar in either iteration or percentage mode; the progress amount is ingored by a progress bar in scanner mode.

Reimplemented from FXProgressBar.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| value | Int |  |  |

### show()

Shows the progress bar.

Reimplemented from FXWindow.

### showNumber(style=AFXPROGRESSBAR_PERCENTAGE)

Shows the progress iteration or percentage text.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| style | Int | AFXPROGRESSBAR_PERCENTAGE | Style flag. |

### Class flags

### **Message ID's.**

| **ID_TIMER** | ID for timer. |
| --- | --- |

### Global flags

### **Flags for progress bar styles.**

| **AFXPROGRESSBAR_PERCENTAGE** | Percentage complete mode. |
| --- | --- |
| **AFXPROGRESSBAR_HORIZONTAL** | Horizontal display. |
| **AFXPROGRESSBAR_VERTICAL** | Vertical display. |
| **AFXPROGRESSBAR_SCANNER** | Scanner mode. |
| **AFXPROGRESSBAR_ITERATOR** | Iterator mode. |




