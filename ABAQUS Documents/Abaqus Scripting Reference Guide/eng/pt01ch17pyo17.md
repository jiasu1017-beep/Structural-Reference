# 17.17 StopConditionDisplayOptions object







The StopConditionDisplayOptions object stores settings that specify how assemblies are to be displayed in a particular viewport when 

```
session.viewports[*name*].assemblyDisplay.stopConditions=ON
```
The StopConditionDisplayOptions object has no constructor. When you create a new viewport, the settings are copied from the current viewport.

**Access**

```
session.viewports[*name*].assemblyDisplay.stopConditionOptions
session.viewports[*name*].layers[*name*].assemblyDisplay\
.stopConditionOptions
```

### 17.17.1 setValues(...)

This method modifies the StopConditionDisplayOptions object.

**Required arguments**

None.

**Optional argument**

*localStopCondition*

A Boolean specifying whether local stop condition symbols are shown. The default value is ON.

**Return value**

None

**Exceptions**

RangeError.

### 17.17.2 Members

The StopConditionDisplayOptions object has members with the same names and descriptions as the arguments to the [setValues](pt01ch17pyo17.md#ker-stopconditiondisplayoptions-setvalues-pyc) method.




