# 36.37 TopologyMemberSize object







The TopologyMemberSize object defines a topology member size geometric restriction.

         The TopologyMemberSize object is derived from the [GeometricRestriction](pt01ch36pyo08.md) object.       

**Access**

```

        import optimization
        mdb.models[*name*].optimizationTasks[*name*].geometricRestrictions[*name*]

```

### 36.37.1 TopologyMemberSize(...)

           This method creates a TopologyMemberSize object.         

**Path**

```

          mdb.models[*name*].optimizationTasks[*name*].TopologyMemberSize

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

*separation*

A Float specifying the minimum gap. The default value is 0.0.

*sizeRestriction*

                 A SymbolicConstant specifying whether to restrict the minimum or maximum thickness or an envelope of both. Possible values are ENVELOPE, MAXIMUM, and MINIMUM. The default value is MINIMUM.               

**Return value**

           A TopologyMemberSize object.         

**Exceptions**

None.

### 36.37.2 setValues(...)

           This method modifies the TopologyMemberSize object.         

**Required arguments**

None.

**Optional arguments**

             The optional arguments to `setValues` are the same as the arguments to the [TopologyMemberSize](pt01ch36pyo37.md#ker-topologymembersize-topologymembersize-pyc) method, except for the *name* argument.           

**Return value**

None

**Exceptions**

None.

### 36.37.3 Members

         The TopologyMemberSize object has members with the same names and descriptions as the arguments to the [TopologyMemberSize](pt01ch36pyo37.md#ker-topologymembersize-topologymembersize-pyc) method.       




