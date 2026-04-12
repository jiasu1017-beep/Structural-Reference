# 60.98 TensionStiffening object







The TensionStiffening object defines the retained tensile stress normal to a crack in a [Concrete](pt02ch60pyo18.md) model.

**Access**

```
materialApi.materials()[*name*].concrete().tensionStiffening()
```

### 60.98.1 TensionStiffening(...)

This method creates a TensionStiffening object.

**Path**

```
materialApi.materials()[*name*].concrete().TensionStiffening
```

**Prototype**

```
odb_TensionStiffening&
TensionStiffening(const odb_SequenceSequenceDouble& table,
                  const odb_String& type,
                  bool temperatureDependency,
                  int dependencies);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*type*

An odb_String specifying how the postcracking behavior is defined. Possible values are "DISPLACEMENT" and "STRAIN". The default value is "STRAIN".

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

If *type*=STRAIN, the table data specify the following:
- Fraction of remaining stress to stress at cracking.
- Absolute value of the direct strain minus the direct strain at cracking.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=DISPLACEMENT, the table data specify the following:- Displacement, ![](../graphics/ker_eqn00372.gif), at which a linear loss of strength after cracking gives zero stress.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A TensionStiffening object.

**Exceptions**

RangeError.

### 60.98.2 Members

The TensionStiffening object has members with the same names and descriptions as the arguments to the [TensionStiffening](pt02ch60pyo98.md#ker-tensionstiffening-tensionstiffening-cpp) method.

### 60.98.3 Corresponding analysis keywords

| [*TENSION STIFFENING](../key/key-link.md#usb-kws-mtensionstiff) |
| --- |




