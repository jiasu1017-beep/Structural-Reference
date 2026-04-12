# 29.92 Solubility object







The Solubility object specifies solubility.

**Access**

```
import material
mdb.models[*name*].materials[*name*].solubility
import odbMaterial
session.odbs[*name*].materials[*name*].solubility
```

### 29.92.1 Solubility(...)

This method creates a Solubility object.

**Path**

```
mdb.models[*name*].materials[*name*].Solubility
session.odbs[*name*].materials[*name*].Solubility
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

- Solubility.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A Solubility object.

**Exceptions**

RangeError.

### 29.92.2 setValues(...)

This method modifies the Solubility object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [Solubility](pt01ch29pyo92.md#ker-solubility-solubility-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.92.3 Members

The Solubility object has members with the same names and descriptions as the arguments to the [Solubility](pt01ch29pyo92.md#ker-solubility-solubility-pyc) method.

### 29.92.4 Corresponding analysis keywords

| [*SOLUBILITY](../key/key-link.md#usb-kws-msolubility) |
| --- |




