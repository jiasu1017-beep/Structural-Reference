# 29.66 LatentHeat object







The LatentHeat object specifies a material's latent heat.

**Access**

```
import material
mdb.models[*name*].materials[*name*].latentHeat
import odbMaterial
session.odbs[*name*].materials[*name*].latentHeat
```

### 29.66.1 LatentHeat(...)

This method creates a LatentHeat object.

**Path**

```
mdb.models[*name*].materials[*name*].LatentHeat
session.odbs[*name*].materials[*name*].LatentHeat
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

None.

**Table data**

- Latent heat per unit mass.
- Solidus temperature.
- Liquidus temperature.

**Return value**

A LatentHeat object.

**Exceptions**

RangeError.

### 29.66.2 setValues(...)

This method modifies the LatentHeat object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [LatentHeat](pt01ch29pyo66.md#ker-latentheat-latentheat-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.66.3 Members

The LatentHeat object has members with the same names and descriptions as the arguments to the [LatentHeat](pt01ch29pyo66.md#ker-latentheat-latentheat-pyc) method.

### 29.66.4 Corresponding analysis keywords

| [*LATENT HEAT](../key/key-link.md#usb-kws-mlatentheat) |
| --- |




