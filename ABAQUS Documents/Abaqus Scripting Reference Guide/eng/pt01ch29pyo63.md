# 29.63 Hysteresis object







The Hysteresis object specifies the creep part of the material model for the hysteretic behavior of elastomers.

**Access**

```
import material
mdb.models[*name*].materials[*name*].hyperelastic.hysteresis
import odbMaterial
session.odbs[*name*].materials[*name*].hyperelastic.hysteresis
```

### 29.63.1 Hysteresis(...)

This method creates a Hysteresis object.

**Path**

```
mdb.models[*name*].materials[*name*].hyperelastic.Hysteresis
session.odbs[*name*].materials[*name*].hyperelastic.Hysteresis
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

None.

**Table data**

- Stress scaling factor.
- Creep parameter.
- Effective stress exponent.
- Creep strain exponent.

**Return value**

A Hysteresis object.

**Exceptions**

RangeError.

### 29.63.2 setValues(...)

This method modifies the Hysteresis object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [Hysteresis](pt01ch29pyo63.md#ker-hysteresis-hysteresis-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.63.3 Members

The Hysteresis object has members with the same names and descriptions as the arguments to the [Hysteresis](pt01ch29pyo63.md#ker-hysteresis-hysteresis-pyc) method.

### 29.63.4 Corresponding analysis keywords

| [*HYSTERESIS](../key/key-link.md#usb-kws-mhysteresis) |
| --- |




