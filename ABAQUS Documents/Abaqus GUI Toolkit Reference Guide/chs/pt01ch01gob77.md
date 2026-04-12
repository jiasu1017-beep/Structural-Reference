# FXFrame





基框架。
![](../graphics/gui-fxframe.png)

### FXFrame(p, opts=FRAME_NORMAL, x=0, y=0, w=0, h=0, pl=DEFAULT_PAD, pr=DEFAULT_PAD, pt=DEFAULT_PAD, pb=DEFAULT_PAD)

构造框架窗口。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| p | FXComposite |  | |
| opts | Int | FRAME_NORMAL | |
| x | Int | 0 | |
| y | Int | 0 | |
| w | Int | 0 | |
| h | Int | 0 | |
| pl | Int | DEFAULT_PAD | |
| pr | Int | DEFAULT_PAD | |
| pt | Int | DEFAULT_PAD | |
| pb | Int | DEFAULT_PAD | |

### getBaseColor()

获取基本 GUI 颜色。

### getBorderColor()

获取边框颜色。

### getBorderWidth()

获取边框宽度。

### getDefaultHeight()

返回默认高度。

从 FXWindow 重新实现。

在 FXArrowButton、FXCheckButton、FXColorBar、FXColorWell、FXColorWheel、FXDial、FXDockTitle、FXHeader、FXLabel、FXMDIDeleteButton、FXMDIRestoreButton、FXMDIMaximizeButton、FXMDIMinimizeButton、FXMDIWindowButton、FXMenuButton、FXProgressBar、FXOption、FXOptionMenu、FXRadioButton、FXHorizontalSeparator、FXVerticalSeparator、FXSlider、FXStatusline、FXTextField、FXToggleButton、FXToolbarGrip、FXToolbarTab 和 AFXProgressBar 中重新实现。

### getDefaultWidth()

返回默认宽度。

从 FXWindow 重新实现。

在 FXArrowButton、FXCheckButton、FXColorBar、FXColorWell、FXColorWheel、FXDial、FXDockTitle、FXHeader、FXLabel、FXMDIDeleteButton、FXMDIRestoreButton、FXMDIMaximizeButton、FXMDIMinimizeButton、FXMDIWindowButton、FXMenuButton、FXProgressBar、FXOption、FXOptionMenu、FXRadioButton、FXHorizontalSeparator、FXVerticalSeparator、FXSlider、FXStatusline、FXTextField、FXToggleButton、FXToolbarGrip、FXToolbarTab 和 AFXProgressBar 中重新实现。

### getFrameStyle()

获取当前框架样式。

### getHiliteColor()

获取高亮颜色。

### getPadBottom()

获取底部内部间距。

### getPadLeft()

获取左侧内部间距。

### getPadRight()

获取右侧内部间距。

### getPadTop()

获取顶部内部间距。

### getShadowColor()

获取阴影颜色。

### setBaseColor(clr)

更改基本 GUI 颜色。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| clr | FXColor |  | |

### setBorderColor(clr)

更改边框颜色。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| clr | FXColor |  | |

### setFrameStyle(style)

更改框架样式。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| style | Int |  | |

### setHiliteColor(clr)

更改高亮颜色。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| clr | FXColor |  | |

### setPadBottom(pb)

更改底部间距。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| pb | Int |  | |

### setPadLeft(pl)

更改左侧间距。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| pl | Int |  | |

### setPadRight(pr)

更改右侧间距。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| pr | Int |  | |

### setPadTop(pt)

更改顶部间距。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| pt | Int |  | |

### setShadowColor(clr)

更改阴影颜色。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| clr | FXColor |  | |

### 全局标志

### **某些子类使用的对齐模式**

| **JUSTIFY_NORMAL** | 默认对齐方式是文本居中。 |
| --- | --- |
| **JUSTIFY_CENTER_X** | 内容水平居中。 |
| **JUSTIFY_LEFT** | 内容左对齐。 |
| **JUSTIFY_RIGHT** | 内容右对齐。 |
| **JUSTIFY_HZ_APART** | JUSTIFY_LEFT 和 JUSTIFY_RIGHT 的组合。 |
| **JUSTIFY_CENTER_Y** | 内容垂直居中。 |
| **JUSTIFY_TOP** | 内容与标签顶部对齐。 |
| **JUSTIFY_BOTTOM** | 内容与标签底部对齐。 |
| **JUSTIFY_VT_APART** | JUSTIFY_TOP 和 JUSTIFY_BOTTOM 的组合。 |





