# 36.39 TopologyPointSymmetry object







The TopologyPointSymmetry object defines a topology point symmetry geometric restriction.

         The TopologyPointSymmetry object is derived from the [GeometricRestriction](pt01ch36pyo08.md) object.       

**Access**

```

        import optimization
        mdb.models[*name*].optimizationTasks[*name*].geometricRestrictions[*name*]

```

### 36.39.1 TopologyPointSymmetry(...)

           This method creates a TopologyPointSymmetry object.         

**Path**

```

          mdb.models[*name*].optimizationTasks[*name*].TopologyPointSymmetry

```

**Required arguments**

*name*

A String specifying the geometric restriction repository key.

*region*

                 A [Region](pt01ch45pyo03.md) object specifying the region to which the geometric restriction is applied.  When used with a [TopologyTask](pt01ch36pyo41.md), there is no default value.  When used with a [ShapeTask](pt01ch36pyo20.md), the default value is MODEL.               

**Optional arguments**

*csys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the position of the symmetry point defined as the origin of a local coordinate system.  If *csys*=`None`, the global coordinate system is used. When this member is queried, it returns an Int. The default value is `None`.               

*ignoreFrozenArea*

                 A Boolean specifying whether to ignore frozen areas. The default value is OFF.               

**Return value**

           A TopologyPointSymmetry object.         

**Exceptions**

None.

### 36.39.2 setValues(...)

           This method modifies the TopologyPointSymmetry object.         

**Required arguments**

None.

**Optional arguments**

             The optional arguments to `setValues` are the same as the arguments to the [TopologyPointSymmetry](pt01ch36pyo39.md#ker-topologypointsymmetry-topologypointsymmetry-pyc) method, except for the *name* argument.           

**Return value**

None

**Exceptions**

None.

### 36.39.3 Members

         The TopologyPointSymmetry object has members with the same names and descriptions as the arguments to the [TopologyPointSymmetry](pt01ch36pyo39.md#ker-topologypointsymmetry-topologypointsymmetry-pyc) method.       




