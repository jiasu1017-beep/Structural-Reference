# 60.3 AnnealTemperature object







The AnnealTemperature object specifies the material annealing temperature.

**Access**

```
materialApi.materials()[*name*].plastic().annealTemperature()
```

### 60.3.1 AnnealTemperature(...)

This method creates an AnnealTemperature object.

**Path**

```
materialApi.materials()[*name*].plastic().AnnealTemperature
```

**Prototype**

```
odb_AnnealTemperature&
AnnealTemperature(const odb_SequenceSequenceDouble& table,
                  int dependencies);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional argument**

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

- The annealing temperature, ![](../graphics/ker_eqn00053.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

An AnnealTemperature object.

**Exceptions**

RangeError.

### 60.3.2 Members

The AnnealTemperature object has members with the same names and descriptions as the arguments to the [AnnealTemperature](pt02ch60pyo03.md#ker-annealtemperature-annealtemperature-cpp) method.

### 60.3.3 Corresponding analysis keywords

| [*ANNEAL TEMPERATURE](../key/key-link.md#usb-kws-mannealtemp) |
| --- |




