# 57.9 PipeProfile object







The PipeProfile object defines the properties of a circular pipe profile.

The PipeProfile object is derived from the [Profile](pt02ch57pyo01.md) object.

**Access**

```
sectionApi.profiles()[*name*]
```

### 57.9.1 PipeProfile(...)

This method creates a PipeProfile object.

**Path**

```
sectionApi.PipeProfile
```

**Prototype**

```
odb_PipeProfile&
PipeProfile(const odb_String& name,
            double r,
            double t,
            const odb_String& formulation);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*r*

A Double specifying the outer radius of the pipe. For more information, see ["Beam cross-section library," Section 29.3.9 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamcrosssectlib).

*t*

A Double specifying the wall thickness of the pipe.

**Optional argument**

*formulation*

An odb_String specifying                       the formulation. Possible values are "THIN_WALL" and "THICK_WALL". The default value is "THIN_WALL".

**Return value**

A PipeProfile object.

**Exceptions**

RangeError.

### 57.9.2 Members

The PipeProfile object has members with the same names and descriptions as the arguments to the [PipeProfile](pt02ch57pyo09.md#ker-pipeprofile-pipeprofile-cpp) method.

### 57.9.3 Corresponding analysis keywords

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=PIPE |
| --- |

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=THICK PIPE |
| --- |




