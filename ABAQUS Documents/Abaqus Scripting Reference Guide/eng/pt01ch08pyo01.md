# 8.1 Profile object







The Profile object defines the geometrical properties of a beam cross-section. Profile is an abstract base type.

**Access**

```
import section
mdb.models[*name*].profiles[*name*]
import odbSection
session.odbs[*name*].profiles[*name*]
```

### 8.1.1 beamProfilesFromOdb(...)

This method creates Profile objects by reading an output database. The new profiles are placed in the `profiles` repository.

**Path**

```
mdb.models[*name*].beamProfilesFromOdb
```

**Required argument**

*fileName*

A String specifying the name of the output database file (including the `.odb` extension) to be read. The String can also be the full path to the output database file if it is located in another directory.

**Optional arguments**

None.

**Return value**

A list of Profile objects.

**Exceptions**

None.

### 8.1.2 Members

The Profile object has the following member:

*name*

A String specifying the repository key.




