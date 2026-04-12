# 25.69 StdXplCosimulation object







The StdXplCosimulation object defines co-simulation behavior between Abaqus/Standard and Abaqus/Explicit.

The StdXplCosimulation object is derived from the [Interaction](pt01ch25pyo01.md) object.

**Access**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.69.1 StdXplCosimulation(...)

This method creates a StdXplCosimulation object.

**Path**

```
mdb.models[*name*].StdXplCosimulation
```

**Required arguments**

*name*

A String specifying the repository key.

*createStepName*

A String specifying the name of the step in which the StdXplCosimulation object is created.

*region*

A [Region](pt01ch45pyo03.md) object specifying the import and export region upon which the co-simulation exchanges data with the coupled analysis program.

**Optional arguments**

*incrementation*

A SymbolicConstant specifying whether the analysis programs use the same time increments or one is allowed to use more time increments than the other before exchanging data. Possible values are ALLOW_SUBCYCLING and LOCKSTEP. The default value is ALLOW_SUBCYCLING.

*stepSize*

A Float specifying the size of the increments to be used by Abaqus/Standard and Abaqus/Explicit. The default value is 0.0.

*stepSizeDefinition*

A SymbolicConstant specifying whether the increment size is the analysis default or a supplied variable. Possible values are DEFAULT and SPECIFIED. The default value is DEFAULT.

**Return value**

A StdXplCosimulation object.

**Exceptions**

None.

### 25.69.2 setValues(...)

This method modifies the StdXplCosimulation object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [StdXplCosimulation](pt01ch25pyo69.md#ker-stdxplcosimulation-stdxplcosimulation-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 25.69.3 Members

The StdXplCosimulation object has members with the same names and descriptions as the arguments to the [StdXplCosimulation](pt01ch25pyo69.md#ker-stdxplcosimulation-stdxplcosimulation-pyc) method.




