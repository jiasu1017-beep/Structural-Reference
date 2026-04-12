# 29.81 PorousFailureCriteria object







The PorousFailureCriteria object specifies the material failure criteria for a porous metal.

**Access**

```
import material
mdb.models[*name*].materials[*name*].porousMetalPlasticity\
.porousFailureCriteria
import odbMaterial
session.odbs[*name*].materials[*name*].porousMetalPlasticity\
.porousFailureCriteria
```

### 29.81.1 PorousFailureCriteria(...)

This method creates a PorousFailureCriteria object.

**Path**

```
mdb.models[*name*].materials[*name*].porousMetalPlasticity\
.PorousFailureCriteria
session.odbs[*name*].materials[*name*].porousMetalPlasticity\
.PorousFailureCriteria
```

**Required arguments**

None.

**Optional arguments**

*fraction*

A Float specifying the void volume fraction at total failure, ![](../graphics/ker_eqn00344.gif). The default value is 1.0.

*criticalFraction*

A Float specifying the critical void volume fraction, ![](../graphics/ker_eqn00345.gif). The default value is 1.0.

**Return value**

A PorousFailureCriteria object.

**Exceptions**

RangeError.

### 29.81.2 setValues(...)

This method modifies the PorousFailureCriteria object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [PorousFailureCriteria](pt01ch29pyo81.md#ker-porousfailurecriteria-porousfailurecriteria-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.81.3 Members

The PorousFailureCriteria object has members with the same names and descriptions as the arguments to the [PorousFailureCriteria](pt01ch29pyo81.md#ker-porousfailurecriteria-porousfailurecriteria-pyc) method.

### 29.81.4 Corresponding analysis keywords

| [*POROUS FAILURE CRITERIA](../key/key-link.md#usb-kws-mporfailcriteria) |
| --- |




