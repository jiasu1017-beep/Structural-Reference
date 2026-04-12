# 29.54 GapFlow object







The GapFlow object specifies tangential flow constitutive parameters for pore pressure cohesive elements.

**Access**

```
import material
mdb.models[*name*].materials[*name*].gapFlow
import odbMaterial
session.odbs[*name*].materials[*name*].gapFlow
```

### 29.54.1 GapFlow(...)

This method creates an GapFlow object.

**Path**

```
mdb.models[*name*].materials[*name*].GapFlow
session.odbs[*name*].materials[*name*].GapFlow
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*kmax*

 `None` or a Float specifying the maximum permeability value that should be used. If *kmax*=`None`, Abaqus assumes that the permeability is not bounded. This value is meaningful only when *type*=NEWTONIAN. The default value is `None`.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

*type*

A SymbolicConstant specifying the type of gap flow. Possible values are NEWTONIAN and POWER_LAW. The default value is NEWTONIAN.

**Table data**

If *type*=NEWTONIAN the table data specify the following:
- Pore viscosity.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=POWER_LAW the table data specify the following:- Consistency.
- Exponent.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A GapFlow object.

**Exceptions**

None.

### 29.54.2 setValues(...)

This method modifies the GapFlow object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [GapFlow](pt01ch29pyo54.md#ker-gapflow-gapflow-pyc) method.

**Return value**

None

**Exceptions**

None.

### 29.54.3 Members

The GapFlow object has members with the same names and descriptions as the arguments to the [GapFlow](pt01ch29pyo54.md#ker-gapflow-gapflow-pyc) method.

### 29.54.4 Corresponding analysis keywords

| [*GAP FLOW](../key/key-link.md#usb-kws-mgapflow) |
| --- |




