# AFXFlyoutItem






该类包含一个放置在飞出按钮弹出菜单中的按钮。
![](../graphics/gui-afxflyoutitem.png)

### AFXFlyoutItem(p, text, ic=None, tgt=None, sel=0, opts=ICON_ABOVE_TEXT| BUTTON_TOOLBAR| FRAME_RAISED| FRAME_THICK, x=0, y=0, w=0, h=0, pl=0, pr=0, pt=0, pb=0)

构造函数。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| p | FXComposite |  | 父 widget。 |
| text | String |  | 标签字符串。 |
| ic | FXIcon | None | 图标。 |
| tgt | FXObject | None | 消息目标。 |
| sel | Int | 0 | 消息 ID。 |
| opts | Int | ICON_ABOVE_TEXT| BUTTON_TOOLBAR| FRAME_RAISED| FRAME_THICK | 选项和提示。 |
| x | Int | 0 | 原点 X 坐标。 |
| y | Int | 0 | 原点 Y 坐标。 |
| w | Int | 0 | widget 的宽度。 |
| h | Int | 0 | widget 的高度。 |
| pl | Int | 0 | 左边距。 |
| pr | Int | 0 | 右边距。 |
| pt | Int | 0 | 顶边距。 |
| pb | Int | 0 | 底边距。 |

### canFocus()

返回 True（因为飞出条目可以接收焦点）。

从 FXButton 重新实现。

### hide()

隐藏飞出条目。

从 FXWindow 重新实现。

### setIcon(ic)

设置飞出条目的图标。

从 FXLabel 重新实现。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| ic | FXIcon |  |  |




