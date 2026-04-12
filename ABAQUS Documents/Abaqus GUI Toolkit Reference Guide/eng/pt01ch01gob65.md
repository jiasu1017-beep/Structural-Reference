# AFXVerticalAligner







This class is used to automatically vertically align its children "container" widgets (e.g. AFXTextField or AFXComboBox). The width of the first widget in the container of each child of the vertical aligner is set to the width of the widest first widget of all the vertical aligner's children. 
![](../graphics/gui-afxverticalaligner.png)

### AFXVerticalAligner(p, opts=0, x=0, y=0, w=0, h=0, pl=0, pr=0, pt=0, pb=0, hs=DEFAULT_SPACING, vs=DEFAULT_SPACING)

Constructor.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| p | FXComposite |  | Parent widget. |
| opts | Int | 0 | Options and hints. |
| x | Int | 0 | X coordinate of the origin. |
| y | Int | 0 | Y coordinate of the origin. |
| w | Int | 0 | Width of the widget. |
| h | Int | 0 | Height of the widget. |
| pl | Int | 0 | Left padding (margin). |
| pr | Int | 0 | Right padding (margin). |
| pt | Int | 0 | Top padding (margin). |
| pb | Int | 0 | Bottom padding (margin). |
| hs | Int | DEFAULT_SPACING | Horizontal spacing. |
| vs | Int | DEFAULT_SPACING | Vertical spacing. |

### create()

Creates the aligner.

Reimplemented from FXComposite.

### getDefaultHeight()

Returns the default height.

Reimplemented from FXVerticalFrame.

### getDefaultWidth()

Returns the default width.

Reimplemented from FXVerticalFrame.




