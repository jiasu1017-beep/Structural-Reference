# 57.11 TProfile object







The TProfile object defines the properties of a T profile.

The TProfile object is derived from the [Profile](pt02ch57pyo01.md) object.

**Access**

```
sectionApi.profiles()[*name*]
```

### 57.11.1 TProfile(...)

This method creates a TProfile object.

**Path**

```
sectionApi.TProfile
```

**Prototype**

```
odb_TProfile&
TProfile(const odb_String& name,
         double b,
         double h,
         double l,
         double tf,
         double tw);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*b*

A positive Double specifying the *b* dimension (flange width) of the T profile. For more information, see ["Beam cross-section library," Section 29.3.9 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamcrosssectlib).

*h*

A positive Double specifying the *h* dimension (height) of the T profile.

*l*

A positive Double specifying the *l* dimension (offset of 1–axis from the edge of web) of the T profile.

*tf*

A positive Double specifying the *tf* dimension (flange thickness) of the T profile (*tf < h*).

*tw*

A positive Double specifying the *tw* dimension (web thickness) of the T profile (*tw< b*).

**Optional arguments**

None.

**Return value**

A TProfile object.

**Exceptions**

RangeError.

### 57.11.2 Members

The TProfile object has members with the same names and descriptions as the arguments to the [TProfile](pt02ch57pyo11.md#ker-tprofile-tprofile-cpp) method.

### 57.11.3 Corresponding analysis keywords

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=I |
| --- |




