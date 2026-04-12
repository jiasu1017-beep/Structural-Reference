# 48.9 ConstrainedSketchParameter object







The ConstrainedSketchParameter               object stores the definition of a parameter in the sketch.

**Access**

```
import sketch
mdb.models[*name*].sketches[*name*].parameters[*i*]
```

### 48.9.1 Parameter(...)

This method creates a parameter and optionally associates a dimension with this parameter.

**Path**

```
mdb.models[*name*].sketches[*name*].Parameter
```

**Required argument**

*name*

A String specifying the name of the ConstrainedSketchParameter                              object. No two parameters in the same [ConstrainedSketch](pt01ch48pyo01.md)                              can have the same name.

**Optional arguments**

*path*

A String specifying the [ConstrainedSketchDimension](pt01ch48pyo03.md)                              object with which this parameter is associated.

*expression*

A String specifying the expression or value associated with the ConstrainedSketchParameter.

*previousParameter*

A String specifying the name of the previous ConstrainedSketchParameter, if it exists. The *previousParameter*                              argument implies an order among the parameters. No two parameters can reference the same parameter as the previous parameter.

**Return value**

A ConstrainedSketchParameter object.

**Exceptions**

None.

### 48.9.2 Members

The ConstrainedSketchParameter object has the following members:

*name*

A String specifying the name of the ConstrainedSketchParameter                  object.

*path*

A String specifying the path to the [ConstrainedSketchDimension](pt01ch48pyo03.md)                     that depends on this ConstrainedSketchParameter.

*expression*

A String specifying an expression or value associated with this ConstrainedSketchParameter.

*previousParameter*

A String specifying the name of the ConstrainedSketchParameter                     that appears before this one in the ordered list.




