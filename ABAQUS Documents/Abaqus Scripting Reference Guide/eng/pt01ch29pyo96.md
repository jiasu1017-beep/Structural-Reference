# 29.96 Swelling object







The Swelling object specifies time-dependent volumetric swelling for a material.

**Access**

```
import material
mdb.models[*name*].materials[*name*].swelling
import odbMaterial
session.odbs[*name*].materials[*name*].swelling
```

### 29.96.1 Swelling(...)

This method creates a Swelling object.

**Path**

```
mdb.models[*name*].materials[*name*].Swelling
session.odbs[*name*].materials[*name*].Swelling
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

This argument is valid only when *law*=INPUT.

**Optional arguments**

*law*

A SymbolicConstant specifying the type of data defining the swelling behavior. Possible values are INPUT and USER. The default value is INPUT.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

- Volumetric swelling strain rate.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A Swelling object.

**Exceptions**

RangeError.

### 29.96.2 setValues(...)

This method modifies the Swelling object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [Swelling](pt01ch29pyo96.md#ker-swelling-swelling-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.96.3 Members

The Swelling object has members with the same names and descriptions as the arguments to the [Swelling](pt01ch29pyo96.md#ker-swelling-swelling-pyc) method.

In addition, the Swelling object can have the following member:

*ratios*

A [Ratios](pt01ch29pyo86.md) object.

### 29.96.4 Corresponding analysis keywords

| [*SWELLING](../key/key-link.md#usb-kws-mswelling) |
| --- |




