# 60.69 MohrCoulombHardening object







The MohrCoulombHardening object specifies hardening for the Mohr-Coulomb plasticity model.

**Access**

```
materialApi.materials()[*name*].mohrCoulombPlasticity()\
.mohrCoulombHardening()
```

### 60.69.1 MohrCoulombHardening(...)

This method creates a MohrCoulombHardening object.

**Path**

```
materialApi.materials()[*name*].mohrCoulombPlasticity()\
.MohrCoulombHardening
```

**Prototype**

```
odb_MohrCoulombHardening&
MohrCoulombHardening(const odb_SequenceSequenceDouble& table,
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

- Cohesion yield stress.
- The absolute value of the corresponding plastic strain.(The first tabular value entered must always be zero.)
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A MohrCoulombHardening object.

**Exceptions**

RangeError.

### 60.69.2 Members

The MohrCoulombHardening object has members with the same names and descriptions as the arguments to the [MohrCoulombHardening](pt02ch60pyo69.md#ker-mohrcoulombhardening-mohrcoulombhardening-cpp) method.

### 60.69.3 Corresponding analysis keywords

| [*MOHR COULOMB HARDENING](../key/key-link.md#usb-kws-mmohrcoulombhardening) |
| --- |




