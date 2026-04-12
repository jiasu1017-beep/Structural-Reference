# 8.8 LProfile object







The LProfile object defines the properties of a L profile.

The LProfile object is derived from the [Profile](pt01ch08pyo01.md) object.

**Access**

```
import section
mdb.models[*name*].profiles[*name*]
import odbSection
session.odbs[*name*].profiles[*name*]
```

### 8.8.1 LProfile(...)

This method creates a LProfile object.

**Path**

```
mdb.models[*name*].LProfile
session.odbs[*name*].LProfile
```

**Required arguments**

*name*

A String specifying the repository key.

*a*

A positive Float specifying the *a* dimension (flange length) of the L profile. For more information, see ["Beam cross-section library," Section 29.3.9 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamcrosssectlib).

*b*

A positive Float specifying the *b* dimension (flange length) of the L profile.

*t1*

A positive Float specifying the *t1* dimension (flange thickness) of the L profile (*t1 < b*).

*t2*

A positive Float specifying the *t2* dimension (flange thickness) of the L profile (*t2< a*).

**Optional arguments**

None.

**Return value**

A LProfile object.

**Exceptions**

RangeError.

### 8.8.2 setValues(...)

This method modifies the LProfile object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [LProfile](pt01ch08pyo08.md#ker-lprofile-lprofile-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 8.8.3 Members

The LProfile object has members with the same names and descriptions as the arguments to the [LProfile](pt01ch08pyo08.md#ker-lprofile-lprofile-pyc) method.

### 8.8.4 Corresponding analysis keywords

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=L |
| --- |




