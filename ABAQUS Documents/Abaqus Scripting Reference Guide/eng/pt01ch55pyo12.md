# 55.12 SymbolStyle object







The SymbolStyle object is used to define the marker properties to be used when drawing curves.

 SymbolStyle objects can be created using the methods described below. 

**Access**

```
import visualization
session.charts[*name*].axes1[*i*].axisData.curves[*i*].symbolStyle
session.charts[*name*].axes2[*i*].axisData.curves[*i*].symbolStyle
session.charts[*name*].curves[*name*].symbolStyle
session.curves[*name*].symbolStyle
session.defaultChartOptions.defaultAxis1Options.axisData.curves[*i*]\
.symbolStyle
session.defaultChartOptions.defaultAxis2Options.axisData.curves[*i*]\
.symbolStyle
session.xyPlots[*name*].charts[*name*].axes1[*i*].axisData.curves[*i*]\
.symbolStyle
session.xyPlots[*name*].charts[*name*].axes2[*i*].axisData.curves[*i*]\
.symbolStyle
session.xyPlots[*name*].charts[*name*].curves[*name*].symbolStyle
session.xyPlots[*name*].curves[*name*].symbolStyle
```

### 55.12.1 SymbolStyle(...)

This method creates a SymbolStyle object.

**Path**

```
session.SymbolStyle
```

```
xyPlot.SymbolStyle
```

**Required arguments**

None.

**Optional arguments**

*color*

A String specifying the color to be used when drawing a marker with this SymbolStyle object. The default value is "White".

*show*

A Boolean specifying whether to draw the marker when using this SymbolStyle object. The default value is ON.

*marker*

A SymbolicConstant specifying the marker type be used when drawing symbols using this SymbolStyle object. Possible values are:
- FILLED_CIRCLE
- FILLED_SQUARE
- FILLED_DIAMOND
- FILLED_TRI
- HOLLOW_CIRCLE
- HOLLOW_SQUARE
- HOLLOW_DIAMOND
- HOLLOW_TRI
- CROSS
- XMARKER
- POINT

The default value is FILLED_CIRCLE.

*size*

A Float specifying the marker size to be used when drawing markers using this SymbolStyle object. The default value is 2.0.

**Return value**

A SymbolStyle object.

**Exceptions**

ColorError

### 55.12.2 setValues(...)

This method modifies the SymbolStyle object.

**Required arguments**

None.

**Optional arguments**

*color*

A String specifying the color to be used when drawing a marker with this SymbolStyle object. The default value is "White".

*show*

A Boolean specifying whether to draw the marker when using this SymbolStyle object. The default value is ON.

*marker*

A SymbolicConstant specifying the marker type be used when drawing symbols using this SymbolStyle object. Possible values are:
- FILLED_CIRCLE
- FILLED_SQUARE
- FILLED_DIAMOND
- FILLED_TRI
- HOLLOW_CIRCLE
- HOLLOW_SQUARE
- HOLLOW_DIAMOND
- HOLLOW_TRI
- CROSS
- XMARKER
- POINT

The default value is FILLED_CIRCLE.

*size*

A Float specifying the marker size to be used when drawing markers using this SymbolStyle object. The default value is 2.0.

**Return value**

None

**Exceptions**

None.

### 55.12.3 Members

The SymbolStyle object has members with the same names and descriptions as the arguments to the [setValues](pt01ch55pyo12.md#ker-symbolstyle-setvalues-pyc) method.




