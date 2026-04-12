# 2.5 AdaptivityIteration object







 The AdaptivityIteration object contains information about a given iteration of the varying topology adaptivity process (adaptive remeshing).

**Access**

```
import job
mdb.adaptivityProcesses[*name*].iterations[*i*]
```

### 2.5.1 AdaptivityIteration(...)

This method creates an AdaptivityIteration object.

**Path**

```
mdb.adaptivityProcesses[*name*].AdaptivityIteration
```

**Required arguments**

*iteration*

An Int specifying the sequence number for this iteration in the adaptivity process.

*jobName*

A String specifying the name of the job that was run for this iteration.

*modelName*

A String specifying the name of the model that was analyzed and remeshed in this iteration.

*odbPath*

A String specifying the path to the ODB file that was created for this iteration.

*remeshingErrors*

An Int specifying the number of part instances which generated errors while remeshing the model in this iteration of the adaptivity process.

**Optional arguments**

None.

**Return value**

An AdaptivityIteration object.

**Exceptions**

None.

### 2.5.2 Members

The AdaptivityIteration object has members with the same names and descriptions as the arguments to the [AdaptivityIteration](pt01ch02pyo05.md#ker-adaptivityiteration-adaptivityiteration-pyc) method.

In addition, the AdaptivityIteration object can have the following member:

*ruleResults*

A repository of [RuleResult](pt01ch02pyo12.md) objects specifying the calculated results from sizing functions corresponding to the [RemeshingRule](pt01ch02pyo11.md) objects for this iteration of an adaptivity process.




