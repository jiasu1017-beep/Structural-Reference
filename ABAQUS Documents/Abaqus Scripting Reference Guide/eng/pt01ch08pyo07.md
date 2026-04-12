# 8.7 IProfile object







The IProfile object defines the properties of an I profile.

The IProfile object is derived from the [Profile](pt01ch08pyo01.md) object.

**Access**

```
import section
mdb.models[*name*].profiles[*name*]
import odbSection
session.odbs[*name*].profiles[*name*]
```

### 8.7.1 IProfile(...)

This method creates an IProfile object.

**Path**

```
mdb.models[*name*].IProfile
session.odbs[*name*].IProfile
```

**Required arguments**

*name*

A String specifying the repository key.

*l*

A Float specifying the *l* dimension (offset of 1–axis from the bottom flange surface) of the I profile. For more information, see ["Beam cross-section library," Section 29.3.9 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamcrosssectlib).

*h*

A Float specifying the *h* dimension (height) of the I profile.

*b1*

A Float specifying the *b1* dimension (bottom flange width) of the I profile.

*b2*

A Float specifying the *b2* dimension (top flange width) of the I profile.

*t1*

A Float specifying the *t1* dimension (bottom flange thickness) of the I profile.

*t2*

A Float specifying the *t2* dimension (top flange thickness) of the I profile.

*t3*

A Float specifying the *t3* dimension (web thickness) of the I profile.

**Optional arguments**

None.

**Return value**

An IProfile object.

**Exceptions**

RangeError.

### 8.7.2 setValues(...)

This method modifies the IProfile object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [IProfile](pt01ch08pyo07.md#ker-iprofile-iprofile-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 8.7.3 Members

The IProfile object has members with the same names and descriptions as the arguments to the [IProfile](pt01ch08pyo07.md#ker-iprofile-iprofile-pyc) method.

### 8.7.4 Corresponding analysis keywords

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=I |
| --- |




