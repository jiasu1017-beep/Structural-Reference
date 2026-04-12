# FXDialogBox







DialogBox window. When receiving ID_CANCEL or ID_ACCEPT, the DialogBox breaks out of the modal loop and returns False or True, respectively. To close the DialogBox when not running modally, simply send it ID_HIDE. 
![](../graphics/gui-fxdialogbox.png)

### FXDialogBox(a, name, opts=DECOR_TITLE| DECOR_BORDER, x=0, y=0, w=0, h=0, pl=10, pr=10, pt=10, pb=10, hs=4, vs=4)

Construct free-floating dialog.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| a | FXApp |  |  |
| name | String |  |  |
| opts | Int | DECOR_TITLE| DECOR_BORDER |  |
| x | Int | 0 |  |
| y | Int | 0 |  |
| w | Int | 0 |  |
| h | Int | 0 |  |
| pl | Int | 10 |  |
| pr | Int | 10 |  |
| pt | Int | 10 |  |
| pb | Int | 10 |  |
| hs | Int | 4 |  |
| vs | Int | 4 |  |

### FXDialogBox(owner, name, opts=DECOR_TITLE| DECOR_BORDER, x=0, y=0, w=0, h=0, pl=10, pr=10, pt=10, pb=10, hs=4, vs=4)

Construct dialog which will always float over the owner window.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| owner | FXWindow |  |  |
| name | String |  |  |
| opts | Int | DECOR_TITLE| DECOR_BORDER |  |
| x | Int | 0 |  |
| y | Int | 0 |  |
| w | Int | 0 |  |
| h | Int | 0 |  |
| pl | Int | 10 |  |
| pr | Int | 10 |  |
| pt | Int | 10 |  |
| pb | Int | 10 |  |
| hs | Int | 4 |  |
| vs | Int | 4 |  |

### execute(placement=PLACEMENT_CURSOR)

Run modal invocation of the dialog.

Reimplemented in FXInputDialog, and FXReplaceDialog.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| placement | Int | PLACEMENT_CURSOR |  |

### Class flags

### ** **

| **ID_CANCEL** | Closes the dialog, cancel the entry. |
| --- | --- |
| **ID_ACCEPT** | Closes the dialog, accept the entry. |




