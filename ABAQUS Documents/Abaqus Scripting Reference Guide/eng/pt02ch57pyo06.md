# 57.6 HexagonalProfile object







The HexagonalProfile object defines the properties of a hexagonal profile.

The HexagonalProfile object is derived from the [Profile](pt02ch57pyo01.md) object.

**Access**

```
sectionApi.profiles()[*name*]
```

### 57.6.1 HexagonalProfile(...)

This method creates a HexagonalProfile object.

**Path**

```
sectionApi.HexagonalProfile
```

**Prototype**

```
odb_HexagonalProfile&
HexagonalProfile(const odb_String& name,
                 double r,
                 double t);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*r*

A positive Double specifying the *r* dimension (outer radius) of the hexagonal profile. For more information, see ["Beam cross-section library," Section 29.3.9 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamcrosssectlib).

*t*

A positive Double specifying the *t* dimension (wall thickness) of the hexagonal profile, *t < (sqrt(3)/2)r*.

**Optional arguments**

None.

**Return value**

A HexagonalProfile object.

**Exceptions**

RangeError.

### 57.6.2 Members

The HexagonalProfile object has members with the same names and descriptions as the arguments to the [HexagonalProfile](pt02ch57pyo06.md#ker-hexagonalprofile-hexagonalprofile-cpp) method.

### 57.6.3 Corresponding analysis keywords

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=HEX |
| --- |




