# 29.26 Creep object







The Creep object defines a creep law.

**Access**

```
import material
mdb.models[*name*].materials[*name*].creep
import odbMaterial
session.odbs[*name*].materials[*name*].creep
```

### 29.26.1 Creep(...)

This method creates a Creep object.

**Path**

```
mdb.models[*name*].materials[*name*].Creep
session.odbs[*name*].materials[*name*].Creep
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*law*

A SymbolicConstant specifying the strain-hardening law. Possible values are STRAIN, TIME, HYPERBOLIC_SINE, and USER. The default value is STRAIN.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

If *law*=STRAIN or *law*=TIME, the table data specify the following:
- ![](../graphics/ker_eqn00010.gif).
- ![](../graphics/ker_eqn00088.gif).
- ![](../graphics/ker_eqn00089.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *law*=HYPERBOLIC_SINE, the table data specify the following:- ![](../graphics/ker_eqn00010.gif).
- ![](../graphics/ker_eqn00150.gif).
- ![](../graphics/ker_eqn00088.gif).
- ![](../graphics/ker_eqn00151.gif), if the data depend on temperature.
- ![](../graphics/ker_eqn00096.gif).
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A Creep object.

**Exceptions**

RangeError.

### 29.26.2 setValues(...)

This method modifies the Creep object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [Creep](pt01ch29pyo26.md#ker-creep-creep-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.26.3 Members

The Creep object has members with the same names and descriptions as the arguments to the [Creep](pt01ch29pyo26.md#ker-creep-creep-pyc) method.

In addition, the Creep object can have the following members:

*ornl*

An [Ornl](pt01ch29pyo73.md) object.

*potential*

A [Potential](pt01ch29pyo83.md) object.

### 29.26.4 Corresponding analysis keywords

| [*CREEP](../key/key-link.md#usb-kws-mcreep) |
| --- |




