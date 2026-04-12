# 60.85 RateDependent object







The RateDependent object defines a rate-dependent viscoplastic model.

**Access**

```
materialApi.materials()[*name*].crushableFoam().rateDependent()
materialApi.materials()[*name*].druckerPrager().rateDependent()
materialApi.materials()[*name*].plastic().rateDependent()
```

### 60.85.1 RateDependent(...)

This method creates a RateDependent object.

**Path**

```
materialApi.materials()[*name*].crushableFoam().RateDependent
materialApi.materials()[*name*].druckerPrager().RateDependent
materialApi.materials()[*name*].plastic().RateDependent
```

**Prototype**

```
odb_RateDependent&
RateDependent(const odb_SequenceSequenceDouble& table,
              const odb_String& type,
              bool temperatureDependency,
              int dependencies);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*type*

An odb_String specifying the type of rate-dependent data. Possible values are "POWER_LAW", "YIELD_RATIO", and "JOHNSON_COOK". The default value is "POWER_LAW".

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

If *type*=POWER_LAW, the table data specify the following:
- ![](../graphics/ker_eqn00172.gif).
- ![](../graphics/ker_eqn00088.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=YIELD_RATIO, the table data specify the following:- Yield stress ratio, ![](../graphics/ker_eqn00357.gif).
- Equivalent plastic strain rate, ![](../graphics/ker_eqn00337.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=JOHNSON_COOK, the table data specify the following:- ![](../graphics/ker_eqn00039.gif).
- ![](../graphics/ker_eqn00358.gif).

**Return value**

A RateDependent object.

**Exceptions**

RangeError.

### 60.85.2 Members

The RateDependent object has members with the same names and descriptions as the arguments to the [RateDependent](pt02ch60pyo85.md#ker-ratedependent-ratedependent-cpp) method.

### 60.85.3 Corresponding analysis keywords

| [*RATE DEPENDENT](../key/key-link.md#usb-kws-mratedependent) |
| --- |




