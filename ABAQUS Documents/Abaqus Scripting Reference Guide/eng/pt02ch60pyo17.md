# 60.17 CombinedTestData object







The CombinedTestData object specifies simultaneously the normalized shear and bulk compliances or relaxation moduli as functions of time.

**Access**

```
materialApi.materials()[*name*].viscoelastic().combinedTestData()
```

### 60.17.1 CombinedTestData(...)

This method creates a CombinedTestData object.

**Path**

```
materialApi.materials()[*name*].viscoelastic().CombinedTestData
```

**Prototype**

```
odb_CombinedTestData&
CombinedTestData(const odb_SequenceSequenceDouble& table,
                 odb_Union volinf,
                 odb_Union shrinf);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below. The values of the table data depend on the value of the *time* member of the [Viscoelastic](pt02ch60pyo106.md) object.

**Optional arguments**

*volinf*

The string "NONE" or a Double specifying a normalized volume. The value of *volinf* depends on the value of the *time* member of the [Viscoelastic](pt02ch60pyo106.md) object. The default value is "NONE".

If *time*="RELAXATION_TEST_DATA", *volinf* specifies the value of the long-term normalized volumetric modulus, ![](../graphics/ker_eqn00113.gif).

If *time*="CREEP_TEST_DATA", *volinf* specifies the value of the long-term normalized volumetric compliance, ![](../graphics/ker_eqn00114.gif).

*shrinf*

The string "NONE" or a Double specifying a normalized shear. The value of *shrinf* depends on the value of the *time* member of the [Viscoelastic](pt02ch60pyo106.md) object. The default value is "NONE".

If *time*="RELAXATION_TEST_DATA", *shrinf* specifies the value of the long-term normalized shear modulus, ![](../graphics/ker_eqn00115.gif).

If *time*="CREEP_TEST_DATA", *shrinf* specifies the value of the long-term normalized shear compliance, ![](../graphics/ker_eqn00116.gif).

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

### 60.17.2 Members

The CombinedTestData object has members with the same names and descriptions as the arguments to the [CombinedTestData](pt02ch60pyo17.md#ker-combinedtestdata-combinedtestdata-cpp) method.

### 60.17.3 Corresponding analysis keywords

| [*COMBINED TEST DATA](../key/key-link.md#usb-kws-mcombinedtestdata) |
| --- |




