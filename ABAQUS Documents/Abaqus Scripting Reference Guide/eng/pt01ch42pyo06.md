# 42.6 FluidVelocity object







The FluidVelocity object stores the data for fluid velocity Predefined fields.

The FluidVelocity object is derived from the [PredefinedField](pt01ch42pyo01.md) object.

**Access**

```
import load
mdb.models[*name*].predefinedFields[*name*]
```

### 42.6.1 FluidVelocity(...)

This method creates a FluidVelocity object.

**Path**

```
mdb.models[*name*].FluidVelocity
```

**Required arguments**

*name*

A String specifying the repository key.

*createStepName*

A String specifying the name of the step in which the predefined field is created.

*region*

A Region specifying the domain of the fluid velocity. Use 'None' to specify the whole model.

**Optional arguments**

*velocity1*

A Float specifying the fluid velocity in the 1 direction. The default value is 0.0.

*velocity2*

A Float specifying the fluid velocity in the 2 direction. The default value is 0.0.

*velocity3*

A Float specifying the fluid velocity in the 3 direction. The default value is 0.0.

**Return value**

A FluidVelocity object.

**Exceptions**

None.

### 42.6.2 setValues(...)

This method modifies the FluidVelocity object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [FluidVelocity](pt01ch42pyo06.md#ker-fluidvelocity-fluidvelocity-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 42.6.3 Members

The FluidVelocity object can have the following members:

*name*

A String specifying the repository key.

*velocity1*

A Float specifying the fluid velocity in the 1 direction. The default value is 0.0.

*velocity2*

A Float specifying the fluid velocity in the 2 direction. The default value is 0.0.

*velocity3*

A Float specifying the fluid velocity in the 3 direction. The default value is 0.0.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the predefined field is applied. *Region* is ignored if the predefined field has an *instances* member available.  *Region* is also ignored if the predefined field has a *distributionType* member available, and *distributionType*=FROM_FILE or FROM_FILE_AND_USER_DEFINED.

### 42.6.4 Corresponding analysis keywords

| [*INITIAL CONDITIONS](../key/key-link.md#usb-kws-minitialcond), TYPE=VELOCITY, ELEMENT AVERAGE |
| --- |




