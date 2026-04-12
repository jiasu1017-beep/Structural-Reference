# 29.71 MoistureSwelling object







The MoistureSwelling object defines moisture-driven swelling.

**Access**

```
import material
mdb.models[*name*].materials[*name*].moistureSwelling
import odbMaterial
session.odbs[*name*].materials[*name*].moistureSwelling
```

### 29.71.1 MoistureSwelling(...)

This method creates a MoistureSwelling object.

**Path**

```
mdb.models[*name*].materials[*name*].MoistureSwelling
session.odbs[*name*].materials[*name*].MoistureSwelling
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

None.

**Table data**

- Volumetric moisture swelling strain, ![](../graphics/ker_eqn00294.gif).
- Saturation, ![](../graphics/ker_eqn00234.gif). This value must lie in the range ![](../graphics/ker_eqn00295.gif).

**Return value**

A MoistureSwelling object.

**Exceptions**

None.

### 29.71.2 setValues(...)

This method modifies the MoistureSwelling object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [MoistureSwelling](pt01ch29pyo71.md#ker-moistureswelling-moistureswelling-pyc) method.

**Return value**

None

**Exceptions**

None.

### 29.71.3 Members

The MoistureSwelling object has members with the same names and descriptions as the arguments to the [MoistureSwelling](pt01ch29pyo71.md#ker-moistureswelling-moistureswelling-pyc) method.

In addition, the MoistureSwelling object can have the following member:

*ratios*

A [Ratios](pt01ch29pyo86.md) object.

### 29.71.4 Corresponding analysis keywords

| [*MOISTURE SWELLING](../key/key-link.md#usb-kws-mmoistureswell) |
| --- |




