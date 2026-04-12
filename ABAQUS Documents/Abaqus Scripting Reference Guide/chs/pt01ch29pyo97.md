# 29.97 TensionCutOff object







The TensionCutOff object specifies tension cutoff for different material models for example the Mohr-Coulomb plasticity model.

**Access**

```
import material
mdb.models[*name*].materials[*name*].mohrCoulombPlasticity.tensionCutOff
import odbMaterial
session.odbs[*name*].materials[*name*].mohrCoulombPlasticity.tensionCutOff
```

### 29.97.1 TensionCutOff(...)

This method creates a TensionCutOff object.

**Path**

```
mdb.models[*name*].materials[*name*].mohrCoulombPlasticity.TensionCutOff
session.odbs[*name*].materials[*name*].mohrCoulombPlasticity.TensionCutOff
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

- Tension cutoff stress.
- The value of the corresponding tensile plastic strain.(The first tabular value entered must always be zero.)
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A TensionCutOff object.

**Exceptions**

RangeError.

### 29.97.2 setValues(...)

This method modifies the TensionCutOff object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [TensionCutOff](pt01ch29pyo97.md#ker-tensioncutoff-tensioncutoff-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.97.3 Members

The TensionCutOff object has members with the same names and descriptions as the arguments to the [TensionCutOff](pt01ch29pyo97.md#ker-tensioncutoff-tensioncutoff-pyc) method.

### 29.97.4 Corresponding analysis keywords

| [*TENSION CUTOFF](../key/key-link.md#usb-kws-mtensioncutoff) |
| --- |




