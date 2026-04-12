# AFXOptionTreeItem







This class is a tree widget with check buttons. 
![](../graphics/gui-afxoptiontreeitem.png)

### AFXOptionTreeItem(p, label, tgt=None, sel=0, opts=0, x=0, y=0, w=0, h=0, pl=DEFAULT_SPACING, pr=DEFAULT_SPACING, pt=DEFAULT_SPACING, pb=DEFAULT_SPACING, hs=DEFAULT_SPACING, vs=DEFAULT_SPACING)

Constructor creating a top-level (root) tree item.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| p | FXComposite |  | Parent widget. |
| label | String |  | Label text. |
| tgt | FXObject | None | Message target. |
| sel | Int | 0 | Message ID. |
| opts | Int | 0 | Options and hints. |
| x | Int | 0 | X coordinate of origin. |
| y | Int | 0 | Y coordinate of origin. |
| w | Int | 0 | Width of the widget. |
| h | Int | 0 | Height of the widget. |
| pl | Int | DEFAULT_SPACING | Left padding. |
| pr | Int | DEFAULT_SPACING | Right padding. |
| pt | Int | DEFAULT_SPACING | Top padding. |
| pb | Int | DEFAULT_SPACING | Bottom padding. |
| hs | Int | DEFAULT_SPACING | Horizontal spacing. |
| vs | Int | DEFAULT_SPACING | Vertical spacing. |

### addItemAfter(label, tgt=None, sel=0)

Creates a new tree item as a sibling after (below) the tree item.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| label | String |  | Item label. |
| tgt | FXObject | None | Item target. |
| sel | Int | 0 | Item selector. |

### addItemBefore(label, tgt=None, sel=0)

Creates a new tree item as a sibling before (above) the tree item.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| label | String |  | Item label. |
| tgt | FXObject | None | Item target. |
| sel | Int | 0 | Item selector. |

### addItemFirst(label, tgt=None, sel=0)

Creates a new tree item as the first child of the tree item.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| label | String |  | Item label. |
| tgt | FXObject | None | Item target. |
| sel | Int | 0 | Item selector. |

### addItemLast(label, tgt=None, sel=0)

Creates a new tree item as the last child of the tree item.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| label | String |  | Item label. |
| tgt | FXObject | None | Item target. |
| sel | Int | 0 | Item selector. |

### childAtIndex(index)

Returns the child tree at the given index.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  | Index. |

### collapse()

Collapses (hides) the children.

### computeDefaultArrowSize()

Computes default size of the arrow button.

### containsChild(tree)

Checks whether the given tree is a child of this object.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| tree | AFXOptionTreeItem |  | Item. |

### create()

Creates the tree item.

Reimplemented from FXComposite.

### disable()

Disables the tree item.

Reimplemented from FXWindow.

### enable()

Enables the tree item.

Reimplemented from FXWindow.

### expand()

Expands (shows) the children.

### getArrowSize()

Returns the size of the arrow button.

### getCheck()

Returns the check state of the tree item.

### getDefaultWidth()

Returns the default width of the tree item.

Reimplemented from FXPacker.

### getFirst()

Returns the first child tree.

Reimplemented from FXWindow.

### getLast()

Returns the last child tree.

Reimplemented from FXWindow.

### getNext()

Returns the next sibling tree.

Reimplemented from FXWindow.

### getParent()

Returns the parent tree widget, or NULL if the tree item is the root.

Reimplemented from FXWindow.

### getPrev()

Returns the previous sibling tree.

Reimplemented from FXWindow.

### getText()

Returns the label text shown in the tree item's check button.

### hasVisibleChildren()

Checks whether the tree item has any visible children.

### hide()

Hides the tree item.

Reimplemented from FXWindow.

### indexOfChild(tree)

Returns the index of an immediate child tree, or -1 if not found.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| tree | AFXOptionTreeItem |  | Item. |

### isChildOf(tree)

Checks whether this object is contained in the given tree.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| tree | AFXOptionTreeItem |  | Item. |

### isExpanded()

Checks whether the tree item shows its children.

### numChildren()

Returns the number of child trees.

Reimplemented from FXWindow.

### setArrowSize(size)

Sets the size of the arrow button for this object and all its children.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| size | Int |  | Size. |

### setCheck(check, notify, propagating=False)

Sets the check state of the tree item and its children, optionally notifying targets.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| check | Int |  | Check state. |
| notify | Bool |  | Notification flag. |
| propagating | Bool | False | Propagation flag. |

### setCheck(check=True)

Sets the check state of the tree item and its children.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| check | Int | True | Check state. |

### setText(txt)

Sets the label text shown in the tree item's check button.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| txt | String |  | Label text. |

### show()

Shows the tree item.

Reimplemented from FXWindow.

### updateCheck(notify)

Updates the check state of the tree item and its ancestors.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| notify | Bool |  | Notification flag. |

### Class flags

### **Message ID's.**

| **ID_TOGGLEEXPAND** | Toggles display of frame with children. |
| --- | --- |
| **ID_CHECKSTATE** | Represents checked state of this object. |
| **ID_SUBTREE** | Container for the subtree. |
| **ID_EXPAND** | Expands frame with children. |
| **ID_COLLAPSE** | Collapses frame with children. |




