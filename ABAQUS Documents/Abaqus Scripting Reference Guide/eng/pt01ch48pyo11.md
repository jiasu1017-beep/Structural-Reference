# 48.11 ConstrainedSketchVertexArray object







The ConstrainedSketchVertexArray               is a sequence of [ConstrainedSketchVertex](pt01ch48pyo10.md)               objects.

**Access**

```
import sketch
mdb.models[*name*].sketches[*name*].vertices[*i*]
```

### 48.11.1 findAt(...)

This method returns the [ConstrainedSketchVertex](pt01ch48pyo10.md)                     located at the given coordinates.

**Required argument**

*coordinates*

A sequence of Floats specifying the *X*- and *Y*-coordinates of the object to find.

**Optional argument**

*printWarning*

A Boolean specifying whether a message is to be printed to the CLI if no entity is found at the specified location. The default value is True.

**Return value**

A [ConstrainedSketchVertex](pt01ch48pyo10.md)                     object.

**Exceptions**

None.

### 48.11.2 Members

The ConstrainedSketchVertexArray object has no members.




