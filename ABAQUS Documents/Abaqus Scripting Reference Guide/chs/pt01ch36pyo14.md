# 36.14 PenetrationCheck object







The PenetrationCheck object defines a penetration check geometric restriction.

         The PenetrationCheck object is derived from the [GeometricRestriction](pt01ch36pyo08.md) object.       

**Access**

```

        import optimization
        mdb.models[*name*].optimizationTasks[*name*].geometricRestrictions[*name*]

```

### 36.14.1 PenetrationCheck(...)

           This method creates a PenetrationCheck object.         

**Path**

```

          mdb.models[*name*].optimizationTasks[*name*].PenetrationCheck

```

**Required arguments**

*name*

A String specifying the geometric restriction repository key.

*penetrationCheckRegion*

                 A [Region](pt01ch45pyo03.md) object specifying the penetration check region.               

*region*

                 A [Region](pt01ch45pyo03.md) object specifying the region to which the geometric restriction is applied.  When used with a [TopologyTask](pt01ch36pyo41.md), there is no default value.  When used with a [ShapeTask](pt01ch36pyo20.md), the default value is MODEL.               

**Optional argument**

*presumeFeasibleRegionAtStart*

                 A Boolean specifying whether to ignore the geometric restriction in the first design cycle. The default value is ON.               

**Return value**

           A PenetrationCheck object.         

**Exceptions**

None.

### 36.14.2 setValues(...)

           This method modifies the PenetrationCheck object.         

**Required arguments**

None.

**Optional arguments**

             The optional arguments to `setValues` are the same as the arguments to the [PenetrationCheck](pt01ch36pyo14.md#ker-penetrationcheck-penetrationcheck-pyc) method, except for the *name* argument.           

**Return value**

None

**Exceptions**

None.

### 36.14.3 Members

         The PenetrationCheck object has members with the same names and descriptions as the arguments to the [PenetrationCheck](pt01ch36pyo14.md#ker-penetrationcheck-penetrationcheck-pyc) method.       




