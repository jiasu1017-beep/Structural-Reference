# FXIconList







Icon List Widget
![](../graphics/gui-fxiconlist.png)

### FXIconList(p, tgt=None, sel=0, opts=ICONLIST_NORMAL, x=0, y=0, w=0, h=0)

Construct icon list.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| p | FXComposite |  |  |
| tgt | FXObject | None |  |
| sel | Int | 0 |  |
| opts | Int | ICONLIST_NORMAL |  |
| x | Int | 0 |  |
| y | Int | 0 |  |
| w | Int | 0 |  |
| h | Int | 0 |  |

### appendHeader(text, icon=None, size=1)

Append header with given text and optional icon.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| text | String |  |  |
| icon | FXIcon | None |  |
| size | Int | 1 |  |

### appendItem(text, big=None, mini=None, ptr=None, notify=False)

Append new item with given text and optional icons, and user-data pointer.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| text | String |  |  |
| big | FXIcon | None |  |
| mini | FXIcon | None |  |
| ptr | String | None |  |
| notify | Bool | False |  |

### appendItem(item, notify=False)

Append a [possibly subclassed] item to the end of the list.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| item | FXIconItem |  |  |
| notify | Bool | False |  |

### canFocus()

Icon list can receive focus.

Reimplemented from FXWindow.

### clearItems(notify=False)

Remove all items from list.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| notify | Bool | False |  |

### create()

Create server-side resources.

Reimplemented from FXComposite.

Reimplemented in FXFileList.

### deselectItem(index, notify=False)

Deselect item at index.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |
| notify | Bool | False |  |

### detach()

Detach server-side resources.

Reimplemented from FXComposite.

Reimplemented in FXFileList.

### disableItem(index)

Disable item at index.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |

### enableItem(index)

Enable item at index.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |

### extendSelection(index, notify=False)

Extend selection from anchor index to index.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |
| notify | Bool | False |  |

### findItem(text, start=-1, flags=SEARCH_FORWARD| SEARCH_WRAP)

Search items for item by name, starting from start item; the flags argument controls the search direction, and case sensitivity.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| text | String |  |  |
| start | Int | -1 |  |
| flags | Int | SEARCH_FORWARD| SEARCH_WRAP |  |

### getAnchorItem()

Return anchor item index, or -1 if none.

### getContentHeight()

Return content height.

Reimplemented from FXScrollArea.

### getContentWidth()

Compute and return content width.

Reimplemented from FXScrollArea.

### getCurrentItem()

Return current item index, or -1 if none.

### getCursorItem()

Return index of item under cursor, or -1 if none.

### getFont()

Return text font.

### getHeader()

Return header control.

### getHeaderIcon(index)

Return icon of header at index.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |

### getHeaderSize(index)

Return width of header at index.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |

### getHeaderText(index)

Return text of header at index.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |

### getHelpText()

Get the status line help text for this widget.

### getItemAt(x, y)

Return index of item at x,y, or -1 if none.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| x | Int |  |  |
| y | Int |  |  |

### getItemBigIcon(index)

Return big icon of item at index.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |

### getItemData(index)

Return item user-data pointer.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |

### getItemHeight()

Return item height.

### getItemMiniIcon(index)

Return mini icon of item at index.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |

### getItemSpace()

Return maximum item space.

### getItemText(index)

Return item text.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |

### getItemWidth()

Return item width.

### getListStyle()

Get the current icon list style.

### getNumCols()

Return number of columns.

### getNumHeaders()

Return number of headers.

### getNumItems()

Return number of items.

### getNumRows()

Return number of rows.

### getSelBackColor()

Return selected text background.

### getSelTextColor()

Return selected text color.

### getSortFunc()

Return sort function.

### getTextColor()

Return normal text color.

### getViewportHeight()

Return viewport size.

Reimplemented from FXScrollArea.

### hitItem(index, x, y, ww=1, hh=1)

Return item hit code: 0 outside, 1 icon, 2 text.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |
| x | Int |  |  |
| y | Int |  |  |
| ww | Int | 1 |  |
| hh | Int | 1 |  |

### insertItem(index, text, big=None, mini=None, ptr=None, notify=False)

Insert item at index with given text, icons, and user-data pointer.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |
| text | String |  |  |
| big | FXIcon | None |  |
| mini | FXIcon | None |  |
| ptr | String | None |  |
| notify | Bool | False |  |

### insertItem(index, item, notify=False)

Insert a new [possibly subclassed] item at the give index.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |
| item | FXIconItem |  |  |
| notify | Bool | False |  |

### isItemCurrent(index)

Return True if item at index is current.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |

### isItemEnabled(index)

Return True if item at index is enabled.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |

### isItemSelected(index)

Return True if item at index is selected.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |

### isItemVisible(index)

Return True if item at index is visible.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |

