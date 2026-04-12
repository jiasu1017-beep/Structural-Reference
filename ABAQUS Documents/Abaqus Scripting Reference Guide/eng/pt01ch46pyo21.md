# 46.21 ShellSection object







The ShellSection object defines the properties of a shell section. The ShellSection object is derived from the [Section](pt01ch46pyo01.md) object. The ShellSection object has no explicit constructor and no methods or members.

The ShellSection object is derived from the [Section](pt01ch46pyo01.md) object.

**Access**

```
import section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.21.1 Members

The ShellSection object can have the following members:

*name*

A String specifying the repository key.

*transverseShear*

A [TransverseShearShell](pt01ch46pyo25.md) object specifying the transverse shear stiffness properties.




