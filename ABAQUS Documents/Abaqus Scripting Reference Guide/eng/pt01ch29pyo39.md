# 29.39 DetonationPoint object







A DetonationPoint object specifies a suboption of the Eos object. The DetonationPoint object defines either isotropic linear elastic shear or linear viscous shear behavior for a hydrodynamic material.

**Access**

```
import material
mdb.models[*name*].materials[*name*].eos.detonationPoint
import odbMaterial
session.odbs[*name*].materials[*name*].eos.detonationPoint
```

### 29.39.1 DetonationPoint(...)

This method creates a DetonationPoint object.

**Path**

```
mdb.models[*name*].materials[*name*].eos.DetonationPoint
session.odbs[*name*].materials[*name*].eos.DetonationPoint
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

None.

**Table data**

- X value for coordinate of detonation point.
- Y value for coordinate of detonation point.
- Z value for coordinate of detonation point.
- Detonation delay time.

**Return value**

A DetonationPoint object.

**Exceptions**

None.

### 29.39.2 setValues(...)

This method modifies the DetonationPoint object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [DetonationPoint](pt01ch29pyo39.md#ker-detonationpoint-detonationpoint-pyc) method.

**Return value**

None

**Exceptions**

None.

### 29.39.3 Members

The DetonationPoint object has members with the same names and descriptions as the arguments to the [DetonationPoint](pt01ch29pyo39.md#ker-detonationpoint-detonationpoint-pyc) method.

### 29.39.4 Corresponding analysis keywords

| [*DETONATION POINT](../key/key-link.md#usb-kws-mdetonationpt) |
| --- |




