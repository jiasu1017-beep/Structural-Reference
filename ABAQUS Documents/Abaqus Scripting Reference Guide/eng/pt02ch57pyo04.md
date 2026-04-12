# 57.4 CircularProfile object







The CircularProfile object defines the properties of a solid circular profile.

The CircularProfile object is derived from the [Profile](pt02ch57pyo01.md) object.

**Access**

```
sectionApi.profiles()[*name*]
```

### 57.4.1 CircularProfile(...)

This method creates a CircularProfile object.

**Path**

```
sectionApi.CircularProfile
```

**Prototype**

```
odb_CircularProfile&
CircularProfile(const odb_String& name,
                double r);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*r*

A positive Double specifying the *r* dimension (outer radius) of the circular profile. For more information, see ["Beam cross-section library," Section 29.3.9 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamcrosssectlib).

**Optional arguments**

None.

**Return value**

A CircularProfile object.

**Exceptions**

RangeError.

### 57.4.2 Members

The CircularProfile object has members with the same names and descriptions as the arguments to the [CircularProfile](pt02ch57pyo04.md#ker-circularprofile-circularprofile-cpp) method.

### 57.4.3 Corresponding analysis keywords

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=CIRC |
| --- |




