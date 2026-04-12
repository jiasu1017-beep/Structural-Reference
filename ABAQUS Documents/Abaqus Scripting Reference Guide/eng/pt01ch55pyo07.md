# 55.7 DefaultChartOptions object







The DefaultChartOptions object is used to hold on default chart and axis attributes. The DefaultChartOptions object attributes are used whenever Chart or Axis are created. A DefaultChartOptions object is automatically created when opening a session.

**Access**

```
import visualization
session.defaultChartOptions
```

### 55.7.1 setValues(...)

This method modifies the DefaultChartOptions object.

**Required arguments**

None.

**Optional arguments**

*areaStyle*

An [AreaStyle](pt01ch55pyo03.md) object specifying an [AreaStyle](pt01ch55pyo03.md) used to hold on to the default display properties for the chart area.

*aspectRatio*

A Float specifying the default aspect ratio of the grid area. A value of -1 specifies that the gridArea will take up all available space. The default value is 1.

*defaultAxis1Options*

An [Axis](pt01ch55pyo04.md) object specifying an [Axis](pt01ch55pyo04.md) object used to hold on to the default properties for direction 1 axes—the abscissa for a Cartesian chart.

*defaultAxis2Options*

An [Axis](pt01ch55pyo04.md) object specifying an [Axis](pt01ch55pyo04.md) object used to hold on to the default properties for direction 2 axes—the ordinate for a Cartesian chart.

*gridArea*

An [Area](pt01ch55pyo02.md) object specifying how to display the grid area by default.

*legend*

A [Legend](pt01ch55pyo09.md) object specifying  the default attributes for the legend of the chart.

*majorAxis1GridStyle*

A [LineStyle](pt01ch55pyo10.md) object specifying  the default line properties to be used when drawing major gridlines along axis 1.

*majorAxis2GridStyle*

A [LineStyle](pt01ch55pyo10.md) object specifying  the default line properties to be used when drawing major gridlines along axis 2.

*minorAxis1GridStyle*

A [LineStyle](pt01ch55pyo10.md) object specifying  the default line properties to be used when drawing minor gridlines along axis 1.

*minorAxis2GridStyle*

A [LineStyle](pt01ch55pyo10.md) object specifying  the default line properties to be used when drawing minor gridlines along axis 2.

*tagAreaStyle*

An [AreaStyle](pt01ch55pyo03.md) object specifying  the default area properties to be used when creating tags.

*tagBorder*

A [LineStyle](pt01ch55pyo10.md) object specifying  the default tag area border properties to be used when creating tags.

*tagTextStyle*

A [TextStyle](pt01ch55pyo13.md) object specifying  the default text properties to be used when creating tags.

*useQuantityType*

A Boolean specifying whether to use the [QuantityType](pt01ch55pyo11.md) to associate curves with axes. The default value is ON.

**Return value**

None

**Exceptions**

None.

### 55.7.2 Members

The DefaultChartOptions object has members with the same names and descriptions as the arguments to the [setValues](pt01ch55pyo07.md#ker-defaultchartoptions-setvalues-pyc) method.




