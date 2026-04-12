# 17.18 SymbolDisplayOptions object







The SymbolDisplayOptions object stores settings that specify how the assembly is displayed in a particular viewport. The SymbolDisplayOptions object has no constructor. When you create a new viewport, the settings are copied from the current viewport.

**Access**

```
session.viewports[*name*].assemblyDisplay.symbolOptions
session.viewports[*name*].layers[*name*].assemblyDisplay.symbolOptions
```

### 17.18.1 setValues(...)

This method modifies the SymbolDisplayOptions object.

**Required arguments**

None.

**Optional arguments**

*otherSymbolSize*

An Int specifying the size of the scalar attribute symbols. Possible values are 1 ![](../graphics/ker_eqn00013.gif) *scalarSymbolSize* ![](../graphics/ker_eqn00013.gif) 30. The default value is 6.

*arrowSymbolSize*

An Int specifying the size of the vector and tensor attribute symbols. Possible values are 1 ![](../graphics/ker_eqn00013.gif) *vectorSymbolSize* ![](../graphics/ker_eqn00013.gif) 30. The default value is 6.

*faceSymbolDensity*

An Int specifying the relative density of the attribute symbols drawn on geometric faces. Possible values are 1 ![](../graphics/ker_eqn00013.gif) *faceSymbolDensity* ![](../graphics/ker_eqn00013.gif) 10. The default value is 5.

*edgeSymbolDensity*

An Int specifying the relative density of the attribute symbols drawn on geometric edges. Possible values are 1 ![](../graphics/ker_eqn00013.gif) *edgeSymbolDensity* ![](../graphics/ker_eqn00013.gif) 10. The default value is 5.

*meshSymbolFraction*

A Float specifying the fraction of the attribute symbols drawn on orphan mesh regions. Possible values are 0.0 ![](../graphics/ker_eqn00013.gif) *meshSymbolFraction* ![](../graphics/ker_eqn00013.gif) 1.0. The default value is 1.0.

*showFields*

A Boolean specifying whether symbols should be scaled based on analytical field value. The default value is ON.

**Return value**

None

**Exceptions**

None.

### 17.18.2 Members

The SymbolDisplayOptions object has members with the same names and descriptions as the arguments to the [setValues](pt01ch17pyo18.md#ker-symboldisplayoptions-setvalues-pyc) method.




