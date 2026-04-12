# 36.11 ObjectiveFunction object







         The ObjectiveFunction object defines the objective of the optimization.       

**Access**

```

        import optimization
        mdb.models[*name*].optimizationTasks[*name*].objectiveFunctions[*name*]

```

### 36.11.1 ObjectiveFunction(...)

           This method creates an ObjectiveFunction object.         

**Path**

```

          mdb.models[*name*].optimizationTasks[*name*].ObjectiveFunction

```

**Required arguments**

*name*

A String specifying the objective function repository key.

*objectives*

                 An [OptimizationObjectiveArray](pt01ch36pyo13.md) object.               

**Optional argument**

*target*

                 A SymbolicConstant specifying the target of the objective function. Possible values are MINIMIZE, MAXIMIZE, and MINIMIZE_MAXIMUM. The default value is MINIMIZE.               

**Return value**

           An ObjectiveFunction object.         

**Exceptions**

InvalidNameError and RangeError.

### 36.11.2 setValues(...)

           This method modifies the ObjectiveFunction object.         

**Required arguments**

None.

**Optional arguments**

             The optional arguments to `setValues` are the same as the arguments to the [ObjectiveFunction](pt01ch36pyo11.md#ker-objectivefunction-objectivefunction-pyc) method, except for the *name* argument.           

**Return value**

None

**Exceptions**

RangeError.

### 36.11.3 Members

         The ObjectiveFunction object has members with the same names and descriptions as the arguments to the [ObjectiveFunction](pt01ch36pyo11.md#ker-objectivefunction-objectivefunction-pyc) method.       




