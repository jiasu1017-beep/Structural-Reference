# 2.6 AdaptivityProcess object







The AdaptivityProcess object defines a series of jobs that will be submitted for analysis. Abaqus performs adaptive remeshing between each job.

**Access**

```
import job
mdb.adaptivityProcesses[*name*]
```

### 2.6.1 AdaptivityProcess(...)

This method creates an AdaptivityProcess object.

**Path**

```
mdb.AdaptivityProcess
```

**Required arguments**

*name*

A String specifying the name of the Adaptivity Process.

*job*

A [ModelJob](pt01ch26pyo04.md) object specifying a job to be used as the prototype for all analysis jobs run by the adaptivity process.

**Optional arguments**

*maxIterations*

An Int specifying the maximum number of analysis jobs that will be run by the Adaptivity Process. Abaqus performs adaptive remeshing between each analysis. The default value is 3.

*jobPrefix*

A String specifying the prefix to use for jobs created by the adaptivity process. An empty string indicates that the name of the adaptivity process should be used. The default value is an empty string.

**Return value**

An AdaptivityProcess object.

**Exceptions**

AbaqusException.

### 2.6.2 submit(...)

This method begins the process of analysis and adaptive remeshing.

**Required arguments**

None.

**Optional arguments**

*waitForCompletion*

A Boolean specifying whether to interrupt the execution of a script until the end of the adaptive remeshing process is reached.

*datacheckJob*

A Boolean specifying whether to run the adaptivity as a datacheck analysis. The default value is False. The datacheckJob and continueJob arguments cannot both be True.

*continueJob*

A Boolean specifying whether to run the adaptivity as a continuation analysis. The default value is False. The datacheckJob and continueJob arguments cannot both be True.

**Return value**

None

**Exceptions**

None.

### 2.6.3 setValues(...)

This method modifies the AdaptivityProcess object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [AdaptivityProcess](pt01ch02pyo06.md#ker-adaptivityprocess-adaptivityprocess-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

### 2.6.4 Members

The AdaptivityProcess object has members with the same names and descriptions as the arguments to the [AdaptivityProcess](pt01ch02pyo06.md#ker-adaptivityprocess-adaptivityprocess-pyc) method.

In addition, the AdaptivityProcess object can have the following members:

*status*

A SymbolicConstant specifying the status of the adaptivity process. Possible values are SUBMITTED, RUNNING, ABORTED, TERMINATED, and COMPLETED.

*iterations*

A repository of [AdaptivityIteration](pt01ch02pyo05.md) objects specifying the [AdaptivityIteration](pt01ch02pyo05.md) objects received during running the adaptivity process.




