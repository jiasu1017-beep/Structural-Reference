# 46.25 TransverseShearShell object







The TransverseShearShell object defines the transverse shear stiffness properties of a shell section.

**Access**

```
import section
mdb.models[*name*].sections[*name*].transverseShear
import odbSection
session.odbs[*name*].sections[*name*].transverseShear
```

### 46.25.1 TransverseShearShell(...)

This method creates a TransverseShearShell object.

**Path**

```
mdb.models[*name*].sections[*name*].TransverseShearShell
session.odbs[*name*].sections[*name*].TransverseShearShell
```

**Required arguments**

*k11*

A Float specifying the shear stiffness of the section in the first direction.

*k22*

A Float specifying the shear stiffness of the section in the second direction.

*k12*

A Float specifying the coupling term in the shear stiffness of the section.

**Optional arguments**

None.

**Return value**

A TransverseShearShell object.

**Exceptions**

None.

### 46.25.2 setValues(...)

This method modifies the TransverseShearShell object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [TransverseShearShell](pt01ch46pyo25.md#ker-transverseshearshell-transverseshearshell-pyc) method.

**Return value**

None

**Exceptions**

None.

### 46.25.3 Members

The TransverseShearShell object has members with the same names and descriptions as the arguments to the [TransverseShearShell](pt01ch46pyo25.md#ker-transverseshearshell-transverseshearshell-pyc) method.

### 46.25.4 Corresponding analysis keywords

| [*TRANSVERSE SHEAR STIFFNESS](../key/key-link.md#usb-kws-mtransshearstiff) |
| --- |




