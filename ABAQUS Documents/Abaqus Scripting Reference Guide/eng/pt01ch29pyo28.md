# 29.28 CrushableFoamHardening object







The CrushableFoamHardening object specifies hardening for the crushable foam plasticity model.

**Access**

```
import material
mdb.models[*name*].materials[*name*].crushableFoam.crushableFoamHardening
import odbMaterial
session.odbs[*name*].materials[*name*].crushableFoam\
.crushableFoamHardening
```

### 29.28.1 CrushableFoamHardening(...)

This method creates a CrushableFoamHardening object.

**Path**

```
mdb.models[*name*].materials[*name*].crushableFoam.CrushableFoamHardening
session.odbs[*name*].materials[*name*].crushableFoam\
.CrushableFoamHardening
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

- The yield stress in uniaxial compression, ![](../graphics/ker_eqn00102.gif).
- The absolute value of the corresponding plastic strain.(The first tabular value entered must always be zero.)
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A CrushableFoamHardening object.

**Exceptions**

RangeError.

### 29.28.2 setValues(...)

This method modifies the CrushableFoamHardening object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [CrushableFoamHardening](pt01ch29pyo28.md#ker-crushablefoamhardening-crushablefoamhardening-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.28.3 Members

The CrushableFoamHardening object has members with the same names and descriptions as the arguments to the [CrushableFoamHardening](pt01ch29pyo28.md#ker-crushablefoamhardening-crushablefoamhardening-pyc) method.

### 29.28.4 Corresponding analysis keywords

| [*CRUSHABLE FOAM HARDENING](../key/key-link.md#usb-kws-mcrushfoamhardening) |
| --- |




