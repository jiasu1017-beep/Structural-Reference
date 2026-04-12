# 29.17 CombinedTestData object







The CombinedTestData object specifies simultaneously the normalized shear and bulk compliances or relaxation moduli as functions of time.

**Access**

```
import material
mdb.models[*name*].materials[*name*].viscoelastic.combinedTestData
import odbMaterial
session.odbs[*name*].materials[*name*].viscoelastic.combinedTestData
```

### 29.17.1 CombinedTestData(...)

This method creates a CombinedTestData object.

**Path**

```
mdb.models[*name*].materials[*name*].viscoelastic.CombinedTestData
session.odbs[*name*].materials[*name*].viscoelastic.CombinedTestData
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below. The values of the table data depend on the value of the *time* member of the [Viscoelastic](pt01ch29pyo106.md) object.

**Optional arguments**

*volinf*

 `None` or a Float specifying a normalized volume. The value of *volinf* depends on the value of the *time* member of the [Viscoelastic](pt01ch29pyo106.md) object. The default value is `None`.

If *time*=RELAXATION_TEST_DATA, *volinf* specifies the value of the long-term normalized volumetric modulus, ![](../graphics/ker_eqn00113.gif).

If *time*=CREEP_TEST_DATA, *volinf* specifies the value of the long-term normalized volumetric compliance, ![](../graphics/ker_eqn00114.gif).

*shrinf*

 `None` or a Float specifying a normalized shear. The value of *shrinf* depends on the value of the *time* member of the [Viscoelastic](pt01ch29pyo106.md) object. The default value is `None`.

If *time*=RELAXATION_TEST_DATA, *shrinf* specifies the value of the long-term normalized shear modulus, ![](../graphics/ker_eqn00115.gif).

If *time*=CREEP_TEST_DATA, *shrinf* specifies the value of the long-term normalized shear compliance, ![](../graphics/ker_eqn00116.gif).

**Table data**

If *time*=RELAXATION_TEST_DATA, the table data specify the following: 
- Normalized shear modulus, ![](../graphics/ker_eqn00117.gif) ![](../graphics/ker_eqn00118.gif).
- Normalized volumetric (bulk) modulus, ![](../graphics/ker_eqn00119.gif) ![](../graphics/ker_eqn00120.gif).
- Time ![](../graphics/ker_eqn00093.gif) ![](../graphics/ker_eqn00121.gif).

If *time*=CREEP_TEST_DATA, the table data specify the following:- Normalized shear compliance, ![](../graphics/ker_eqn00122.gif) ![](../graphics/ker_eqn00123.gif).
- Normalized volumetric (bulk) compliance, ![](../graphics/ker_eqn00124.gif) ![](../graphics/ker_eqn00125.gif).
- Time ![](../graphics/ker_eqn00093.gif) ![](../graphics/ker_eqn00126.gif).

**Return value**

A CombinedTestData object.

**Exceptions**

None.

### 29.17.2 setValues(...)

This method modifies the CombinedTestData object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [CombinedTestData](pt01ch29pyo17.md#ker-combinedtestdata-combinedtestdata-pyc) method.

**Return value**

None

**Exceptions**

None.

### 29.17.3 Members

The CombinedTestData object has members with the same names and descriptions as the arguments to the [CombinedTestData](pt01ch29pyo17.md#ker-combinedtestdata-combinedtestdata-pyc) method.

### 29.17.4 Corresponding analysis keywords

| [*COMBINED TEST DATA](../key/key-link.md#usb-kws-mcombinedtestdata) |
| --- |




