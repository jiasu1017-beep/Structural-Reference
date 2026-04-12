# 36.40 TopologyRotationalSymmetry object







The TopologyRotationalSymmetry object defines a topology rotational symmetry geometric restriction.

         The TopologyRotationalSymmetry object is derived from the [GeometricRestriction](pt01ch36pyo08.md) object.       

**Access**

```

        import optimization
        mdb.models[*name*].optimizationTasks[*name*].geometricRestrictions[*name*]

```

### 36.40.1 TopologyRotationalSymmetry(...)

           This method creates a TopologyRotationalSymmetry object.         

**Path**

```

          mdb.models[*name*].optimizationTasks[*name*].TopologyRotationalSymmetry

```

**Required arguments**

*name*

A String specifying the geometric restriction repository key.

*angle*

A Float specifying the repeating segment size, an angle in degrees.

*region*

                 A [Region](pt01ch45pyo03.md) object specifying the region to which the geometric restriction is applied.  When used with a [TopologyTask](pt01ch36pyo41.md), there is no default value.  When used with a [ShapeTask](pt01ch36pyo20.md), the default value is MODEL.               

**Optional arguments**

*axis*

                 A SymbolicConstant specifying the axis of symmetry. Possible values are AXIS_1, AXIS_2, and AXIS_3. The default value is AXIS_1.               

*csys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system. If *csys*=`None`, the global coordinate system is used. When this member is queried, it returns an Int. The default value is `None`.               

*ignoreFrozenArea*

                 A Boolean specifying whether to ignore frozen areas. The default value is OFF.               

**Return value**

           A TopologyRotationalSymmetry object.         

**Exceptions**

None.

### 36.40.2 setValues(...)

           This method modifies the TopologyRotationalSymmetry object.         

**Required arguments**

None.

**Optional arguments**

             The optional arguments to `setValues` are the same as the arguments to the [TopologyRotationalSymmetry](pt01ch36pyo40.md#ker-topologyrotationalsymmetry-topologyrotationalsymmetr-pyc) method, except for the *name* argument.           

**Return value**

None

**Exceptions**

None.

### 36.40.3 Members

         The TopologyRotationalSymmetry object has members with the same names and descriptions as the arguments to the [TopologyRotationalSymmetry](pt01ch36pyo40.md#ker-topologyrotationalsymmetry-topologyrotationalsymmetr-pyc) method.       




