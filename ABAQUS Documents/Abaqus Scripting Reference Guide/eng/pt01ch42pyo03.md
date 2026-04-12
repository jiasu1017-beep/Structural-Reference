# 42.3 FluidDensity object







The FluidDensity object stores the data for fluid density predefined fields.

The FluidDensity object is derived from the [PredefinedField](pt01ch42pyo01.md) object.

**Access**

```
import load
mdb.models[*name*].predefinedFields[*name*]
```

### 42.3.1 FluidDensity(...)

This method creates a FluidDensity object.

**Path**

```
mdb.models[*name*].FluidDensity
```

**Required arguments**

*name*

A String specifying the repository key.

*createStepName*

A String specifying the name of the step in which the predefined field is created.

*region*

A Region specifying the domain of the fluid density. Use 'None' to specify the whole model.

**Optional argument**

*density*

A Float specifying the fluid density. The default value is 0.0.

**Return value**

A FluidDensity object.

**Exceptions**

None.

### 42.3.2 setValues(...)

This method modifies the FluidDensity object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [FluidDensity](pt01ch42pyo03.md#ker-fluiddensity-fluiddensity-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 42.3.3 Members

The FluidDensity object can have the following members:

*name*

A String specifying the repository key.

*density*

A Float specifying the fluid density. The default value is 0.0.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the predefined field is applied. *Region* is ignored if the predefined field has an *instances* member available.  *Region* is also ignored if the predefined field has a *distributionType* member available, and *distributionType*=FROM_FILE or FROM_FILE_AND_USER_DEFINED.

### 42.3.4 Corresponding analysis keywords

| [*INITIAL CONDITIONS](../key/key-link.md#usb-kws-minitialcond), TYPE=DENSITY |
| --- |




