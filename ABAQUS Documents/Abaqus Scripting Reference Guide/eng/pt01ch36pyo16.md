# 36.16 ShapeMemberSize object







The ShapeMemberSize object defines a shape member size geometric restriction.

         The ShapeMemberSize object is derived from the [GeometricRestriction](pt01ch36pyo08.md) object.       

**Access**

```

        import optimization
        mdb.models[*name*].optimizationTasks[*name*].geometricRestrictions[*name*]

```

### 36.16.1 ShapeMemberSize(...)

           This method creates a ShapeMemberSize object.         

**Path**

```

          mdb.models[*name*].optimizationTasks[*name*].ShapeMemberSize

```

**Required arguments**

*name*

A String specifying the geometric restriction repository key.

*region*

                 A [Region](pt01ch45pyo03.md) object specifying the region to which the geometric restriction is applied.  When used with a [TopologyTask](pt01ch36pyo41.md), there is no default value.  When used with a [ShapeTask](pt01ch36pyo20.md), the default value is MODEL.               

**Optional arguments**

*maxThickness*

A Float specifying the maximum thickness. The default value is 0.0.

*minThickness*

A Float specifying the minimum thickness. The default value is 0.0.

*sizeRestriction*

                 A SymbolicConstant specifying whether to restrict the minimum or maximum thickness. Possible values are MAXIMUM and MINIMUM. The default value is MINIMUM.               

**Return value**

           A ShapeMemberSize object.         

**Exceptions**

None.

### 36.16.2 setValues(...)

           This method modifies the ShapeMemberSize object.         

**Required arguments**

None.

**Optional arguments**

             The optional arguments to `setValues` are the same as the arguments to the [ShapeMemberSize](pt01ch36pyo16.md#ker-shapemembersize-shapemembersize-pyc) method, except for the *name* argument.           

**Return value**

None

**Exceptions**

None.

### 36.16.3 Members

         The ShapeMemberSize object has members with the same names and descriptions as the arguments to the [ShapeMemberSize](pt01ch36pyo16.md#ker-shapemembersize-shapemembersize-pyc) method.       




