# 60.83 Potential object







The Potential object defines an anisotropic yield/creep model.

**Access**

```
materialApi.materials()[*name*].creep().potential()
materialApi.materials()[*name*].plastic().potential()
materialApi.materials()[*name*].viscous().potential()
```

### 60.83.1 Potential(...)

This method creates a Potential object.

**Path**

```
materialApi.materials()[*name*].creep().Potential
materialApi.materials()[*name*].plastic().Potential
materialApi.materials()[*name*].viscous().Potential
```

**Prototype**

```
odb_Potential&
Potential(const odb_SequenceSequenceDouble& table,
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

- ![](../graphics/ker_eqn00350.gif).
- ![](../graphics/ker_eqn00351.gif).
- ![](../graphics/ker_eqn00352.gif).
- ![](../graphics/ker_eqn00353.gif).
- ![](../graphics/ker_eqn00354.gif).
- ![](../graphics/ker_eqn00355.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A Potential object.

**Exceptions**

RangeError.

### 60.83.2 Members

The Potential object has members with the same names and descriptions as the arguments to the [Potential](pt02ch60pyo83.md#ker-potential-potential-cpp) method.

### 60.83.3 Corresponding analysis keywords

| [*POTENTIAL](../key/key-link.md#usb-kws-mpotential) |
| --- |




