# 42.4 FluidThermalEnergy object







The FluidThermalEnergy object stores the data for fluid thermal energy predefined fields. This predefined field is applicable only when an energy equation has been selected in a flow step.

The FluidThermalEnergy object is derived from the [PredefinedField](pt01ch42pyo01.md) object.

**Access**

```
import load
mdb.models[*name*].predefinedFields[*name*]
```

### 42.4.1 FluidThermalEnergy(...)

This method creates a FluidThermalEnergy object.

**Path**

```
mdb.models[*name*].FluidThermalEnergy
```

**Required arguments**

*name*

A String specifying the repository key.

*createStepName*

A String specifying the name of the step in which the predefined field is created.

*region*

A Region specifying the domain of the fluid thermal energy. Use 'None' to specify the whole model.

**Optional arguments**

*temperature*

A Float specifying the fluid temperature. The default value is 0.0.

*distributionType*

A SymbolicConstant specifying whether the load is uniform. Possible values are MAGNITUDE, ANALYTICAL_FIELD, and DISCRETE_FIELD. The default value is MAGNITUDE.

**Return value**

A FluidThermalEnergy object.

**Exceptions**

None.

### 42.4.2 setValues(...)

This method modifies the FluidThermalEnergy object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [FluidThermalEnergy](pt01ch42pyo04.md#ker-fluidthermalenergy-fluidthermalenergy-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 42.4.3 Members

The FluidThermalEnergy object can have the following members:

*name*

A String specifying the repository key.

*temperature*

A Float specifying the fluid temperature. The default value is 0.0.

*distributionType*

A SymbolicConstant specifying whether the load is uniform. Possible values are MAGNITUDE, ANALYTICAL_FIELD, and DISCRETE_FIELD. The default value is MAGNITUDE.

*field*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) object associated with this predefined field. The *field* argument applies only when *distributionType*=ANALYTICAL_FIELD. The default value is an empty string.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the predefined field is applied. *Region* is ignored if the predefined field has an *instances* member available.  *Region* is also ignored if the predefined field has a *distributionType* member available, and *distributionType*=FROM_FILE or FROM_FILE_AND_USER_DEFINED.

### 42.4.4 Corresponding analysis keywords

| [*INITIAL CONDITIONS](../key/key-link.md#usb-kws-minitialcond), TYPE=TEMPERATURE, ELEMENT AVERAGE |
| --- |




