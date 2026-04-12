# 25.73 SurfaceThicknessAssignment object







The SurfaceThicknessAssignment object stores the surface thickness assignment definition for surfaces in [ContactExp](pt01ch25pyo19.md) and [ContactStd](pt01ch25pyo24.md) objects. The SurfaceThicknessAssignment object has no constructor or members.

**Access**

```
import interaction
mdb.models[*name*].interactions[*name*].surfaceThicknessAssignments
```

### 25.73.1 changeValuesInStep(...)

This method allows modification of surface thickness assignments already defined on surfaces in a given step.

**Required arguments**

*stepName*

A String specifying the name of the step in which the surface thickness assignments are to be modified.

*index*

An Int specifying the position of the surface thickness assignment whose value is to be modified.

*value*

A tuple specifying the value of the surface thickness assignments for the surface whose index is referenced. Each tuple contains two entries:
- A Float or a SymbolicConstant specifying the overriding thickness value to be used in the contact definition. Possible values of the SymbolicConstant are ORIGINAL and THINNING. The SymbolicConstant THINNING can be specified only in an Abaqus/Explicit analysis.
- A Float specifying a scale factor that multiplies the thickness value specified in the second entry.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 25.73.2 appendInStep(...)

This method allows addition of surface thickness assignments to new surfaces in a given step.

**Required arguments**

*stepName*

A String specifying the name of the step in which new surface thickness assignments are to be defined.

*assignments*

A sequence of tuples specifying the surface thickness assignments. Each tuple contains three entries:
- A region object or the SymbolicConstant GLOBAL specifying the surface to which the thickness is assigned.
- A Float or a SymbolicConstant specifying the overriding thickness value to be used in the contact definition. Possible values of the SymbolicConstant are ORIGINAL and THINNING. The SymbolicConstant THINNING can be specified only in an Abaqus/Explicit analysis.
- A Float specifying a scale factor that multiplies the thickness value specified in the second entry.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 25.73.3 delete(...)

The `delete` method allows you to delete existing surface thickness assignments.

**Required argument**

*indices*

A sequence of Ints specifying the index of each surface thickness assignment to delete.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 25.73.4 Members

The SurfaceThicknessAssignment object has no members.

### 25.73.5 Corresponding analysis keywords

| [*SURFACE PROPERTY ASSIGNMENT](../key/key-link.md#usb-kws-hsurfpropassign), PROPERTY=THICKNESS |
| --- |




