# 19.9 Inertia object







The Inertia object is the abstract base type for [HeatCapacitance](pt01ch19pyo08.md), [NonstructuralMass](pt01ch19pyo10.md), and [PointMassInertia](pt01ch19pyo12.md).

**Access**

```
import part
mdb.models[*name*].parts[*name*].engineeringFeatures.inertias[*name*]
import assembly
mdb.models[*name*].rootAssembly.engineeringFeatures.inertias[*name*]
```

### 19.9.1 resume()

This method resumes the inertia that was previously suppressed.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 19.9.2 suppress()

This method suppresses the inertia.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 19.9.3 Members

The Inertia object has the following members:

*name*

A String specifying the repository key.

*suppressed*

A Boolean specifying whether the inertia is suppressed or not. The default value is OFF.




