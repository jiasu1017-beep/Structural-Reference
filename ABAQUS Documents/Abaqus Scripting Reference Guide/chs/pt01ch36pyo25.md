# 36.25 SizingMemberSize object







The SizingMemberSize object defines a sizing member size geometric restriction.

         The SizingMemberSize object is derived from the [GeometricRestriction](pt01ch36pyo08.md) object.       

**Access**

```

        import optimization
        mdb.models[*name*].optimizationTasks[*name*].geometricRestrictions[*name*]

```

### 36.25.1 SizingMemberSize(...)

           This method creates a SizingMemberSize object.         

**Path**

```

          mdb.models[*name*].optimizationTasks[*name*].SizingMemberSize

```

**Required arguments**

*name*

A String specifying the geometric restriction repository key.

*region*

                 A [Region](pt01ch45pyo03.md) object specifying the region to which the geometric restriction is applied.               

*minWidth*

A Float specifying the min width. 

### 36.25.2 setValues(...)

           This method modifies the sizingMemberSize object.         

**Required arguments**

None.

**Optional arguments**

             The optional arguments to `setValues` are the same as the arguments to the [sizingMemberSize](pt01ch36pyo25.md#ker-sizingmembersize-sizingmembersize-pyc) method, except for the *name* argument.           

**Return value**

None

**Exceptions**

None.

### 36.25.3 Members

         The sizingMemberSize object has members with the same names and descriptions as the arguments to the [sizingMemberSize](pt01ch36pyo25.md#ker-sizingmembersize-sizingmembersize-pyc) method.       




