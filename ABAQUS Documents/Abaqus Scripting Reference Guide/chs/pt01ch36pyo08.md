# 36.8 GeometricRestriction object







         The GeometricRestriction object is the abstract base type for other GeometricRestriction objects. The GeometricRestriction object has no explicit constructor. The methods and members of the GeometricRestriction object are common to all objects derived from GeometricRestriction.       

**Access**

```

        import optimization
        mdb.models[*name*].optimizationTasks[*name*].geometricRestrictions[*name*]

```

### 36.8.1 Members

         The GeometricRestriction object can have the following members:       

*name*

A String specifying the geometric restriction repository key.

*region*

               A [Region](pt01ch45pyo03.md) object specifying the region to which the geometric restriction is applied.  When used with a [TopologyTask](pt01ch36pyo41.md), there is no default value.  When used with a [ShapeTask](pt01ch36pyo20.md), the default value is MODEL.             