### killFocus()

Remove the focus from this window.

Reimplemented from FXWindow.

### killSelection(notify=False)

Deselect all items.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| notify | Bool | False |  |

### makeItemVisible(index)

Scroll to make item at index visible.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |

### moveContents(x, y)

Move contents to the specified position.

Reimplemented from FXScrollArea.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| x | Int |  |  |
| y | Int |  |  |

### position(x, y, w, h)

Move and resize this window in the parent's coordinates.

Reimplemented from FXWindow.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| x | Int |  |  |
| y | Int |  |  |
| w | Int |  |  |
| h | Int |  |  |

### prependItem(text, big=None, mini=None, ptr=None, notify=False)

Append new item with given text and optional icons, and user-data pointer.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| text | String |  |  |
| big | FXIcon | None |  |
| mini | FXIcon | None |  |
| ptr | String | None |  |
| notify | Bool | False |  |

### prependItem(item, notify=False)

Append a [possibly subclassed] item to the end of the list.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| item | FXIconItem |  |  |
| notify | Bool | False |  |

### recalc()

Recalculate layout.

Reimplemented from FXWindow.

### removeHeader(index)

Remove header at index.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |

### removeItem(index, notify=False)

Remove item from list.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |
| notify | Bool | False |  |

### replaceItem(index, text, big=None, mini=None, ptr=None, notify=False)

Replace items text, icons, and user-data pointer.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |
| text | String |  |  |
| big | FXIcon | None |  |
| mini | FXIcon | None |  |
| ptr | String | None |  |
| notify | Bool | False |  |

### replaceItem(index, item, notify=False)

Replace the item with a [possibly subclassed] item.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |
| item | FXIconItem |  |  |
| notify | Bool | False |  |

### resize(w, h)

Resize this window to the specified width and height.

Reimplemented from FXWindow.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| w | Int |  |  |
| h | Int |  |  |

### retrieveItem(index)

Return the item at the given index.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |

### selectInRectangle(x, y, w, h, notify=False)

Select items in rectangle.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| x | Int |  |  |
| y | Int |  |  |
| w | Int |  |  |
| h | Int |  |  |
| notify | Bool | False |  |

### selectItem(index, notify=False)

Select item at index.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |
| notify | Bool | False |  |

### setAnchorItem(index)

Change anchor item index.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |

### setCurrentItem(index, notify=False)

Change current item index.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |
| notify | Bool | False |  |

### setFocus()

Move the focus to this window.

Reimplemented from FXWindow.

### setFont(fnt)

Change text font.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| fnt | FXFont |  |  |

### setHeaderIcon(index, icon)

Change icon of header at index.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |
| icon | FXIcon |  |  |

### setHeaderSize(index, size)

Change size of header at index.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |
| size | Int |  |  |

### setHeaderText(index, text)

Change text of header at index.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |
| text | String |  |  |

### setHelpText(text)

Set the status line help text for this widget.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| text | String |  |  |

### setItemBigIcon(index, icon)

Change item big icon.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |
| icon | FXIcon |  |  |

### setItemData(index, ptr)

Change item user-data pointer.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |
| ptr | String |  |  |

### setItemMiniIcon(index, icon)

Change item mini icon.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |
| icon | FXIcon |  |  |

### setItemSpace(s)

Change maximum item space for each item.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| s | Int |  |  |

### setItemText(index, text)

Change item text.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |
| text | String |  |  |

### setListStyle(style)

Set the current icon list style.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| style | Int |  |  |

### setSelBackColor(clr)

Change selected text background.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| clr | FXColor |  |  |

### setSelTextColor(clr)

Change selected text color.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| clr | FXColor |  |  |

### setSortFunc(func)

Change sort function.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| func | FXIconListSortFunc |  |  |

### setTextColor(clr)

Change normal text color.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| clr | FXColor |  |  |

### sortItems()

Sort items.

### toggleItem(index, notify=False)

Toggle item at index.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |
| notify | Bool | False |  |

### updateItem(index)

Repaint item at index.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  |  |

### Global flags

### **Icon list styles**

| **ICONLIST_EXTENDEDSELECT** | Extended selection mode. |
| --- | --- |
| **ICONLIST_SINGLESELECT** | At most one selected item. |
| **ICONLIST_BROWSESELECT** | Always exactly one selected item. |
| **ICONLIST_MULTIPLESELECT** | Multiple selection mode. |
| **ICONLIST_AUTOSIZE** | Automatically size item spacing. |
| **ICONLIST_DETAILED** | List mode. |
| **ICONLIST_MINI_ICONS** | Mini Icon mode. |
| **ICONLIST_BIG_ICONS** | Big Icon mode. |
| **ICONLIST_ROWS** | Row-wise mode. |
| **ICONLIST_COLUMNS** | Column-wise mode. |




