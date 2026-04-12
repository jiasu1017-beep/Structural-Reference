# 36.22 SizingClusterAreas object







The SizingClusterAreas object defines a sizing cluster areas geometric restriction.

         The SizingClusterAreas object is derived from the [GeometricRestriction](pt01ch36pyo08.md) object.       

**Access**

```

        import optimization
        mdb.models[*name*].optimizationTasks[*name*].geometricRestrictions[*name*]

```

### 36.22.1 SizingClusterAreas(...)

           This method creates a SizingClusterAreas object.         

**Path**

```

          mdb.models[*name*].optimizationTasks[*name*].SizingClusterAreas

```

**Required argument**

*name*

A String specifying the geometric restriction repository key.

*regions*

                 Tuple of [Region](pt01ch45pyo03.md) objects specifying the regions to which the geometric restriction is applied.               

**Return value**

           A SizingClusterAreas object.         

**Exceptions**

None.

### 36.22.2 setValues(...)

           This method modifies the SizingClusterAreas object.         

**Required arguments**

None.

**Optional arguments**

             The optional arguments to `setValues` are the same as the arguments to the [SizingClusterAreas](pt01ch36pyo22.md#ker-sizingclusterareas-sizingclusterareas-pyc) method, except for the *name* argument.           

**Return value**

None

**Exceptions**

None.

### 36.22.3 Members

         The SizingClusterAreas object has members with the same names and descriptions as the arguments to the [SizingClusterAreas](pt01ch36pyo22.md#ker-sizingclusterareas-sizingclusterareas-pyc) method.       




