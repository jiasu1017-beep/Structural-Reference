# 36.1 OptimizationTask object







         The OptimizationTask object is the abstract base type for other OptimizationTask objects. The OptimizationTask object has no explicit constructor. The methods and members of the OptimizationTask object are common to all objects derived from OptimizationTask.       

**Access**

```

        import optimization
        mdb.models[*name*].optimizationTasks[*name*]

```

### 36.1.1 Members

         The OptimizationTask object can have the following members:       

*name*

A String specifying the optimization task repository key.

*region*

               The SymbolicConstant MODEL or a [Region](pt01ch45pyo03.md) object specifying the region to which the optimization task is applied. The default value is MODEL.             

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




