# 36.7 FrozenArea object







The FrozenArea object defines a frozen area geometric restriction.

         The FrozenArea object is derived from the [GeometricRestriction](pt01ch36pyo08.md) object.       

**Access**

```

        import optimization
        mdb.models[*name*].optimizationTasks[*name*].geometricRestrictions[*name*]

```

### 36.7.1 FrozenArea(...)

           This method creates a FrozenArea object.         

**Path**

```

          mdb.models[*name*].optimizationTasks[*name*].FrozenArea

```

**Required argument**

*name*

A String specifying the geometric restriction repository key.

**Optional argument**

*region*

                 A [Region](pt01ch45pyo03.md) object specifying the region to which the geometric restriction is applied.  When used with a [TopologyTask](pt01ch36pyo41.md), there is no default value.  When used with a [ShapeTask](pt01ch36pyo20.md), the default value is MODEL.               

**Return value**

           A FrozenArea object.         

**Exceptions**

None.

### 36.7.2 setValues(...)

           This method modifies the FrozenArea object.         

**Required arguments**

None.

**Optional arguments**

             The optional arguments to `setValues` are the same as the arguments to the [FrozenArea](pt01ch36pyo07.md#ker-frozenarea-frozenarea-pyc) method, except for the *name* argument.           

**Return value**

None

**Exceptions**

None.

### 36.7.3 Members

         The FrozenArea object has members with the same names and descriptions as the arguments to the [FrozenArea](pt01ch36pyo07.md#ker-frozenarea-frozenarea-pyc) method.       




