# 29.93 SoretEffect object







The SoretEffect object defines temperature gradient driven mass diffusion.

**Access**

```
import material
mdb.models[*name*].materials[*name*].diffusivity.soretEffect
import odbMaterial
session.odbs[*name*].materials[*name*].diffusivity.soretEffect
```

### 29.93.1 SoretEffect(...)

This method creates a SoretEffect object.

**Path**

```
mdb.models[*name*].materials[*name*].diffusivity.SoretEffect
session.odbs[*name*].materials[*name*].diffusivity.SoretEffect
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

- Soret effect factor, ![](../graphics/ker_eqn00367.gif).
- Concentration.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A SoretEffect object.

**Exceptions**

RangeError.

### 29.93.2 setValues(...)

This method modifies the SoretEffect object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [SoretEffect](pt01ch29pyo93.md#ker-soreteffect-soreteffect-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.93.3 Members

The SoretEffect object has members with the same names and descriptions as the arguments to the [SoretEffect](pt01ch29pyo93.md#ker-soreteffect-soreteffect-pyc) method.

### 29.93.4 Corresponding analysis keywords

| [*KAPPA](../key/key-link.md#usb-kws-mkappa) |
| --- |




