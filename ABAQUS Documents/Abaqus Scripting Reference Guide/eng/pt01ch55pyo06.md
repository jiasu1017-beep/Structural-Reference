# 55.6 Chart object







The Chart object is used to display [XYCurve](pt01ch55pyo15.md) objects. A Chart object is automatically created when creating an [XYPlot](pt01ch55pyo16.md) object

**Access**

```
import visualization
session.charts[*name*]
session.xyPlots[*name*].charts[*name*]
```

### 55.6.1 autoColor(...)

This method distributes the colors on all curves displayed in the chart using the color palette defined by the xyColors object.

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

### 55.6.2 autoSymbol()

This method distributes the symbols on all curves displayed in the chart.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 55.6.3 fitCurves()

This method resets the transform of the chart. It cancels any zoom or pan action.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 55.6.4 getAxis1(...)

This method returns the [Axis](pt01ch55pyo04.md) object used for displaying the Axis1 of the [XYCurve](pt01ch55pyo15.md) specified by name or object or used for the given [QuantityType](pt01ch55pyo11.md) object.

**Required arguments**

*curve*

The name or the [XYCurve](pt01ch55pyo15.md) object associated to the [Axis](pt01ch55pyo04.md) object.

*quantityType*

The [QuantityType](pt01ch55pyo11.md) object associated to the [Axis](pt01ch55pyo04.md) object.

**Optional arguments**

None.

**Return value**

An [Axis](pt01ch55pyo04.md) object.

**Exceptions**

If the given [XYCurve](pt01ch55pyo15.md) is not used in the Chart.

XypError: Curve not found:

If both arguments are specified.

```
TypeError: Specify curve or quantityType; too many arguments; expected 1, got 2.
```

If the given [QuantityType](pt01ch55pyo11.md) is not used in the Chart.

```
ValueError: QuantityType not found
```

### 55.6.5 getAxis2(...)

This method returns the [Axis](pt01ch55pyo04.md) object used for displaying the Axis2 of the [XYCurve](pt01ch55pyo15.md) specified by name or object or used for the given [QuantityType](pt01ch55pyo11.md) object.

**Required arguments**

*curve*

The name or the [XYCurve](pt01ch55pyo15.md) object associated to the [Axis](pt01ch55pyo04.md) object.

*quantityType*

The [QuantityType](pt01ch55pyo11.md) object associated to the [Axis](pt01ch55pyo04.md) object.

**Optional arguments**

None.

**Return value**

An [Axis](pt01ch55pyo04.md) object.

**Exceptions**

If the given [XYCurve](pt01ch55pyo15.md) is not used in the Chart.

XypError: Curve not found:

If both arguments are specified.

```
TypeError: Specify curve or quantityType; too many arguments; expected 1, got 2.
```

If the given [QuantityType](pt01ch55pyo11.md) is not used in the Chart.

```
ValueError: QuantityType not found
```

### 55.6.6 moveAxisUp(...)

This method moves the relative position of the given [Axis](pt01ch55pyo04.md) object up in the axis sequence of the Chart.

**Required argument**

*axis*

The [Axis](pt01ch55pyo04.md) object to be moved.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 55.6.7 moveAxisDown(...)

This method moves the relative position of the given [Axis](pt01ch55pyo04.md) object down in the axis sequence of the Chart.

**Required argument**

*axis*

The [Axis](pt01ch55pyo04.md) object to be moved.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 55.6.8 removeCurve(...)

This method removes the given [XYCurve](pt01ch55pyo15.md) from the Chart.

**Required argument**

*curve*

The XYCurve name or the [XYCurve](pt01ch55pyo15.md) object or a sequence of XYCurve names or [XYCurve](pt01ch55pyo15.md) objects to be removed from the Chart.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 55.6.9 setValues(...)

This method modifies the Chart object.

**Required arguments**

None.

**Optional arguments**

*chart*

A Chart object from which attributes are to be copied.

*curvesToPlot*

A sequence of Strings specifying the names of the curves to plot. In addition to this type, the argument can also be one of the following:
- A String specifying the name of the curve to plot.
- An [XYCurve](pt01ch55pyo15.md) object specifying the curve to plot.
- A sequence of [XYCurve](pt01ch55pyo15.md) objects specifying the curves to plot (as returned by the `curveSet` method).

*aspectRatio*

A Float specifying the aspect ratio of the grid area. A value of -1 specifies that the gridArea will take up all available space. The default value is 1.

*transform*

A sequence of Floats specifying a transformation matrix used to scale or pan along the axes of the Chart.

*view*

A [View](pt01ch54pyo01.md) object.

*useQuantityType*

A Boolean specifying whether to use the [QuantityType](pt01ch55pyo11.md) to associate curves with axes. The default value is ON.

**Return value**

None

**Exceptions**

RangeError.

### 55.6.10 Members

The Chart object can have the following members:

*name*

A String specifying the name of the Chart object.

*useQuantityType*

A Boolean specifying whether to use the [QuantityType](pt01ch55pyo11.md) to associate curves with axes. The default value is ON.

*aspectRatio*

A Float specifying the aspect ratio of the grid area. A value of -1 specifies that the gridArea will take up all available space. The default value is 1.

*curves*

A repository of [XYCurve](pt01ch55pyo15.md) objects specifying a repository of [XYCurve](pt01ch55pyo15.md) objects to display in the Chart.

*axes1*

An [AxisArray](pt01ch55pyo04.md) object specifying a read-only sequence of axis objects displayed as axes1 - the abscissa for a Cartesian chart.

*axes2*

An [AxisArray](pt01ch55pyo04.md) object specifying a read-only sequence of axis objects displayed as axes2 - the ordinate for a Cartesian chart.

*area*

An [Area](pt01ch55pyo02.md) object specifying  position, padding, background and borders of the chart.

*gridArea*

An [Area](pt01ch55pyo02.md) object specifying how to display the grid area.

*legend*

A [Legend](pt01ch55pyo09.md) object specifying  the attributes for the legend of the chart.

*majorAxis1GridStyle*

A [LineStyle](pt01ch55pyo10.md) object specifying  the line properties to be used when drawing major gridlines along axis 1.

*majorAxis2GridStyle*

A [LineStyle](pt01ch55pyo10.md) object specifying  the line properties to be used when drawing major gridlines along axis 2.

*minorAxis1GridStyle*

A [LineStyle](pt01ch55pyo10.md) object specifying  the line properties to be used when drawing minor gridlines along axis 1.

*minorAxis2GridStyle*

A [LineStyle](pt01ch55pyo10.md) object specifying  the line properties to be used when drawing minor gridlines along axis 2.

*tagTextStyle*

A [TextStyle](pt01ch55pyo13.md) object specifying  the text properties to be used when creating tags.

*tagAreaStyle*

An [AreaStyle](pt01ch55pyo03.md) object specifying  the area properties to be used when creating tags.

*tagBorder*

A [LineStyle](pt01ch55pyo10.md) object specifying  the tag area border properties to be used when creating tags.

*transform*

A tuple of Floats specifying a transformation matrix used to scale or pan along the axes of the Chart.




