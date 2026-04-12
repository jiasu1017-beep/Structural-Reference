# 29.14 CastIronTensionHardening object







The CastIronTensionHardening object specifies hardening for the Cast- Iron plasticity model.

**Access**

```
import material
mdb.models[*name*].materials[*name*].castIronPlasticity\
.castIronTensionHardening
import odbMaterial
session.odbs[*name*].materials[*name*].castIronPlasticity\
.castIronTensionHardening
```

### 29.14.1 CastIronTensionHardening(...)

This method creates a CastIronTensionHardening object.

**Path**

```
mdb.models[*name*].materials[*name*].castIronPlasticity\
.CastIronTensionHardening
session.odbs[*name*].materials[*name*].castIronPlasticity\
.CastIronTensionHardening
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

- Yield stress in uniaxial tension, ![](../graphics/ker_eqn00104.gif).
- The absolute value of the corresponding plastic strain.(The first tabular value entered must always be zero.)
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A CastIronTensionHardening object.

**Exceptions**

RangeError.

### 29.14.2 setValues(...)

This method modifies the CastIronTensionHardening object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [CastIronTensionHardening](pt01ch29pyo14.md#ker-castirontensionhardening-castirontensionhardening-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.14.3 Members

The CastIronTensionHardening object has members with the same names and descriptions as the arguments to the [CastIronTensionHardening](pt01ch29pyo14.md#ker-castirontensionhardening-castirontensionhardening-pyc) method.

### 29.14.4 Corresponding analysis keywords

| [*CAST IRON TENSION HARDENING](../key/key-link.md#usb-kws-mcastirontenhardening) |
| --- |




