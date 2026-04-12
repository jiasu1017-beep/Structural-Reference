# 36.34 StopCondition object







         The StopCondition object is the abstract base type for other StopCondition objects. The StopCondition object has no explicit constructor. The methods and members of the StopCondition object are common to all objects derived from StopCondition.       

**Access**

```

        import optimization
        mdb.models[*name*].optimizationTasks[*name*].stopConditions[*name*]

```

### 36.34.1 Members

         The StopCondition object can have the following members:       

*name*

A String specifying the stop condition repository key.

*region*

               The SymbolicConstant MODEL or a [Region](pt01ch45pyo03.md) object specifying the region to which the stop condition is applied. The default value is MODEL.             




