# 8.4 CircularProfile object







The CircularProfile object defines the properties of a solid circular profile.

The CircularProfile object is derived from the [Profile](pt01ch08pyo01.md) object.

**Access**

```
import section
mdb.models[*name*].profiles[*name*]
import odbSection
session.odbs[*name*].profiles[*name*]
```

### 8.4.1 CircularProfile(...)

This method creates a CircularProfile object.

**Path**

```
mdb.models[*name*].CircularProfile
session.odbs[*name*].CircularProfile
```

**Required arguments**

*name*

A String specifying the repository key.

*r*

A positive Float specifying the *r* dimension (outer radius) of the circular profile. For more information, see ["Beam cross-section library," Section 29.3.9 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamcrosssectlib).

**Optional arguments**

None.

**Return value**

A CircularProfile object.

**Exceptions**

RangeError.

### 8.4.2 setValues(...)

This method modifies the CircularProfile object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [CircularProfile](pt01ch08pyo04.md#ker-circularprofile-circularprofile-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 8.4.3 Members

The CircularProfile object has members with the same names and descriptions as the arguments to the [CircularProfile](pt01ch08pyo04.md#ker-circularprofile-circularprofile-pyc) method.

### 8.4.4 Corresponding analysis keywords

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=CIRC |
| --- |




