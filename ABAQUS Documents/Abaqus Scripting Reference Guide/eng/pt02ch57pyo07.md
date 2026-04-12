# 57.7 IProfile object







The IProfile object defines the properties of an I profile.

The IProfile object is derived from the [Profile](pt02ch57pyo01.md) object.

**Access**

```
sectionApi.profiles()[*name*]
```

### 57.7.1 IProfile(...)

This method creates an IProfile object.

**Path**

```
sectionApi.IProfile
```

**Prototype**

```
odb_IProfile&
IProfile(const odb_String& name,
         double l,
         double h,
         double b1,
         double b2,
         double t1,
         double t2,
         double t3);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*l*

A Double specifying the *l* dimension (offset of 1–axis from the bottom flange surface) of the I profile. For more information, see ["Beam cross-section library," Section 29.3.9 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamcrosssectlib).

*h*

A Double specifying the *h* dimension (height) of the I profile.

*b1*

A Double specifying the *b1* dimension (bottom flange width) of the I profile.

*b2*

A Double specifying the *b2* dimension (top flange width) of the I profile.

*t1*

A Double specifying the *t1* dimension (bottom flange thickness) of the I profile.

*t2*

A Double specifying the *t2* dimension (top flange thickness) of the I profile.

*t3*

A Double specifying the *t3* dimension (web thickness) of the I profile.

**Optional arguments**

None.

**Return value**

An IProfile object.

**Exceptions**

RangeError.

### 57.7.2 Members

The IProfile object has members with the same names and descriptions as the arguments to the [IProfile](pt02ch57pyo07.md#ker-iprofile-iprofile-cpp) method.

### 57.7.3 Corresponding analysis keywords

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=I |
| --- |




