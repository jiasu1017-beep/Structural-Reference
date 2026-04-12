# 13.4 DisplayBody object







The DisplayBody object defines a constraint such that the specified instance is used for display only and does not take part in the analysis. However it will still be visible during postprocessing and its position at any frame will be defined by the translation and rotation of the specified control points.

The DisplayBody object is derived from the [Constraint](pt01ch13pyo01.md) object.

**Access**

```
import interaction
mdb.models[*name*].constraints[*name*]
```

### 13.4.1 DisplayBody(...)

This method creates a DisplayBody object.

**Path**

```
mdb.models[*name*].DisplayBody
```

**Required arguments**

*name*

A String specifying the constraint repository key.

*instance*

A [PartInstance](pt01ch06pyo04.md) object specifying the part instance that is to be used for display only.

*controlPoints*

A [ModelDotArray](pt01ch07pyo12.md) object specifying the motion of the [PartInstance](pt01ch06pyo04.md). The control points may be Vertex, ReferencePoint, or MeshNode objects. Their motion will control the motion of the PartInstance. If this argument is set to an empty sequence, the PartInstance will remain fixed in space during the analysis. The sequence can have either one object or three objects.

**Optional arguments**

None.

**Return value**

A DisplayBody object.

**Exceptions**

None.

### 13.4.2 setValues(...)

This method modifies the DisplayBody object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [DisplayBody](pt01ch13pyo04.md#ker-displaybody-displaybody-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

None.

### 13.4.3 Members

The DisplayBody object has members with the same names and descriptions as the arguments to the [DisplayBody](pt01ch13pyo04.md#ker-displaybody-displaybody-pyc) method.

In addition, the DisplayBody object has the following member:

*suppressed*

A Boolean specifying whether the constraint is suppressed or not. The default value is OFF.

### 13.4.4 Corresponding analysis keywords

| [*DISPLAY BODY](../key/key-link.md#usb-kws-mdisplaybody) |
| --- |




