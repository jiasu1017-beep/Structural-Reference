# 60.75 Piezoelectric object







The Piezoelectric object specifies piezoelectric material properties.

**Access**

```
materialApi.materials()[*name*].piezoelectric()
```

### 60.75.1 Piezoelectric(...)

This method creates a Piezoelectric object.

**Path**

```
materialApi.materials()[*name*].Piezoelectric
```

**Prototype**

```
odb_Piezoelectric&
Piezoelectric(const odb_SequenceSequenceDouble& table,
              const odb_String& type,
              bool temperatureDependency,
              int dependencies);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*type*

An odb_String specifying the type of material coefficients for the piezoelectric property. Possible values are "STRAIN" and "STRESS". The default value is "STRESS".

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

If *type*=STRESS, the table data specify the following:
- ![](../graphics/ker_eqn00297.gif).
- ![](../graphics/ker_eqn00298.gif).
- ![](../graphics/ker_eqn00299.gif).
- ![](../graphics/ker_eqn00300.gif).
- ![](../graphics/ker_eqn00301.gif).
- ![](../graphics/ker_eqn00302.gif).
- ![](../graphics/ker_eqn00303.gif).
- ![](../graphics/ker_eqn00304.gif).
- ![](../graphics/ker_eqn00305.gif).
- ![](../graphics/ker_eqn00306.gif).
- ![](../graphics/ker_eqn00307.gif).
- ![](../graphics/ker_eqn00308.gif).
- ![](../graphics/ker_eqn00309.gif).
- ![](../graphics/ker_eqn00310.gif).
- ![](../graphics/ker_eqn00311.gif).
- ![](../graphics/ker_eqn00312.gif).
- ![](../graphics/ker_eqn00313.gif).
- ![](../graphics/ker_eqn00314.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=STRAIN, the table data specify the following:- ![](../graphics/ker_eqn00315.gif).
- ![](../graphics/ker_eqn00316.gif).
- ![](../graphics/ker_eqn00317.gif).
- ![](../graphics/ker_eqn00318.gif).
- ![](../graphics/ker_eqn00319.gif).
- ![](../graphics/ker_eqn00320.gif).
- ![](../graphics/ker_eqn00321.gif).
- ![](../graphics/ker_eqn00322.gif).
- ![](../graphics/ker_eqn00323.gif).
- ![](../graphics/ker_eqn00324.gif).
- ![](../graphics/ker_eqn00325.gif).
- ![](../graphics/ker_eqn00326.gif).
- ![](../graphics/ker_eqn00327.gif).
- ![](../graphics/ker_eqn00328.gif).
- ![](../graphics/ker_eqn00329.gif).
- ![](../graphics/ker_eqn00330.gif).
- ![](../graphics/ker_eqn00331.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A Piezoelectric object.

**Exceptions**

None.

### 60.75.2 Members

The Piezoelectric object has members with the same names and descriptions as the arguments to the [Piezoelectric](pt02ch60pyo75.md#ker-piezoelectric-piezoelectric-cpp) method.

### 60.75.3 Corresponding analysis keywords

| [*PIEZOELECTRIC](../key/key-link.md#usb-kws-mpiezoelect) |
| --- |




