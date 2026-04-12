# 60.12 CastIronCompressionHardening object







The CastIronCompressionHardening object specifies hardening for the Cast- Iron plasticity model.

**Access**

```
materialApi.materials()[*name*].castIronPlasticity()\
.castIronCompressionHardening()
```

### 60.12.1 CastIronCompressionHardening(...)

This method creates a CastIronCompressionHardening object.

**Path**

```
materialApi.materials()[*name*].castIronPlasticity()\
.CastIronCompressionHardening
```

**Prototype**

```
odb_CastIronCompressionHardening&
CastIronCompressionHardening(const odb_SequenceSequenceDouble& table,
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

- Yield stress in compression, ![](../graphics/ker_eqn00102.gif).
- The absolute value of the corresponding plastic strain.(The first tabular value entered must always be zero.)
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A CastIronCompressionHardening object.

**Exceptions**

RangeError.

### 60.12.2 Members

The CastIronCompressionHardening object has members with the same names and descriptions as the arguments to the [CastIronCompressionHardening](pt02ch60pyo12.md#ker-castironcompressionhardening-castironcompressionhard-cpp) method.

### 60.12.3 Corresponding analysis keywords

| [*CAST IRON COMPRESSION HARDENING](../key/key-link.md#usb-kws-mcastironcomhardening) |
| --- |




