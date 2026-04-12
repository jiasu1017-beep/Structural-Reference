# 55.14 Title object







The Title object is used to store the display attributes of the XYPlot title. An Title object is automatically created when creating a [XYPlot](pt01ch55pyo16.md) object.

**Access**

```
import visualization
session.defaultPlot.title
session.xyPlots[*name*].title
```

### 55.14.1 setValues(...)

This method modifies the Title object.

**Required arguments**

None.

**Optional arguments**

*title*

A Title object from which attributes are to be copied.

*text*

A String specifying  the text to appear as a title. By default the title is set to the [XYPlot](pt01ch55pyo16.md) object name. The default value is an empty string.

*area*

An [Area](pt01ch55pyo02.md) object specifying the area of the title.

*useDefault*

A Boolean specifying whether to show the default title. The default value is OFF.

*titleStyle*

A [TextStyle](pt01ch55pyo13.md) object specifying  the text properties used to display the legend title.

**Return value**

None

**Exceptions**

None.

### 55.14.2 Members

The Title object can have the following members:

*useDefault*

A Boolean specifying whether to show the default title. The default value is OFF.

*area*

An [Area](pt01ch55pyo02.md) object specifying the area of the title.

*text*

A String specifying  the text to appear as a title. By default the title is set to the [XYPlot](pt01ch55pyo16.md) object name. The default value is an empty string.

*titleStyle*

A [TextStyle](pt01ch55pyo13.md) object specifying  the text properties used to display the legend title.




