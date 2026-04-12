# 34.10 HistoryRegion object







The HistoryRegion object contains history data for a single location in the model.

**Access**

```
import odbAccess
session.odbs[*name*].steps[*name*].historyRegions[*name*]
```

### 34.10.1 HistoryRegion(...)

This method creates a HistoryRegion object.

**Path**

```
session.odbs[*name*].steps[*name*].HistoryRegion
```

**Required arguments**

*name*

A String specifying the name of the HistoryRegion object.

*description*

A String specifying the description of the HistoryRegion object.

*point*

A [HistoryPoint](pt01ch34pyo09.md) object specifying the point to which the history data refer.

**Optional argument**

*loadCase*

 `None` or an [OdbLoadCase](pt01ch34pyo16.md) object specifying the load case associated with the HistoryRegion object. The default value is `None`.

**Return value**

A HistoryRegion object.

**Exceptions**

None.

### 34.10.2 getSubset(...)

This method returns a subset of the data in the HistoryRegion object.

**Required argument**

*variableName*

A String specifying the name of the output variable to return.

**Optional arguments**

None.

**Return value**

A HistoryRegion object.

**Exceptions**

None.

### 34.10.3 getSubset(...)

This method returns a subset of the data in the HistoryRegion object.

**Required argument**

*start*

A Float specifying the start of the subset. This is the same as the first item in the data array member of the [HistoryOutput](pt01ch34pyo08.md) object.

**Optional arguments**

None.

**Return value**

A HistoryRegion object.

**Exceptions**

None.

### 34.10.4 getSubset(...)

This method returns a subset of the data in the HistoryRegion object.

**Required arguments**

*start*

A Float specifying the start of the subset. This is the same as the first item in the data array member of the [HistoryOutput](pt01ch34pyo08.md) object.

*end*

A Float specifying the end of the subset.

**Optional arguments**

None.

**Return value**

A HistoryRegion object.

**Exceptions**

None.

### 34.10.5 Members

The HistoryRegion object has members with the same names and descriptions as the arguments to the [HistoryRegion](pt01ch34pyo10.md#ker-historyregion-historyregion-pyc) method.

In addition, the HistoryRegion object can have the following members:

*position*

A SymbolicConstant specifying the position of the history output. Possible values are NODAL, INTEGRATION_POINT, WHOLE_ELEMENT, WHOLE_REGION, and WHOLE_MODEL.

*historyOutputs*

A repository of [HistoryOutput](pt01ch34pyo08.md) objects.




