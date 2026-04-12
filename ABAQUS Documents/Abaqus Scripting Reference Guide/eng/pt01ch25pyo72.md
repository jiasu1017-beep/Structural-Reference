# 25.72 SurfaceOffsetAssignment object







The SurfaceOffsetAssignment object stores the surface offset fraction assignment definition for surfaces in [ContactExp](pt01ch25pyo19.md) and [ContactStd](pt01ch25pyo24.md) objects. The SurfaceOffsetAssignment object has no constructor or members.

**Access**

```
import interaction
mdb.models[*name*].interactions[*name*].surfaceOffsetAssignments
```

### 25.72.1 changeValuesInStep(...)

This method allows modification of surface offset fraction assignments already defined on surfaces in a given step.

**Required arguments**

*stepName*

A String specifying the name of the step in which the surface offset assignments are to be modified.

*index*

An Int specifying the position of the surface offset fraction assignment whose value is to be modified.

*value*

A tuple specifying the value of the surface offset assignments for the surface whose index is referenced. Each tuple contains one entry:
- A Float or a SymbolicConstant specifying the surface offset fraction value to be used for the surface. Possible values of the SymbolicConstant are ORIGINAL, SPOS, and SNEG.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 25.72.2 appendInStep(...)

This method allows addition of surface offset fraction assignments to new surfaces in a given step.

**Required arguments**

*stepName*

A String specifying the name of the step in which new surface offset fraction assignments are to be defined.

*assignments*

A sequence of tuples specifying the surface offset fraction assignments. Each tuple contains two entries:
- A region object or the SymbolicConstant GLOBAL specifying the surface to which the offset fraction is assigned.
- A Float or a SymbolicConstant specifying the surface offset fraction value to be used for the surface. Possible values of the SymbolicConstant are ORIGINAL, SPOS, and SNEG.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 25.72.3 delete(...)

The `delete` method allows you to delete existing surface offset fraction assignments.

**Required argument**

*indices*

A sequence of Ints specifying the index of each surface offset fraction assignment to delete.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 25.72.4 Members

The SurfaceOffsetAssignment object has no members.

### 25.72.5 Corresponding analysis keywords

| [*SURFACE PROPERTY ASSIGNMENT](../key/key-link.md#usb-kws-hsurfpropassign), PROPERTY=OFFSET FRACTION |
| --- |




