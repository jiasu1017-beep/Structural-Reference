# 26.1 Job object







The Job object is the abstract base type for other Job objects. The Job object has no explicit constructor. The methods and members of the Job object are common to all objects derived from Job.

**Access**

```
import job
mdb.coexecutions[*name*].jobs[*name*]
mdb.jobs[*name*]
```

### 26.1.1 kill()

This method kills the analysis of a job.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 26.1.2 submit(...)

This method submits a job for analysis.

**Required arguments**

None.

**Optional arguments**

*consistencyChecking*

A Boolean specifying whether to perform consistency checking for the job. The default value is ON. It is not recommended to turn the consistency checking off unless you are absolutely sure the model is consistent.

*datacheckJob*

A Boolean specifying whether to run the job as a datacheck analysis. The default value is False. The datacheckJob and continueJob arguments cannot both be True.

*continueJob*

A Boolean specifying whether to run the job as a continuation analysis. The default value is False. The datacheckJob and continueJob arguments cannot both be True.

**Return value**

None

**Exceptions**

None.

### 26.1.3 waitForCompletion()

This method interrupts the execution of the script until the end of the analysis. If you call the `waitForCompletion` method and the *status* member is neither SUBMITTED nor RUNNING, Abaqus assumes the analysis has either completed or aborted and returns immediately. 

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 26.1.4 Members

The Job object can have the following members:

*name*

A String specifying the name of the new job. The name must be a valid Abaqus/CAE object name.

*type*

A SymbolicConstant specifying the type of job. Possible values are ANALYSIS, SYNTAXCHECK, RECOVER, and RESTART. The default value is ANALYSIS.

                If the object has the type [JobFromInputFile](pt01ch26pyo02.md), *type*=RESTART is not available.

*waitHours*

An Int specifying the number of hours to wait before submitting the job. This argument is ignored if *queue* is set. The default value is 0.

This argument works in conjunction with *waitMinutes*. *waitHours* and *atTime* are mutually exclusive.

*waitMinutes*

An Int specifying the number of minutes to wait before submitting the job. This argument is ignored if *queue* is set. The default value is 0.

This argument works in conjunction with *waitHours*. *waitMinutes* and *atTime* are mutually exclusive.

*numCpus*

An Int specifying the number of CPUs to use for this analysis if parallel processing is available. Possible values are *numCpus* ![](../graphics/ker_eqn00060.gif) 0. The default value is 1.

*memory*

An Int specifying the amount of memory available to Abaqus analysis. The value should be expressed in the units supplied in                      *memoryUnits*. The default value is 90.

*memoryUnits*

A SymbolicConstant specifying the units for the amount of memory used in an Abaqus analysis. Possible values are PERCENTAGE, MEGA_BYTES, and GIGA_BYTES. The default value is PERCENTAGE.

*getMemoryFromAnalysis*

A Boolean specifying whether to retrieve the recommended memory settings from the last datacheck or analysis run and use those values in subsequent submissions. The default value is ON.

*explicitPrecision*

A SymbolicConstant specifying whether to use the double precision version of Abaqus/Explicit. Possible values are SINGLE, FORCE_SINGLE, DOUBLE, DOUBLE_CONSTRAINT_ONLY, and DOUBLE_PLUS_PACK. The default value is SINGLE.

*nodalOutputPrecision*

A SymbolicConstant specifying the precision of the nodal output written to the output database. Possible values are SINGLE and FULL. The default value is SINGLE.

*parallelizationMethodExplicit*

A SymbolicConstant specifying the parallelization method for Abaqus/Explicit. Possible values are LOOP and DOMAIN. The default value is LOOP.

*numDomains*

An Int specifying the number of domains for parallel execution in Abaqus/Explicit. When *parallelizationMethodExplicit*=DOMAIN, *numDomains* must be a multiple of *numCpus*. The default value is 1.

*activateLoadBalancing*

A Boolean specifying whether to activate dyanmic load balancing for jobs running on multiple processors with multiple domains in Abaqus/Explicit. The default value is OFF.

*multiprocessingMode*

A SymbolicConstant specifying whether an analysis is decomposed into threads or into multiple processes that communicate through a message passing interface (MPI). Possible values are DEFAULT, THREADS, and MPI. The default value is DEFAULT.

*analysis*

A SymbolicConstant specifying whether the job will be analyzed by Abaqus/Standard, Abaqus/Explicit, or Abaqus/CFD. Possible values are STANDARD, EXPLICIT, CFD, and UNKNOWN.

If the object has the type [JobFromInputFile](pt01ch26pyo02.md), *analysis*=UNKNOWN.

*status*

A SymbolicConstant specifying the status of the analysis. Possible values are SUBMITTED, RUNNING, ABORTED, TERMINATED, COMPLETED, CHECK_RUNNING, and CHECK_COMPLETED.

If the *message* member is empty, *status* is set to NONE.

*queue*

A String specifying the name of the queue to which to submit the job. The default value is an empty string.

**Note:**You can use the *queue* argument when creating a Job object on a Windows workstation; however, remote queues are available only on UNIX platforms.

*atTime*

A String specifying the time at which to submit the job. If *queue* is empty, the string syntax must be valid for the UNIX                   `at` command. If *queue* is set, the syntax must be valid according to the system administrator. The default value is an empty string.

**Note:**You can use the *atTime* argument when creating a Job object on a Windows workstation; however, the `at` command is available only on UNIX platforms.

*scratch*

A String specifying the location of the scratch directory. The default value is an empty string.

*userSubroutine*

A String specifying the file containing the user's subroutine definitions. The default value is an empty string.

*messages*

A [MessageArray](pt01ch26pyo03.md) object specifying the messages received during an analysis.

*environment*

A tuple of Strings specifying the environment variables and their values.

### 26.1.5 Corresponding analysis keywords

| [*HEADING](../key/key-link.md#usb-kws-mheading) |
| --- |
| [*PREPRINT](../key/key-link.md#usb-kws-mpreprint) |




