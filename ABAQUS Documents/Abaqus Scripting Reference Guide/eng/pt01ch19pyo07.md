# 19.7 Fastener object







The Fastener object is the abstract base type for [PointFastener](pt01ch19pyo11.md), [DiscreteFastener](pt01ch19pyo06.md), and [AssembledFastener](pt01ch19pyo02.md).

**Access**

```
import part
mdb.models[*name*].parts[*name*].engineeringFeatures.fasteners[*name*]
import assembly
mdb.models[*name*].rootAssembly.engineeringFeatures.fasteners[*name*]
```

### 19.7.1 resume()

This method resumes the fastener that was previously suppressed.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 19.7.2 suppress()

This method suppresses the fastener.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 19.7.3 Members

The Fastener object has the following members:

*name*

A String specifying the repository key.

*suppressed*

A Boolean specifying whether the fastener is suppressed or not. The default value is OFF.




