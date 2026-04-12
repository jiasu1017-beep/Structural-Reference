# 60.92 Solubility object







The Solubility object specifies solubility.

**Access**

```
materialApi.materials()[*name*].solubility()
```

### 60.92.1 Solubility(...)

This method creates a Solubility object.

**Path**

```
materialApi.materials()[*name*].Solubility
```

**Prototype**

```
odb_Solubility&
Solubility(const odb_SequenceSequenceDouble& table,
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

- Solubility.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A Solubility object.

**Exceptions**

RangeError.

### 60.92.2 Members

The Solubility object has members with the same names and descriptions as the arguments to the [Solubility](pt02ch60pyo92.md#ker-solubility-solubility-cpp) method.

### 60.92.3 Corresponding analysis keywords

| [*SOLUBILITY](../key/key-link.md#usb-kws-msolubility) |
| --- |




