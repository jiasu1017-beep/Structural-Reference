# 8.9 PipeProfile object







The PipeProfile object defines the properties of a circular pipe profile.

The PipeProfile object is derived from the [Profile](pt01ch08pyo01.md) object.

**Access**

```
import section
mdb.models[*name*].profiles[*name*]
import odbSection
session.odbs[*name*].profiles[*name*]
```

### 8.9.1 PipeProfile(...)

This method creates a PipeProfile object.

**Path**

```
mdb.models[*name*].PipeProfile
session.odbs[*name*].PipeProfile
```

**Required arguments**

*name*

A String specifying the repository key.

*r*

A Float specifying the outer radius of the pipe. For more information, see ["Beam cross-section library," Section 29.3.9 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamcrosssectlib).

*t*

A Float specifying the wall thickness of the pipe.

**Optional argument**

*formulation*

A SymbolicConstant specifying                       the formulation. Possible values are THIN_WALL and THICK_WALL. The default value is THIN_WALL.

**Return value**

A PipeProfile object.

**Exceptions**

RangeError.

### 8.9.2 setValues(...)

This method modifies the PipeProfile object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [PipeProfile](pt01ch08pyo09.md#ker-pipeprofile-pipeprofile-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 8.9.3 Members

The PipeProfile object has members with the same names and descriptions as the arguments to the [PipeProfile](pt01ch08pyo09.md#ker-pipeprofile-pipeprofile-pyc) method.

### 8.9.4 Corresponding analysis keywords

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=PIPE |
| --- |

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=THICK PIPE |
| --- |




