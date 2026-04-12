# 8.3 BoxProfile object







The BoxProfile object defines the properties of a box profile.

The BoxProfile object is derived from the [Profile](pt01ch08pyo01.md) object.

**Access**

```
import section
mdb.models[*name*].profiles[*name*]
import odbSection
session.odbs[*name*].profiles[*name*]
```

### 8.3.1 BoxProfile(...)

This method creates a BoxProfile object.

**Path**

```
mdb.models[*name*].BoxProfile
session.odbs[*name*].BoxProfile
```

**Required arguments**

*name*

A String specifying the repository key.

*a*

A Float specifying the *a* dimension of the box profile. For more information, see ["Beam cross-section library," Section 29.3.9 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamcrosssectlib).

*b*

A Float specifying the *b* dimension of the box profile.

*uniformThickness*

A Boolean specifying whether the thickness is uniform.

*t1*

A Float specifying the uniform wall thickness if *uniformThickness*=ON, and the wall thickness of the first segment if *uniformThickness*=OFF.

**Optional arguments**

*t2*

A Float specifying the wall thickness of the second segment. *t2* is required only when *uniformThickness*=OFF. The default value is 0.0.

*t3*

A Float specifying the wall thickness of the third segment. *t3* is required only when *uniformThickness*=OFF. The default value is 0.0.

*t4*

A Float specifying the wall thickness of the fourth segment. *t4* is required only when *uniformThickness*=OFF. The default value is 0.0.

**Return value**

A BoxProfile object.

**Exceptions**

RangeError.

### 8.3.2 setValues(...)

This method modifies the BoxProfile object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [BoxProfile](pt01ch08pyo03.md#ker-boxprofile-boxprofile-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 8.3.3 Members

The BoxProfile object has members with the same names and descriptions as the arguments to the [BoxProfile](pt01ch08pyo03.md#ker-boxprofile-boxprofile-pyc) method.

### 8.3.4 Corresponding analysis keywords

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=BOX |
| --- |




