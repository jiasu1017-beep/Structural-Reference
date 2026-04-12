# 29.35 Damping object







The Damping object specifies material damping.

**Access**

```
import material
mdb.models[*name*].materials[*name*].damping
import odbMaterial
session.odbs[*name*].materials[*name*].damping
```

### 29.35.1 Damping(...)

This method creates a Damping object.

**Path**

```
mdb.models[*name*].materials[*name*].Damping
session.odbs[*name*].materials[*name*].Damping
```

**Required arguments**

None.

**Optional arguments**

*alpha*

A Float specifying the ![](../graphics/ker_eqn00161.gif) factor to create mass proportional damping in direct-integration and explicit dynamics. The default value is 0.0.

*beta*

A Float specifying the ![](../graphics/ker_eqn00162.gif) factor to create stiffness proportional damping in direct-integration and explicit dynamics. The default value is 0.0.

*composite*

A Float specifying the fraction of critical damping to be used with this material in calculating composite damping factors for the modes (for use in modal dynamics). The default value is 0.0.

This argument applies only to Abaqus/Standard analyses.

*structural*

A Float specifying the structural factor to create material damping in direct-integration and explicit dynamics. The default value is 0.0.

**Return value**

A Damping object.

**Exceptions**

RangeError.

### 29.35.2 setValues(...)

This method modifies the Damping object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [Damping](pt01ch29pyo35.md#ker-damping-damping-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.35.3 Members

The Damping object has members with the same names and descriptions as the arguments to the [Damping](pt01ch29pyo35.md#ker-damping-damping-pyc) method.

### 29.35.4 Corresponding analysis keywords

| [*DAMPING](../key/key-link.md#usb-kws-mdamping) |
| --- |




