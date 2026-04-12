# 29.15 ClayHardening object







The ClayHardening object specifies hardening for the clay plasticity model.

**Access**

```
import material
mdb.models[*name*].materials[*name*].clayPlasticity.clayHardening
import odbMaterial
session.odbs[*name*].materials[*name*].clayPlasticity.clayHardening
```

### 29.15.1 ClayHardening(...)

This method creates a ClayHardening object.

**Path**

```
mdb.models[*name*].materials[*name*].clayPlasticity.ClayHardening
session.odbs[*name*].materials[*name*].clayPlasticity.ClayHardening
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

- The hydrostatic pressure stress at yield, ![](../graphics/ker_eqn00105.gif).
- The absolute value of the corresponding volumetric plastic strain.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A ClayHardening object.

**Exceptions**

RangeError.

### 29.15.2 setValues(...)

This method modifies the ClayHardening object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ClayHardening](pt01ch29pyo15.md#ker-clayhardening-clayhardening-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.15.3 Members

The ClayHardening object has members with the same names and descriptions as the arguments to the [ClayHardening](pt01ch29pyo15.md#ker-clayhardening-clayhardening-pyc) method.

### 29.15.4 Corresponding analysis keywords

| [*CLAY HARDENING](../key/key-link.md#usb-kws-mclayhardening) |
| --- |




