# 60.91 SimpleShearTestData object







The SimpleShearTestData object provides simple shear test data.

**Access**

```
materialApi.materials()[*name*].hyperfoam().simpleShearTestData()
```

### 60.91.1 SimpleShearTestData(...)

This method creates a SimpleShearTestData object.

**Path**

```
materialApi.materials()[*name*].hyperfoam().SimpleShearTestData
```

**Prototype**

```
odb_SimpleShearTestData&
SimpleShearTestData(const odb_SequenceSequenceDouble& table);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

None.

**Table data**

- Nominal shear stress, ![](../graphics/ker_eqn00332.gif).
- Nominal shear strain, ![](../graphics/ker_eqn00040.gif).
- Nominal transverse stress, ![](../graphics/ker_eqn00366.gif) (normal to edge with shear stress). This stress value is optional.

**Return value**

A SimpleShearTestData object.

**Exceptions**

None.

### 60.91.2 Members

The SimpleShearTestData object has members with the same names and descriptions as the arguments to the [SimpleShearTestData](pt02ch60pyo91.md#ker-simplesheartestdata-simplesheartestdata-cpp) method.

### 60.91.3 Corresponding analysis keywords

| [*SIMPLE SHEAR TEST DATA](../key/key-link.md#usb-kws-msimplesheartestdata) |
| --- |




