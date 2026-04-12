# 60.14 CastIronTensionHardening object







The CastIronTensionHardening object specifies hardening for the Cast- Iron plasticity model.

**Access**

```
materialApi.materials()[*name*].castIronPlasticity()\
.castIronTensionHardening()
```

### 60.14.1 CastIronTensionHardening(...)

This method creates a CastIronTensionHardening object.

**Path**

```
materialApi.materials()[*name*].castIronPlasticity()\
.CastIronTensionHardening
```

**Prototype**

```
odb_CastIronTensionHardening&
CastIronTensionHardening(const odb_SequenceSequenceDouble& table,
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

- Yield stress in uniaxial tension, ![](../graphics/ker_eqn00104.gif).
- The absolute value of the corresponding plastic strain.(The first tabular value entered must always be zero.)
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A CastIronTensionHardening object.

**Exceptions**

RangeError.

### 60.14.2 Members

The CastIronTensionHardening object has members with the same names and descriptions as the arguments to the [CastIronTensionHardening](pt02ch60pyo14.md#ker-castirontensionhardening-castirontensionhardening-cpp) method.

### 60.14.3 Corresponding analysis keywords

| [*CAST IRON TENSION HARDENING](../key/key-link.md#usb-kws-mcastirontenhardening) |
| --- |




