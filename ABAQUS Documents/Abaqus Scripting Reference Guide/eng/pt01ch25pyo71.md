# 25.71 SurfaceFeatureAssignment object







The SurfaceFeatureAssignment object stores the surface feature angle assignment definition for surfaces in [ContactExp](pt01ch25pyo19.md)  or [ContactStd](pt01ch25pyo24.md) objects. The SurfaceFeatureAssignment object has no constructor or members.

**Access**

```
import interaction
mdb.models[*name*].interactions[*name*].surfaceFeatureAssignments
```

### 25.71.1 changeValuesInStep(...)

This method allows modification of surface feature angle assignments already defined on surfaces in a given step.

**Required arguments**

*stepName*

A String specifying the name of the step in which the surface feature assignments are to be modified.

*index*

An Int specifying the position of the surface feature angle assignment whose value is to be modified.

*value*

A tuple specifying the value of the surface feature assignments for the surface whose index is referenced. Each tuple contains one entry:
- A Float or a SymbolicConstant specifying the overriding surface feature angle value to be used for the surface. Possible values of the SymbolicConstant are PERIMETER, ALL, PICKED, or NONE. The ALL and PICKED values cannot be specified with the GLOBAL region constant, and can be used only in the Explicit version of general contact.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 25.71.2 appendInStep(...)

This method allows addition of surface feature angle assignments to new surfaces in a given step.

**Required arguments**

*stepName*

A String specifying the name of the step in which new surface feature angle assignments are to be defined.

*assignments*

A sequence of tuples specifying the surface feature angle assignments. Each tuple contains two entries:
- A region object or the SymbolicConstant GLOBAL specifying the surface to which the feature angle is assigned.
- A Float or a SymbolicConstant specifying the overriding surface feature angle value to be used for the surface. Possible values of the SymbolicConstant are PERIMETER, ALL, PICKED, or NONE. The ALL and PICKED values cannot be specified with the GLOBAL region constant, and can be used only in the Explicit version of general contact.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 25.71.3 delete(...)

The `delete` method allows you to delete existing surface feature angle assignments from a [ContactExp](pt01ch25pyo19.md) object.

**Required argument**

*indices*

A sequence of Ints specifying the index of each surface feature angle assignment to delete.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 25.71.4 Members

The SurfaceFeatureAssignment object has no members.

### 25.71.5 Corresponding analysis keywords

| [*SURFACE PROPERTY ASSIGNMENT](../key/key-link.md#usb-kws-hsurfpropassign), PROPERTY=FEATURE EDGE CRITERIA |
| --- |




