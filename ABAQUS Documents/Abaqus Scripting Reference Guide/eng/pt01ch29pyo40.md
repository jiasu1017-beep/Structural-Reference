# 29.40 Dielectric object







The Dielectric object specifies dielectric material properties.

**Access**

```
import material
mdb.models[*name*].materials[*name*].dielectric
import odbMaterial
session.odbs[*name*].materials[*name*].dielectric
```

### 29.40.1 Dielectric(...)

This method creates a Dielectric object.

**Path**

```
mdb.models[*name*].materials[*name*].Dielectric
session.odbs[*name*].materials[*name*].Dielectric
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*type*

A SymbolicConstant specifying the dielectric behavior. Possible values are ISOTROPIC, ORTHOTROPIC, and ANISOTROPIC. The default value is ISOTROPIC.

*frequencyDependency*

A Boolean specifying whether the data depend on frequency. The default value is OFF.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

If *type*=ISOTROPIC, the table data specify the following:
- Dielectric constant.
- Frequency, if the data depend on frequency.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=ORTHOTROPIC, the table data specify the following:- ![](../graphics/ker_eqn00166.gif).
- ![](../graphics/ker_eqn00167.gif).
- ![](../graphics/ker_eqn00168.gif).
- Frequency, if the data depend on frequency.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=ANISOTROPIC, the table data specify the following:- ![](../graphics/ker_eqn00166.gif).
- ![](../graphics/ker_eqn00169.gif).
- ![](../graphics/ker_eqn00167.gif).
- ![](../graphics/ker_eqn00170.gif).
- ![](../graphics/ker_eqn00171.gif).
- ![](../graphics/ker_eqn00168.gif).
- Frequency, if the data depend on frequency.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A Dielectric object.

**Exceptions**

None.

### 29.40.2 setValues(...)

This method modifies the Dielectric object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [Dielectric](pt01ch29pyo40.md#ker-dielectric-dielectric-pyc) method.

**Return value**

None

**Exceptions**

None.

### 29.40.3 Members

The Dielectric object has members with the same names and descriptions as the arguments to the [Dielectric](pt01ch29pyo40.md#ker-dielectric-dielectric-pyc) method.

### 29.40.4 Corresponding analysis keywords

| [*DIELECTRIC](../key/key-link.md#usb-kws-mdielectric) |
| --- |




