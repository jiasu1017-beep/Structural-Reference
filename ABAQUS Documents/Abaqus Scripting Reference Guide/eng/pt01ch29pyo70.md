# 29.70 MohrCoulombPlasticity object







The MohrCoulombPlasticity object specifies the extended Mohr-Coulomb plasticity model.

**Access**

```
import material
mdb.models[*name*].materials[*name*].mohrCoulombPlasticity
import odbMaterial
session.odbs[*name*].materials[*name*].mohrCoulombPlasticity
```

### 29.70.1 MohrCoulombPlasticity(...)

This method creates a MohrCoulombPlasticity object.

**Path**

```
mdb.models[*name*].materials[*name*].MohrCoulombPlasticity
session.odbs[*name*].materials[*name*].MohrCoulombPlasticity
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*deviatoricEccentricity*

 `None` or a Float specifying the flow potential eccentricity in the deviatoric plane, ![](../graphics/ker_eqn00289.gif); 1/2 ![](../graphics/ker_eqn00290.gif) 1.0. If *deviatoricEccentricity*=`None`, Abaqus calculates the value using the specified Mohr-Coulomb angle of friction. The default value is `None`.

*meridionalEccentricity*

A Float specifying the flow potential eccentricity in the meridional plane, ![](../graphics/ker_eqn00062.gif). The default value is 0.1.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

*useTensionCutoff*

A Boolean specifying whether tension cutoff specification is needed. The default value is OFF.

**Table data**

The table data specify the following:
- Friction angle (given in degrees), ![](../graphics/ker_eqn00291.gif), at high confining pressure in the ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00292.gif) plane.
- Dilation angle, ![](../graphics/ker_eqn00132.gif), at high confining pressure in the ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00293.gif) plane.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A MohrCoulombPlasticity object.

**Exceptions**

RangeError.

### 29.70.2 setValues(...)

This method modifies the MohrCoulombPlasticity object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [MohrCoulombPlasticity](pt01ch29pyo70.md#ker-mohrcoulombplasticity-mohrcoulombplasticity-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.70.3 Members

The MohrCoulombPlasticity object has members with the same names and descriptions as the arguments to the [MohrCoulombPlasticity](pt01ch29pyo70.md#ker-mohrcoulombplasticity-mohrcoulombplasticity-pyc) method.

In addition, the MohrCoulombPlasticity object can have the following members:

*mohrCoulombHardening*

A [MohrCoulombHardening](pt01ch29pyo69.md) object.

*tensionCutOff*

A [TensionCutOff](pt01ch29pyo97.md) object.

### 29.70.4 Corresponding analysis keywords

| [*MOHR COULOMB](../key/key-link.md#usb-kws-mmohrcoulomb) |
| --- |




