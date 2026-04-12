# 29.11 CapPlasticity object







The CapPlasticity object specifies the modified Drucker-Prager/Cap plasticity model.

**Access**

```
import material
mdb.models[*name*].materials[*name*].capPlasticity
import odbMaterial
session.odbs[*name*].materials[*name*].capPlasticity
```

### 29.11.1 CapPlasticity(...)

This method creates a CapPlasticity object.

**Path**

```
mdb.models[*name*].materials[*name*].CapPlasticity
session.odbs[*name*].materials[*name*].CapPlasticity
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

- Material cohesion, ![](../graphics/ker_eqn00082.gif), in the ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00093.gif) plane (Abaqus/Standard) or in the ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00094.gif) plane (Abaqus/Explicit).
- Material angle of friction, ![](../graphics/ker_eqn00095.gif), in the ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00093.gif) plane (Abaqus/Standard) or in the ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00094.gif) plane (Abaqus/Explicit). Give the value in degrees.
- Cap eccentricity parameter, ![](../graphics/ker_eqn00096.gif). Its value must be greater than zero (typically 0.0 ![](../graphics/ker_eqn00097.gif) 1.0).
- Initial cap yield surface position, ![](../graphics/ker_eqn00098.gif).
- Transition surface radius parameter, ![](../graphics/ker_eqn00090.gif). The default value is 0.0 (i.e., no transition surface).
- (Not used in Abaqus/Explicit) ![](../graphics/ker_eqn00099.gif), the ratio of the flow stress in triaxial tension to the flow stress in triaxial compression. Possible values are 0.778 ![](../graphics/ker_eqn00100.gif) 1.0. If the default value of 0.0 is accepted, Abaqus/Standard assumes ![](../graphics/ker_eqn00101.gif) 1.0.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A CapPlasticity object.

**Exceptions**

RangeError.

### 29.11.2 setValues(...)

This method modifies the CapPlasticity object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [CapPlasticity](pt01ch29pyo11.md#ker-capplasticity-capplasticity-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.11.3 Members

The CapPlasticity object has members with the same names and descriptions as the arguments to the [CapPlasticity](pt01ch29pyo11.md#ker-capplasticity-capplasticity-pyc) method.

In addition, the CapPlasticity object can have the following members:

*capCreepCohesion*

A [CapCreepCohesion](pt01ch29pyo08.md) object.

*capCreepConsolidation*

A [CapCreepConsolidation](pt01ch29pyo09.md) object.

*capHardening*

A [CapHardening](pt01ch29pyo10.md) object.

### 29.11.4 Corresponding analysis keywords

| [*CAP PLASTICITY](../key/key-link.md#usb-kws-mcapplasticity) |
| --- |




