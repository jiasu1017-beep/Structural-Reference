# 29.61 Hyperfoam object







The Hyperfoam object specifies elastic properties for a hyperelastic foam.

**Access**

```
import material
mdb.models[*name*].materials[*name*].hyperfoam
import odbMaterial
session.odbs[*name*].materials[*name*].hyperfoam
```

### 29.61.1 Hyperfoam(...)

This method creates a Hyperfoam object.

**Path**

```
mdb.models[*name*].materials[*name*].Hyperfoam
session.odbs[*name*].materials[*name*].Hyperfoam
```

**Required arguments**

None.

**Optional arguments**

*testData*

A Boolean specifying whether test data are supplied. The default value is OFF.

*poisson*

 `None` or a Float specifying the effective Poisson's ratio, ![](../graphics/ker_eqn00164.gif), of the material. This argument is valid only when *testData*=ON. The default value is `None`.

*n*

An Int specifying the order of the strain energy potential. Possible values are 1 ![](../graphics/ker_eqn00283.gif) 6. The default value is 1.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*moduli*

A SymbolicConstant specifying the time-dependence of the material constants. Possible values are INSTANTANEOUS and LONG_TERM. The default value is LONG_TERM.

*table*

A sequence of sequences of Floats specifying the items described below. This argument is valid only when *testData*=OFF. The default value is an empty sequence.

**Table data**

The items in the table data specify the following for values of ![](../graphics/ker_eqn00088.gif):
- ![](../graphics/ker_eqn00268.gif) and ![](../graphics/ker_eqn00269.gif) for ![](../graphics/ker_eqn00270.gif) from 1 to ![](../graphics/ker_eqn00088.gif).
- ![](../graphics/ker_eqn00284.gif).
- Temperature, if the data depend on temperature. Temperature dependence is not allowed for 4 ![](../graphics/ker_eqn00272.gif) 6 in an Abaqus/Explicit analysis.

**Return value**

A Hyperfoam object.

**Exceptions**

RangeError.

### 29.61.2 setValues(...)

This method modifies the Hyperfoam object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [Hyperfoam](pt01ch29pyo61.md#ker-hyperfoam-hyperfoam-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.61.3 Members

The Hyperfoam object has members with the same names and descriptions as the arguments to the [Hyperfoam](pt01ch29pyo61.md#ker-hyperfoam-hyperfoam-pyc) method.

In addition, the Hyperfoam object can have the following members:

*biaxialTestData*

A [BiaxialTestData](pt01ch29pyo04.md) object.

*volumetricTestData*

A [VolumetricTestData](pt01ch29pyo110.md) object.

*planarTestData*

A [PlanarTestData](pt01ch29pyo76.md) object.

*simpleShearTestData*

A [SimpleShearTestData](pt01ch29pyo91.md) object.

*uniaxialTestData*

A [UniaxialTestData](pt01ch29pyo101.md) object.

### 29.61.4 Corresponding analysis keywords

| [*HYPERFOAM](../key/key-link.md#usb-kws-mhyperfoam) |
| --- |




