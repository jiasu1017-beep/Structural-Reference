# 42.2 FluidCavityPressure object







The FluidCavityPressure object stores the data for initial fluid cavity pressures.  The base class*region* argument can not be specifed with this object.

The FluidCavityPressure object is derived from the [PredefinedField](pt01ch42pyo01.md) object.

**Access**

```
import load
mdb.models[*name*].predefinedFields[*name*]
```

### 42.2.1 FluidCavityPressure(...)

This method creates a FluidCavityPressure object.

**Path**

```
mdb.models[*name*].FluidCavityPressure
```

**Required arguments**

*name*

A String specifying the repository key.

*fluidCavity*

A String specifying the name of a Fluid Cavity Interaction.

*fluidPressure*

A Float specifying the initial fluid pressure.

**Optional arguments**

None.

**Return value**

A FluidCavityPressure object.

**Exceptions**

None.

### 42.2.2 setValues(...)

This method modifies the FluidCavityPressure object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [FluidCavityPressure](pt01ch42pyo02.md#ker-fluidcavitypressure-fluidcavitypressure-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

None.

### 42.2.3 Members

The FluidCavityPressure object has members with the same names and descriptions as the arguments to the [FluidCavityPressure](pt01ch42pyo02.md#ker-fluidcavitypressure-fluidcavitypressure-pyc) method.

In addition, the FluidCavityPressure object can have the following member:

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the predefined field is applied. *Region* is ignored if the predefined field has an *instances* member available.  *Region* is also ignored if the predefined field has a *distributionType* member available, and *distributionType*=FROM_FILE or FROM_FILE_AND_USER_DEFINED.

### 42.2.4 Corresponding analysis keywords

| [*INITIAL CONDITIONS](../key/key-link.md#usb-kws-minitialcond), TYPE=FLUID PRESSURE |
| --- |




