# 16.2 DisplayGroupInstance object







A DisplayGroupInstance object stores the IDs of the entities displayed in a viewport. The DisplayGroupInstance object has no constructor. When you set a display group to be plotted in a viewport, Abaqus/CAE creates a DisplayGroupInstance object for each display group and places it in the [DisplayGroupInstanceRepository](pt01ch16pyo03.md) object.

**Access**

```
import assembly
session.viewports[*name*].assemblyDisplay.displayGroupInstances[*name*]
session.viewports[*name*].layers[*name*].assemblyDisplay\
.displayGroupInstances[*name*]
import visualization
session.viewports[*name*].layers[*name*].odbDisplay\
.displayGroupInstances[*name*]
import part
session.viewports[*name*].layers[*name*].partDisplay\
.displayGroupInstances[*name*]
session.viewports[*name*].odbDisplay.displayGroupInstances[*name*]
session.viewports[*name*].partDisplay.displayGroupInstances[*name*]
```

### 16.2.1 nodes()

This method is used to obtain the list of nodes present in the DisplayGroupInstance object. It returns a Dictionary object keyed by part instance names, the value of which is a list of user node labels belonging to the part instance and contained in the DisplayGroupInstance object. This method is available only for DisplayGroupInstance objects that are members of the DisplayGroupInstance repository member of [OdbDisplay](pt01ch35pyo01.md) object.

**Arguments**

None.

**Return value**

A Dictionary object.

**Exceptions**

None.

### 16.2.2 elements()

This method returns the list of elements present in the DisplayGroupInstance object. The `elements` method returns a Dictionary object that uses part instance names for the keys. The value of the items in the Dictionary object is a List of user element labels that belong to the part instance and are contained in the DisplayGroupInstance object. This method is available only for DisplayGroupInstance objects that are members of the DisplayGroupInstance repository member of the [OdbDisplay](pt01ch35pyo01.md) object.

**Arguments**

None.

**Return value**

A Dictionary object.

**Exceptions**

None.

### 16.2.3 setValues(...)

This method modifies the DisplayGroupInstance object. The `setValues` method is available only for DisplayGroupInstance objects that are members of the DisplayGroupInstance repository member of the [OdbDisplay](pt01ch35pyo01.md) object. 

**Required arguments**

None.

**Optional argument**

*lockOptions*

A Boolean specifying whether the display options stored on the DisplayGroupInstance object should be synchronized with changes to the viewport display options. This member is available only for DisplayGroupInstance objects that are members of the DisplayGroupInstance repository member of the [OdbDisplay](pt01ch35pyo01.md) object. The default value is OFF.

**Return value**

None

**Exceptions**

None.

### 16.2.4 Members

The DisplayGroupInstance object can have the following members:

*name*

A String specifying the repository key.

*lockOptions*

A Boolean specifying whether the display options stored on the DisplayGroupInstance object should be synchronized with changes to the viewport display options. This member is available only for DisplayGroupInstance objects that are members of the DisplayGroupInstance repository member of the [OdbDisplay](pt01ch35pyo01.md) object. The default value is OFF.

*odbDisplayOptions*

An [OdbDisplayOptions](pt01ch40pyo18.md) object specifying this member is available only for DisplayGroupInstance objects that are members of the DisplayGroupInstance repository member of the [OdbDisplay](pt01ch35pyo01.md) object.




