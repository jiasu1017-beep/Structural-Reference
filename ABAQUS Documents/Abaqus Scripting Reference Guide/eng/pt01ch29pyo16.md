# 29.16 ClayPlasticity object







The ClayPlasticity object specifies the extended Cam-clay plasticity model.

**Access**

```
import material
mdb.models[*name*].materials[*name*].clayPlasticity
import odbMaterial
session.odbs[*name*].materials[*name*].clayPlasticity
```

### 29.16.1 ClayPlasticity(...)

This method creates a ClayPlasticity object.

**Path**

```
mdb.models[*name*].materials[*name*].ClayPlasticity
session.odbs[*name*].materials[*name*].ClayPlasticity
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*intercept*

 `None` or a Float specifying ![](../graphics/ker_eqn00106.gif), the intercept of the virgin consolidation line with the void ratio axis in a plot of void ratio versus the logarithm of pressure stress. The default value is `None`.

This argument is valid only if *hardening*=EXPONENTIAL.

*hardening*

A SymbolicConstant specifying the type of hardening/softening definition. Possible values are EXPONENTIAL and TABULAR. The default value is EXPONENTIAL.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

If *hardening*=EXPONENTIAL, the table data specify the following:
- Logarithmic plastic bulk modulus, ![](../graphics/ker_eqn00107.gif) (dimensionless).
- Stress ratio at critical state, ![](../graphics/ker_eqn00108.gif).
- The initial yield surface size, ![](../graphics/ker_eqn00109.gif).
- ![](../graphics/ker_eqn00095.gif), the parameter defining the size of the yield surface on the "wet" side of critical state.
- ![](../graphics/ker_eqn00099.gif), the ratio of the flow stress in triaxial tension to the flow stress in triaxial compression. ![](../graphics/ker_eqn00110.gif). If the default value of 0.0 is accepted, a value of 1.0 is assumed.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *hardening*=TABULAR, the table data specify the following:- Stress ratio at critical state, ![](../graphics/ker_eqn00108.gif).
- The initial volumetric plastic strain, ![](../graphics/ker_eqn00111.gif), corresponding to ![](../graphics/ker_eqn00112.gif) according to the [ClayHardening](pt01ch29pyo15.md) definition.
- ![](../graphics/ker_eqn00095.gif), the parameter defining the size of the yield surface on the "wet" side of critical state.
- ![](../graphics/ker_eqn00099.gif), the ratio of the flow stress in triaxial tension to the flow stress in triaxial compression. ![](../graphics/ker_eqn00110.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A ClayPlasticity object.

**Exceptions**

RangeError.

### 29.16.2 setValues(...)

This method modifies the ClayPlasticity object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ClayPlasticity](pt01ch29pyo16.md#ker-clayplasticity-clayplasticity-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.16.3 Members

The ClayPlasticity object has members with the same names and descriptions as the arguments to the [ClayPlasticity](pt01ch29pyo16.md#ker-clayplasticity-clayplasticity-pyc) method.

In addition, the ClayPlasticity object can have the following member:

*clayHardening*

A [ClayHardening](pt01ch29pyo15.md) object.

### 29.16.4 Corresponding analysis keywords

| [*CLAY PLASTICITY](../key/key-link.md#usb-kws-mclayplast) |
| --- |




