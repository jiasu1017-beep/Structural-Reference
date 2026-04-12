# 60.2 AcousticMedium object







The AcousticMedium object specifies the acoustic properties of a material.

**Access**

```
materialApi.materials()[*name*].acousticMedium()
```

### 60.2.1 AcousticMedium(...)

This method creates an AcousticMedium object.

**Path**

```
materialApi.materials()[*name*].AcousticMedium
```

**Prototype**

```
odb_AcousticMedium&
AcousticMedium(bool acousticVolumetricDrag,
           bool temperatureDependencyB,
           bool temperatureDependencyV,
           int dependenciesB,
           int dependenciesV,
           const odb_SequenceSequenceDouble& bulkTable,
           const odb_SequenceSequenceDouble& volumetricTable);
```

**Required arguments**

None.

**Optional arguments**

*acousticVolumetricDrag*

A Boolean specifying whether the volumetricTable data is specified. The default value is false.

*temperatureDependencyB*

A Boolean specifying whether the data in *bulkTable* depend on temperature. The default value is false.

*temperatureDependencyV*

A Boolean specifying whether the data in *volumetricTable* depend on temperature. The default value is false.

*dependenciesB*

An Int specifying the number of field variable dependencies for the data in *bulkTable*. The default value is 0.

*dependenciesV*

An Int specifying the number of field variable dependencies for the data in *volumetricTable*. The default value is 0.

*bulkTable*

An odb_SequenceSequenceDouble specifying the following:
- Bulk modulus.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

The default value is an empty sequence.

*volumetricTable*

An odb_SequenceSequenceDouble specifying the following:
- Volumetric drag.
- Frequency.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

The default value is an empty sequence.

**Return value**

An AcousticMedium object.

**Exceptions**

RangeError.

### 60.2.2 Members

The AcousticMedium object has members with the same names and descriptions as the arguments to the [AcousticMedium](pt02ch60pyo02.md#ker-acousticmedium-acousticmedium-cpp) method.

### 60.2.3 Corresponding analysis keywords

| [*ACOUSTIC MEDIUM](../key/key-link.md#usb-kws-macousticmed) |
| --- |




