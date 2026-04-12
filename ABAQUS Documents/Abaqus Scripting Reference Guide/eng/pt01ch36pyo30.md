# 36.30 SizingThicknessControl object







The SizingThicknessControl object defines a sizing thickness control geometric restriction.

         The SizingThicknessControl object is derived from the [GeometricRestriction](pt01ch36pyo08.md) object.       

**Access**

```

        import optimization
        mdb.models[*name*].optimizationTasks[*name*].geometricRestrictions[*name*]

```

### 36.30.1 SizingThicknessControl(...)

           This method creates a SizingThicknessControl object.         

**Path**

```

          mdb.models[*name*].optimizationTasks[*name*].SizingThicknessControl

```

**Required arguments**

*name*

A String specifying the geometric restriction repository key.

*region*

                 A [Region](pt01ch45pyo03.md) object specifying the region to which the geometric restriction is applied.               

*thicknessRestrictionBy*

              A SymbolicConstant specifying whether to define thickness restriction by value or fraction. Possible values are VALUE and FRACTION.              

**Optional arguments**

**Note:**You must specify either *maxThickness* or *minThickness*.

*maxThickness*

                 A Float specifying the maximum thickness.               

*minThickness*

                 A Float specifying the minimum thickness.               

**Return value**

           A SizingThicknessControl object.         

**Exceptions**

None.

### 36.30.2 setValues(...)

           This method modifies the SizingThicknessControl object.         

**Required arguments**

None.

**Optional arguments**

             The optional arguments to `setValues` are the same as the arguments to the [SizingThicknessControl](pt01ch36pyo30.md#ker-sizingthicknesscontrol-sizingthicknesscontrol-pyc) method, except for the *name* argument.           

**Return value**

None

**Exceptions**

None.

### 36.30.3 Members

         The SizingThicknessControl object has members with the same names and descriptions as the arguments to the [SizingThicknessControl](pt01ch36pyo30.md#ker-sizingthicknesscontrol-sizingthicknesscontrol-pyc) method.       




