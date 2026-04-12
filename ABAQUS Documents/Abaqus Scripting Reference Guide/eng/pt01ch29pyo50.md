# 29.50 FailStrain object







The FailStrain object defines parameters for strain-based failure measures.

**Access**

```
import material
mdb.models[*name*].materials[*name*].elastic.failStrain
import odbMaterial
session.odbs[*name*].materials[*name*].elastic.failStrain
```

### 29.50.1 FailStrain(...)

This method creates a FailStrain object.

**Path**

```
mdb.models[*name*].materials[*name*].elastic.FailStrain
session.odbs[*name*].materials[*name*].elastic.FailStrain
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

- Tensile strain limit in fiber direction, ![](../graphics/ker_eqn00246.gif).
- Compressive strain limit in fiber direction, ![](../graphics/ker_eqn00247.gif).
- Tensile strain limit in transverse direction, ![](../graphics/ker_eqn00248.gif).
- Compressive strain limit in transverse direction, ![](../graphics/ker_eqn00249.gif).
- Shear strain limit in the ![](../graphics/ker_eqn00083.gif)--![](../graphics/ker_eqn00084.gif) plane, ![](../graphics/ker_eqn00250.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A FailStrain object.

**Exceptions**

RangeError.

### 29.50.2 setValues(...)

This method modifies the FailStrain object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [FailStrain](pt01ch29pyo50.md#ker-failstrain-failstrain-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.50.3 Members

The FailStrain object has members with the same names and descriptions as the arguments to the [FailStrain](pt01ch29pyo50.md#ker-failstrain-failstrain-pyc) method.

### 29.50.4 Corresponding analysis keywords

| [*FAIL STRAIN](../key/key-link.md#usb-kws-mefailstrain) |
| --- |




