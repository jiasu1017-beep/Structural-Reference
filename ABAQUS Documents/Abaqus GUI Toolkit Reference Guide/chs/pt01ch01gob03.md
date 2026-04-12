# AFXColorButton






该类包含一个标签和颜色井，双击时允许用户调出颜色对话框。当连接到 AFXStringKeyword 时，此 widget 会以十六进制格式（例如"FF0000"）将按钮当前颜色值分配给关键字。
![](../graphics/gui-afxcolorbutton.png)

### AFXColorButton(p, text, tgt=None, sel=0, opts=0, x=0, y=0, w=0, h=0, pl=DEFAULT_SPACING, pr=DEFAULT_SPACING, pt=DEFAULT_SPACING, pb=DEFAULT_SPACING)

构造函数。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| p | FXComposite |  | 父 widget。 |
| text | String |  | 标签字符串。 |
| tgt | FXObject | None | 消息目标。 |
| sel | Int | 0 | 消息 ID。 |
| opts | Int | 0 | 选项和提示。 |
| x | Int | 0 | 原点 X 坐标。 |
| y | Int | 0 | 原点 Y 坐标。 |
| w | Int | 0 | widget 的宽度。 |
| h | Int | 0 | widget 的宽度。 |
| pl | Int | DEFAULT_SPACING | 左边距。 |
| pr | Int | DEFAULT_SPACING | 右边距。 |
| pt | Int | DEFAULT_SPACING | 顶边距。 |
| pb | Int | DEFAULT_SPACING | 底边距。 |

### create()

创建颜色按钮 widget。

从 FXComposite 重新实现。

### disable()

禁用颜色按钮。

从 FXWindow 重新实现。

### enable()

启用颜色按钮。

从 FXWindow 重新实现。

### getHelpText()

返回状态栏帮助文本。

### getLabelFont()

返回标签字体。

### getLabelText()

返回标签字符串。

### getRGBA()

返回按钮的颜色。

### getTipText()

返回工具提示消息。

### setHelpText(text)

设置状态栏帮助文本。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| text | String |  |  |

### setLabelFont(fnt)

设置标签字体。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| fnt | FXFont |  |  |

### setLabelText(txt)

设置标签字符串。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| txt | String |  |  |

### setRGBA(clr)

设置按钮的颜色。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| clr | FXColor |  |  |

### setTipText(text)

设置工具提示消息。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| text | String |  |  |

### 类标志

### **消息 ID。**

| **ID_COLORWELL** | 颜色按钮的 ID。 |
| --- | --- |

### 全局标志

### **AFX 颜色按钮选项的标志。**

| **AFXCOLORBUTTON_VERTICAL** | 将标签置于按钮上方。 |
| --- | --- |




