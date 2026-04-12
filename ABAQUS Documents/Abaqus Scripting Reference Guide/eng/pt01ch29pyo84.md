# 29.84 PressureEffect object







The PressureEffect object defines equivalent pressure stress driven mass diffusion.

**Access**

```
import material
mdb.models[*name*].materials[*name*].diffusivity.pressureEffect
import odbMaterial
session.odbs[*name*].materials[*name*].diffusivity.pressureEffect
```

### 29.84.1 PressureEffect(...)

This method creates a PressureEffect object.

**Path**

```
mdb.models[*name*].materials[*name*].diffusivity.PressureEffect
session.odbs[*name*].materials[*name*].diffusivity.PressureEffect
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

- Pressure stress factor, ![](../graphics/ker_eqn00356.gif).
- Concentration.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A PressureEffect object.

**Exceptions**

RangeError.

### 29.84.2 setValues(...)

This method modifies the PressureEffect object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [PressureEffect](pt01ch29pyo84.md#ker-pressureeffect-pressureeffect-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.84.3 Members

The PressureEffect object has members with the same names and descriptions as the arguments to the [PressureEffect](pt01ch29pyo84.md#ker-pressureeffect-pressureeffect-pyc) method.

### 29.84.4 Corresponding analysis keywords

| [*KAPPA](../key/key-link.md#usb-kws-mkappa) |
| --- |




