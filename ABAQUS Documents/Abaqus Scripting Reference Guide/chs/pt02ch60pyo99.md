# 60.99 TriaxialTestData object







The TriaxialTestData object provides triaxial test data.

**Access**

```
materialApi.materials()[*name*].druckerPrager().triaxialTestData()
```

### 60.99.1 TriaxialTestData(...)

This method creates a TriaxialTestData object.

**Path**

```
materialApi.materials()[*name*].druckerPrager().TriaxialTestData
```

**Prototype**

```
odb_TriaxialTestData&
TriaxialTestData(const odb_SequenceSequenceDouble& table,
                 odb_Union a,
                 odb_Union b,
                 odb_Union pt);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*a*

The string "NONE" or a Double specifying the value of the material constant ![](../graphics/ker_eqn00278.gif). "NONE" is used when the value is unknown or it is not held fixed at the input value. The default value is "NONE".

*b*

The string "NONE" or a Double specifying the value of the material constant ![](../graphics/ker_eqn00038.gif). "NONE" is used when the value is unknown or it is not held fixed at the input value. The default value is "NONE".

*pt*

The string "NONE" or a Double specifying the value of the material constant ![](../graphics/ker_eqn00373.gif). "NONE" is used when the value is unknown or it is not held fixed at the input value. The default value is "NONE".

**Table data**

- Sign and magnitude of confining stress, ![](../graphics/ker_eqn00374.gif).
- Sign and magnitude of the stress in loading direction, ![](../graphics/ker_eqn00375.gif).

**Return value**

A TriaxialTestData object.

**Exceptions**

RangeError.

### 60.99.2 Members

The TriaxialTestData object has members with the same names and descriptions as the arguments to the [TriaxialTestData](pt02ch60pyo99.md#ker-triaxialtestdata-triaxialtestdata-cpp) method.

### 60.99.3 Corresponding analysis keywords

| [*TRIAXIAL TEST DATA](../key/key-link.md#usb-kws-mtritestdata) |
| --- |




