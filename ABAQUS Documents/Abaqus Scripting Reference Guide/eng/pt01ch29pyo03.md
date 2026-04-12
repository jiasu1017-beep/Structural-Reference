# 29.3 AnnealTemperature object







The AnnealTemperature object specifies the material annealing temperature.

**Access**

```
import material
mdb.models[*name*].materials[*name*].plastic.annealTemperature
import odbMaterial
session.odbs[*name*].materials[*name*].plastic.annealTemperature
```

### 29.3.1 AnnealTemperature(...)

This method creates an AnnealTemperature object.

**Path**

```
mdb.models[*name*].materials[*name*].plastic.AnnealTemperature
session.odbs[*name*].materials[*name*].plastic.AnnealTemperature
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional argument**

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

- The annealing temperature, ![](../graphics/ker_eqn00053.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

An AnnealTemperature object.

**Exceptions**

RangeError.

### 29.3.2 setValues(...)

This method modifies the AnnealTemperature object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [AnnealTemperature](pt01ch29pyo03.md#ker-annealtemperature-annealtemperature-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.3.3 Members

The AnnealTemperature object has members with the same names and descriptions as the arguments to the [AnnealTemperature](pt01ch29pyo03.md#ker-annealtemperature-annealtemperature-pyc) method.

### 29.3.4 Corresponding analysis keywords

| [*ANNEAL TEMPERATURE](../key/key-link.md#usb-kws-mannealtemp) |
| --- |




