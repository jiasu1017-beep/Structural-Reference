# 60.24 Conductivity object







The Conductivity object specifies thermal conductivity.

**Access**

```
materialApi.materials()[*name*].conductivity()
```

### 60.24.1 Conductivity(...)

This method creates a Conductivity object.

**Path**

```
materialApi.materials()[*name*].Conductivity
```

**Prototype**

```
odb_Conductivity&
Conductivity(const odb_SequenceSequenceDouble& table,
             const odb_String& type,
             bool temperatureDependency,
             int dependencies);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*type*

An odb_String specifying the type of conductivity. Possible values are "ISOTROPIC", "ORTHOTROPIC", and "ANISOTROPIC". The default value is "ISOTROPIC".

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

If *type*=ISOTROPIC, the table data specify the following:
- Conductivity, ![](../graphics/ker_eqn00143.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=ORTHOTROPIC, the table data specify the following:- ![](../graphics/ker_eqn00144.gif).
- ![](../graphics/ker_eqn00145.gif).
- ![](../graphics/ker_eqn00146.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=ANISOTROPIC, the table data specify the following:- ![](../graphics/ker_eqn00144.gif).
- ![](../graphics/ker_eqn00147.gif).
- ![](../graphics/ker_eqn00145.gif).
- ![](../graphics/ker_eqn00148.gif).
- ![](../graphics/ker_eqn00149.gif).
- ![](../graphics/ker_eqn00146.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A Conductivity object.

**Exceptions**

RangeError.

### 60.24.2 Members

The Conductivity object has members with the same names and descriptions as the arguments to the [Conductivity](pt02ch60pyo24.md#ker-conductivity-conductivity-cpp) method.

### 60.24.3 Corresponding analysis keywords

| [*CONDUCTIVITY](../key/key-link.md#usb-kws-mconductivity) |
| --- |




