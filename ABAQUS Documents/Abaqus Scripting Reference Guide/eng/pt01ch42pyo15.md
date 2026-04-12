# 42.15 Velocity object







The Velocity object stores the data for an initial velocity predefined field.

The Velocity object is derived from the [PredefinedField](pt01ch42pyo01.md) object.

**Access**

```
import load
mdb.models[*name*].predefinedFields[*name*]
```

### 42.15.1 Velocity(...)

This method creates a Velocity predefined field object.

**Path**

```
mdb.models[*name*].Velocity
```

**Required arguments**

*name*

A String specifying the repository key.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the predefined field is applied. *Region* is ignored if the predefined field has an *instances* member available.  *Region* is also ignored if the predefined field has a *distributionType* member available, and *distributionType*=FROM_FILE or FROM_FILE_AND_USER_DEFINED.

*velocity1*

A Float specifying the first component of the velocity.

*velocity2*

A Float specifying the second component of the velocity.

*velocity3*

A Float specifying the third component of the velocity.

*omega*

A Float specifying the angular velocity.

*axisBegin*

A sequence of Floats specifying the *X-*, *Y-*, and *Z*- coordinates of the starting point of the axis about which *omega* is defined.

*axisEnd*

A sequence of Floats specifying the *X-*, *Y-*, and *Z*- coordinates of the end point of the axis about which *omega* is defined.

**Optional arguments**

*field*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) object associated with this predefined field. The *field* argument applies only when *distributionType*=FIELD_ANALYTICAL. The default value is an empty string.

*distributionType*

A SymbolicConstant specifying whether the load is uniform. Possible values are MAGNITUDE and FIELD_ANALYTICAL. The default value is MAGNITUDE.

**Return value**

A Velocity object.

**Exceptions**

None.

### 42.15.2 setValues(...)

This method modifies the Velocity object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [Velocity](pt01ch42pyo15.md#ker-velocity-velocity-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

None.

### 42.15.3 Members

The Velocity object has members with the same names and descriptions as the arguments to the [Velocity](pt01ch42pyo15.md#ker-velocity-velocity-pyc) method.

### 42.15.4 Corresponding analysis keywords

| [*INITIAL CONDITIONS](../key/key-link.md#usb-kws-minitialcond), TYPE=VELOCITY |
| --- |
| [*INITIAL CONDITIONS](../key/key-link.md#usb-kws-minitialcond), TYPE=ROTATING VELOCITY |




