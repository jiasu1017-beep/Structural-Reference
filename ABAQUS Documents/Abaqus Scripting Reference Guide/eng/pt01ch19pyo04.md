# 19.4 Crack object







The Crack object is the abstract base type for [ContourIntegral](pt01ch19pyo03.md) and future crack objects.

**Access**

```
import part
mdb.models[*name*].parts[*name*].engineeringFeatures.cracks[*name*]
import assembly
mdb.models[*name*].rootAssembly.engineeringFeatures.cracks[*name*]
```

### 19.4.1 resume()

This method resumes the crack that was previously suppressed.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 19.4.2 suppress()

This method suppresses the crack.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 19.4.3 Members

The Crack object has the following members:

*name*

A String specifying the repository key.

*suppressed*

A Boolean specifying whether the crack is suppressed or not. The default value is OFF.




