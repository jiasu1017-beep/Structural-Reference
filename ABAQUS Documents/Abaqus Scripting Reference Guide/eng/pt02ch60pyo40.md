# 60.40 Dielectric object







The Dielectric object specifies dielectric material properties.

**Access**

```
materialApi.materials()[*name*].dielectric()
```

### 60.40.1 Dielectric(...)

This method creates a Dielectric object.

**Path**

```
materialApi.materials()[*name*].Dielectric
```

**Prototype**

```
odb_Dielectric&
Dielectric(const odb_SequenceSequenceDouble& table,
           const odb_String& type,
           bool frequencyDependency,
           bool temperatureDependency,
           int dependencies);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*type*

An odb_String specifying the dielectric behavior. Possible values are "ISOTROPIC", "ORTHOTROPIC", and "ANISOTROPIC". The default value is "ISOTROPIC".

*frequencyDependency*

A Boolean specifying whether the data depend on frequency. The default value is false.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

If *type*=ISOTROPIC, the table data specify the following:
- Dielectric constant.
- Frequency, if the data depend on frequency.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=ORTHOTROPIC, the table data specify the following:- ![](../graphics/ker_eqn00166.gif).
- ![](../graphics/ker_eqn00167.gif).
- ![](../graphics/ker_eqn00168.gif).
- Frequency, if the data depend on frequency.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=ANISOTROPIC, the table data specify the following:- ![](../graphics/ker_eqn00166.gif).
- ![](../graphics/ker_eqn00169.gif).
- ![](../graphics/ker_eqn00167.gif).
- ![](../graphics/ker_eqn00170.gif).
- ![](../graphics/ker_eqn00171.gif).
- ![](../graphics/ker_eqn00168.gif).
- Frequency, if the data depend on frequency.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A Dielectric object.

**Exceptions**

None.

### 60.40.2 Members

The Dielectric object has members with the same names and descriptions as the arguments to the [Dielectric](pt02ch60pyo40.md#ker-dielectric-dielectric-cpp) method.

### 60.40.3 Corresponding analysis keywords

| [*DIELECTRIC](../key/key-link.md#usb-kws-mdielectric) |
| --- |




