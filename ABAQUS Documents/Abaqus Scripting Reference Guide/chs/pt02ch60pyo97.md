# 60.97 TensionCutOff object







The TensionCutOff object specifies tension cutoff for different material models for example the Mohr-Coulomb plasticity model.

**Access**

```
materialApi.materials()[*name*].mohrCoulombPlasticity().tensionCutOff()
```

### 60.97.1 TensionCutOff(...)

This method creates a TensionCutOff object.

**Path**

```
materialApi.materials()[*name*].mohrCoulombPlasticity().TensionCutOff
```

**Prototype**

```
odb_TensionCutOff&
TensionCutOff(const odb_SequenceSequenceDouble& table,
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

- Tension cutoff stress.
- The value of the corresponding tensile plastic strain.(The first tabular value entered must always be zero.)
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A TensionCutOff object.

**Exceptions**

RangeError.

### 60.97.2 Members

The TensionCutOff object has members with the same names and descriptions as the arguments to the [TensionCutOff](pt02ch60pyo97.md#ker-tensioncutoff-tensioncutoff-cpp) method.

### 60.97.3 Corresponding analysis keywords

| [*TENSION CUTOFF](../key/key-link.md#usb-kws-mtensioncutoff) |
| --- |




