# 60.28 CrushableFoamHardening object







The CrushableFoamHardening object specifies hardening for the crushable foam plasticity model.

**Access**

```
materialApi.materials()[*name*].crushableFoam().crushableFoamHardening()
```

### 60.28.1 CrushableFoamHardening(...)

This method creates a CrushableFoamHardening object.

**Path**

```
materialApi.materials()[*name*].crushableFoam().CrushableFoamHardening
```

**Prototype**

```
odb_CrushableFoamHardening&
CrushableFoamHardening(const odb_SequenceSequenceDouble& table,
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

- The yield stress in uniaxial compression, ![](../graphics/ker_eqn00102.gif).
- The absolute value of the corresponding plastic strain.(The first tabular value entered must always be zero.)
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A CrushableFoamHardening object.

**Exceptions**

RangeError.

### 60.28.2 Members

The CrushableFoamHardening object has members with the same names and descriptions as the arguments to the [CrushableFoamHardening](pt02ch60pyo28.md#ker-crushablefoamhardening-crushablefoamhardening-cpp) method.

### 60.28.3 Corresponding analysis keywords

| [*CRUSHABLE FOAM HARDENING](../key/key-link.md#usb-kws-mcrushfoamhardening) |
| --- |




