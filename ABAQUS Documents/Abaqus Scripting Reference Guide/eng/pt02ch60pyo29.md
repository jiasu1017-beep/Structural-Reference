# 60.29 CycledPlastic object







The CycledPlastic object specifies cycled yield stress data for the ORNL constitutive model.

**Access**

```
materialApi.materials()[*name*].plastic().cycledPlastic()
```

### 60.29.1 CycledPlastic(...)

This method creates a CycledPlastic object.

**Path**

```
materialApi.materials()[*name*].plastic().CycledPlastic
```

**Prototype**

```
odb_CycledPlastic&
CycledPlastic(const odb_SequenceSequenceDouble& table,
              bool temperatureDependency);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional argument**

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

**Table data**

- Yield stress.
- Plastic strain.
- Temperature, if the data depend on temperature.

**Return value**

A CycledPlastic object.

**Exceptions**

None.

### 60.29.2 Members

The CycledPlastic object has members with the same names and descriptions as the arguments to the [CycledPlastic](pt02ch60pyo29.md#ker-cycledplastic-cycledplastic-cpp) method.

### 60.29.3 Corresponding analysis keywords

| [*CYCLED PLASTIC](../key/key-link.md#usb-kws-mcycledplastic) |
| --- |




