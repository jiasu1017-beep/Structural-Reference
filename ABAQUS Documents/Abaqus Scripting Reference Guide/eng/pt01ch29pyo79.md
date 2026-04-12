# 29.79 PorousBulkModuli object







The PorousBulkModuli object defines bulk moduli for soils and rocks.

**Access**

```
import material
mdb.models[*name*].materials[*name*].porousBulkModuli
import odbMaterial
session.odbs[*name*].materials[*name*].porousBulkModuli
```

### 29.79.1 PorousBulkModuli(...)

This method creates a PorousBulkModuli object.

**Path**

```
mdb.models[*name*].materials[*name*].PorousBulkModuli
session.odbs[*name*].materials[*name*].PorousBulkModuli
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional argument**

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

**Table data**

- Bulk modulus of solid grains.
- Bulk modulus of permeating fluid.
- Temperature, if the data depend on temperature.

**Return value**

A PorousBulkModuli object.

**Exceptions**

None.

### 29.79.2 setValues(...)

This method modifies the PorousBulkModuli object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [PorousBulkModuli](pt01ch29pyo79.md#ker-porousbulkmoduli-porousbulkmoduli-pyc) method.

**Return value**

None

**Exceptions**

None.

### 29.79.3 Members

The PorousBulkModuli object has members with the same names and descriptions as the arguments to the [PorousBulkModuli](pt01ch29pyo79.md#ker-porousbulkmoduli-porousbulkmoduli-pyc) method.

### 29.79.4 Corresponding analysis keywords

| [*POROUS BULK MODULI](../key/key-link.md#usb-kws-mporousbulkmod) |
| --- |




