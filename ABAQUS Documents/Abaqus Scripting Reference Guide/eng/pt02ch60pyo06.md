# 60.6 BrittleFailure object







The BrittleFailure object specifies the brittle failure of the material.

**Access**

```
materialApi.materials()[*name*].brittleCracking().brittleFailure()
```

### 60.6.1 BrittleFailure(...)

This method creates a BrittleFailure object.

**Path**

```
materialApi.materials()[*name*].brittleCracking().BrittleFailure
```

**Prototype**

```
odb_BrittleFailure&
BrittleFailure(const odb_SequenceSequenceDouble& table,
               bool temperatureDependency,
               int dependencies,
               const odb_String& failureCriteria);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

*failureCriteria*

An odb_String specifying the failure criteria. Possible values are "UNIDIRECTIONAL", "BIDIRECTIONAL", and "TRIDIRECTIONAL". The default value is "UNIDIRECTIONAL".

**Table data**

If parent [BrittleCracking](pt02ch60pyo05.md) member *type*=STRAIN the table data specify the following:
- Direct cracking failure strain.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If parent [BrittleCracking](pt02ch60pyo05.md) member *type*=DISPLACEMENT or *type*=GFI the table data specify the following:- Direct cracking failure displacement.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A BrittleFailure object.

**Exceptions**

RangeError.

### 60.6.2 Members

The BrittleFailure object has members with the same names and descriptions as the arguments to the [BrittleFailure](pt02ch60pyo06.md#ker-brittlefailure-brittlefailure-cpp) method.

### 60.6.3 Corresponding analysis keywords

| [*BRITTLE FAILURE](../key/key-link.md#usb-kws-mbrittlefailure) |
| --- |




