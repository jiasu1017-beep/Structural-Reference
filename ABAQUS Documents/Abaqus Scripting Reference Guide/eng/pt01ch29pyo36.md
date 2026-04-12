# 29.36 DeformationPlasticity object







The DeformationPlasticity object specifies the deformation plasticity model.

**Access**

```
import material
mdb.models[*name*].materials[*name*].deformationPlasticity
import odbMaterial
session.odbs[*name*].materials[*name*].deformationPlasticity
```

### 29.36.1 DeformationPlasticity(...)

This method creates a DeformationPlasticity object.

**Path**

```
mdb.models[*name*].materials[*name*].DeformationPlasticity
session.odbs[*name*].materials[*name*].DeformationPlasticity
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional argument**

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

**Table data**

- Young's modulus, ![](../graphics/ker_eqn00163.gif).
- Poisson's ratio, ![](../graphics/ker_eqn00164.gif).
- Yield stress, ![](../graphics/ker_eqn00165.gif).
- Exponent, ![](../graphics/ker_eqn00088.gif).
- Yield offset, ![](../graphics/ker_eqn00090.gif).
- Temperature, if the data depend on temperature.

**Return value**

A DeformationPlasticity object.

**Exceptions**

RangeError.

### 29.36.2 setValues(...)

This method modifies the DeformationPlasticity object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [DeformationPlasticity](pt01ch29pyo36.md#ker-deformationplasticity-deformationplasticity-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.36.3 Members

The DeformationPlasticity object has members with the same names and descriptions as the arguments to the [DeformationPlasticity](pt01ch29pyo36.md#ker-deformationplasticity-deformationplasticity-pyc) method.

### 29.36.4 Corresponding analysis keywords

| [*DEFORMATION PLASTICITY](../key/key-link.md#usb-kws-mdeformplas) |
| --- |




