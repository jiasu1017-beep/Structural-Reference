# AFXItemProvider







This class provides a way to supply items to widgets, such as AFXComboBox and AFXList. 
![](../graphics/gui-afxitemprovider.png)

### AFXItemProvider(initialItems='')

Constructor.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| initialItems | String | '' | Sequence string with initial items. |

### append(str)

Appends a string to the item string.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| str | String |  |  |

### append(ch)

Appends a character to the item string.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| ch | String |  |  |

### empty()

Returns True if the item string is empty.

### getItems()

Returns a sequence string that contains all of the provider's items.

### getVersion()

Returns the version of provider's items.

### reset(sz=0)

Clears the contents of the item string and reallocates space.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| sz | Int | 0 |  |

### setItems(newItems)

Sets all of the providers's items, clearing any previous items first.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| newItems | String |  | Sequence string with new items. |




