# 36.36 TopologyDemoldControl object







The TopologyDemoldControl object defines a topology demold control geometric restriction.

         The TopologyDemoldControl object is derived from the [GeometricRestriction](pt01ch36pyo08.md) object.       

**Access**

```

        import optimization
        mdb.models[*name*].optimizationTasks[*name*].geometricRestrictions[*name*]

```

### 36.36.1 TopologyDemoldControl(...)

           This method creates a TopologyDemoldControl object.         

**Path**

```

          mdb.models[*name*].optimizationTasks[*name*].TopologyDemoldControl

```

**Required arguments**

*name*

A String specifying the geometric restriction repository key.

*region*

                 A [Region](pt01ch45pyo03.md) object specifying the region to which the geometric restriction is applied.  When used with a [TopologyTask](pt01ch36pyo41.md), there is no default value.  When used with a [ShapeTask](pt01ch36pyo20.md), the default value is MODEL.               

**Optional arguments**

*csys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system of the *pullDirection*. If *csys*=`None`, the global coordinate system is used. When this member is queried, it returns an Int. The default value is `None`.               

*draftAngle*

A Float specifying the draft angle. The default value is 0.0.

*collisionCheckRegion*

                 The SymbolicConstant DEMOLD_REGION or a [Region](pt01ch45pyo03.md) object specifying the collision check region.  If the value is DEMOLD_REGION, then the value of *region* is used as both the demold region and the collision check region. The default value is DEMOLD_REGION.               

*pointRegion*

                 A [Region](pt01ch45pyo03.md) object specifying the point on a plane perpendicular to the pull direction, used to specify the central plane when *technique* is POINT.               

*pullDirection*

                 A [VertexArray](pt01ch07pyo15.md) object of length 2 specifying the demold pull direction. Instead of through a [Vertex](pt01ch07pyo15.md), each point may be specified through a tuple of coordinates.               

*technique*

                 A SymbolicConstant specifying the demold technique. Possible values are AUTO, AUTO_TIGHT, POINT, SURFACE, and STAMP. The default value is AUTO.               

**Return value**

           A TopologyDemoldControl object.         

**Exceptions**

None.

### 36.36.2 setValues(...)

           This method modifies the TopologyDemoldControl object.         

**Required arguments**

None.

**Optional arguments**

             The optional arguments to `setValues` are the same as the arguments to the [TopologyDemoldControl](pt01ch36pyo36.md#ker-topologydemoldcontrol-topologydemoldcontrol-pyc) method, except for the *name* argument.           

**Return value**

None

**Exceptions**

None.

### 36.36.3 Members

         The TopologyDemoldControl object has members with the same names and descriptions as the arguments to the [TopologyDemoldControl](pt01ch36pyo36.md#ker-topologydemoldcontrol-topologydemoldcontrol-pyc) method.       




