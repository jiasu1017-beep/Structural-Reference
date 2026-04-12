# 29.12 CastIronCompressionHardening object







The CastIronCompressionHardening object specifies hardening for the Cast- Iron plasticity model.

**Access**

```
import material
mdb.models[*name*].materials[*name*].castIronPlasticity\
.castIronCompressionHardening
import odbMaterial
session.odbs[*name*].materials[*name*].castIronPlasticity\
.castIronCompressionHardening
```

### 29.12.1 CastIronCompressionHardening(...)

This method creates a CastIronCompressionHardening object.

**Path**

```
mdb.models[*name*].materials[*name*].castIronPlasticity\
.CastIronCompressionHardening
session.odbs[*name*].materials[*name*].castIronPlasticity\
.CastIronCompressionHardening
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

- Yield stress in compression, ![](../graphics/ker_eqn00102.gif).
- The absolute value of the corresponding plastic strain.(The first tabular value entered must always be zero.)
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A CastIronCompressionHardening object.

**Exceptions**

RangeError.

### 29.12.2 setValues(...)

This method modifies the CastIronCompressionHardening object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [CastIronCompressionHardening](pt01ch29pyo12.md#ker-castironcompressionhardening-castironcompressionhard-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.12.3 Members

The CastIronCompressionHardening object has members with the same names and descriptions as the arguments to the [CastIronCompressionHardening](pt01ch29pyo12.md#ker-castironcompressionhardening-castironcompressionhard-pyc) method.

### 29.12.4 Corresponding analysis keywords

| [*CAST IRON COMPRESSION HARDENING](../key/key-link.md#usb-kws-mcastironcomhardening) |
| --- |




