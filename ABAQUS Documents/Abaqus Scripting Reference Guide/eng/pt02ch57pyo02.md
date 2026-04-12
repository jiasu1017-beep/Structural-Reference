# 57.2 ArbitraryProfile object







The ArbitraryProfile object defines the properties of an arbitrary profile.

The ArbitraryProfile object is derived from the [Profile](pt02ch57pyo01.md) object.

**Access**

```
sectionApi.profiles()[*name*]
```

### 57.2.1 ArbitraryProfile(...)

This method creates a ArbitraryProfile object.

**Path**

```
sectionApi.ArbitraryProfile
```

**Prototype**

```
odb_ArbitraryProfile&
ArbitraryProfile(const odb_String& name,
                 const odb_SequenceSequenceDouble& table);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*table*

An odb_SequenceSequenceDouble specifying the items described below.

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

### 57.2.2 Members

The ArbitraryProfile object has members with the same names and descriptions as the arguments to the [ArbitraryProfile](pt02ch57pyo02.md#ker-arbitraryprofile-arbitraryprofile-cpp) method.

### 57.2.3 Corresponding analysis keywords

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=ARBITRARY |
| --- |




