# 60.44 DruckerPragerHardening object







The DruckerPragerHardening object specifies hardening for Drucker-Prager plasticity models.

**Access**

```
materialApi.materials()[*name*].druckerPrager().druckerPragerHardening()
```

### 60.44.1 DruckerPragerHardening(...)

This method creates a DruckerPragerHardening object.

**Path**

```
materialApi.materials()[*name*].druckerPrager().DruckerPragerHardening
```

**Prototype**

```
odb_DruckerPragerHardening&
DruckerPragerHardening(const odb_SequenceSequenceDouble& table,
                       const odb_String& type,
                       bool rate,
                       bool temperatureDependency,
                       int dependencies);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*type*

An odb_String specifying the type of data defining the hardening behavior. Possible values are "COMPRESSION", "TENSION", and "SHEAR". The default value is "COMPRESSION".

*rate*

A Boolean specifying whether the data depend on rate. The default value is false.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

- Yield stress.
- Absolute value of the corresponding plastic strain. (The first tabular value entered must always be zero.)
- Equivalent plastic strain rate, ![](../graphics/ker_eqn00181.gif), for which this hardening curve applies.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A DruckerPragerHardening object.

**Exceptions**

RangeError.

### 60.44.2 Members

The DruckerPragerHardening object has members with the same names and descriptions as the arguments to the [DruckerPragerHardening](pt02ch60pyo44.md#ker-druckerpragerhardening-druckerpragerhardening-cpp) method.

### 60.44.3 Corresponding analysis keywords

| [*DRUCKER PRAGER HARDENING](../key/key-link.md#usb-kws-mdruckerhardening) |
| --- |




