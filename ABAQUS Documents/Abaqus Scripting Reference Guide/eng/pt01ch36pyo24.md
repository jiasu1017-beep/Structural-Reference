# 36.24 SizingFrozenArea object







The SizingFrozenArea object defines a sizing frozen area geometric restriction.

         The SizingFrozenArea  object is derived from the [GeometricRestriction](pt01ch36pyo08.md) object.       

**Access**

```

        import optimization
        mdb.models[*name*].optimizationTasks[*name*].geometricRestrictions[*name*]

```

### 36.24.1 SizingFrozenArea (...)

           This method creates a SizingFrozenArea  object.         

**Path**

```

          mdb.models[*name*].optimizationTasks[*name*].SizingFrozenArea

```

**Required argument**

*name*

A String specifying the geometric restriction repository key.

*region*

  A [Region](pt01ch45pyo03.md) object specifying the region to which the geometric restriction is applied.  

**Optional arguments**

None.

**Return value**

    A SizingFrozenArea  object.         

**Exceptions**

None.

### 36.24.2 setValues(...)

           This method modifies the SizingFrozenArea  object.         

**Required arguments**

None.

**Optional arguments**

             The optional arguments to `setValues` are the same as the arguments to the [SizingFrozenArea](pt01ch36pyo24.md#ker-sizingfrozenarea-sizingfrozenarea-pyc) method, except for the *name* argument.           

**Return value**

None

**Exceptions**

None.

### 36.24.3 Members

         The SizingFrozenArea  object has members with the same names and descriptions as the arguments to the [SizingFrozenArea](pt01ch36pyo24.md#ker-sizingfrozenarea-sizingfrozenarea-pyc) method.       




