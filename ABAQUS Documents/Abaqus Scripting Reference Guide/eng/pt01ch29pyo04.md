# 29.4 BiaxialTestData object







The BiaxialTestData object provides equibiaxial test data (compression and/or tension).

**Access**

```
import material
mdb.models[*name*].materials[*name*].hyperelastic.biaxialTestData
mdb.models[*name*].materials[*name*].hyperfoam.biaxialTestData
mdb.models[*name*].materials[*name*].mullinsEffect.biaxialTests[*i*]
import odbMaterial
session.odbs[*name*].materials[*name*].hyperelastic.biaxialTestData
session.odbs[*name*].materials[*name*].hyperfoam.biaxialTestData
session.odbs[*name*].materials[*name*].mullinsEffect.biaxialTests[*i*]
```

### 29.4.1 BiaxialTestData(...)

This method creates a BiaxialTestData object.

**Path**

```
mdb.models[*name*].materials[*name*].hyperelastic.BiaxialTestData
mdb.models[*name*].materials[*name*].hyperfoam.BiaxialTestData
mdb.models[*name*].materials[*name*].mullinsEffect.BiaxialTestData
session.odbs[*name*].materials[*name*].hyperelastic.BiaxialTestData
session.odbs[*name*].materials[*name*].hyperfoam.BiaxialTestData
session.odbs[*name*].materials[*name*].mullinsEffect.BiaxialTestData
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the following:
- Nominal stress, ![](../graphics/ker_eqn00086.gif).
- Nominal strain, ![](../graphics/ker_eqn00087.gif).

**Optional arguments**

*smoothing*

 `None` or an Int specifying the value for smoothing. If *smoothing*=`None`, no smoothing is employed. The default value is `None`.

*lateralNominalStrain*

A Boolean specifying whether to include lateral nominal strain. The default value is OFF.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Return value**

A BiaxialTestData object.

**Exceptions**

None.

### 29.4.2 setValues(...)

This method modifies the BiaxialTestData object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [BiaxialTestData](pt01ch29pyo04.md#ker-biaxialtestdata-biaxialtestdata-pyc) method.

**Return value**

None

**Exceptions**

None.

### 29.4.3 Members

The BiaxialTestData object has members with the same names and descriptions as the arguments to the [BiaxialTestData](pt01ch29pyo04.md#ker-biaxialtestdata-biaxialtestdata-pyc) method.

### 29.4.4 Corresponding analysis keywords

| [*BIAXIAL TEST DATA](../key/key-link.md#usb-kws-mbitestdata) |
| --- |




