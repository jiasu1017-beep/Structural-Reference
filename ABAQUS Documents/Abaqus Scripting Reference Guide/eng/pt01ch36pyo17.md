# 36.17 ShapePlanarSymmetry object







The ShapePlanarSymmetry object defines a shape planar symmetry geometric restriction.

         The ShapePlanarSymmetry object is derived from the [GeometricRestriction](pt01ch36pyo08.md) object.       

**Access**

```

        import optimization
        mdb.models[*name*].optimizationTasks[*name*].geometricRestrictions[*name*]

```

### 36.17.1 ShapePlanarSymmetry(...)

           This method creates a ShapePlanarSymmetry object.         

**Path**

```

          mdb.models[*name*].optimizationTasks[*name*].ShapePlanarSymmetry

```

**Required arguments**

*name*

A String specifying the geometric restriction repository key.

*clientDirection*

                 A [VertexArray](pt01ch07pyo15.md) object of length 2 specifying the vector positioned at the *csys* origin which is normal to the symmetry plane.  Instead of through a [Vertex](pt01ch07pyo15.md), each point may be specified through a tuple of coordinates.               

*region*

                 A [Region](pt01ch45pyo03.md) object specifying the region to which the geometric restriction is applied.  When used with a [TopologyTask](pt01ch36pyo41.md), there is no default value.  When used with a [ShapeTask](pt01ch36pyo20.md), the default value is MODEL.               

**Optional arguments**

*csys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system. If *csys*=`None`, the global coordinate system is used. When this member is queried, it returns an Int. The default value is `None`.               

*masterPointDetermination*

                 A SymbolicConstant specifying the rule for determining the master node. Possible values are MAXIMUM and MINIMUM. The default value is MAXIMUM.               

*presumeFeasibleRegionAtStart*

                 A Boolean specifying whether to ignore the geometric restriction in the first design cycle. The default value is ON.               

*tolerance1*

A Float specifying the geometric tolerance in the 1-direction. The default value is 0.01.

*tolerance2*

A Float specifying the geometric tolerance in the 2-direction. The default value is 0.01.

*tolerance3*

A Float specifying the geometric tolerance in the 3-direction. The default value is 0.01.

**Return value**

           A ShapePlanarSymmetry object.         

**Exceptions**

None.

### 36.17.2 setValues(...)

           This method modifies the ShapePlanarSymmetry object.         

**Required arguments**

None.

**Optional arguments**

             The optional arguments to `setValues` are the same as the arguments to the [ShapePlanarSymmetry](pt01ch36pyo17.md#ker-shapeplanarsymmetry-shapeplanarsymmetry-pyc) method, except for the *name* argument.           

**Return value**

None

**Exceptions**

None.

### 36.17.3 Members

         The ShapePlanarSymmetry object has members with the same names and descriptions as the arguments to the [ShapePlanarSymmetry](pt01ch36pyo17.md#ker-shapeplanarsymmetry-shapeplanarsymmetry-pyc) method.       




