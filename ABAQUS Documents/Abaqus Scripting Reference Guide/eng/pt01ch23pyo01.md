# 23.1 FieldReportOptions object







The FieldReportOptions object stores settings used by the `writeFieldReport` method when you write a [FieldOutput](pt01ch34pyo06.md) object to an ASCII file. The FieldReportOptions object has no constructor. Abaqus creates the *fieldReportOptions* member when you import the Visualization module.

**Access**

```
import visualization
session.defaultFieldReportOptions
session.fieldReportOptions
```

### 23.1.1 setValues(...)

This method modifies the FieldReportOptions object.

**Required arguments**

None.

**Optional arguments**

*numColumns*

An Int specifying the number of columns to display for the tabular report. The default value is 80.

*numberFormat*

A [NumberFormat](pt01ch47pyo09.md) object specifying the format type, number of digits and precision used to print the numeric output. 

*printXYData*

A Boolean specifying whether to include *X–Y* data values in the tabular report. The default value is ON.

*printTotal*

A Boolean specifying whether to include column totals in the tabular report. The default value is ON.

*printMinMax*

A Boolean specifying whether to include column summary minimum and maximum values in the tabular report. The default value is ON.

*pageWidth*

A SymbolicConstant specifying how the width of the tabular report is to be determined. Possible values are NO_LIMIT and SPECIFY. The default value is NO_LIMIT.

*columnLayout*

A SymbolicConstant specifying how values are to be presented in the tabular report. Possible values are SINGLE_TABLE and SEPARATE_TABLES. The default value is SINGLE_TABLE.

*sort*

A SymbolicConstant specifying the order in which values are to be sorted within a tabular report. Possible values are ASCENDING and DESCENDING. The default value is ASCENDING.

**Return value**

A FieldReportOptions object.

**Exceptions**

None.

### 23.1.2 Members

The FieldReportOptions object has members with the same names and descriptions as the arguments to the [setValues](pt01ch23pyo01.md#ker-fieldreportoptions-setvalues-pyc) method.




