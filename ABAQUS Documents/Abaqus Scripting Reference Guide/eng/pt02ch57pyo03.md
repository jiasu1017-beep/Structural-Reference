# 57.3 BoxProfile object







The BoxProfile object defines the properties of a box profile.

The BoxProfile object is derived from the [Profile](pt02ch57pyo01.md) object.

**Access**

```
sectionApi.profiles()[*name*]
```

### 57.3.1 BoxProfile(...)

This method creates a BoxProfile object.

**Path**

```
sectionApi.BoxProfile
```

**Prototype**

```
odb_BoxProfile&
BoxProfile(const odb_String& name,
           double a,
           double b,
           bool uniformThickness,
           double t1,
           double t2,
           double t3,
           double t4);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*a*

A Double specifying the *a* dimension of the box profile. For more information, see ["Beam cross-section library," Section 29.3.9 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamcrosssectlib).

*b*

A Double specifying the *b* dimension of the box profile.

*uniformThickness*

A Boolean specifying whether the thickness is uniform.

*t1*

A Double specifying the uniform wall thickness if *uniformThickness*=true, and the wall thickness of the first segment if *uniformThickness*=false.

**Optional arguments**

*t2*

A Double specifying the wall thickness of the second segment. *t2* is required only when *uniformThickness*=false. The default value is 0.0.

*t3*

A Double specifying the wall thickness of the third segment. *t3* is required only when *uniformThickness*=false. The default value is 0.0.

*t4*

A Double specifying the wall thickness of the fourth segment. *t4* is required only when *uniformThickness*=false. The default value is 0.0.

**Return value**

A BoxProfile object.

**Exceptions**

RangeError.

### 57.3.2 Members

The BoxProfile object has members with the same names and descriptions as the arguments to the [BoxProfile](pt02ch57pyo03.md#ker-boxprofile-boxprofile-cpp) method.

### 57.3.3 Corresponding analysis keywords

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=BOX |
| --- |




