# 60.15 ClayHardening object







The ClayHardening object specifies hardening for the clay plasticity model.

**Access**

```
materialApi.materials()[*name*].clayPlasticity().clayHardening()
```

### 60.15.1 ClayHardening(...)

This method creates a ClayHardening object.

**Path**

```
materialApi.materials()[*name*].clayPlasticity().ClayHardening
```

**Prototype**

```
odb_ClayHardening&
ClayHardening(const odb_SequenceSequenceDouble& table,
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

- The hydrostatic pressure stress at yield, ![](../graphics/ker_eqn00105.gif).
- The absolute value of the corresponding volumetric plastic strain.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A ClayHardening object.

**Exceptions**

RangeError.

### 60.15.2 Members

The ClayHardening object has members with the same names and descriptions as the arguments to the [ClayHardening](pt02ch60pyo15.md#ker-clayhardening-clayhardening-cpp) method.

### 60.15.3 Corresponding analysis keywords

| [*CLAY HARDENING](../key/key-link.md#usb-kws-mclayhardening) |
| --- |




