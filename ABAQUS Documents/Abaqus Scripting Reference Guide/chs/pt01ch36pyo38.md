# 36.38 TopologyPlanarSymmetry object







The TopologyPlanarSymmetry object defines a topology planar symmetry geometric restriction.

         The TopologyPlanarSymmetry object is derived from the [GeometricRestriction](pt01ch36pyo08.md) object.       

**Access**

```

        import optimization
        mdb.models[*name*].optimizationTasks[*name*].geometricRestrictions[*name*]

```

### 36.38.1 TopologyPlanarSymmetry(...)

           This method creates a TopologyPlanarSymmetry object.         

**Path**

```

          mdb.models[*name*].optimizationTasks[*name*].TopologyPlanarSymmetry

```

**Required arguments**

*name*

A String specifying the geometric restriction repository key.

*region*

                 A [Region](pt01ch45pyo03.md) object specifying the region to which the geometric restriction is applied.  When used with a [TopologyTask](pt01ch36pyo41.md), there is no default value.  When used with a [ShapeTask](pt01ch36pyo20.md), the default value is MODEL.               

**Optional arguments**

*axis*

                 A SymbolicConstant specifying the axis of symmetry. Possible values are AXIS_1, AXIS_2, and AXIS_3. The default value is AXIS_1.               

*csys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system. If *csys*=`None`, the global coordinate system is used. When this member is queried, it returns an Int. The default value is `None`.               

*ignoreFrozenArea*

                 A Boolean specifying whether to ignore frozen areas. The default value is OFF.               

**Return value**

           A TopologyPlanarSymmetry object.         

**Exceptions**

None.

### 36.38.2 setValues(...)

           This method modifies the TopologyPlanarSymmetry object.         

**Required arguments**

None.

**Optional arguments**

             The optional arguments to `setValues` are the same as the arguments to the [TopologyPlanarSymmetry](pt01ch36pyo38.md#ker-topologyplanarsymmetry-topologyplanarsymmetry-pyc) method, except for the *name* argument.           

**Return value**

None

**Exceptions**

None.

### 36.38.3 Members

         The TopologyPlanarSymmetry object has members with the same names and descriptions as the arguments to the [TopologyPlanarSymmetry](pt01ch36pyo38.md#ker-topologyplanarsymmetry-topologyplanarsymmetry-pyc) method.       




