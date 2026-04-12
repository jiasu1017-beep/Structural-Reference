# 57.12 TrapezoidalProfile object







The TrapezoidalProfile object defines the properties of a trapezoidal profile.

The TrapezoidalProfile object is derived from the [Profile](pt02ch57pyo01.md) object.

**Access**

```
sectionApi.profiles()[*name*]
```

### 57.12.1 TrapezoidalProfile(...)

This method creates a TrapezoidalProfile object.

**Path**

```
sectionApi.TrapezoidalProfile
```

**Prototype**

```
odb_TrapezoidalProfile&
TrapezoidalProfile(const odb_String& name,
                   double a,
                   double b,
                   double c,
                   double d);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*a*

A positive Double specifying the *a* dimension of the Trapezoidal profile. For more information, see ["Beam cross-section library," Section 29.3.9 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamcrosssectlib).

*b*

A positive Double specifying the *b* dimension of the Trapezoidal profile.

*c*

A positive Double specifying the *c* dimension of the Trapezoidal profile.

*d*

A Double specifying the *d* dimension of the Trapezoidal profile.

**Optional arguments**

None.

**Return value**

A TrapezoidalProfile object.

**Exceptions**

RangeError.

### 57.12.2 Members

The TrapezoidalProfile object has members with the same names and descriptions as the arguments to the [TrapezoidalProfile](pt02ch57pyo12.md#ker-trapezoidalprofile-trapezoidalprofile-cpp) method.

### 57.12.3 Corresponding analysis keywords

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=TRAPEZOID |
| --- |




