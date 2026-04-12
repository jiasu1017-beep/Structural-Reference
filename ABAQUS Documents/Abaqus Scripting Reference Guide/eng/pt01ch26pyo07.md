# 26.7 OptimizationProcess object







The OptimizationProcess object defines a process to perform an optimization of a model defined using an optimization task.

**Access**

```
import job
mdb.optimizationProcesses[*name*]
```

### 26.7.1 OptimizationProcess(...)

This method creates an OptimizationProcess object.

**Path**

```
mdb.OptimizationProcess
```

**Required arguments**

*name*

A String specifying name of the optimization process.

*model*

A String specifying name of the model to be used for the optimization process.

*task*

A String specifying name of the optimization task to be used for the optimization process.

*prototypeJob*

A String specifying name of the job to be used as the prototype for all analysis jobs run by the optimization process.

**Optional arguments**

*description*

A String specifying a description of the optimization process.

*maxDesignCycle*

An Int specifying the maximum number of allowed design cycles for the optimization process. The default value is 15.

*dataSaveFrequency*

An Enum specifying whether Abaqus should save every iteration file in the optimization process or a selection of iteration files saved at a user-specified frequency. If you set *dataSaveFrequency*=OPT_DATASAVE_EVERY_CYCLE, Abaqus saves every iteration file; if you set *dataSaveFrequency*=OPT_DATASAVE_SPECIFY_CYCLE, ). Abaqus saves iteration files according to the frequency defined by the *saveEvery* parameter. The default is OPT_DATASAVE_SPECIFY_CYCLE.

*saveInitial*

A Boolean specifying whether the initial cycle should be saved when *dataSaveFrequency* is OPT_DATASAVE_SPECIFY_CYCLE. The default value is True.

*saveFirst*

A Boolean specifying whether the first cycle should be saved when *dataSaveFrequency* is OPT_DATASAVE_SPECIFY_CYCLE. The default value is True.

*saveLast*

A Boolean specifying whether the last cycle should be saved when *dataSaveFrequency* is OPT_DATASAVE_SPECIFY_CYCLE. The default value is True.

*saveEvery*

An Int specifying every nth cycle iterations to be saved when *dataSaveFrequency* is OPT_DATASAVE_SPECIFY_CYCLE. Abaqus saves file iterations for every nth iteration after iteration 1; if you set *saveEvery*=3, Abaqus saves file iterations for cycles 1, 4, 7, and so on. The default value is None.

**Return value**

An OptimizationProcess object.

**Exceptions**

AbaqusException.

### 26.7.2 writeParAndInputFiles()

         This method allows you to write par and input files for an optimization task.       

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 26.7.3 submit(...)

This method submits an optimization process.

**Required arguments**

None.

**Optional argument**

*validate*

A Boolean specifying whether Abaqus should perform the validation of the optimization process only. The default value is False.

**Return value**

None

**Exceptions**

None.

### 26.7.4 waitForCompletion()

This method interrupts the execution of the script until the end of all the analyses. If you call the `waitForCompletion` method and the *status* member is neither SUBMITTED nor RUNNING, Abaqus assumes the analysis has either completed or aborted and returns immediately.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 26.7.5 extract(...)

This method extracts a surface mesh from the optimized model.

**Required arguments**

*outputFileName*

Name of the output file for the extracted surface mesh.

*designCycle*

The design cycle number for which the surface mesh should be extracted.

**Optional arguments**

*isoValue*

Value used to determine the positions on the element edges where the new nodes are created. Value between 0 and 1. Default: 0.3

*smoothCycles*

Number of smoothing cycles; if set to 0, no smoothing is performed. Default: 5

*reductionPercent*

Defines the percent of faces that should be removed during the data reduction. If set to 0, no data reduction occurs. If set to 100, the data reduction stops when no faces can be removed (that is checked using reductionAngle parameter). Value between 0 and 100. Default: 0

*reductionAngle*

Defines the maximal angle between adjacent faces at a node such that the node may be removed during the data reduction. Value in degrees between 0 and 90. Default:15

*targetVolume*

Defines the target volume that is to be achieved iteratively by varying the isovalue. Value between 0 and 1. Default: 0

*extractFormat*

Tuple for the types of format of the output. Values are (OPT_EXTRACT_SMOOTH_ABAQUS_INPUT_FILE, OPT_EXTRACT_SMOOTH_STL). Default: OPT_EXTRACT_SMOOTH_ABAQUS_INPUT_FILE

*resultFiltering*

Possible string values are OFF or MODERATE or FULL. Defines if the element material values are to be filtered (averaged locally) before the isocut, and to what extent. Default: OFF

**Return value**

None

**Exceptions**

None.

### 26.7.6 setValues(...)

This method modifies the OptimizationProcess object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [OptimizationProcess](pt01ch26pyo07.md#ker-optimizationprocess-optimizationprocess-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

### 26.7.7 Members

The OptimizationProcess object has members with the same names and descriptions as the arguments to the [OptimizationProcess](pt01ch26pyo07.md#ker-optimizationprocess-optimizationprocess-pyc) method.

### 26.7.8 Corresponding analysis keywords




