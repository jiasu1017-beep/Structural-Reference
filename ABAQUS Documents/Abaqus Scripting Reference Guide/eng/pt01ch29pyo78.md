# 29.78 PoreFluidExpansion object







The PoreFluidExpansion object specifies the thermal expansion coefficient for a hydraulic fluid.

**Access**

```
import material
mdb.models[*name*].materials[*name*].poreFluidExpansion
import odbMaterial
session.odbs[*name*].materials[*name*].poreFluidExpansion
```

### 29.78.1 PoreFluidExpansion(...)

This method creates a PoreFluidExpansion object.

**Path**

```
mdb.models[*name*].materials[*name*].PoreFluidExpansion
session.odbs[*name*].materials[*name*].PoreFluidExpansion
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*zero*

A Float specifying the value of ![](../graphics/ker_eqn00061.gif). The default value is 0.0.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

- Mean coefficient of thermal expansion, ![](../graphics/ker_eqn00239.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A PoreFluidExpansion object.

**Exceptions**

RangeError.

### 29.78.2 setValues(...)

This method modifies the PoreFluidExpansion object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [PoreFluidExpansion](pt01ch29pyo78.md#ker-porefluidexpansion-porefluidexpansion-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.78.3 Members

The PoreFluidExpansion object has members with the same names and descriptions as the arguments to the [PoreFluidExpansion](pt01ch29pyo78.md#ker-porefluidexpansion-porefluidexpansion-pyc) method.

### 29.78.4 Corresponding analysis keywords

| [*EXPANSION](../key/key-link.md#usb-kws-mexpansion) |
| --- |




