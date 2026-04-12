# 36.15 ShapeDemoldControl object







The ShapeDemoldControl object defines a shape demold control geometric restriction.

         The ShapeDemoldControl object is derived from the [GeometricRestriction](pt01ch36pyo08.md) object.       

**Access**

```

        import optimization
        mdb.models[*name*].optimizationTasks[*name*].geometricRestrictions[*name*]

```

### 36.15.1 ShapeDemoldControl(...)

           This method creates a ShapeDemoldControl object.         

**Path**

```

          mdb.models[*name*].optimizationTasks[*name*].ShapeDemoldControl

```

**Required arguments**

*name*

A String specifying the geometric restriction repository key.

*pullDirection*

                 A [VertexArray](pt01ch07pyo15.md) object of length 2 specifying the demold pull direction. Instead of through a [Vertex](pt01ch07pyo15.md), each point may be specified through a tuple of coordinates.               

*region*

                 A [Region](pt01ch45pyo03.md) object specifying the region to which the geometric restriction is applied.  When used with a [TopologyTask](pt01ch36pyo41.md), there is no default value.  When used with a [ShapeTask](pt01ch36pyo20.md), the default value is MODEL.               

**Optional arguments**

*collisionCheckRegion*

                 The SymbolicConstant DEMOLD_REGION or a [Region](pt01ch45pyo03.md) object specifying the collision check region.  If the value is DEMOLD_REGION, then the value of *region* is used as both the demold region and the collision check region. The default value is DEMOLD_REGION.               

*csys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system of the *pullDirection*. If *csys*=`None`, the global coordinate system is used. When this member is queried, it returns an Int. The default value is `None`.               

*drawAngle*

A Float specifying the draw angle. The default value is 0.0.

*masterPointDetermination*

                 A SymbolicConstant specifying the rule for assigning point priority. Possible values are MAXIMUM and MINIMUM. The default value is MAXIMUM.               

*presumeFeasibleRegionAtStart*

                 A Boolean specifying whether to ignore the geometric restriction in the first design cycle. The default value is ON.               

*tolerance1*

A Float specifying the geometric tolerance in the 1-direction. The default value is 0.01.

*tolerance2*

A Float specifying the geometric tolerance in the 2-direction. The default value is 0.01.

*tolerance3*

A Float specifying the geometric tolerance in the 3-direction. The default value is 0.01.

*undercutTolerance*

A Float specifying the undercut tolerance. The default value is 0.0.

**Return value**

           A ShapeDemoldControl object.         

**Exceptions**

None.

### 36.15.2 setValues(...)

           This method modifies the ShapeDemoldControl object.         

**Required arguments**

None.

**Optional arguments**

             The optional arguments to `setValues` are the same as the arguments to the [ShapeDemoldControl](pt01ch36pyo15.md#ker-shapedemoldcontrol-shapedemoldcontrol-pyc) method, except for the *name* argument.           

**Return value**

None

**Exceptions**

None.

### 36.15.3 Members

         The ShapeDemoldControl object has members with the same names and descriptions as the arguments to the [ShapeDemoldControl](pt01ch36pyo15.md#ker-shapedemoldcontrol-shapedemoldcontrol-pyc) method.       




