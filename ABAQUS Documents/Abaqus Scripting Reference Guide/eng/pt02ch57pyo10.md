# 57.10 RectangularProfile object







The RectangularProfile object defines the properties of a solid rectangular profile.

The RectangularProfile object is derived from the [Profile](pt02ch57pyo01.md) object.

**Access**

```
sectionApi.profiles()[*name*]
```

### 57.10.1 RectangularProfile(...)

This method creates a RectangularProfile object.

**Path**

```
sectionApi.RectangularProfile
```

**Prototype**

```
odb_RectangularProfile&
RectangularProfile(const odb_String& name,
                   double a,
                   double b);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*a*

A positive Double specifying the *a* dimension of the rectangular profile. For more information, see ["Beam cross-section library," Section 29.3.9 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamcrosssectlib).

*b*

A positive Double specifying the *b* dimension of the rectangular profile.

**Optional arguments**

None.

**Return value**

A RectangularProfile object.

**Exceptions**

RangeError.

### 57.10.2 Members

The RectangularProfile object has members with the same names and descriptions as the arguments to the [RectangularProfile](pt02ch57pyo10.md#ker-rectangularprofile-rectangularprofile-cpp) method.

### 57.10.3 Corresponding analysis keywords

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=RECT |
| --- |




