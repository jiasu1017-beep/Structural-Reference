# 60.4 BiaxialTestData object







The BiaxialTestData object provides equibiaxial test data (compression and/or tension).

**Access**

```
materialApi.materials()[*name*].hyperelastic().biaxialTestData()
materialApi.materials()[*name*].hyperfoam().biaxialTestData()
materialApi.materials()[*name*].mullinsEffect().biaxialTests(*i*)
```

### 60.4.1 BiaxialTestData(...)

This method creates a BiaxialTestData object.

**Path**

```
materialApi.materials()[*name*].hyperelastic().BiaxialTestData
materialApi.materials()[*name*].hyperfoam().BiaxialTestData
materialApi.materials()[*name*].mullinsEffect().BiaxialTestData
```

**Prototype**

```
odb_BiaxialTestData&
BiaxialTestData(const odb_SequenceSequenceDouble& table,
                odb_Union smoothing,
                bool lateralNominalStrain,
                bool temperatureDependency,
                int dependencies);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the following:
- Nominal stress, ![](../graphics/ker_eqn00086.gif).
- Nominal strain, ![](../graphics/ker_eqn00087.gif).

**Optional arguments**

*smoothing*

The string "NONE" or an Int specifying the value for smoothing. If *smoothing*="NONE", no smoothing is employed. The default value is "NONE".

*lateralNominalStrain*

A Boolean specifying whether to include lateral nominal strain. The default value is false.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Return value**

A BiaxialTestData object.

**Exceptions**

None.

### 60.4.2 Members

The BiaxialTestData object has members with the same names and descriptions as the arguments to the [BiaxialTestData](pt02ch60pyo04.md#ker-biaxialtestdata-biaxialtestdata-cpp) method.

### 60.4.3 Corresponding analysis keywords

| [*BIAXIAL TEST DATA](../key/key-link.md#usb-kws-mbitestdata) |
| --- |




