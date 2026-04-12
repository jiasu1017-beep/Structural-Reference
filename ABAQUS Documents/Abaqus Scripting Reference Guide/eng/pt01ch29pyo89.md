# 29.89 ShearRetention object







The ShearRetention object defines the reduction of the shear modulus associated with crack surfaces in a [Concrete](pt01ch29pyo18.md) model as a function of the tensile strain across the crack.

**Access**

```
import material
mdb.models[*name*].materials[*name*].concrete.shearRetention
import odbMaterial
session.odbs[*name*].materials[*name*].concrete.shearRetention
```

### 29.89.1 ShearRetention(...)

This method creates a ShearRetention object.

**Path**

```
mdb.models[*name*].materials[*name*].concrete.ShearRetention
session.odbs[*name*].materials[*name*].concrete.ShearRetention
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

- ![](../graphics/ker_eqn00363.gif) for dry concrete. The default value is 1.0.
- ![](../graphics/ker_eqn00364.gif) for dry concrete. The default value is a very large number (full shear retention).
- ![](../graphics/ker_eqn00363.gif) for wet concrete. The default value is 1.0.
- ![](../graphics/ker_eqn00364.gif) for wet concrete. The default value is a very large number (full shear retention).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A ShearRetention object.

**Exceptions**

RangeError.

### 29.89.2 setValues(...)

This method modifies the ShearRetention object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ShearRetention](pt01ch29pyo89.md#ker-shearretention-shearretention-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.89.3 Members

The ShearRetention object has members with the same names and descriptions as the arguments to the [ShearRetention](pt01ch29pyo89.md#ker-shearretention-shearretention-pyc) method.

### 29.89.4 Corresponding analysis keywords

| [*SHEAR RETENTION](../key/key-link.md#usb-kws-mshearretention) |
| --- |




