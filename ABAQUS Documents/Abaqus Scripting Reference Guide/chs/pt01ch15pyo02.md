# 15.2 DatumAxis object







The DatumAxis object has no direct constructor; it is created when a [Feature](pt01ch20pyo01.md) object is created. For example, the `DatumAxisByCylFace` method creates a Feature object that creates a DatumAxis object. 

The DatumAxis object is derived from the [Datum](pt01ch15pyo01.md) object.

**Access**

```
import part
mdb.models[*name*].parts[*name*].datums[*i*]
import assembly
mdb.models[*name*].rootAssembly.allinstances.datums[*i*]
mdb.models[*name*].rootAssembly.datums[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].datums[*i*]
```

### 15.2.1 Members

The DatumAxis object has the following members:

*pointOn*

A tuple of Floats specifying the *X*-, *Y*-, and *Z*-coordinates of a point located on the datum.

*direction*

A tuple of Floats specifying a sequence of three Floats specifying the direction of the axis.




