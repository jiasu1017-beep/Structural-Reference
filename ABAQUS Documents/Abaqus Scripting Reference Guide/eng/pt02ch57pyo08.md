# 57.8 LProfile object







The LProfile object defines the properties of a L profile.

The LProfile object is derived from the [Profile](pt02ch57pyo01.md) object.

**Access**

```
sectionApi.profiles()[*name*]
```

### 57.8.1 LProfile(...)

This method creates a LProfile object.

**Path**

```
sectionApi.LProfile
```

**Prototype**

```
odb_LProfile&
LProfile(const odb_String& name,
         double a,
         double b,
         double t1,
         double t2);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*a*

A positive Double specifying the *a* dimension (flange length) of the L profile. For more information, see ["Beam cross-section library," Section 29.3.9 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamcrosssectlib).

*b*

A positive Double specifying the *b* dimension (flange length) of the L profile.

*t1*

A positive Double specifying the *t1* dimension (flange thickness) of the L profile (*t1 < b*).

*t2*

A positive Double specifying the *t2* dimension (flange thickness) of the L profile (*t2< a*).

**Optional arguments**

None.

**Return value**

A LProfile object.

**Exceptions**

RangeError.

### 57.8.2 Members

The LProfile object has members with the same names and descriptions as the arguments to the [LProfile](pt02ch57pyo08.md#ker-lprofile-lprofile-cpp) method.

### 57.8.3 Corresponding analysis keywords

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=L |
| --- |




