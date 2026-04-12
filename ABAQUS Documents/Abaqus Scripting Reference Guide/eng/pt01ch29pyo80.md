# 29.80 PorousElastic object







The PorousElastic object specifies elastic material properties for porous materials.

**Access**

```
import material
mdb.models[*name*].materials[*name*].porousElastic
import odbMaterial
session.odbs[*name*].materials[*name*].porousElastic
```

### 29.80.1 PorousElastic(...)

This method creates a PorousElastic object.

**Path**

```
mdb.models[*name*].materials[*name*].PorousElastic
session.odbs[*name*].materials[*name*].PorousElastic
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*shear*

A SymbolicConstant specifying the shear definition form. Possible values are G and POISSON. The default value is POISSON.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

If *shear*=G, the table data specify the following:
- The logarithmic bulk modulus, ![](../graphics/ker_eqn00342.gif). (Dimensionless.)
- The shear modulus, ![](../graphics/ker_eqn00182.gif).
- The elastic tensile limit, ![](../graphics/ker_eqn00343.gif). (This value cannot be negative.)
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *shear*=POISSON, the table data specify the following:- The logarithmic bulk modulus, ![](../graphics/ker_eqn00342.gif). (Dimensionless.)
- The Poisson's ratio, ![](../graphics/ker_eqn00164.gif).
- The elastic tensile limit, ![](../graphics/ker_eqn00343.gif). (This value cannot be negative.)
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A PorousElastic object.

**Exceptions**

RangeError.

### 29.80.2 setValues(...)

This method modifies the PorousElastic object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [PorousElastic](pt01ch29pyo80.md#ker-porouselastic-porouselastic-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.80.3 Members

The PorousElastic object has members with the same names and descriptions as the arguments to the [PorousElastic](pt01ch29pyo80.md#ker-porouselastic-porouselastic-pyc) method.

### 29.80.4 Corresponding analysis keywords

| [*POROUS ELASTIC](../key/key-link.md#usb-kws-mporouselastic) |
| --- |




