# 8.6 HexagonalProfile object







The HexagonalProfile object defines the properties of a hexagonal profile.

The HexagonalProfile object is derived from the [Profile](pt01ch08pyo01.md) object.

**Access**

```
import section
mdb.models[*name*].profiles[*name*]
import odbSection
session.odbs[*name*].profiles[*name*]
```

### 8.6.1 HexagonalProfile(...)

This method creates a HexagonalProfile object.

**Path**

```
mdb.models[*name*].HexagonalProfile
session.odbs[*name*].HexagonalProfile
```

**Required arguments**

*name*

A String specifying the repository key.

*r*

A positive Float specifying the *r* dimension (outer radius) of the hexagonal profile. For more information, see ["Beam cross-section library," Section 29.3.9 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamcrosssectlib).

*t*

A positive Float specifying the *t* dimension (wall thickness) of the hexagonal profile, *t < (sqrt(3)/2)r*.

**Optional arguments**

None.

**Return value**

A HexagonalProfile object.

**Exceptions**

RangeError.

### 8.6.2 setValues(...)

This method modifies the HexagonalProfile object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [HexagonalProfile](pt01ch08pyo06.md#ker-hexagonalprofile-hexagonalprofile-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 8.6.3 Members

The HexagonalProfile object has members with the same names and descriptions as the arguments to the [HexagonalProfile](pt01ch08pyo06.md#ker-hexagonalprofile-hexagonalprofile-pyc) method.

### 8.6.4 Corresponding analysis keywords

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=HEX |
| --- |




