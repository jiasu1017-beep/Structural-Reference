# 36.21 SingleTermDesignResponse object







The SingleTermDesignResponse object defines a single-term design response.

         The SingleTermDesignResponse object is derived from the [DesignResponse](pt01ch36pyo04.md) object.       

**Access**

```

        import optimization
        mdb.models[*name*].optimizationTasks[*name*].designResponses[*name*]

```

### 36.21.1 SingleTermDesignResponse(...)

           This method creates a SingleTermDesignResponse object.         

**Path**

```

          mdb.models[*name*].optimizationTasks[*name*].SingleTermDesignResponse

```

**Required arguments**

*name*

A String specifying the design response repository key.

*identifier*

A String specifying the name of the variable identifier.

**Optional arguments**

*csys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system. If *csys*=`None`, the global coordinate system is used. When this member is queried, it returns an Int. The default value is `None`.               

*drivingRegion*

 `None` or a sequence of Floats specifying the driving region used when *identifier* is an internal nodal variable. The default value is `None`.               

*operation*

                 A SymbolicConstant specifying the operation used on values in the region. Possible values are MAXIMUM, MINIMUM, and SUM. The default value is SUM.               

*region*

                 The SymbolicConstant MODEL or a [Region](pt01ch45pyo03.md) object specifying the region of the design response variable. The default value is MODEL.               

*shellLayer*

                 A SymbolicConstant specifying the location used for shell layer values. Possible values are BOTTOM, MAXIMUM, MIDDLE, MINIMUM, and TOP. The default value is MAXIMUM.               

*stepOperation*

                 A SymbolicConstant specifying the operation used on values across steps and load cases. Possible values are MAXIMUM, MINIMUM, and SUM. The default value is SUM.               

*stepOptions*

                 A [StepOptionArray](pt01ch36pyo33.md) object.               

**Return value**

           A SingleTermDesignResponse object.         

**Exceptions**

None.

### 36.21.2 setValues(...)

           This method modifies the SingleTermDesignResponse object.         

**Required arguments**

None.

**Optional arguments**

             The optional arguments to `setValues` are the same as the arguments to the [SingleTermDesignResponse](pt01ch36pyo21.md#ker-singletermdesignresponse-singletermdesignresponse-pyc) method, except for the *name* argument.           

**Return value**

None

**Exceptions**

None.

### 36.21.3 Members

         The SingleTermDesignResponse object has members with the same names and descriptions as the arguments to the [SingleTermDesignResponse](pt01ch36pyo21.md#ker-singletermdesignresponse-singletermdesignresponse-pyc) method.       




