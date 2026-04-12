# 2.12 RuleResult object







The RuleResult object contains result information corresponding to a [RemeshingRule](pt01ch02pyo11.md) object for an adaptivity iteration.

**Access**

```
import job
mdb.adaptivityProcesses[*name*].iterations[*i*].ruleResults[*name*]
```

### 2.12.1 RuleResult(...)

This method creates a RuleResult with data for a [RemeshingRule](pt01ch02pyo11.md) for a given adaptivity iteration.

**Path**

```
mdb.adaptivityProcesses[*name*].iterations[*i*].RuleResult
```

**Required arguments**

*name*

A String specifying the name of the Remeshing Rule to which these results correspond.

*indicatorResults*

A repository of [ErrorIndicatorResult](pt01ch02pyo09.md) objects specifying the calculated results from the sizing function corresponding to the error indicator variables for the Remeshing Rule.

*numElems*

An Int specifying the number of elements before remeshing in the region of the Remeshing Rule.

*minSizeElemCount*

An Int specifying the number of elements that were constrained to the minimum element size by the Remeshing Rule.

**Optional argument**

*satisfiedVars*

A sequence of Strings specifying the error indicator variables that have satisfied the Remeshing Rule.

**Return value**

A RuleResult object.

**Exceptions**

AbaqusException.

### 2.12.2 Members

The RuleResult object has members with the same names and descriptions as the arguments to the [RuleResult](pt01ch02pyo12.md#ker-ruleresult-ruleresult-pyc) method.




