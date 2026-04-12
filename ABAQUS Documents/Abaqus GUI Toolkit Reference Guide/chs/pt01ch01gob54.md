# AFXTextField





此类包含一个标签，该标签位于文本字段之前，允许用户输入文本。
![](../graphics/gui-afxtextfield.png)

### AFXTextField(p, ncols, labelText, tgt=None, sel=0, opts=AFXTEXTFIELD_STRING, x=0, y=0, w=0, h=0, pl=DEFAULT_PAD, pr=DEFAULT_PAD, pt=DEFAULT_PAD, pb=DEFAULT_PAD)

构造函数。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| p | FXComposite |  | 父 widget。 |
| ncols | Int |  | 列数。 |
| labelText | String |  | 标签字符串。 |
| tgt | FXObject | None | 消息目标。 |
| sel | Int | 0 | 消息 ID。 |
| opts | Int | AFXTEXTFIELD_STRING | 选项和提示。 |
| x | Int | 0 | 原点 X 坐标。 |
| y | Int | 0 | 原点 Y 坐标。 |
| w | Int | 0 | widget 宽度。 |
| h | Int | 0 | widget 高度。 |
| pl | Int | DEFAULT_PAD | 左边距。 |
| pr | Int | DEFAULT_PAD | 右边距。 |
| pt | Int | DEFAULT_PAD | 顶部边距。 |
| pb | Int | DEFAULT_PAD | 底部边距。 |

### create()

创建文本字段。

从 FXComposite 重新实现。

### disable()

禁用文本字段。

从 FXWindow 重新实现。

### enable()

启用文本字段。

从 FXWindow 重新实现。

### getCheck()

返回复选按钮或单选按钮的状态。

### getCursorPos()

返回光标位置。

### getDefaultWidth()

返回文本字段的默认宽度。

从 FXPacker 重新实现。

### getExponentType()

返回实数和复数类型文本字段的指数类型。

### getImaginaryText()

返回复数文本字段的虚部文本。

### getJustify()

返回文本对齐模式。

### getLabelFont()

返回标签字体。

### getLabelText()

返回标签文本。

### getNumColumns()

返回列数。

### getPrecision()

返回实数和复数类型文本字段的精度。

### getText()

返回文本。

### getValueType()

返回文本字段的值类型（AFXTEXTFIELD_FLOAT 等）。

### isEditable()

如果输入字段中的文本可以编辑，则返回 True。

### isReadOnlyState()

如果文本字段处于只读状态，则返回 True。

### isVerticalLayout()

如果布局方向为垂直，则返回 True。

### setCheck(state)

设置复选按钮或单选按钮的状态。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| state | Bool |  | 复选状态。 |

### setCheckButtonSelector(sel)

设置复选按钮或单选按钮的消息 ID。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| sel | Int |  | 选择器。 |

### setCheckButtonTarget(checkVal=False)

设置复选按钮或单选按钮的消息目标。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| checkVal | Bool | False | 复选状态。 |

### setCursorPos(pos)

设置光标位置。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| pos | Int |  | 位置。 |

### setEditable(edit=True)

设置文本字段的编辑状态。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| edit | Bool | True | 如果为 True，则可以编辑文本。 |

### setExponentType(e)

设置实数和复数类型文本字段的指数类型。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| e | FXExponent |  | 指数类型。 |

### setFocus()

将焦点移到文本字段。

从 FXWindow 重新实现。

### setFocusAndSelection()

将焦点设置到输入字段并选择其内容。

### setFocusToCheckButton()

将焦点移到 widget 的复选按钮或单选按钮（如果存在）。

### setFocusToImaginaryTextField()

将焦点移到虚部输入字段。

### setFocusToTextField()

将焦点移到 widget 的输入字段。

### setImaginaryFocusAndSelection()

将焦点设置到虚部输入字段并选择其内容。

### setImaginaryText(text)

设置复数文本字段的虚部文本。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| text | String |  | 虚部文本字段文本。 |

### setJustify(mode)

设置文本对齐模式。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| mode | Int |  | 对齐标志。 |

### setLabelFont(fnt)

设置标签文本字体。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| fnt | FXFont |  | 标签字体。 |

### setLabelText(txt)

设置标签文本。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| txt | String |  | 标签文本。 |

### setNumColumns(cols)

设置列数。注意：列宽基于所用字体的"m"宽度。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| cols | Int |  | 列数。 |

### setPrecision(p)

设置实数和复数类型文本字段的精度。限制：如果 AFXTextField widget 使用 AFXFloatKeyword 对象作为其目标，则 widget 必须具有 AFXTEXTFIELD_FLOAT 作为其选项之一，精度设置才能生效。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| p | Int |  | 精度。 |

### setReadOnlyState(readonly=True)

设置文本字段的只读状态。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| readonly | Bool | True | 只读状态。 |

### setSelection(pos, len)

从给定位置开始选择指定数量的字符。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| pos | Int |  | 位置。 |
| len | Int |  | 长度。 |

### setText(text)

设置输入字段中的文本。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| text | String |  | 文本字段文本。 |

### setValueType(type)

设置文本字段的值类型（AFXTEXTFIELD_FLOAT 等）。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| type | Int |  | 值类型。 |

### setVerticalLayout(vertical)

设置文本字段的布局方向。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| vertical | Bool |  | 垂直标志。 |

### 类标志

### **消息 ID。**

| **ID_SETIMAGINARYVALUE** | 用于设置虚部值的 ID。 |
| --- | --- |
| **ID_GETIMAGINARYVALUE** | 用于获取虚部值的 ID。 |
| **ID_BUTTON** | 用于复选/单选按钮的 ID。 |
| **ID_TEXT** | 用于文本字段的 ID。 |
| **ID_IMG_TEXT** | 用于带虚部的文本字段的 ID。 |

### 全局标志

### **AFX 文本字段选项标志。**

| **AFXTEXTFIELD_STRING** | 值字段是字符串。 |
| --- | --- |
| **AFXTEXTFIELD_INTEGER** | 值字段是整数。 |
| **AFXTEXTFIELD_FLOAT** | 值字段是双精度浮点数。 |
| **AFXTEXTFIELD_COMPLEX** | 值字段由复数的实部和虚部组成。 |
| **AFXTEXTFIELD_CHECKBUTTON** | 使用复选按钮代替标签。 |
| **AFXTEXTFIELD_RADIOBUTTON** | 使用单选按钮代替标签。 |
| **AFXTEXTFIELD_VERTICAL** | 将标签或按钮定向在文本字段上方。 |
| **AFXTEXTFIELD_READONLY** | 将文本字段配置为只读状态。 |
| **AFXTEXTFIELD_IME** | 允许 IME（日语等）输入。 |





