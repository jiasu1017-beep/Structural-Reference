# 60.86 Ratios object







The Ratios object specifies ratios that define anisotropic swelling.

**Access**

```
materialApi.materials()[*name*].moistureSwelling().ratios()
materialApi.materials()[*name*].swelling().ratios()
```

### 60.86.1 Ratios(...)

This method creates a Ratios object.

**Path**

```
materialApi.materials()[*name*].moistureSwelling().Ratios
materialApi.materials()[*name*].swelling().Ratios
```

**Prototype**

```
odb_Ratios&
Ratios(const odb_SequenceSequenceDouble& table,
       bool temperatureDependency,
       int dependencies);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

- ![](../graphics/ker_eqn00359.gif).
- ![](../graphics/ker_eqn00360.gif).
- ![](../graphics/ker_eqn00361.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A Ratios object.

**Exceptions**

RangeError.

### 60.86.2 Members

The Ratios object has members with the same names and descriptions as the arguments to the [Ratios](pt02ch60pyo86.md#ker-ratios-ratios-cpp) method.

### 60.86.3 Corresponding analysis keywords

| [*RATIOS](../key/key-link.md#usb-kws-mswellratios) |
| --- |




