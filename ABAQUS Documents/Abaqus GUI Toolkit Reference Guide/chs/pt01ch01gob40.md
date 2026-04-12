# AFXOptionTreeList





此类提供选项组的滚动列表，这些选项可以作为一个组或单独切换打开或关闭。
![](../graphics/gui-afxoptiontreelist.png)

### AFXOptionTreeList(p, nvis, opts=0, x=0, y=0, w=0, h=0, pl=DEFAULT_SPACING, pr=DEFAULT_SPACING, pt=DEFAULT_SPACING, pb=DEFAULT_SPACING, hs=DEFAULT_SPACING, vs=DEFAULT_SPACING)

构造函数。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| p | FXComposite |  | 父窗口部件。 |
| nvis | Int |  | 列表可见项目数。 |
| opts | Int | 0 | 选项和提示。 |
| x | Int | 0 | 原点的 X 坐标。 |
| y | Int | 0 | 原点的 Y 坐标。 |
| w | Int | 0 | 窗口部件的宽度。 |
| h | Int | 0 | 窗口部件的高度。 |
| pl | Int | DEFAULT_SPACING | 左边距。 |
| pr | Int | DEFAULT_SPACING | 右边距。 |
| pt | Int | DEFAULT_SPACING | 顶部边距。 |
| pb | Int | DEFAULT_SPACING | 底部边距。 |
| hs | Int | DEFAULT_SPACING | 水平间距。 |
| vs | Int | DEFAULT_SPACING | 垂直间距。 |

### addItemFirst(text, tgt=None, msg=0)

使用给定文本作为列表的第一个项目添加新项目。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| text | String |  | 项目文本。 |
| tgt | FXObject | None | 项目目标。 |
| msg | Int | 0 | 项目选择器。 |

### addItemLast(text, tgt=None, msg=0)

使用给定文本作为列表的最后一个项目添加新项目。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| text | String |  | 项目文本。 |
| tgt | FXObject | None | 项目目标。 |
| msg | Int | 0 | 项目选择器。 |

### clearItems()

从列表中移除所有项目。

### computeItemHeight(p=None)

计算用作默认高度计算基础的项目大小。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| p | AFXOptionTreeItem | None | 项目。 |

### createItem(text, tgt, msg)

创建新的树项目对象。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| text | String |  | 项目文本。 |
| tgt | FXObject |  | 项目目标。 |
| msg | Int |  | 项目选择器。 |

### getContentHeight()

返回内容高度。

从 FXScrollWindow 重新实现。

### getContents()

返回内容窗口。

### getContentWidth()

返回内容宽度。

从 FXScrollWindow 重新实现。

### getDefaultHeight()

返回默认高度。

从 FXScrollArea 重新实现。

### getDefaultWidth()

返回默认宽度。

从 FXScrollArea 重新实现。

### getFirstItem()

返回第一个根项目。

### getHSpacing()

返回水平子项间距。

### getLastItem()

返回最后一个根项目。

### getNumItems()

返回顶级项目数。

### getNumVisible()

返回可见项目数。

### getPadBottom()

返回底部边距。

### getPadLeft()

返回左边距。

### getPadRight()

返回右边距。

### getPadTop()

返回顶部边距。

### getVSpacing()

返回垂直子项间距。

### layout()

重新计算布局。

从 FXScrollWindow 重新实现。

### moveContents(x, y)

将内容移动到指定位置。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| x | Int |  | X 位置。 |
| y | Int |  | Y 位置 |

### removeItem(item)

从列表中移除给定项目。如果给定项目不存在，此方法不执行任何操作。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| item | AFXOptionTreeItem |  | 要移除的项目。 |

### setHSpacing(hs)

设置水平子项间距。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| hs | Int |  | 水平间距。 |

### setNumVisible(nvis)

设置可见项目数。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| nvis | Int |  | 可见项目数。 |

### setPadBottom(pb)

设置底部边距。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| pb | Int |  | 底部边距。 |

### setPadLeft(pl)

设置左边距。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| pl | Int |  | 左边距。 |

### setPadRight(pr)

设置右边距。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| pr | Int |  | 右边距。 |

### setPadTop(pt)

设置顶部边距。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| pt | Int |  | 顶部边距。 |

### setVSpacing(vs)

设置垂直子项间距。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| vs | Int |  | 垂直间距。 |

### 类标志

### **消息 ID。**

| **ID_CONTENTS** | 内容窗口的 ID。 |
| --- | --- |



