# 9.32 FluidWallConditionBCState object







The FluidWallConditionBCState object stores the propagating data of a fluid wall condition boundary condition in a step. One instance of this object is created internally by the [FluidWallConditionBC](pt01ch09pyo31.md) object for each step. The instance is also deleted internally by the [FluidWallConditionBC](pt01ch09pyo31.md) object.

The FluidWallConditionBCState object has no constructor or methods.

The FluidWallConditionBCState object is derived from the [BoundaryConditionState](pt01ch09pyo08.md) object.

**Access**

```
import load
mdb.models[*name*].steps[*name*].boundaryConditionStates[*name*]
```

### 9.32.1 Members

The FluidWallConditionBCState object has the following members:

*type*

A SymbolicConstant specifying the type of wall condition boundary condition. Possible values are INFILTRATION, NO_SLIP, and SHEAR. The default value is NO_SLIP.

*v1*

 `None` or a Float specifying the velocity component in the 1-direction of the global coordinate system. The default value is `None`.

*v2*

 `None` or a Float specifying the velocity component in the 2-direction of the global coordinate system. The default value is `None`.

*v3*

 `None` or a Float specifying the velocity component in the 3-direction of the global coordinate system. The default value is `None`.

*velocityAmplitude*

 `None` or a String specifying the name of the amplitude reference that gives the variation of the velocities with time. The default value is NONE.

*thermalEnergyType*

A SymbolicConstant specifying the type of boundary condition defined on thermal energy equation. Possible values are HEAT_FLUX, NONE, and TEMPERATURE. The default value is NONE.

*temperature*

 `None` or a Float specifying the temperature magnitude. The default value is `None`.

*heatFlux*

 `None` or a Float specifying the heat flux magnitude. The default value is `None`.

*thermalEnergyAmplitude*

 `None` or a String specifying the name of the amplitude reference that gives the variation of the boundary condition values with time on thermal energy equation. The default value is NONE.

*kineticEnergy*

 `None` or a Float specifying the kinetic energy magnitude. The default value is `None`.

*kineticEnergyAmplitude*

 `None` or a String specifying the name of the amplitude reference that gives the variation of the kinetic energy with time. The default value is NONE.

*dissipationRate*

 `None` or a Float specifying the dissipation rate magnitude. The default value is `None`.

*dissipationRateAmplitude*

 `None` or a String specifying the name of the amplitude reference that gives the variation of the dissipation rate with time. The default value is NONE.

*eddyViscosity*

 `None` or a Float specifying the eddy viscosity magnitude. The default value is `None`.

*eddyViscosityAmplitude*

 `None` or a String specifying the name of the amplitude reference that gives the variation of the eddy viscosity with time. The default value is NONE.

*typeState*

A SymbolicConstant specifying the propagation state of the *type* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*v1State*

A SymbolicConstant specifying the propagation state of the *v1* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*v2State*

A SymbolicConstant specifying the propagation state of the *v2* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*v3State*

A SymbolicConstant specifying the propagation state of the *v3* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*velocityAmplitudeState*

A SymbolicConstant specifying the propagation state of the *velocityAmplitude* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*thermalEnergyTypeState*

A SymbolicConstant specifying the propagation state of the *thermalEnergyType* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*temperatureState*

A SymbolicConstant specifying the propagation state of the *temperature* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*heatFluxState*

A SymbolicConstant specifying the propagation state of the *heatFlux* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*thermalEnergyAmplitudeState*

A SymbolicConstant specifying the propagation state of the *thermalEnergyAmplitude* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*kineticEnergyState*

A SymbolicConstant specifying the propagation state of the *kineticEnergy* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*kineticEnergyAmplitudeState*

A SymbolicConstant specifying the propagation state of the *kineticEnergyAmplitude* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*dissipationRateState*

A SymbolicConstant specifying the propagation state of the *dissipationRate* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*dissipationRateAmplitudeState*

A SymbolicConstant specifying the propagation state of the *dissipationRateAmplitude* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*eddyViscosityState*

A SymbolicConstant specifying the propagation state of the *eddyViscosity* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*eddyViscosityAmplitudeState*

A SymbolicConstant specifying the propagation state of the *eddyViscosityAmplitude* member. Possible values are UNSET, SET, UNCHANGED, and FREED.

*amplitudeState*

A SymbolicConstant specifying the propagation state of the amplitude reference. Possible values are UNSET, SET, UNCHANGED, FREED, and MODIFIED.

*status*

A SymbolicConstant specifying the propagation state of the [BoundaryConditionState](pt01ch09pyo08.md) object. Possible values are:
- NOT_YET_ACTIVE
- CREATED
- PROPAGATED
- MODIFIED
- DEACTIVATED
- NO_LONGER_ACTIVE
- TYPE_NOT_APPLICABLE
- INSTANCE_NOT_APPLICABLE
- PROPAGATED_FROM_BASE_STATE
- MODIFIED_FROM_BASE_STATE
- DEACTIVATED_FROM_BASE_STATE
- BUILT_INTO_MODES

*amplitude*

A String specifying the name of the amplitude reference. The String is empty if the boundary condition has no amplitude reference.

### 9.32.2 Corresponding analysis keywords

| [*DSLOAD](../key/key-link.md#usb-kws-hdsload), TYPE=ACCELERATION (load type label: DIST, TEMP, TURBNU, VELX, VELY, or VELZ) |
| --- |

| [*DSFLUX](../key/key-link.md#usb-kws-hdsflux) (load type label: S) |
| --- |




