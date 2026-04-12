# 29.38 Depvar object







The Depvar object specifies solution-dependent state variables.

**Access**

```
import material
mdb.models[*name*].materials[*name*].depvar
import odbMaterial
session.odbs[*name*].materials[*name*].depvar
```

### 29.38.1 Depvar(...)

This method creates a Depvar object.

**Path**

```
mdb.models[*name*].materials[*name*].Depvar
session.odbs[*name*].materials[*name*].Depvar
```

**Required arguments**

None.

**Optional arguments**

*deleteVar*

An Int specifying the state variable number controlling the element deletion flag. The default value is 0.

This argument applies only to Abaqus/Explicit analyses.

*n*

An Int specifying the number of solution-dependent state variables required at each integration point. The default value is 0.

**Return value**

A Depvar object.

**Exceptions**

RangeError.

### 29.38.2 setValues(...)

This method modifies the Depvar object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [Depvar](pt01ch29pyo38.md#ker-depvar-depvar-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.38.3 Members

The Depvar object has members with the same names and descriptions as the arguments to the [Depvar](pt01ch29pyo38.md#ker-depvar-depvar-pyc) method.

### 29.38.4 Corresponding analysis keywords

| [*DEPVAR](../key/key-link.md#usb-kws-mdepvar) |
| --- |




