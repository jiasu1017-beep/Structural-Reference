# 8.11 TProfile object







The TProfile object defines the properties of a T profile.

The TProfile object is derived from the [Profile](pt01ch08pyo01.md) object.

**Access**

```
import section
mdb.models[*name*].profiles[*name*]
import odbSection
session.odbs[*name*].profiles[*name*]
```

### 8.11.1 TProfile(...)

This method creates a TProfile object.

**Path**

```
mdb.models[*name*].TProfile
session.odbs[*name*].TProfile
```

**Required arguments**

*name*

A String specifying the repository key.

*b*

A positive Float specifying the *b* dimension (flange width) of the T profile. For more information, see ["Beam cross-section library," Section 29.3.9 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamcrosssectlib).

*h*

A positive Float specifying the *h* dimension (height) of the T profile.

*l*

A positive Float specifying the *l* dimension (offset of 1–axis from the edge of web) of the T profile.

*tf*

A positive Float specifying the *tf* dimension (flange thickness) of the T profile (*tf < h*).

*tw*

A positive Float specifying the *tw* dimension (web thickness) of the T profile (*tw< b*).

**Optional arguments**

None.

**Return value**

A TProfile object.

**Exceptions**

RangeError.

### 8.11.2 setValues(...)

This method modifies the TProfile object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [TProfile](pt01ch08pyo11.md#ker-tprofile-tprofile-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 8.11.3 Members

The TProfile object has members with the same names and descriptions as the arguments to the [TProfile](pt01ch08pyo11.md#ker-tprofile-tprofile-pyc) method.

### 8.11.4 Corresponding analysis keywords

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=I |
| --- |




