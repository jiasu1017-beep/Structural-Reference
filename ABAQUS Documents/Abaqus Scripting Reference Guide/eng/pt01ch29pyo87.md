# 29.87 Regularization object







The Regularization object defines the tolerance to be used for regularizing material data.

**Access**

```
import material
mdb.models[*name*].materials[*name*].regularization
import odbMaterial
session.odbs[*name*].materials[*name*].regularization
```

### 29.87.1 Regularization(...)

This method creates a Regularization object.

**Path**

```
mdb.models[*name*].materials[*name*].Regularization
session.odbs[*name*].materials[*name*].Regularization
```

**Required arguments**

None.

**Optional arguments**

*rtol*

A Float specifying the tolerance to be used for regularizing material data. The default value is 0.03.

*strainRateRegularization*

A SymbolicConstant specifying the form of regularization of strain-rate-dependent material data. Possible values are LOGARITHMIC and LINEAR. The default value is LOGARITHMIC.

**Return value**

A Regularization object.

**Exceptions**

RangeError.

### 29.87.2 setValues(...)

This method modifies the Regularization object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [Regularization](pt01ch29pyo87.md#ker-regularization-regularization-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.87.3 Members

The Regularization object has members with the same names and descriptions as the arguments to the [Regularization](pt01ch29pyo87.md#ker-regularization-regularization-pyc) method.

### 29.87.4 Corresponding analysis keywords

| [*DASHPOT](../key/key-link.md#usb-kws-mdashpot) |
| --- |




