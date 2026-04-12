# 36.29 SizingTask object







The SizingTask object defines a Sizing task.

         The SizingTask object is derived from the [OptimizationTask](pt01ch36pyo01.md) object.       

**Access**

```

        import optimization
        mdb.models[*name*].optimizationTasks[*name*]

```

### 36.29.1 SizingTask(...)

           This method creates a SizingTask object.         

**Path**

```

          mdb.models[*name*].SizingTask

```

**Required argument**

*name*

A String specifying the optimization task repository key.

**Optional arguments**

*elementthicknessDeltaStopCriteria*

                 A Float specifying the stop criteria based upon the change in element thickness. The default value is 0.510–2.               

*freezeBoundaryConditionRegions*

                 A Boolean specifying whether to exclude elements with boundary conditions from the optimization. The default value is OFF.               

*freezeLoadRegions*

                 A Boolean specifying whether to exclude elements with loads and elements with loaded nodes from the optimization. The default value is ON.               

*modeTrackingRegion*

 `None` or a [Region](pt01ch45pyo03.md) object specifying the region to use for mode tracking. The default value is `None`.                 

*numFulfilledStopCriteria*

An Int specifying the number of stop criteria. The default value is 2.

*numTrackedModes*

An Int specifying the number of modes included in mode tracking. The default value is 5.

*objectiveFunctionDeltaStopCriteria*

                 A Float specifying the stop criteria based upon the change in objective function. The default value is 0.001.               

*stopCriteriaDesignCycle*

An Int specifying the first design cycle used to evaluate convergence criteria. The default value is 4.

*thicknessMoveLimit*

A Float specifying the maximum change in thickness per design cycle. The default value is 0.25.

*thicknessUpdateStrategy*

                 A SymbolicConstant specifying the strategy for how the thickness is updated in the method of moving asymptotes. Possible values are NORMAL, CONSERVATIVE, and AGGRESSIVE. The default value is NORMAL.               

**Return value**

           A SizingTask object.         

**Exceptions**

None.

### 36.29.2 setValues(...)

           This method modifies the SizingTask object.         

**Required arguments**

None.

**Optional arguments**

             The optional arguments to `setValues` are the same as the arguments to the [SizingTask](pt01ch36pyo29.md#ker-sizingtask-sizingtask-pyc) method, except for the *name* argument.           

**Return value**

None

**Exceptions**

None.

### 36.29.3 Members

         The SizingTask object has members with the same names and descriptions as the arguments to the [SizingTask](pt01ch36pyo29.md#ker-sizingtask-sizingtask-pyc) method.       

         In addition, the SizingTask object can have the following members:       

*designResponses*

               A repository of [DesignResponse](pt01ch36pyo04.md) objects.             

*objectiveFunctions*

               A repository of [ObjectiveFunction](pt01ch36pyo11.md) objects.             

*optimizationConstraints*

               A repository of [OptimizationConstraint](pt01ch36pyo12.md) objects.             

*geometricRestrictions*

               A repository of [GeometricRestriction](pt01ch36pyo08.md) objects.             

*stopConditions*

               A repository of [StopCondition](pt01ch36pyo34.md) objects.             




