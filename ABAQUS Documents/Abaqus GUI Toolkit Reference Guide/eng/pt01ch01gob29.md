# AFXList







This class is a list widget that allows displaying items in a scrollable window.
![](../graphics/gui-afxlist.png)

### AFXList(p, nvis, tgt=None, sel=0, opts=0, x=0, y=0, w=0, h=0)

Constructor.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| p | FXComposite |  | Parent widget. |
| nvis | Int |  | Number of visible items. |
| tgt | FXObject | None | Message target. |
| sel | Int | 0 | Message ID. |
| opts | Int | 0 | Options and hints. |
| x | Int | 0 | X coordinate of origin. |
| y | Int | 0 | Y coordinate of origin. |
| w | Int | 0 | Width of the widget. |
| h | Int | 0 | Height of the widget. |

### appendItem(text, icon=None, sel=0)

Adds a new item to the end of the list.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| text | String |  |  |
| icon | FXIcon | None |  |
| sel | Int | 0 |  |

### disable()

Disables the list.

Reimplemented from FXWindow.

### enable()

Enables the list.

Reimplemented from FXWindow.

### getAutoCommit()

Returns the auto-commit flag.

### getDefaultHeight()

Returns the default height of the list.

Reimplemented from FXList.

### getItemIndexForData(data)

Returns the index of the first item with the associated data or -1 if not found.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| data |  |  |  |

### getItemProvider()

Returns the provider of the list's items.

### getSingleSelection()

Returns the index of the uniquely selected item. If more than one item or no items are selected, returns -1.

### insertItem(index, text, icon=None, sel=0)

Inserts a new item at the given index.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |
| text | String |  |  |
| icon | FXIcon | None |  |
| sel | Int | 0 |  |

### replaceItem(index, text, icon=None, sel=0)

Replaces the item at the given index.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |
| text | String |  |  |
| icon | FXIcon | None |  |
| sel | Int | 0 |  |

### setAutoCommit(commit)

Sets the auto-commit option for handling double clicks. This option is turned on by default.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| commit | Bool |  |  |

### setItemProvider(cp)

Sets the provider of the list's items.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| cp | FXObject |  |  |

### Global flags

### **Flags for AFX list options.**

| **AFXLIST_NO_AUTOCOMMIT** | Don't automatically commit on double click. |
| --- | --- |




