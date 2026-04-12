# 29.44 DruckerPragerHardening object







The DruckerPragerHardening object specifies hardening for Drucker-Prager plasticity models.

**Access**

```
import material
mdb.models[*name*].materials[*name*].druckerPrager.druckerPragerHardening
import odbMaterial
session.odbs[*name*].materials[*name*].druckerPrager\
.druckerPragerHardening
```

### 29.44.1 DruckerPragerHardening(...)

This method creates a DruckerPragerHardening object.

**Path**

```
mdb.models[*name*].materials[*name*].druckerPrager.DruckerPragerHardening
session.odbs[*name*].materials[*name*].druckerPrager\
.DruckerPragerHardening
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*type*

A SymbolicConstant specifying the type of data defining the hardening behavior. Possible values are COMPRESSION, TENSION, and SHEAR. The default value is COMPRESSION.

*rate*

A Boolean specifying whether the data depend on rate. The default value is OFF.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

- Yield stress.
- Absolute value of the corresponding plastic strain. (The first tabular value entered must always be zero.)
- Equivalent plastic strain rate, ![](../graphics/ker_eqn00181.gif), for which this hardening curve applies.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A DruckerPragerHardening object.

**Exceptions**

RangeError.

### 29.44.2 setValues(...)

This method modifies the DruckerPragerHardening object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [DruckerPragerHardening](pt01ch29pyo44.md#ker-druckerpragerhardening-druckerpragerhardening-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.44.3 Members

The DruckerPragerHardening object has members with the same names and descriptions as the arguments to the [DruckerPragerHardening](pt01ch29pyo44.md#ker-druckerpragerhardening-druckerpragerhardening-pyc) method.

### 29.44.4 Corresponding analysis keywords

| [*DRUCKER PRAGER HARDENING](../key/key-link.md#usb-kws-mdruckerhardening) |
| --- |




