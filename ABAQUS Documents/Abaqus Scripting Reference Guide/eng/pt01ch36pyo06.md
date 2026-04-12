# 36.6 FixedRegion object







The FixedRegion object defines a fixed region geometric restriction.

         The FixedRegion object is derived from the [GeometricRestriction](pt01ch36pyo08.md) object.       

**Access**

```

        import optimization
        mdb.models[*name*].optimizationTasks[*name*].geometricRestrictions[*name*]

```

### 36.6.1 FixedRegion(...)

           This method creates a FixedRegion object.         

**Path**

```

          mdb.models[*name*].optimizationTasks[*name*].FixedRegion

```

**Required arguments**

*name*

A String specifying the geometric restriction repository key.

*region*

                 A [Region](pt01ch45pyo03.md) object specifying the region to which the geometric restriction is applied.  When used with a [TopologyTask](pt01ch36pyo41.md), there is no default value.  When used with a [ShapeTask](pt01ch36pyo20.md), the default value is MODEL.               

**Optional arguments**

*csys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system. If *csys*=`None`, the global coordinate system is used. When this member is queried, it returns an Int. The default value is `None`.               

*presumeFeasibleRegionAtStart*

                 A Boolean specifying whether to ignore the geometric restriction in the first design cycle. The default value is ON.               

*u1*

                 A Boolean specifying whether to fix the region in the 1-direction. The default value is OFF.               

*u2*

                 A Boolean specifying whether to fix the region in the 2-direction. The default value is OFF.               

*u3*

                 A Boolean specifying whether to fix the region in the 3-direction. The default value is OFF.               

**Return value**

           A FixedRegion object.         

**Exceptions**

None.

### 36.6.2 setValues(...)

           This method modifies the FixedRegion object.         

**Required arguments**

None.

**Optional arguments**

             The optional arguments to `setValues` are the same as the arguments to the [FixedRegion](pt01ch36pyo06.md#ker-fixedregion-fixedregion-pyc) method, except for the *name* argument.           

**Return value**

None

**Exceptions**

None.

### 36.6.3 Members

         The FixedRegion object has members with the same names and descriptions as the arguments to the [FixedRegion](pt01ch36pyo06.md#ker-fixedregion-fixedregion-pyc) method.       




