# 9.19 DisplacementBC object







The DisplacementBC object stores the data for a displacement/rotation boundary condition.

The DisplacementBC object is derived from the [BoundaryCondition](pt01ch09pyo01.md) object.

**Access**

```
import load
mdb.models[*name*].boundaryConditions[*name*]
```

### 9.19.1 DisplacementBC(...)

This method creates a DisplacementBC object.

**Path**

```
mdb.models[*name*].DisplacementBC
```

**Required arguments**

*name*

A String specifying the boundary condition repository key.

*createStepName*

A String specifying the name of the step in which the boundary condition is created.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the boundary condition is applied.

**Optional arguments**

*fieldName*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) or [DiscreteField](pt01ch21pyo04.md) object associated with this boundary condition. The *fieldName* argument applies only when *distributionType*=FIELD or *distributionType*=DISCRETE_FIELD. The default value is an empty string.

*u1*

A Float, a Complex, or a SymbolicConstant specifying the displacement component in the 1-direction. Possible values for the SymbolicConstant are UNSET and SET. The default value is UNSET.

**Note:**Although *u1*, *u2*, *u3*, *ur1*, *ur2*, and *ur3* are optional arguments, at least one of them must be specified.

*u2*

A Float, a Complex, or a SymbolicConstant specifying the displacement component in the 2-direction. Possible values for the SymbolicConstant are UNSET and SET. The default value is UNSET.

*u3*

A Float, a Complex, or a SymbolicConstant specifying the displacement component in the 3-direction. Possible values for the SymbolicConstant are UNSET and SET. The default value is UNSET.

*ur1*

A Float, a Complex, or a SymbolicConstant specifying the rotational displacement component about the 1-direction. Possible values for the SymbolicConstant are UNSET and SET. The default value is UNSET.

*ur2*

A Float, a Complex, or a SymbolicConstant specifying the rotational displacement component about the 2-direction. Possible values for the SymbolicConstant are UNSET and SET. The default value is UNSET.

*ur3*

A Float, a Complex, or a SymbolicConstant specifying the rotational displacement component about the 3-direction. Possible values for the SymbolicConstant are UNSET and SET. The default value is UNSET.

*fixed*

A Boolean specifying whether the boundary condition should remain fixed at the current values at the start of the step. The default value is OFF.

*amplitude*

A String or the SymbolicConstant UNSET specifying the name of the amplitude reference. UNSET should be used if the boundary condition has no amplitude reference. The default value is UNSET. You should provide the *amplitude* argument only if it is valid for the specified step.

*distributionType*

A SymbolicConstant specifying how the boundary condition is distributed spatially. Possible values are UNIFORM, USER_DEFINED, FIELD, and DISCRETE_FIELD. The default value is UNIFORM.

*localCsys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system of the boundary condition's degrees of freedom. If *localCsys*=`None`, the degrees of freedom are defined in the global coordinate system. The default value is `None`.

*buckleCase*

A SymbolicConstant specifying how the boundary condition is defined in a [*BUCKLE](../key/key-link.md#usb-kws-hbuckle) analysis. Possible values are NOT_APPLICABLE, STRESS_PERTURBATION, BUCKLING_MODES, and PERTURBATION_AND_BUCKLING. The default value is NOT_APPLICABLE.

**Return value**

A DisplacementBC object.

**Exceptions**

None.

### 9.19.2 setValues(...)

This method modifies the data for an existing DisplacementBC object in the step where it is created.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [DisplacementBC](pt01ch09pyo19.md#ker-displacementbc-displacementbc-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 9.19.3 setValuesInStep(...)

This method modifies the propagating data for an existing DisplacementBC object in the specified step.

**Required argument**

*stepName*

A String specifying the name of the step in which the boundary condition is modified.

**Optional arguments**

*u1*

A Float, a Complex, or a SymbolicConstant specifying the displacement component in the 1-direction. Possible values for the SymbolicConstant are SET, UNCHANGED, and FREED.

*u2*

A Float, a Complex, or a SymbolicConstant specifying the displacement component in the 2-direction. Possible values for the SymbolicConstant are SET, UNCHANGED, and FREED.

*u3*

A Float, a Complex, or a SymbolicConstant specifying the displacement component in the 3-direction. Possible values for the SymbolicConstant are SET, UNCHANGED, and FREED.

*ur1*

A Float, a Complex, or a SymbolicConstant specifying the rotational displacement component about the 1-direction. Possible values for the SymbolicConstant are SET, UNCHANGED, and FREED.

*ur2*

A Float, a Complex, or a SymbolicConstant specifying the rotational displacement component about the 2-direction. Possible values for the SymbolicConstant are SET, UNCHANGED, and FREED.

*ur3*

A Float, a Complex, or a SymbolicConstant specifying the rotational displacement component about the 3-direction. Possible values for the SymbolicConstant are SET, UNCHANGED, and FREED.

*amplitude*

A String or a SymbolicConstant specifying the name of the amplitude reference. Possible values for the SymbolicConstant are UNCHANGED and FREED. UNCHANGED should be used if the amplitude is propagated from the previous analysis step. FREED should be used if the boundary condition is changed to have no amplitude reference. You should provide the *amplitude* argument only if it is valid for the specified step.

*buckleCase*

A SymbolicConstant specifying how the boundary condition is defined in a [*BUCKLE](../key/key-link.md#usb-kws-hbuckle) analysis. Possible values are NOT_APPLICABLE, STRESS_PERTURBATION, BUCKLING_MODES, and PERTURBATION_AND_BUCKLING. The default value is NOT_APPLICABLE.

**Return value**

None

**Exceptions**

None.

### 9.19.4 Members

The DisplacementBC object can have the following members:

*name*

A String specifying the boundary condition repository key.

*distributionType*

A SymbolicConstant specifying how the boundary condition is distributed spatially. Possible values are UNIFORM, USER_DEFINED, FIELD, and DISCRETE_FIELD. The default value is UNIFORM.

*fixed*

A Boolean specifying whether the boundary condition should remain fixed at the current values at the start of the step. The default value is OFF.

*buckleCase*

A SymbolicConstant specifying how the boundary condition is defined in a [*BUCKLE](../key/key-link.md#usb-kws-hbuckle) analysis. Possible values are NOT_APPLICABLE, STRESS_PERTURBATION, BUCKLING_MODES, and PERTURBATION_AND_BUCKLING. The default value is NOT_APPLICABLE.

*fieldName*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) or [DiscreteField](pt01ch21pyo04.md) object associated with this boundary condition. The *fieldName* argument applies only when *distributionType*=FIELD or *distributionType*=DISCRETE_FIELD. The default value is an empty string.

*category*

A SymbolicConstant specifying the category of the boundary condition. Possible values are MECHANICAL and THERMAL.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the boundary condition is applied.

*localCsys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system of the boundary condition's degrees of freedom. If *localCsys*=`None`, the degrees of freedom are defined in the global coordinate system. The default value is `None`.




