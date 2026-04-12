# 29.85 RateDependent object







The RateDependent object defines a rate-dependent viscoplastic model.

**Access**

```
import material
mdb.models[*name*].materials[*name*].crushableFoam.rateDependent
mdb.models[*name*].materials[*name*].druckerPrager.rateDependent
mdb.models[*name*].materials[*name*].plastic.rateDependent
import odbMaterial
session.odbs[*name*].materials[*name*].crushableFoam.rateDependent
session.odbs[*name*].materials[*name*].druckerPrager.rateDependent
session.odbs[*name*].materials[*name*].plastic.rateDependent
```

### 29.85.1 RateDependent(...)

This method creates a RateDependent object.

**Path**

```
mdb.models[*name*].materials[*name*].crushableFoam.RateDependent
mdb.models[*name*].materials[*name*].druckerPrager.RateDependent
mdb.models[*name*].materials[*name*].plastic.RateDependent
session.odbs[*name*].materials[*name*].crushableFoam.RateDependent
session.odbs[*name*].materials[*name*].druckerPrager.RateDependent
session.odbs[*name*].materials[*name*].plastic.RateDependent
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*type*

A SymbolicConstant specifying the type of rate-dependent data. Possible values are POWER_LAW, YIELD_RATIO, and JOHNSON_COOK. The default value is POWER_LAW.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

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

### 29.85.2 setValues(...)

This method modifies the RateDependent object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [RateDependent](pt01ch29pyo85.md#ker-ratedependent-ratedependent-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.85.3 Members

The RateDependent object has members with the same names and descriptions as the arguments to the [RateDependent](pt01ch29pyo85.md#ker-ratedependent-ratedependent-pyc) method.

### 29.85.4 Corresponding analysis keywords

| [*RATE DEPENDENT](../key/key-link.md#usb-kws-mratedependent) |
| --- |




