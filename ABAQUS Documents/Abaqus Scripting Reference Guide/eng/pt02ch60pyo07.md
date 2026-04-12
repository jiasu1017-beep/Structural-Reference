# 60.7 BrittleShear object







The BrittleShear object specifies the postcracking shear behavior of a material used in a brittle cracking model.

**Access**

```
materialApi.materials()[*name*].brittleCracking().brittleShear()
```

### 60.7.1 BrittleShear(...)

This method creates a BrittleShear object.

**Path**

```
materialApi.materials()[*name*].brittleCracking().BrittleShear
```

**Prototype**

```
odb_BrittleShear&
BrittleShear(const odb_SequenceSequenceDouble& table,
             bool temperatureDependency,
             int dependencies,
             const odb_String& type);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

*type*

An odb_String specifying the type of postcracking shear behavior. Possible values are "RETENTION_FACTOR" and "POWER_LAW". The default value is "RETENTION_FACTOR".

**Table data**

If *type*=RETENTION_FACTOR the table data specify the following:
- Shear retention factor.
- Crack opening strain.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=POWER_LAW the table data specify the following:- e.
- p.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A BrittleShear object.

**Exceptions**

RangeError.

### 60.7.2 Members

The BrittleShear object has members with the same names and descriptions as the arguments to the [BrittleShear](pt02ch60pyo07.md#ker-brittleshear-brittleshear-cpp) method.

### 60.7.3 Corresponding analysis keywords

| [*BRITTLE SHEAR](../key/key-link.md#usb-kws-mbrittleshear) |
| --- |




