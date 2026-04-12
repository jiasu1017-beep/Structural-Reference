# 60.61 Hyperfoam object







The Hyperfoam object specifies elastic properties for a hyperelastic foam.

**Access**

```
materialApi.materials()[*name*].hyperfoam()
```

### 60.61.1 Hyperfoam(...)

This method creates a Hyperfoam object.

**Path**

```
materialApi.materials()[*name*].Hyperfoam
```

**Prototype**

```
odb_Hyperfoam&
Hyperfoam(bool testData,
          odb_Union poisson,
          int n,
          bool temperatureDependency,
          const odb_String& moduli,
          const odb_SequenceSequenceDouble& table);
```

**Required arguments**

None.

**Optional arguments**

*testData*

A Boolean specifying whether test data are supplied. The default value is false.

*poisson*

The string "NONE" or a Double specifying the effective Poisson's ratio, ![](../graphics/ker_eqn00164.gif), of the material. This argument is valid only when *testData*=true. The default value is "NONE".

*n*

An Int specifying the order of the strain energy potential. Possible values are 1 ![](../graphics/ker_eqn00283.gif) 6. The default value is 1.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*moduli*

An odb_String specifying the time-dependence of the material constants. Possible values are "INSTANTANEOUS" and "LONG_TERM". The default value is "LONG_TERM".

*table*

An odb_SequenceSequenceDouble specifying the items described below. This argument is valid only when *testData*=false. The default value is an empty sequence.

**Table data**

The items in the table data specify the following for values of ![](../graphics/ker_eqn00088.gif):
- ![](../graphics/ker_eqn00268.gif) and ![](../graphics/ker_eqn00269.gif) for ![](../graphics/ker_eqn00270.gif) from 1 to ![](../graphics/ker_eqn00088.gif).
- ![](../graphics/ker_eqn00284.gif).
- Temperature, if the data depend on temperature. Temperature dependence is not allowed for 4 ![](../graphics/ker_eqn00272.gif) 6 in an Abaqus/Explicit analysis.

**Return value**

A Hyperfoam object.

**Exceptions**

RangeError.

### 60.61.2 Members

The Hyperfoam object has members with the same names and descriptions as the arguments to the [Hyperfoam](pt02ch60pyo61.md#ker-hyperfoam-hyperfoam-cpp) method.

In addition, the Hyperfoam object can have the following members:

**Prototype**

```
odb_BiaxialTestData biaxialTestData() const;
odb_VolumetricTestData volumetricTestData() const;
odb_PlanarTestData planarTestData() const;
odb_SimpleShearTestData simpleShearTestData() const;
odb_UniaxialTestData uniaxialTestData() const;
```

*biaxialTestData*

A [BiaxialTestData](pt02ch60pyo04.md) object.

*volumetricTestData*

A [VolumetricTestData](pt02ch60pyo110.md) object.

*planarTestData*

A [PlanarTestData](pt02ch60pyo76.md) object.

*simpleShearTestData*

A [SimpleShearTestData](pt02ch60pyo91.md) object.

*uniaxialTestData*

A [UniaxialTestData](pt02ch60pyo101.md) object.

### 60.61.3 Corresponding analysis keywords

| [*HYPERFOAM](../key/key-link.md#usb-kws-mhyperfoam) |
| --- |




