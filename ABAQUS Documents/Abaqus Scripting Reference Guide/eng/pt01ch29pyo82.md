# 29.82 PorousMetalPlasticity object







The PorousMetalPlasticity object specifies a porous metal plasticity model.

**Access**

```
import material
mdb.models[*name*].materials[*name*].porousMetalPlasticity
import odbMaterial
session.odbs[*name*].materials[*name*].porousMetalPlasticity
```

### 29.82.1 PorousMetalPlasticity(...)

This method creates a PorousMetalPlasticity object.

**Path**

```
mdb.models[*name*].materials[*name*].PorousMetalPlasticity
session.odbs[*name*].materials[*name*].PorousMetalPlasticity
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*relativeDensity*

 `None` or a Float specifying the initial relative density of the material, ![](../graphics/ker_eqn00346.gif). The default value is `None`.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

- ![](../graphics/ker_eqn00347.gif).
- ![](../graphics/ker_eqn00348.gif).
- ![](../graphics/ker_eqn00349.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A PorousMetalPlasticity object.

**Exceptions**

RangeError.

### 29.82.2 setValues(...)

This method modifies the PorousMetalPlasticity object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [PorousMetalPlasticity](pt01ch29pyo82.md#ker-porousmetalplasticity-porousmetalplasticity-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.82.3 Members

The PorousMetalPlasticity object has members with the same names and descriptions as the arguments to the [PorousMetalPlasticity](pt01ch29pyo82.md#ker-porousmetalplasticity-porousmetalplasticity-pyc) method.

In addition, the PorousMetalPlasticity object can have the following members:

*porousFailureCriteria*

A [PorousFailureCriteria](pt01ch29pyo81.md) object.

*voidNucleation*

A [VoidNucleation](pt01ch29pyo109.md) object.

### 29.82.4 Corresponding analysis keywords

| [*POROUS METAL PLASTICITY](../key/key-link.md#usb-kws-mpormetalplas) |
| --- |




