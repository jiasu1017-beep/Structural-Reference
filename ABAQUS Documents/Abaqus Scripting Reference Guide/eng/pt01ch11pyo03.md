# 11.3 Layer object







Objects can be superimposed by displaying them in different layers of a viewport.

**Access**

```
session.viewports[*name*].layers[*name*]
```

### 11.3.1 Layer(...)

This method creates a Layer object in the Layer repository.

**Path**

```
session.viewports[*name*].Layer
```

**Required argument**

*name*

A String specifying the repository key.

**Optional argument**

*copyViewName*

A String specifying the name of the layer to copy.

**Return value**

A Layer object.

**Exceptions**

None.

### 11.3.2 moveBefore(...)

This method moves the layer object before another object in the layer repository.

**Required argument**

*name*

A String specifying the name of the other Layer object.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 11.3.3 moveAfter(...)

This method moves the layer object after another object in the layer repository.

**Required argument**

*name*

A String specifying the name of the other Layer object.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 11.3.4 Members

The Layer object has members with the same names and descriptions as the arguments to the [Layer](pt01ch11pyo03.md#ker-layer-layer-pyc) method.

In addition, the Layer object can have the following members:

*displayedObject*

A [Displayable](#ker-displayable-pyc) object specifying the object to be displayed. The [Displayable](#ker-displayable-pyc)                       type is an abstract generalization. The concrete possible types are [Part](pt01ch37pyo01.md)                     , [Assembly](pt01ch06pyo01.md)                     , [ConstrainedSketch](pt01ch48pyo01.md)                     , [Odb](pt01ch34pyo01.md)                     , or [XYPlot](pt01ch55pyo16.md)                     .

*view*

A [View](pt01ch54pyo01.md) object specifying the object that controls viewing of the layer.

*odbDisplay*

An [OdbDisplay](pt01ch35pyo01.md) object specifying the display options for the [Odb](pt01ch34pyo01.md)                       object.

*partDisplay*

A [PartDisplayOptions](pt01ch17pyo16.md) object specifying the display options for the [Part](pt01ch37pyo01.md)                       object.

*assemblyDisplay*

An [AssemblyDisplayOptions](pt01ch17pyo01.md) object specifying the display options for the [Assembly](pt01ch06pyo01.md)                       object.




