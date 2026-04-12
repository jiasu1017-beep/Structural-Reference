# 8.5 GeneralizedProfile object







The GeneralizedProfile object defines the properties of a profile via its area, moment of inertia, etc.

The GeneralizedProfile object is derived from the [Profile](pt01ch08pyo01.md) object.

**Access**

```
import section
mdb.models[*name*].profiles[*name*]
import odbSection
session.odbs[*name*].profiles[*name*]
```

### 8.5.1 GeneralizedProfile(...)

This method creates a GeneralizedProfile object.

**Path**

```
mdb.models[*name*].GeneralizedProfile
session.odbs[*name*].GeneralizedProfile
```

**Required arguments**

*name*

A String specifying the repository key.

*area*

A Float specifying the cross-sectional area for the profile.

*i11*

A Float specifying the moment of inertia for bending about the 1-axis, ![](../graphics/ker_eqn00019.gif).

*i12*

A Float specifying the moment of inertia for cross bending, ![](../graphics/ker_eqn00020.gif).

*i22*

A Float specifying the moment of inertia for bending about the 2-axis, ![](../graphics/ker_eqn00021.gif).

*j*

A Float specifying the torsional constant, ![](../graphics/ker_eqn00022.gif).

*gammaO*

A Float specifying the sectorial moment, ![](../graphics/ker_eqn00023.gif).

*gammaW*

A Float specifying the warping constant, ![](../graphics/ker_eqn00024.gif).

**Optional arguments**

None.

**Return value**

A GeneralizedProfile object.

**Exceptions**

RangeError.

### 8.5.2 setValues(...)

This method modifies the GeneralizedProfile object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [GeneralizedProfile](pt01ch08pyo05.md#ker-generalizedprofile-generalizedprofile-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 8.5.3 Members

The GeneralizedProfile object has members with the same names and descriptions as the arguments to the [GeneralizedProfile](pt01ch08pyo05.md#ker-generalizedprofile-generalizedprofile-pyc) method.

### 8.5.4 Corresponding analysis keywords

| [*BEAM GENERAL SECTION](../key/key-link.md#usb-kws-mbeamgensect), SECTION=GENERAL or NONLINEAR GENERAL |
| --- |




