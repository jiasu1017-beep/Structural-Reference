# 8.10 RectangularProfile object







The RectangularProfile object defines the properties of a solid rectangular profile.

The RectangularProfile object is derived from the [Profile](pt01ch08pyo01.md) object.

**Access**

```
import section
mdb.models[*name*].profiles[*name*]
import odbSection
session.odbs[*name*].profiles[*name*]
```

### 8.10.1 RectangularProfile(...)

This method creates a RectangularProfile object.

**Path**

```
mdb.models[*name*].RectangularProfile
session.odbs[*name*].RectangularProfile
```

**Required arguments**

*name*

A String specifying the repository key.

*a*

A positive Float specifying the *a* dimension of the rectangular profile. For more information, see ["Beam cross-section library," Section 29.3.9 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamcrosssectlib).

*b*

A positive Float specifying the *b* dimension of the rectangular profile.

**Optional arguments**

None.

**Return value**

A RectangularProfile object.

**Exceptions**

RangeError.

### 8.10.2 setValues(...)

This method modifies the RectangularProfile object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [RectangularProfile](pt01ch08pyo10.md#ker-rectangularprofile-rectangularprofile-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 8.10.3 Members

The RectangularProfile object has members with the same names and descriptions as the arguments to the [RectangularProfile](pt01ch08pyo10.md#ker-rectangularprofile-rectangularprofile-pyc) method.

### 8.10.4 Corresponding analysis keywords

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=RECT |
| --- |




