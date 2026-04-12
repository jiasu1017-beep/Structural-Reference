# 16.1 DisplayGroup object







 DisplayGroup objects are used to select a subset of the entities displayed in the viewport. 

**Access**

```
session.displayGroups[*name*]
import assembly
session.viewports[*name*].assemblyDisplay.displayGroup
session.viewports[*name*].layers[*name*].assemblyDisplay.displayGroup
import visualization
session.viewports[*name*].layers[*name*].odbDisplay.displayGroup
import part
session.viewports[*name*].layers[*name*].partDisplay.displayGroup
session.viewports[*name*].odbDisplay.displayGroup
session.viewports[*name*].partDisplay.displayGroup
```

### 16.1.1 DisplayGroup(...)

This method creates a DisplayGroup object.

**Path**

```
session.DisplayGroup
```

**Required arguments**

*name*

A String specifying the repository key.

*leaf*

A [Leaf](pt01ch16pyo04.md) object specifying the items in the display group.

**Optional arguments**

None.

**Return value**

A DisplayGroup object.

**Exceptions**

InvalidNameError.

### 16.1.2 add(...)

This method adds the specified items to the display group.

**Required argument**

*leaf*

A [Leaf](pt01ch16pyo04.md) object specifying the items to add to the display group.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 16.1.3 either(...)

This method redefines the display group to be only those items that are not shared by the *leaf* argument and by the display group.

**Required argument**

*leaf*

A [Leaf](pt01ch16pyo04.md) object specifying the items to be excluded from the display group.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 16.1.4 intersect(...)

This method redefines the display group to be only those items that are shared by the *leaf* argument and the display group.

**Required argument**

*leaf*

A [Leaf](pt01ch16pyo04.md) object specifying the items to be included in the display group.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 16.1.5 redoLast()

This method redoes the last undone operation on the display group.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 16.1.6 remove(...)

This method removes the specified items from the display group.

**Required argument**

*leaf*

A [Leaf](pt01ch16pyo04.md) object specifying the items to remove from the display group.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 16.1.7 replace(...)

This method replaces the contents of the display group with the specified items.

**Required argument**

*leaf*

A [Leaf](pt01ch16pyo04.md) object specifying the items with which to replace the current display group contents.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 16.1.8 undoLast()

This method undoes the last operation performed on the display group.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 16.1.9 Members

The DisplayGroup object has the following members:

*canUndo*

A Boolean specifying whether Undo is possible or not.

*canRedo*

A Boolean specifying whether Redo is possible or not.

*name*

A String specifying the repository key.

*module*

A SymbolicConstant specifying the module in which the display group has been created. The possible values are PART, ASSEMBLY, PART_ASSEMBLY, ODB, and ALL.

*modelName*

A String specifying the name of the model to which the display group belongs when the module is part- or assembly-based.

*partName*

A String specifying the name of the part to which the display group belongs when the module is part-based.




