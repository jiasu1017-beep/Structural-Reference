# 19.13 SpringDashpot object







The SpringDashpot object is the abstract base type for the [SpringDashpotToGround](pt01ch19pyo14.md) and [TwoPointSpringDashpot](pt01ch19pyo15.md) objects.

**Access**

```
import part
mdb.models[*name*].parts[*name*].engineeringFeatures.springDashpots[*name*]
import assembly
mdb.models[*name*].rootAssembly.engineeringFeatures.springDashpots[*name*]
```

### 19.13.1 resume()

This method resumes the spring/dashpot that was previously suppressed.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 19.13.2 suppress()

This method suppresses the spring/dashpot.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 19.13.3 Members

The SpringDashpot object has the following members:

*name*

A String specifying the repository key.

*suppressed*

A Boolean specifying whether the spring/dashpot is suppressed or not. The default value is OFF.




