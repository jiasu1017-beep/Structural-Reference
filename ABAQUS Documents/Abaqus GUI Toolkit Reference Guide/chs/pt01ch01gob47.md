# AFXProgressBar





此类包含一个进度条，可以多种不同样式显示工作进度。
![](../graphics/gui-afxprogressbar.png)

### AFXProgressBar(p, tgt=None, sel=0, opts=FRAME_SUNKEN| FRAME_THICK, x=0, y=0, w=0, h=0, pl=DEFAULT_PAD, pr=DEFAULT_PAD, pt=DEFAULT_PAD, pb=DEFAULT_PAD)

构造函数。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| p | FXComposite |  | 父窗口部件。 |
| tgt | FXObject | None | 消息目标。 |
| sel | Int | 0 | 消息 ID。 |
| opts | Int | FRAME_SUNKEN| FRAME_THICK | 选项和提示。 |
| x | Int | 0 | 原点的 X 坐标。 |
| y | Int | 0 | 原点的 Y 坐标。 |
| w | Int | 0 | 窗口部件的宽度。 |
| h | Int | 0 | 窗口部件的高度。 |
| pl | Int | DEFAULT_PAD | 左边距（填充）。 |
| pr | Int | DEFAULT_PAD | 右边距（填充）。 |
| pt | Int | DEFAULT_PAD | 顶部边距（填充）。 |
| pb | Int | DEFAULT_PAD | 底部边距（填充）。 |

### create()

创建进度条。

从 FXProgressBar 重新实现。

### getBarStyle()

返回进度条样式。

从 FXProgressBar 重新实现。

### getDefaultHeight()

返回默认高度。

从 FXProgressBar 重新实现。

### getDefaultWidth()

返回默认宽度。

从 FXProgressBar 重新实现。

### getNumCursorBoxes()

返回显示的光标框数量。

### getProgress()

返回当前进度值。

从 FXProgressBar 重新实现。

### getTotal()

返回总进度值。

从 FXProgressBar 重新实现。

### hide()

隐藏进度条。

从 FXWindow 重新实现。

### hideNumber()

隐藏进度条迭代或百分比文本。

从 FXProgressBar 重新实现。

### setBarStyle(style)

设置进度条样式。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| style | Int |  | 样式标志。 |

### setNumCursorBoxes(nb)

设置要显示的光标框数量。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| nb | Int |  | 框数量。 |

### setProgress(value)

设置用于迭代或百分比模式进度条的当前进度值；在扫描器模式下，进度值被忽略。

从 FXProgressBar 重新实现。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| value | Int |  |  |

### setTotal(value)

设置用于迭代或百分比模式进度条的总进度值；在扫描器模式下，进度值被忽略。

从 FXProgressBar 重新实现。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| value | Int |  |  |

### show()

显示进度条。

从 FXWindow 重新实现。

### showNumber(style=AFXPROGRESSBAR_PERCENTAGE)

显示进度迭代或百分比文本。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| style | Int | AFXPROGRESSBAR_PERCENTAGE | 样式标志。 |

### 类标志

### **消息 ID。**

| **ID_TIMER** | 计时器的 ID。 |
| --- | --- |

### 全局标志

### **进度条样式的标志。**

| **AFXPROGRESSBAR_PERCENTAGE** | 百分比完成模式。 |
| --- | --- |
| **AFXPROGRESSBAR_HORIZONTAL** | 水平显示。 |
| **AFXPROGRESSBAR_VERTICAL** | 垂直显示。 |
| **AFXPROGRESSBAR_SCANNER** | 扫描器模式。 |
| **AFXPROGRESSBAR_ITERATOR** | 迭代器模式。 |



