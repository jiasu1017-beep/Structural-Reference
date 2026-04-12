# 36.35 TopologyCyclicSymmetry object







The TopologyCyclicSymmetry object defines a topology cyclic symmetry geometric restriction.

         The TopologyCyclicSymmetry object is derived from the [GeometricRestriction](pt01ch36pyo08.md) object.       

**Access**

```

        import optimization
        mdb.models[*name*].optimizationTasks[*name*].geometricRestrictions[*name*]

```

### 36.35.1 TopologyCyclicSymmetry(...)

           This method creates a TopologyCyclicSymmetry object.         

**Path**

```

          mdb.models[*name*].optimizationTasks[*name*].TopologyCyclicSymmetry

```

**Required arguments**

*name*

A String specifying the geometric restriction repository key.

*region*

                 A [Region](pt01ch45pyo03.md) object specifying the region to which the geometric restriction is applied.  When used with a [TopologyTask](pt01ch36pyo41.md), there is no default value.  When used with a [ShapeTask](pt01ch36pyo20.md), the default value is MODEL.               

*translation*

A Float specifying the translation distance.

**Optional arguments**

*axis*

                 A SymbolicConstant specifying the translation direction defined along an axis positioned at the *csys* origin. Possible values are AXIS_1, AXIS_2, and AXIS_3. The default value is AXIS_1.               

*csys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system. If *csys*=`None`, the global coordinate system is used. When this member is queried, it returns an Int. The default value is `None`.               

*ignoreFrozenArea*

                 A Boolean specifying whether to ignore frozen areas. The default value is OFF.               

**Return value**

           A TopologyCyclicSymmetry object.         

**Exceptions**

None.

### 36.35.2 setValues(...)

           This method modifies the TopologyCyclicSymmetry object.         

**Required arguments**

None.

**Optional arguments**

             The optional arguments to `setValues` are the same as the arguments to the [TopologyCyclicSymmetry](pt01ch36pyo35.md#ker-topologycyclicsymmetry-topologycyclicsymmetry-pyc) method, except for the *name* argument.           

**Return value**

None

**Exceptions**

None.

### 36.35.3 Members

         The TopologyCyclicSymmetry object has members with the same names and descriptions as the arguments to the [TopologyCyclicSymmetry](pt01ch36pyo35.md#ker-topologycyclicsymmetry-topologycyclicsymmetry-pyc) method.       




