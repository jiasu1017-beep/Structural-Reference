# 60.13 CastIronPlasticity object







The CastIronPlasticity object specifies the Cast Iron plasticity model.

**Access**

```
materialApi.materials()[*name*].castIronPlasticity()
```

### 60.13.1 CastIronPlasticity(...)

This method creates a CastIronPlasticity object.

**Path**

```
materialApi.materials()[*name*].CastIronPlasticity
```

**Prototype**

```
odb_CastIronPlasticity&
CastIronPlasticity(const odb_SequenceSequenceDouble& table,
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

The table data specify the following:
- Plastic Poisson's ratio, ![](../graphics/ker_eqn00103.gif) (dimensionless).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A CastIronPlasticity object.

**Exceptions**

RangeError.

### 60.13.2 Members

The CastIronPlasticity object has members with the same names and descriptions as the arguments to the [CastIronPlasticity](pt02ch60pyo13.md#ker-castironplasticity-castironplasticity-cpp) method.

In addition, the CastIronPlasticity object can have the following members:

**Prototype**

```
odb_CastIronTensionHardening castIronTensionHardening() const;
odb_CastIronCompressionHardening castIronCompressionHardening() const;
```

*castIronTensionHardening*

A [CastIronTensionHardening](pt02ch60pyo14.md) object.

*castIronCompressionHardening*

A [CastIronCompressionHardening](pt02ch60pyo12.md) object.

### 60.13.3 Corresponding analysis keywords

| [*CAST IRON PLASTICITY](../key/key-link.md#usb-kws-mcastironplastic) |
| --- |




