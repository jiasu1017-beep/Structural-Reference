# 8.12 TrapezoidalProfile object







The TrapezoidalProfile object defines the properties of a trapezoidal profile.

The TrapezoidalProfile object is derived from the [Profile](pt01ch08pyo01.md) object.

**Access**

```
import section
mdb.models[*name*].profiles[*name*]
import odbSection
session.odbs[*name*].profiles[*name*]
```

### 8.12.1 TrapezoidalProfile(...)

This method creates a TrapezoidalProfile object.

**Path**

```
mdb.models[*name*].TrapezoidalProfile
session.odbs[*name*].TrapezoidalProfile
```

**Required arguments**

*name*

A String specifying the repository key.

*a*

A positive Float specifying the *a* dimension of the Trapezoidal profile. For more information, see ["Beam cross-section library," Section 29.3.9 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamcrosssectlib).

*b*

A positive Float specifying the *b* dimension of the Trapezoidal profile.

*c*

A positive Float specifying the *c* dimension of the Trapezoidal profile.

*d*

A Float specifying the *d* dimension of the Trapezoidal profile.

**Optional arguments**

None.

**Return value**

A TrapezoidalProfile object.

**Exceptions**

RangeError.

### 8.12.2 setValues(...)

This method modifies the TrapezoidalProfile object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [TrapezoidalProfile](pt01ch08pyo12.md#ker-trapezoidalprofile-trapezoidalprofile-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 8.12.3 Members

The TrapezoidalProfile object has members with the same names and descriptions as the arguments to the [TrapezoidalProfile](pt01ch08pyo12.md#ker-trapezoidalprofile-trapezoidalprofile-pyc) method.

### 8.12.4 Corresponding analysis keywords

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=TRAPEZOID |
| --- |




