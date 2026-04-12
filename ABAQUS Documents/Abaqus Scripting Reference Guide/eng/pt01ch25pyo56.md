# 25.56 Radiation object







The Radiation object specifies radiation for a contact interaction property.

**Access**

```
import interaction
mdb.models[*name*].interactionProperties[*name*].radiation
```

### 25.56.1 Radiation(...)

This method creates a Radiation object.

**Path**

```
mdb.models[*name*].interactionProperties[*name*].Radiation
```

**Required arguments**

*masterEmissivity*

A Float specifying the emissivity of the master surface.

*slaveEmissivity*

A Float specifying the emissivity of the slave surface.

*table*

A sequence of sequences of Floats specifying the following:
- Effective viewfactor, ![](../graphics/ker_eqn00081.gif).
- Gap clearance, ![](../graphics/ker_eqn00082.gif).

**Optional arguments**

None.

**Return value**

A Radiation object.

**Exceptions**

None.

### 25.56.2 setValues(...)

This method modifies the Radiation object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [Radiation](pt01ch25pyo56.md#ker-radiation-radiation-pyc) method.

**Return value**

None

**Exceptions**

None.

### 25.56.3 Members

The Radiation object has members with the same names and descriptions as the arguments to the [Radiation](pt01ch25pyo56.md#ker-radiation-radiation-pyc) method.

### 25.56.4 Corresponding analysis keywords

| [*GAP RADIATION](../key/key-link.md#usb-kws-mgapradiation) |
| --- |




