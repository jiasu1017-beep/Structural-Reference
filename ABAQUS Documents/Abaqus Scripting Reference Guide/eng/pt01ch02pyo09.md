# 2.9 ErrorIndicatorResult object







The ErrorIndicatorResult object contains result information corresponding to an error indicator variable in a [RemeshingRule](pt01ch02pyo11.md) object for an adaptivity iteration.

**Access**

```
import job
mdb.adaptivityProcesses[*name*].iterations[*i*].ruleResults[*name*]\
.indicatorResults[*name*]
```

### 2.9.1 ErrorIndicatorResult(...)

This method creates an ErrorIndicatorResult with data for an error indicator variable in a [RemeshingRule](pt01ch02pyo11.md) for a given adaptivity iteration.

**Path**

```
mdb.adaptivityProcesses[*name*].iterations[*i*].ruleResults[*name*]\
.ErrorIndicatorResult
```

**Required arguments**

*name*

A String specifying the name of the error indicator variable to which these results correspond.

*results*

A String-to-Float Dictionary specifying the calculated results from the sizing function corresponding to the error indicator variable represented by this ErrorIndicatorResult.

**Optional arguments**

None.

**Return value**

An ErrorIndicatorResult object.

**Exceptions**

AbaqusException.

### 2.9.2 Members

The ErrorIndicatorResult object has members with the same names and descriptions as the arguments to the [ErrorIndicatorResult](pt01ch02pyo09.md#ker-errorindicatorresult-errorindicatorresult-pyc) method.




