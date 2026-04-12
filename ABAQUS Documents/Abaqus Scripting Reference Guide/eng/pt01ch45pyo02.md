# 45.2 Part object







The following commands operate on Part objects. For more information about the Part object, see ["Part object," Section 37.1](pt01ch37pyo01.md).

**Access**

```
import regionToolset
```

### 45.2.1 clashSets(...)

This command prints a message describing the relationship between the contents of two sets. Possible outcomes are: 
- Both sets are the same.
- Set 2 is a subset of set 1.
- Set 2 is a superset of set 1.
- Set 2 intersects set 1.
- Set 2 touches set 1 (their boundaries intersect).
- Set 2 and set 1 are disjoint.

This command accepts only positional arguments and has no keywords.

**Required arguments**

*arg1*

A Set or Surface object specifying set 1.

*arg2*

A Set or Surface object specifying set 2.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 45.2.2 markSetInternal(...)

This command marks the given Set as internal or external.

**Required arguments**

*setName*

A string specifying the Set name.

*internalSet*

A Boolean specifying whether the Set should be marked as internal.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 45.2.3 markSurfaceInternal(...)

This command marks the given Surface as internal or external.

**Required arguments**

*setName*

A string specifying the Surface name.

*internalSurface*

A Boolean specifying whether the Surface should be marked as internal.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 45.2.4 isSetInternal(...)

This command returns a flag indicating whether the Set is Internal.

**Required argument**

*setName*

A string specifying the Set name.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 45.2.5 isSurfaceInternal(...)

This command returns a flag indicating whether the Surface is Internal.

**Required argument**

*surfaceName*

A string specifying the Surface name.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 45.2.6 deleteSets(...)

This command deletes the given sets from the part.

**Required argument**

*setNames*

A sequence of Strings specifying the set names that will be deleted from the part.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 45.2.7 deleteSurfaces(...)

This command deletes the given surfaces from the part.

**Required argument**

*surfaceNames*

A sequence of Strings specifying the surface names that will be deleted from the part.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.



