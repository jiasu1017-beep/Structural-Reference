# 42.5 FluidTurbulence object







The FluidTurbulence object stores the data for fluid turbulence predefined fields. This predefined field is applicable only when a turbulence model has been selected in a flow step.

The FluidTurbulence object is derived from the [PredefinedField](pt01ch42pyo01.md) object.

**Access**

```
import load
mdb.models[*name*].predefinedFields[*name*]
```

### 42.5.1 FluidTurbulence(...)

This method creates aFluidTurbulence                     object.

**Path**

```
mdb.models[*name*].FluidTurbulence
```

**Required arguments**

*name*

A String specifying the repository key.

*createStepName*

A String specifying the name of the step in which the predefined field is created.

*region*

A Region specifying the domain of the fluid turbulence. Use 'None' to specify the whole model.

**Optional arguments**

*eddyViscosity*

A Float specifying the eddy viscosity for the fluid turbulence. This parameter is applicable only when the Spalart-Allmaras turbulence model has been selected in a flow step. The default value is 0.0.

*dissipationRate*

A Float specifying the dissipation rate for the fluid turbulence. This parameter is applicable only when the k-epsilon renormalization group (RNG) turbulence model has been selected in a flow step. The default value is 0.0.

*turbulentKE*

A Float specifying the kinetic energy for the fluid turbulence. This parameter is applicable only when the k-epsilon renormalization group (RNG) turbulence model has been selected in a flow step. The default value is 0.0.

**Return value**

A FluidTurbulence object.

**Exceptions**

None.

### 42.5.2 setValues(...)

This method modifies the FluidTurbulence object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [FluidTurbulence](pt01ch42pyo05.md#ker-fluidturbulence-fluidturbulence-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 42.5.3 Members

The FluidTurbulence object can have the following members:

*name*

A String specifying the repository key.

*eddyViscosity*

A Float specifying the eddy viscosity for the fluid turbulence. This parameter is applicable only when the Spalart-Allmaras turbulence model has been selected in a flow step. The default value is 0.0.

*dissipationRate*

A Float specifying the dissipation rate for the fluid turbulence. This parameter is applicable only when the k-epsilon renormalization group (RNG) turbulence model has been selected in a flow step. The default value is 0.0.

*turbulentKE*

A Float specifying the kinetic energy for the fluid turbulence. This parameter is applicable only when the k-epsilon renormalization group (RNG) turbulence model has been selected in a flow step. The default value is 0.0.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the predefined field is applied. *Region* is ignored if the predefined field has an *instances* member available.  *Region* is also ignored if the predefined field has a *distributionType* member available, and *distributionType*=FROM_FILE or FROM_FILE_AND_USER_DEFINED.

### 42.5.4 Corresponding analysis keywords

| [*INITIAL CONDITIONS](../key/key-link.md#usb-kws-minitialcond), TYPE=TURBNU, TYPE=TURBKE, TYPE= TURBEPS, ELEMENT AVERAGE |
| --- |




