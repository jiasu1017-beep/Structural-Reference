# 36.9 Growth object







The Growth object defines a growth geometric restriction.

         The Growth object is derived from the [GeometricRestriction](pt01ch36pyo08.md) object.       

**Access**

```

        import optimization
        mdb.models[*name*].optimizationTasks[*name*].geometricRestrictions[*name*]

```

### 36.9.1 Growth(...)

           This method creates a Growth object.         

**Path**

```

          mdb.models[*name*].optimizationTasks[*name*].Growth

```

**Required arguments**

*name*

A String specifying the geometric restriction repository key.

*region*

                 A [Region](pt01ch45pyo03.md) object specifying the region to which the geometric restriction is applied.  When used with a [TopologyTask](pt01ch36pyo41.md), there is no default value.  When used with a [ShapeTask](pt01ch36pyo20.md), the default value is MODEL.               

**Optional arguments**

*growth*

                 A Float specifying the maximum optimization displacement in the growth direction.  Either *growth* or *shrink* or both must be specified. The default value is 0.0.               

*presumeFeasibleRegionAtStart*

                 A Boolean specifying whether to ignore the geometric restriction in the first design cycle. The default value is ON.               

*shrink*

                 A Float specifying the maximum optimization displacement in the shrink direction.  Either *growth* or *shrink* or both must be specified The default value is 0.0.               

**Return value**

           A Growth object.         

**Exceptions**

None.

### 36.9.2 setValues(...)

           This method modifies the Growth object.         

**Required arguments**

None.

**Optional arguments**

             The optional arguments to `setValues` are the same as the arguments to the [Growth](pt01ch36pyo09.md#ker-growth-growth-pyc) method, except for the *name* argument.           

**Return value**

None

**Exceptions**

None.

### 36.9.3 Members

         The Growth object has members with the same names and descriptions as the arguments to the [Growth](pt01ch36pyo09.md#ker-growth-growth-pyc) method.       




