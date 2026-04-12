# 29.99 TriaxialTestData object







The TriaxialTestData object provides triaxial test data.

**Access**

```
import material
mdb.models[*name*].materials[*name*].druckerPrager.triaxialTestData
import odbMaterial
session.odbs[*name*].materials[*name*].druckerPrager.triaxialTestData
```

### 29.99.1 TriaxialTestData(...)

This method creates a TriaxialTestData object.

**Path**

```
mdb.models[*name*].materials[*name*].druckerPrager.TriaxialTestData
session.odbs[*name*].materials[*name*].druckerPrager.TriaxialTestData
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*a*

 `None` or a Float specifying the value of the material constant ![](../graphics/ker_eqn00278.gif). `None` is used when the value is unknown or it is not held fixed at the input value. The default value is `None`.

*b*

 `None` or a Float specifying the value of the material constant ![](../graphics/ker_eqn00038.gif). `None` is used when the value is unknown or it is not held fixed at the input value. The default value is `None`.

*pt*

 `None` or a Float specifying the value of the material constant ![](../graphics/ker_eqn00373.gif). `None` is used when the value is unknown or it is not held fixed at the input value. The default value is `None`.

**Table data**

- Sign and magnitude of confining stress, ![](../graphics/ker_eqn00374.gif).
- Sign and magnitude of the stress in loading direction, ![](../graphics/ker_eqn00375.gif).

**Return value**

A TriaxialTestData object.

**Exceptions**

RangeError.

### 29.99.2 setValues(...)

This method modifies the TriaxialTestData object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [TriaxialTestData](pt01ch29pyo99.md#ker-triaxialtestdata-triaxialtestdata-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.99.3 Members

The TriaxialTestData object has members with the same names and descriptions as the arguments to the [TriaxialTestData](pt01ch29pyo99.md#ker-triaxialtestdata-triaxialtestdata-pyc) method.

### 29.99.4 Corresponding analysis keywords

| [*TRIAXIAL TEST DATA](../key/key-link.md#usb-kws-mtritestdata) |
| --- |




