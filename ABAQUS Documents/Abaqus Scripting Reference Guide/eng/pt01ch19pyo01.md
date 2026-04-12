# 19.1 EngineeringFeature object







The EngineeringFeature object is a container for various specific engineering feature repositories. The EngineeringFeature object has no explicit constructor or methods.

**Access**

```
import part
mdb.models[*name*].parts[*name*].engineeringFeatures
import assembly
mdb.models[*name*].rootAssembly.engineeringFeatures
```

### 19.1.1 assignSeam(...)

This method creates a seam crack along an edge or a face.

**Required argument**

*regions*

A sequence of [Region](pt01ch45pyo03.md) objects specifying the domain of the seam crack. The [Region](pt01ch45pyo03.md) objects must be faces or edges.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 19.1.2 deleteSeam(...)

This method deletes a seam crack.

**Required argument**

*regions*

A sequence of [Region](pt01ch45pyo03.md) objects specifying the domain of the seam crack. The [Region](pt01ch45pyo03.md) objects must be faces or edges.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 19.1.3 Members

The EngineeringFeature object can have the following members:

*inertias*

A repository of [Inertia](pt01ch19pyo09.md) objects.

*cracks*

A repository of [Crack](pt01ch19pyo04.md) objects.

*fasteners*

A repository of [Fastener](pt01ch19pyo07.md) objects.

*springDashpots*

A repository of [SpringDashpot](pt01ch19pyo13.md) objects.




