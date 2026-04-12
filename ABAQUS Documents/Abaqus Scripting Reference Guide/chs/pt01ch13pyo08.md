# 13.8 RigidBody object







The RigidBody object constrains all the degrees of freedom on the specified regions to the degree of freedom of its associated reference point.

The RigidBody object is derived from the [Constraint](pt01ch13pyo01.md) object.

**Access**

```
import interaction
mdb.models[*name*].constraints[*name*]
```

### 13.8.1 RigidBody(...)

This method creates a RigidBody object.

**Path**

```
mdb.models[*name*].RigidBody
```

**Required arguments**

*name*

A String specifying the constraint repository key.

*refPointRegion*

A [Region](pt01ch45pyo03.md) object specifying the reference point.

**Optional arguments**

*bodyRegion*

 `None` or a [Region](pt01ch45pyo03.md) object specifying the elements constrained to the movement of the reference point. The default value is `None`.

*tieRegion*

 `None` or a [Region](pt01ch45pyo03.md) object specifying the nodes tied to the movement of the reference point. The default value is `None`.

*pinRegion*

 `None` or a [Region](pt01ch45pyo03.md) object specifying the nodes pinned to the movement of the reference point. The default value is `None`.

*surfaceRegion*

 `None` or a [Region](pt01ch45pyo03.md) object specifying the analytic surface constrained to the movement of the reference point. The default value is `None`.

*refPointAtCOM*

A Boolean specifying whether the analysis product should recompute the reference point position to be at the center of mass. The default value is OFF.

*isothermal*

A Boolean specifying whether the temperature degree of freedom should be constrained. The default value is OFF.

**Return value**

A RigidBody object.

**Exceptions**

None.

### 13.8.2 setValues(...)

This method modifies the RigidBody object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [RigidBody](pt01ch13pyo08.md#ker-rigidbody-rigidbody-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

None.

### 13.8.3 Members

The RigidBody object has members with the same names and descriptions as the arguments to the [RigidBody](pt01ch13pyo08.md#ker-rigidbody-rigidbody-pyc) method.

In addition, the RigidBody object has the following member:

*suppressed*

A Boolean specifying whether the constraint is suppressed or not. The default value is OFF.

### 13.8.4 Corresponding analysis keywords

| [*RIGID BODY](../key/key-link.md#usb-kws-mrigidbody) |
| --- |




