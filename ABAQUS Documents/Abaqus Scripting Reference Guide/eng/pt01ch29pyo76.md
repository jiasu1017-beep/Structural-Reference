# 29.76 PlanarTestData object







The PlanarTestData object specifies planar test (or pure shear) data (compression and/or tension).

**Access**

```
import material
mdb.models[*name*].materials[*name*].hyperelastic.planarTestData
mdb.models[*name*].materials[*name*].hyperfoam.planarTestData
mdb.models[*name*].materials[*name*].mullinsEffect.planarTests[*i*]
import odbMaterial
session.odbs[*name*].materials[*name*].hyperelastic.planarTestData
session.odbs[*name*].materials[*name*].hyperfoam.planarTestData
session.odbs[*name*].materials[*name*].mullinsEffect.planarTests[*i*]
```

### 29.76.1 PlanarTestData(...)

This method creates a PlanarTestData object.

**Path**

```
mdb.models[*name*].materials[*name*].hyperelastic.PlanarTestData
mdb.models[*name*].materials[*name*].hyperfoam.PlanarTestData
mdb.models[*name*].materials[*name*].mullinsEffect.PlanarTestData
session.odbs[*name*].materials[*name*].hyperelastic.PlanarTestData
session.odbs[*name*].materials[*name*].hyperfoam.PlanarTestData
session.odbs[*name*].materials[*name*].mullinsEffect.PlanarTestData
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*smoothing*

 `None` or an Int specifying the value for smoothing. If *smoothing*=`None`, no smoothing is employed. The default value is `None`.

*lateralNominalStrain*

A Boolean specifying whether to include lateral nominal strain. The default value is OFF.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

For a hyperelastic material model, the table data specify the following:
- Nominal stress, ![](../graphics/ker_eqn00332.gif).
- Nominal strain in the direction of loading, ![](../graphics/ker_eqn00333.gif).

For a hyperfoam material model, the table data specify the following:- Nominal stress, ![](../graphics/ker_eqn00334.gif).
- Nominal strain in the direction of loading, ![](../graphics/ker_eqn00335.gif).
- Nominal transverse strain, ![](../graphics/ker_eqn00336.gif). The default value is 0.

**Return value**

A PlanarTestData object.

**Exceptions**

None.

### 29.76.2 setValues(...)

This method modifies the PlanarTestData object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [PlanarTestData](pt01ch29pyo76.md#ker-planartestdata-planartestdata-pyc) method.

**Return value**

None

**Exceptions**

None.

### 29.76.3 Members

The PlanarTestData object has members with the same names and descriptions as the arguments to the [PlanarTestData](pt01ch29pyo76.md#ker-planartestdata-planartestdata-pyc) method.

### 29.76.4 Corresponding analysis keywords

| [*PLANAR TEST DATA](../key/key-link.md#usb-kws-mplanartestdata) |
| --- |




