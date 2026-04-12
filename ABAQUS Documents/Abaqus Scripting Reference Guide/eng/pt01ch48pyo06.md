# 48.6 ConstrainedSketchGeometryArray object







The ConstrainedSketchGeometryArray               is a sequence of [ConstrainedSketchGeometry](pt01ch48pyo05.md)               objects.

**Access**

```
import sketch
mdb.models[*name*].sketches[*name*].geometry[*i*]
```

### 48.6.1 findAt(...)

This method returns the [ConstrainedSketchGeometry](pt01ch48pyo05.md)                     object located at the given coordinates.

**Required argument**

*coordinates*

A sequence of Floats specifying the *X*- and *Y*-coordinates of the object to find.

**Optional argument**

*printWarning*

A Boolean specifying whether a message is to be printed to the CLI if no entity is found at the specified location. The default value is True.

**Return value**

A [ConstrainedSketchGeometry](pt01ch48pyo05.md)                     object.

**Exceptions**

None.

### 48.6.2 Members

The ConstrainedSketchGeometryArray object has no members.




