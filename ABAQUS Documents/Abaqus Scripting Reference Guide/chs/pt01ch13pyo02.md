# 13.2 AdjustPoints object







The AdjustPoints constraint object is used to adjust points (nodes) to a surface.

The AdjustPoints object is derived from the [Constraint](pt01ch13pyo01.md) object.

**Access**

```
import interaction
mdb.models[*name*].constraints[*name*]
```

### 13.2.1 AdjustPoints(...)

This method creates an AdjustPoints object.

**Path**

```
mdb.models[*name*].AdjustPoints
```

**Required arguments**

*name*

A String specifying the constraint repository key.

*surface*

A [Region](pt01ch45pyo03.md) object specifying the surface to which the *controlPoints* are adjusted.

*controlPoints*

A [Region](pt01ch45pyo03.md) object specifying the constraint control points.

**Optional arguments**

None.

**Return value**

An AdjustPoints object.

**Exceptions**

None.

### 13.2.2 setValues(...)

This method modifies the AdjustPoints object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [AdjustPoints](pt01ch13pyo02.md#ker-adjustpoints-adjustpoints-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

None.

### 13.2.3 Members

The AdjustPoints object has members with the same names and descriptions as the arguments to the [AdjustPoints](pt01ch13pyo02.md#ker-adjustpoints-adjustpoints-pyc) method.

In addition, the AdjustPoints object has the following member:

*suppressed*

A Boolean specifying whether the constraint is suppressed or not. The default value is OFF.

### 13.2.4 Corresponding analysis keywords

| [*ADJUST](../key/key-link.md#usb-kws-madjust) |
| --- |




