# 36.27 SizingPointSymmetry object







The SizingPointSymmetry object defines a sizing point symmetry geometric restriction.

         The SizingPointSymmetry object is derived from the [GeometricRestriction](pt01ch36pyo08.md) object.       

**Access**

```

        import optimization
        mdb.models[*name*].optimizationTasks[*name*].geometricRestrictions[*name*]

```

### 36.27.1 SizingPointSymmetry(...)

           This method creates a SizingPointSymmetry object.         

**Path**

```

          mdb.models[*name*].optimizationTasks[*name*].SizingPointSymmetry

```

**Required arguments**

*name*

A String specifying the geometric restriction repository key.

*region*

                 A [Region](pt01ch45pyo03.md) object specifying the region to which the geometric restriction is applied.                

**Optional arguments**

*csys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the position of the symmetry point defined as the origin of a local coordinate system.  If *csys*=`None`, the global coordinate system is used. When this member is queried, it returns an Int. The default value is `None`.               

*ignoreFrozenArea*

                 A Boolean specifying whether to ignore frozen areas. The default value is OFF.               

**Return value**

           A SizingPointSymmetry object.         

**Exceptions**

None.

### 36.27.2 setValues(...)

           This method modifies the SizingPointSymmetry object.         

**Required arguments**

None.

**Optional arguments**

             The optional arguments to `setValues` are the same as the arguments to the [SizingPointSymmetry](pt01ch36pyo27.md#ker-sizingpointsymmetry-sizingpointsymmetry-pyc) method, except for the *name* argument.           

**Return value**

None

**Exceptions**

None.

### 36.27.3 Members

         The SizingPointSymmetry object has members with the same names and descriptions as the arguments to the [SizingPointSymmetry](pt01ch36pyo27.md#ker-sizingpointsymmetry-sizingpointsymmetry-pyc) method.       




