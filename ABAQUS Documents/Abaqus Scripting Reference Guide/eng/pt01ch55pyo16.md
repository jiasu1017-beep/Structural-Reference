# 55.16 XYPlot object







The XYPlot object is used to display [Chart](pt01ch55pyo06.md) objects.

**Access**

```
import visualization
session.xyPlots[*name*]
```

### 55.16.1 XYPlot(...)

This method creates an empty XYPlot object.

**Path**

```
session.XYPlot
```

**Required argument**

*name*

A String specifying the name of the XYPlot object.

**Optional arguments**

None.

**Return value**

An XYPlot object.

**Exceptions**

InvalidNameError.

### 55.16.2 autoColor(...)

This method distributes the colors on all curves displayed in the XYPlot using the color palette defined by the xyColors [AutoColors](pt01ch47pyo02.md) object.

**Required arguments**

None.

**Optional arguments**

*lines*

A Boolean defining whether color distribution affects curve lines.

*symbols*

A Boolean defining whether color distribution affects curve symbols.

**Return value**

None

**Exceptions**

None.

### 55.16.3 autoSymbol()

This method distributes the symbols on all curves displayed in the XYPlot.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 55.16.4 fitCurves()

This method resets the transform of all the charts of the XYPlot object. It cancels any zoom or pan action.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 55.16.5 next(...)

This method restores the *transform* member of the active [Chart](pt01ch55pyo06.md) object to the next setting in the transform list. (There is a list of eight transforms stored for each chart.) If there is no next transform, no action is taken. 

**Required arguments**

None.

**Optional argument**

*drawImmediately*

A Boolean specifying the viewport should refresh immediately after the command is processed. This is typically only used when writing a script and it is desirable to show intermediate results before the script completes. The default value is False.

**Return value**

None

**Exceptions**

None.

### 55.16.6 previous(...)

This method restores the *transform* member of the active [Chart](pt01ch55pyo06.md) object to the previous setting in the transform list. (There is a list of eight transforms stored for each chart.) If there is no next transform, no action is taken. 

**Required arguments**

None.

**Optional argument**

*drawImmediately*

A Boolean specifying the viewport should refresh immediately after the command is processed. This is typically only used when writing a script and it is desirable to show intermediate results before the script completes. The default value is False.

**Return value**

None

**Exceptions**

None.

### 55.16.7 setValues(...)

This method modifies the XYPlot object.

**Required arguments**

None.

**Optional arguments**

*title*

A [Title](pt01ch55pyo14.md) object specifying the title of the XYPlot object.

*transform*

A sequence of Floats specifying a transformation matrix used to scale or pan along the axes of the active [Chart](pt01ch55pyo06.md) object of this XYPlot.

**Return value**

None

**Exceptions**

None.

### 55.16.8 Members

The XYPlot object has members with the same names and descriptions as the arguments to the [XYPlot](pt01ch55pyo16.md#ker-xyplot-xyplot-pyc) method.

In addition, the XYPlot object can have the following members:

*area*

An [Area](pt01ch55pyo02.md) object specifying  position, padding, background and borders of the XYPlot object.

*title*

A [Title](pt01ch55pyo14.md) object specifying the title of the XYPlot object.

*charts*

A repository of [Chart](pt01ch55pyo06.md) objects.

*curves*

A repository of [XYCurve](pt01ch55pyo15.md) objects.

*transform*

A tuple of Floats specifying a transformation matrix used to scale or pan along the axes of the active [Chart](pt01ch55pyo06.md) object of this XYPlot.




