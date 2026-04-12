# 29.13 CastIronPlasticity object







The CastIronPlasticity object specifies the Cast Iron plasticity model.

**Access**

```
import material
mdb.models[*name*].materials[*name*].castIronPlasticity
import odbMaterial
session.odbs[*name*].materials[*name*].castIronPlasticity
```

### 29.13.1 CastIronPlasticity(...)

This method creates a CastIronPlasticity object.

**Path**

```
mdb.models[*name*].materials[*name*].CastIronPlasticity
session.odbs[*name*].materials[*name*].CastIronPlasticity
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

The table data specify the following:
- Plastic Poisson's ratio, ![](../graphics/ker_eqn00103.gif) (dimensionless).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A CastIronPlasticity object.

**Exceptions**

RangeError.

### 29.13.2 setValues(...)

This method modifies the CastIronPlasticity object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [CastIronPlasticity](pt01ch29pyo13.md#ker-castironplasticity-castironplasticity-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.13.3 Members

The CastIronPlasticity object has members with the same names and descriptions as the arguments to the [CastIronPlasticity](pt01ch29pyo13.md#ker-castironplasticity-castironplasticity-pyc) method.

In addition, the CastIronPlasticity object can have the following members:

*castIronTensionHardening*

A [CastIronTensionHardening](pt01ch29pyo14.md) object.

*castIronCompressionHardening*

A [CastIronCompressionHardening](pt01ch29pyo12.md) object.

### 29.13.4 Corresponding analysis keywords

| [*CAST IRON PLASTICITY](../key/key-link.md#usb-kws-mcastironplastic) |
| --- |




