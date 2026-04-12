# 15.5 DatumPoint object







The DatumPoint object has no direct constructor; it is created when a [Feature](pt01ch20pyo01.md) object is created. For example, the `DatumPointByCoordinate` method creates a Feature object that creates a DatumPoint object.

The DatumPoint object is derived from the [Datum](pt01ch15pyo01.md) object.

**Access**

```
import part
mdb.models[*name*].parts[*name*].datums[*i*]
import assembly
mdb.models[*name*].rootAssembly.allinstances.datums[*i*]
mdb.models[*name*].rootAssembly.datums[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].datums[*i*]
```

### 15.5.1 Members

The DatumPoint object has the following member:

*pointOn*

A tuple of Floats specifying the *X*-, *Y*-, and *Z*-coordinates of a point located on the datum.




