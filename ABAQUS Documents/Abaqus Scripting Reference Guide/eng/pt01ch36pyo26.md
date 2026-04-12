# 36.26 SizingPlanarSymmetry object







The SizingPlanarSymmetry object defines a sizing planar symmetry geometric restriction.

         The SizingPlanarSymmetry object is derived from the [GeometricRestriction](pt01ch36pyo08.md) object.       

**Access**

```

        import optimization
        mdb.models[*name*].optimizationTasks[*name*].geometricRestrictions[*name*]

```

### 36.26.1 SizingPlanarSymmetry(...)

           This method creates a SizingPlanarSymmetry object.         

**Path**

```

          mdb.models[*name*].optimizationTasks[*name*].SizingPlanarSymmetry

```

**Required arguments**

*name*

A String specifying the geometric restriction repository key.

*region*

                 A [Region](pt01ch45pyo03.md) object specifying the region to which the geometric restriction is applied.                

**Optional arguments**

*axis*

                 A SymbolicConstant specifying the axis of symmetry. Possible values are AXIS_1, AXIS_2, and AXIS_3. The default value is AXIS_1.               

*csys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system. If *csys*=`None`, the global coordinate system is used. When this member is queried, it returns an Int. The default value is `None`.               

*ignoreFrozenArea*

                 A Boolean specifying whether to ignore frozen areas. The default value is OFF.               

**Return value**

           A SizingPlanarSymmetry object.         

**Exceptions**

None.

### 36.26.2 setValues(...)

           This method modifies the sizingPlanarSymmetry object.         

**Required arguments**

None.

**Optional arguments**

             The optional arguments to `setValues` are the same as the arguments to the [sizingPlanarSymmetry](pt01ch36pyo26.md#ker-sizingplanarsymmetry-sizingplanarsymmetry-pyc) method, except for the *name* argument.           

**Return value**

None

**Exceptions**

None.

### 36.26.3 Members

         The sizingPlanarSymmetry object has members with the same names and descriptions as the arguments to the [sizingPlanarSymmetry](pt01ch36pyo26.md#ker-sizingplanarsymmetry-sizingplanarsymmetry-pyc) method.       




