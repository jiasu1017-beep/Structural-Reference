# FXList









列表窗口部件
![](../graphics/gui-fxlist.png)

### FXList(p, nvis, tgt=None, sel=0, opts=LIST_NORMAL, x=0, y=0, w=0, h=0)

构造一个具有 nvis 个可见项的列表；列表初始为空。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| p | FXComposite |  |  |
| nvis | Int |  |  |
| tgt | FXObject | None |  |
| sel | Int | 0 |  |
| opts | Int | LIST_NORMAL |  |
| x | Int | 0 |  |
| y | Int | 0 |  |
| w | Int | 0 |  |
| h | Int | 0 |  |

### appendItem(text, icon=None, ptr=None, notify=False)

使用给定文本、可选图标和用户数据指针追加新项。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| text | String |  |  |
| icon | FXIcon | None |  |
| ptr | String | None |  |
| notify | Bool | False |  |

### appendItem(item, notify=False)

将[可能的子类]项追加到列表。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| item | FXListItem |  |  |
| notify | Bool | False |  |

### canFocus()

列表窗口部件可以接收焦点。

从 FXWindow 重新实现。

### clearItems(notify=False)

从列表中移除所有项。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| notify | Bool | False |  |

### create()

创建服务器端资源。

从 FXComposite 重新实现。

### deselectItem(index, notify=False)

取消选择项。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  |  |
| notify | Bool | False |  |

### detach()

分离服务器端资源。

从 FXComposite 重新实现。

### findItem(text, start=-1, flags=SEARCH_FORWARD| SEARCH_WRAP)

按名称搜索项，从起始项开始；flags 参数控制搜索方向和大小写敏感性。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| text | String |  |  |
| start | Int | -1 |  |
| flags | Int | SEARCH_FORWARD| SEARCH_WRAP |  |

### getContentHeight()

返回内容高度。

从 FXScrollArea 重新实现。

### getContentWidth()

计算并返回内容宽度。

从 FXScrollArea 重新实现。

### getCurrentItem()

返回当前项（如果有）。

### getDefaultHeight()

返回默认高度。

从 FXScrollArea 重新实现。

在 AFXList 中重新实现。

### getDefaultWidth()

返回默认宽度。

从 FXScrollArea 重新实现。

### getItemData(index)

返回项的用户数据指针。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  |  |

### getItemHeight(index)

返回项高度。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  |  |

### getItemIcon(index)

返回项图标（如果有）。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  |  |

### getItemText(index)

返回项文本。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  |  |

### getItemWidth(index)

返回项宽度。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  |  |

### getListStyle()

返回列表样式。

### getNumItems()

返回列表中的项数。

### getNumVisible()

返回可见项数。

### insertItem(index, text, icon=None, ptr=None, notify=False)

使用给定文本、图标和用户数据指针在索引处插入项。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  |  |
| text | String |  |  |
| icon | FXIcon | None |  |
| ptr | String | None |  |
| notify | Bool | False |  |

### insertItem(index, item, notify=False)

在给定索引处插入新的[可能的子类]项。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  |  |
| item | FXListItem |  |  |
| notify | Bool | False |  |

### isItemSelected(index)

如果项被选中则返回 True。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  |  |

### isItemVisible(index)

如果项可见则返回 True。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  |  |

### killSelection(notify=False)

取消选择所有项。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| notify | Bool | False |  |

### makeItemVisible(index)

滚动将项带入视图。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  |  |

### recalc()

重新计算布局。

从 FXWindow 重新实现。

### removeItem(index, notify=False)

从列表中移除项。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  |  |
| notify | Bool | False |  |

### replaceItem(index, text, icon=None, ptr=None, notify=False)

替换项的文本、图标和用户数据指针。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  |  |
| text | String |  |  |
| icon | FXIcon | None |  |
| ptr | String | None |  |
| notify | Bool | False |  |

### replaceItem(index, item, notify=False)

用[可能的子类]项替换该项。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  |  |
| item | FXListItem |  |  |
| notify | Bool | False |  |

### retrieveItem(index)

返回给定索引处的项。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  |  |

### selectItem(index, notify=False)

选择项。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  |  |
| notify | Bool | False |  |

### setCurrentItem(index, notify=False)

更改当前项。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  |  |
| notify | Bool | False |  |

### setItemData(index, ptr)

更改项的用户数据指针。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  |  |
| ptr | String |  |  |

### setItemIcon(index, icon)

更改项图标。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  |  |
| icon | FXIcon |  |  |

### setItemText(index, text)

更改项文本。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  |  |
| text | String |  |  |

### setListStyle(style)

更改列表样式。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| style | Int |  |  |

### setNumVisible(nvis)

更改可见项数。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| nvis | Int |  |  |

### 全局标志

### **列表样式**

| **LIST_EXTENDEDSELECT** | 扩展选择模式，允许拖动选择范围内的项。 |
| --- | --- |
| **LIST_SINGLESELECT** | 单选模式，最多允许选择一项。 |
| **LIST_BROWSESELECT** | 浏览选择模式，强制始终选择一项。 |
| **LIST_MULTIPLESELECT** | 多选模式，用于选择单个项。 |
| **LIST_AUTOSELECT** | 自动选择光标下的项。 |





