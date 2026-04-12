# 9.31 FluidWallConditionBC object







The FluidWallConditionBC object stores the data for a fluid wall condition boundary condition.

The FluidWallConditionBC object is derived from the [BoundaryCondition](pt01ch09pyo01.md) object.

**Access**

```
import load
mdb.models[*name*].boundaryConditions[*name*]
```

### 9.31.1 FluidWallConditionBC(...)

This method creates a FluidWallConditionBC object.

**Path**

```
mdb.models[*name*].FluidWallConditionBC
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

A String specifying                       The name of the [AnalyticalField](pt01ch21pyo02.md) or [DiscreteField](pt01ch21pyo04.md) object associated with this boundary condition. The *fieldName* argument applies only when *distributionType*=FIELD or *distributionType*=DISCRETE_FIELD.                     The default value is an empty string.

*distributionType*

A SymbolicConstant specifying how the boundary condition is distributed spatially. Possible values are UNIFORM, USER_DEFINED, FIELD, and DISCRETE_FIELD. The default value is UNIFORM.

*localCsys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system of the boundary condition's degrees of freedom. If *localCsys*=`None`, the degrees of freedom are defined in the global coordinate system. The default value is `None`.

*type*

A SymbolicConstant specifying the type of fluid wall condition boundary condition. Possible values are INFILTRATION, NO_SLIP and SHEAR. The default value is NO_SLIP.

*v1*

A Float or the SymbolicConstant UNSET specifying the velocity component in the 1-direction of the global coordinate system. The default value is UNSET.

*v2*

A Float or the SymbolicConstant UNSET specifying the velocity component in the 2-direction of the global coordinate system. The default value is UNSET.

*v3*

A Float or the SymbolicConstant UNSET specifying the velocity component in the 3-direction of the global coordinate system. The default value is UNSET.

*velocityAmplitude*

A String or the SymbolicConstant UNSET specifying the name of the amplitude reference that gives the variation of the velocities with time. UNSET should be used if the boundary condition has no amplitude reference. The default value is UNSET.

*thermalEnergyType*

A SymbolicConstant specifying the type of boundary condition defined on thermal energy equation. Possible values are HEAT_FLUX, TEMPERATURE, and UNSET. The default value is UNSET.

*temperature*

A Float or the SymbolicConstant UNSET specifying the temperature magnitude. Use a numeric value if *thermalEnergyType*=TEMPERATURE. The default value is UNSET.

*heatFlux*

A Float or the SymbolicConstant UNSET specifying the heat flux magnitude. Use a numeric value if *thermalEnergyType*=HEAT_FLUX. The default value is UNSET.

*thermalEnergyAmplitude*

A String or the SymbolicConstant UNSET specifying the name of the amplitude reference that gives the variation of the boundary condition values with time on thermal energy equation. UNSET should be used if the boundary condition has no amplitude reference. The default value is UNSET.

*kineticEnergy*

A Float or the SymbolicConstantUNSET                              specifying the kinetic energy magnitude. The default value isUNSET                              .

*kineticEnergyAmplitude*

A String or the SymbolicConstant UNSET specifying the name of the amplitude reference that gives the variation of the kinetic energy with time. UNSET should be used if the boundary condition has no amplitude reference. The default value is UNSET.

*dissipationRate*

A Float or the SymbolicConstant UNSET specifying the dissipation rate magnitude. The default value is UNSET.

*dissipationRateAmplitude*

A String or the SymbolicConstant UNSET specifying the name of the amplitude reference that gives the variation of the dissipation rate with time. UNSET should be used if the boundary condition has no amplitude reference. The default value is UNSET.

*eddyViscosity*

A Float or the SymbolicConstant UNSET specifying the eddy viscosity magnitude. The default value is UNSET.

*eddyViscosityAmplitude*

A String or the SymbolicConstant UNSET specifying the name of the amplitude reference that gives the variation of the eddy viscosity with time. UNSET should be used if the boundary condition has no amplitude reference. The default value is UNSET.

**Return value**

A FluidWallConditionBC object.

**Exceptions**

None.

### 9.31.2 setValues(...)

This method modifies the data for an existing FluidWallConditionBC object in the step where it is created.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [FluidWallConditionBC](pt01ch09pyo31.md#ker-fluidwallconditionbc-fluidwallconditionbc-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 9.31.3 setValuesInStep(...)

This method modifies the propagating data for an existing FluidWallConditionBC object in the specified step.

**Required argument**

*stepName*

A String specifying the name of the step in which the boundary condition is modified.

**Optional arguments**

*type*

A SymbolicConstant specifying the type of fluid wall condition boundary condition. Possible values are INFILTRATION, NO_SLIP, and SHEAR.

*v1*

A Float or the SymbolicConstant FREED specifying the velocity component in the 1-direction of the global coordinate system. Use FREED to remove the previously defined value.

*v2*

A Float or the SymbolicConstant FREED specifying the velocity component in the 2-direction of the global coordinate system. Use FREED to remove the previously defined value.

*v3*

A Float or the SymbolicConstant FREED specifying the velocity component in the 3-direction of the global coordinate system. Use FREED to remove the previously defined value.

*velocityAmplitude*

A String or the SymbolicConstant FREED specifying the name of the amplitude reference that gives the variation of the velocities with time. FREED should be used if the boundary condition has no amplitude reference.

*thermalEnergyType*

A SymbolicConstant specifying the type of boundary condition defined on thermal energy equation. Possible values are FREED, HEAT_FLUX, and TEMPERATURE. Use FREED to remove the previously defined value.

*temperature*

A Float or the SymbolicConstant FREED specifying the temperature magnitude. Use a numeric value if *thermalEnergyType*=TEMPERATURE. Otherwise, use FREED to remove the previously defined value.

*heatFlux*

A Float or the SymbolicConstant FREED specifying the heat flux magnitude. Use a numeric value if *thermalEnergyType*=HEAT_FLUX. Otherwise, use FREED to remove the previously defined value.

*thermalEnergyAmplitude*

A String or the SymbolicConstant FREED specifying the name of the amplitude reference that gives the variation of the boundary condition values with time on thermal energy equation. FREED should be used if the boundary condition has no amplitude reference.

*kineticEnergy*

A Float or the SymbolicConstant FREED specifying the kinetic energy magnitude. Use FREED to remove the previously defined value.

*kineticEnergyAmplitude*

A String or the SymbolicConstant FREED specifying the name of the amplitude reference that gives the variation of the kinetic energy with time. FREED should be used if the boundary condition has no amplitude reference.

*dissipationRate*

A Float or the SymbolicConstant FREED specifying the dissipation rate magnitude. Use FREED to remove the previously defined value.

*dissipationRateAmplitude*

A String or the SymbolicConstant FREED specifying the name of the amplitude reference that gives the variation of the dissipation rate with time. FREED should be used if the boundary condition has no amplitude reference.

*eddyViscosity*

A Float or the SymbolicConstant FREED specifying the eddy viscosity magnitude. Use FREED to remove the previously defined value.

*eddyViscosityAmplitude*

A String or the SymbolicConstant FREED specifying the name of the amplitude reference that gives the variation of the eddy viscosity with time. FREED should be used if the boundary condition has no amplitude reference.

**Return value**

None

**Exceptions**

None.

### 9.31.4 Members

The FluidWallConditionBC object can have the following members:

*name*

A String specifying the boundary condition repository key.

*distributionType*

A SymbolicConstant specifying how the boundary condition is distributed spatially. Possible values are UNIFORM, USER_DEFINED, FIELD, and DISCRETE_FIELD. The default value is UNIFORM.

*fieldName*

A String specifying                       The name of the [AnalyticalField](pt01ch21pyo02.md) or [DiscreteField](pt01ch21pyo04.md) object associated with this boundary condition. The *fieldName* argument applies only when *distributionType*=FIELD or *distributionType*=DISCRETE_FIELD.                     The default value is an empty string.

*category*

A SymbolicConstant specifying the category of the boundary condition. Possible values are MECHANICAL and THERMAL.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the boundary condition is applied.

*localCsys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system of the boundary condition's degrees of freedom. If *localCsys*=`None`, the degrees of freedom are defined in the global coordinate system. The default value is `None`.




