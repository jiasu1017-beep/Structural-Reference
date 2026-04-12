# 29.24 Conductivity object







The Conductivity object specifies thermal conductivity.

**Access**

```
import material
mdb.models[*name*].materials[*name*].conductivity
import odbMaterial
session.odbs[*name*].materials[*name*].conductivity
```

### 29.24.1 Conductivity(...)

This method creates a Conductivity object.

**Path**

```
mdb.models[*name*].materials[*name*].Conductivity
session.odbs[*name*].materials[*name*].Conductivity
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*type*

A SymbolicConstant specifying the type of conductivity. Possible values are ISOTROPIC, ORTHOTROPIC, and ANISOTROPIC. The default value is ISOTROPIC.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

If *type*=ISOTROPIC, the table data specify the following:
- Conductivity, ![](../graphics/ker_eqn00143.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=ORTHOTROPIC, the table data specify the following:- ![](../graphics/ker_eqn00144.gif).
- ![](../graphics/ker_eqn00145.gif).
- ![](../graphics/ker_eqn00146.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=ANISOTROPIC, the table data specify the following:- ![](../graphics/ker_eqn00144.gif).
- ![](../graphics/ker_eqn00147.gif).
- ![](../graphics/ker_eqn00145.gif).
- ![](../graphics/ker_eqn00148.gif).
- ![](../graphics/ker_eqn00149.gif).
- ![](../graphics/ker_eqn00146.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A Conductivity object.

**Exceptions**

RangeError.

### 29.24.2 setValues(...)

This method modifies the Conductivity object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [Conductivity](pt01ch29pyo24.md#ker-conductivity-conductivity-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.24.3 Members

The Conductivity object has members with the same names and descriptions as the arguments to the [Conductivity](pt01ch29pyo24.md#ker-conductivity-conductivity-pyc) method.

### 29.24.4 Corresponding analysis keywords

| [*CONDUCTIVITY](../key/key-link.md#usb-kws-mconductivity) |
| --- |




