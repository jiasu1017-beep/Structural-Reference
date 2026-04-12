# AFXSlider





此类提供一个滑块，允许用户通过拖动其值指示器来指定值。
![](../graphics/gui-afxslider.png)

### AFXSlider(p, tgt=None, sel=0, opts=AFXSLIDER_NORMAL, x=0, y=0, w=0, h=0, pl=0, pr=0, pt=0, pb=0)

构造函数。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| p | FXComposite |  | 父窗口部件。 |
| tgt | FXObject | None | 消息目标。 |
| sel | Int | 0 | 消息 ID。 |
| opts | Int | AFXSLIDER_NORMAL | 选项和提示。 |
| x | Int | 0 | 原点的 X 坐标。 |
| y | Int | 0 | 原点的 Y 坐标。 |
| w | Int | 0 | 窗口部件的宽度。 |
| h | Int | 0 | 窗口部件的高度。 |
| pl | Int | 0 | 左边距（填充）。 |
| pr | Int | 0 | 右边距（填充）。 |
| pt | Int | 0 | 顶部边距（填充）。 |
| pb | Int | 0 | 底部边距（填充）。 |

### canFocus()

因为滑块可以接收焦点，所以返回 True。

从 FXWindow 重新实现。

### disable()

禁用滑块。

从 FXWindow 重新实现。

### enable()

启用滑块。

从 FXWindow 重新实现。

### getDecimalPlaces()

返回显示的小数位数。

### getDefaultHeight()

返回默认高度。

从 FXPacker 重新实现。

### getDefaultWidth()

返回默认宽度。

从 FXPacker 重新实现。

### getIncrement()

返回滑块的自动递增/递减值。

### getMaxLabelText()

返回最大标签的文本。

### getMinLabelText()

返回最小标签的文本。

### getRange()

返回表示窗口部件允许的最小和最大值的整数序列（low, high）。

### getSliderStyle()

返回滑块的样式。

### getTipText()

返回滑块的工具提示文本。

### getTitleLabelJustify()

返回标题标签的对齐模式。

### getTitleLabelText()

返回标题标签的文本。

### getValue()

返回滑块的值。

### recalc()

重新计算滑块。重新定义以处理滑块移动。

从 FXWindow 重新实现。

### setDecimalPlaces(dp)

设置显示的小数位数。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| dp | Int |  | 小数位数。 |

### setIncrement(inc)

设置滑块的自动递增/递减值。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| inc | Int |  | 增量。 |

### setMaxLabelText(text)

设置最大标签的文本。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| text | String |  | 最大标签文本。 |

### setMinLabelText(text)

设置最小标签的文本。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| text | String |  | 最小标签文本。 |

### setRange(lo, hi)

设置滑块的最大和最小值。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| lo | Int |  | 最小值。 |
| hi | Int |  | 最大值。 |

### setSliderStyle(style)

设置滑块的样式。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| style | Int |  | 样式标志。 |

### setTipText(text)

设置滑块的工具提示文本。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| text | String |  | 工具提示文本。 |

### setTitleLabelJustify(mode)

设置标题标签的对齐模式。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| mode | Int |  | 对齐模式。 |

### setTitleLabelText(text)

设置标题标签的文本。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| text | String |  | 标题文本。 |

### setValue(value)

设置滑块的值。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| value | Int |  | 值。 |

### show()

显示滑块。

从 FXWindow 重新实现。

### 类标志

### **消息 ID。**

| **ID_SLIDER** | 滑块的 ID。 |
| --- | --- |
| **ID_LAST** | 此类的最后一个 ID。 |

### 全局标志

### **刻度线选项。**

| **AFXSLIDER_HORIZONTAL** | 滑块水平显示。 |
| --- | --- |
| **AFXSLIDER_VERTICAL** | 滑块垂直显示。 |
| **AFXSLIDER_ARROW_UP** | 滑块有指向上方的箭头。 |
| **AFXSLIDER_ARROW_DOWN** | 滑块有指向下方的箭头。 |
| **AFXSLIDER_ARROW_LEFT** | 滑块有指向左方的箭头。 |
| **AFXSLIDER_ARROW_RIGHT** | 滑块有指向右方的箭头。 |
| **AFXSLIDER_INSIDE_BAR** | 滑块在槽内而不是悬挂在槽上。 |
| **AFXSLIDER_SHOW_VALUE** | 显示滑块值。 |
| **AFXSLIDER_ABOVE_TITLE** | 在标题上方显示滑块。 |
| **AFXSLIDER_AFTER_TITLE** | 在标题之后显示滑块。 |
| **AFXSLIDER_NORMAL** | 默认滑块选项——滑块是水平的，在槽内，并在其标题标签上方显示。 |



