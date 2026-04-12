# 29.90 ShearTestData object







The ShearTestData object specifies the normalized shear creep compliance or relaxation modulus as a function of time.

**Access**

```
import material
mdb.models[*name*].materials[*name*].viscoelastic.shearTestData
import odbMaterial
session.odbs[*name*].materials[*name*].viscoelastic.shearTestData
```

### 29.90.1 ShearTestData(...)

This method creates a ShearTestData object.

**Path**

```
mdb.models[*name*].materials[*name*].viscoelastic.ShearTestData
session.odbs[*name*].materials[*name*].viscoelastic.ShearTestData
```

**Required argument**

*table*

A sequence of sequences of Floats specifying values that depend on the *time* member of the [Viscoelastic](pt01ch29pyo106.md) object.

If *time*=RELAXATION_TEST_DATA, the table data specify the following:
- Normalized shear relaxation modulus ![](../graphics/ker_eqn00117.gif). ![](../graphics/ker_eqn00118.gif).
- Time ![](../graphics/ker_eqn00093.gif). ![](../graphics/ker_eqn00121.gif).

If *time*=CREEP_TEST_DATA, the table data specify the following:
- Normalized shear compliance ![](../graphics/ker_eqn00122.gif). ![](../graphics/ker_eqn00365.gif).
- Time ![](../graphics/ker_eqn00093.gif). ![](../graphics/ker_eqn00121.gif).

**Optional argument**

*shrinf*

 `None` or a Float specifying a normalized shear. The value of *shrinf* depends on the value of the *time* member of the [Viscoelastic](pt01ch29pyo106.md) object. The default value is `None`.

If *time*=RELAXATION_TEST_DATA, *shrinf* specifies the value of the long-term, normalized shear modulus ![](../graphics/ker_eqn00115.gif).

If *time*=CREEP_TEST_DATA, *shrinf* specifies the value of the long-term, normalized shear compliance ![](../graphics/ker_eqn00116.gif).

**Return value**

A ShearTestData object.

**Exceptions**

None.

### 29.90.2 setValues(...)

This method modifies the ShearTestData object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ShearTestData](pt01ch29pyo90.md#ker-sheartestdata-sheartestdata-pyc) method.

**Return value**

None

**Exceptions**

None.

### 29.90.3 Members

The ShearTestData object has members with the same names and descriptions as the arguments to the [ShearTestData](pt01ch29pyo90.md#ker-sheartestdata-sheartestdata-pyc) method.

### 29.90.4 Corresponding analysis keywords

| [*SHEAR TEST DATA](../key/key-link.md#usb-kws-msheartestdata) |
| --- |




