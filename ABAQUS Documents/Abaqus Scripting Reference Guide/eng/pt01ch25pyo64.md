# 25.64 SmoothingAssignment object







The SmoothingAssignment object stores the surface smoothing assignment definition for surfaces in [ContactExp](pt01ch25pyo19.md) and [ContactStd](pt01ch25pyo24.md) objects. The SmoothingAssignment object has no constructor or members.

**Access**

```
import interaction
mdb.models[*name*].interactions[*name*].smoothingAssignments
```

### 25.64.1 changeValuesInStep(...)

This method allows modification of surface smoothing assignments already defined on surfaces in a given step.

**Required arguments**

*stepName*

A String specifying the name of the step in which the surface smoothing assignments are to be modified.

*index*

An Int specifying the position of the surface smoothing assignment whose value is to be modified.

*value*

A tuple specifying the value of the surface smoothing assignments for the surface whose index is referenced. Each tuple contains one entry:
- A SymbolicConstant specifying the surface smoothing value to be used for the surface. Possible values of the SymbolicConstant are NONE, REVOLUTION, SPHERICAL, and TOROIDAL.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 25.64.2 appendInStep(...)

This method allows addition of surface smoothing assignments to new surfaces in a given step.

**Required arguments**

*stepName*

A String specifying the name of the step in which new surface smoothing assignments are to be defined.

*assignments*

A sequence of tuples specifying the surface smoothing assignments. Each tuple contains two entries:
- A region object specifying the surface to which the smoothing is assigned.
- A SymbolicConstant specifying the surface smoothing value to be used for the surface. Possible values of the SymbolicConstant are NONE, REVOLUTION, SPHERICAL, and TOROIDAL.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 25.64.3 delete(...)

The `delete` method allows you to delete existing surface smoothing assignments from [ContactExp](pt01ch25pyo19.md) and [ContactStd](pt01ch25pyo24.md) objects.

**Required argument**

*indices*

A sequence of Ints specifying the index of each surface smoothing assignment to delete.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 25.64.4 Members

The SmoothingAssignment object has no members.

### 25.64.5 Corresponding analysis keywords

| [*SURFACE PROPERTY ASSIGNMENT](../key/key-link.md#usb-kws-hsurfpropassign), PROPERTY=GEOMETRIC CORRECTION |
| --- |




