# 8.2 ArbitraryProfile object







The ArbitraryProfile object defines the properties of an arbitrary profile.

The ArbitraryProfile object is derived from the [Profile](pt01ch08pyo01.md) object.

**Access**

```
import section
mdb.models[*name*].profiles[*name*]
import odbSection
session.odbs[*name*].profiles[*name*]
```

### 8.2.1 ArbitraryProfile(...)

This method creates a ArbitraryProfile object.

**Path**

```
mdb.models[*name*].ArbitraryProfile
session.odbs[*name*].ArbitraryProfile
```

**Required arguments**

*name*

A String specifying the repository key.

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

None.

**Table data**

The first sequence in the table specifies the following:
- 1-coordinate of the first point defining the profile.
- 2-coordinate of the first point defining the profile.

All other sequences in the table specify the following:- 1--coordinate of the next point defining the profile.
- 2--coordinate of the next point defining the profile.
- The thickness of the segment ending at that point.

**Return value**

An ArbitraryProfile object.

**Exceptions**

RangeError.

### 8.2.2 setValues(...)

This method modifies the ArbitraryProfile object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ArbitraryProfile](pt01ch08pyo02.md#ker-arbitraryprofile-arbitraryprofile-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 8.2.3 Members

The ArbitraryProfile object has members with the same names and descriptions as the arguments to the [ArbitraryProfile](pt01ch08pyo02.md#ker-arbitraryprofile-arbitraryprofile-pyc) method.

### 8.2.4 Corresponding analysis keywords

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=ARBITRARY |
| --- |




