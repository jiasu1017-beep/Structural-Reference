# 29.69 MohrCoulombHardening object







The MohrCoulombHardening object specifies hardening for the Mohr-Coulomb plasticity model.

**Access**

```
import material
mdb.models[*name*].materials[*name*].mohrCoulombPlasticity\
.mohrCoulombHardening
import odbMaterial
session.odbs[*name*].materials[*name*].mohrCoulombPlasticity\
.mohrCoulombHardening
```

### 29.69.1 MohrCoulombHardening(...)

This method creates a MohrCoulombHardening object.

**Path**

```
mdb.models[*name*].materials[*name*].mohrCoulombPlasticity\
.MohrCoulombHardening
session.odbs[*name*].materials[*name*].mohrCoulombPlasticity\
.MohrCoulombHardening
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

- Cohesion yield stress.
- The absolute value of the corresponding plastic strain.(The first tabular value entered must always be zero.)
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A MohrCoulombHardening object.

**Exceptions**

RangeError.

### 29.69.2 setValues(...)

This method modifies the MohrCoulombHardening object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [MohrCoulombHardening](pt01ch29pyo69.md#ker-mohrcoulombhardening-mohrcoulombhardening-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.69.3 Members

The MohrCoulombHardening object has members with the same names and descriptions as the arguments to the [MohrCoulombHardening](pt01ch29pyo69.md#ker-mohrcoulombhardening-mohrcoulombhardening-pyc) method.

### 29.69.4 Corresponding analysis keywords

| [*MOHR COULOMB HARDENING](../key/key-link.md#usb-kws-mmohrcoulombhardening) |
| --- |




