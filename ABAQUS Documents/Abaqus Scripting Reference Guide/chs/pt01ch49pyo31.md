# 49.31 TempDisplacementDynamicsStep object







The TempDisplacementDynamicsStep object is used to perform a dynamic coupled thermal-stress analysis using explicit integration.

The TempDisplacementDynamicsStep object is derived from the [AnalysisStep](pt01ch49pyo02.md) object.

**Access**

```
import step
mdb.models[*name*].steps[*name*]
```

### 49.31.1 TempDisplacementDynamicsStep(...)

This method creates a TempDisplacementDynamicsStep object. 

**Path**

```
mdb.models[*name*].TempDisplacementDynamicsStep
```

**Required arguments**

*name*

A String specifying the repository key.

*previous*

A String specifying the name of the previous step. The new step appears after this step in the list of analysis steps.

**Optional arguments**

*description*

A String specifying a description of the new step. The default value is an empty string.

*timePeriod*

A Float specifying the time period of the step. The default value is 1.0.

*nlgeom*

A Boolean specifying whether geometric nonlinearities should be accounted for during the step. The default value is OFF.

*timeIncrementationMethod*

A SymbolicConstant specifying the time incrementation method to be used. Possible values are AUTOMATIC_GLOBAL, AUTOMATIC_EBE, FIXED_USER_DEFINED_INC, and FIXED_EBE. The default value is AUTOMATIC_GLOBAL.

*maxIncrement*

 `None` or a Float specifying the maximum time increment allowed. If there is no upper limit, *maxIncrement*=`None`. The default value is `None`.

*scaleFactor*

A Float specifying the factor that is used to scale the time increment. This argument is required only when *timeIncrementationMethod*=AUTOMATIC_GLOBAL, AUTOMATIC_EBE, or FIXED_EBE. The default value is 1.0.

*userDefinedInc*

 `None` or a Float specifying the user-defined time increment. The default value is `None`.

*massScaling*

A [MassScalingArray](pt01ch50pyo09.md) object specifying mass scaling controls. The default value is PREVIOUS_STEP.

*linearBulkViscosity*

A Float specifying the linear bulk viscosity parameter, ![](../graphics/ker_eqn00420.gif). The default value is 0.06.

*quadBulkViscosity*

A Float specifying the quadratic bulk viscosity parameter, ![](../graphics/ker_eqn00421.gif). The default value is 1.2.

*maintainAttributes*

A Boolean specifying whether to retain attributes from an existing step with the same name. The default value is False.

**Return value**

A TempDisplacementDynamicsStep object.

**Exceptions**

RangeError.

### 49.31.2 setValues(...)

This method modifies the TempDisplacementDynamicsStep object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [TempDisplacementDynamicsStep](pt01ch49pyo31.md#ker-tempdisplacementdynamicsstep-tempdisplacementdynamic-pyc) method, except for the *name*, *previous*, and *maintainAttributes* arguments.

**Return value**

None

**Exceptions**

RangeError.

### 49.31.3 Members

The TempDisplacementDynamicsStep object can have the following members:

*name*

A String specifying the repository key.

*timePeriod*

A Float specifying the time period of the step. The default value is 1.0.

*nlgeom*

A Boolean specifying whether geometric nonlinearities should be accounted for during the step. The default value is OFF.

*timeIncrementationMethod*

A SymbolicConstant specifying the time incrementation method to be used. Possible values are AUTOMATIC_GLOBAL, AUTOMATIC_EBE, FIXED_USER_DEFINED_INC, and FIXED_EBE. The default value is AUTOMATIC_GLOBAL.

*maxIncrement*

 `None` or a Float specifying the maximum time increment allowed. If there is no upper limit, *maxIncrement*=`None`. The default value is `None`.

*scaleFactor*

A Float specifying the factor that is used to scale the time increment. This argument is required only when *timeIncrementationMethod*=AUTOMATIC_GLOBAL, AUTOMATIC_EBE, or FIXED_EBE. The default value is 1.0.

*userDefinedInc*

 `None` or a Float specifying the user-defined time increment. The default value is `None`.

*linearBulkViscosity*

A Float specifying the linear bulk viscosity parameter, ![](../graphics/ker_eqn00420.gif). The default value is 0.06.

*quadBulkViscosity*

A Float specifying the quadratic bulk viscosity parameter, ![](../graphics/ker_eqn00421.gif). The default value is 1.2.

*previous*

A String specifying the name of the previous step. The new step appears after this step in the list of analysis steps.

*description*

A String specifying a description of the new step. The default value is an empty string.

*massScaling*

A [MassScalingArray](pt01ch50pyo09.md) object specifying mass scaling controls. The default value is PREVIOUS_STEP.

*explicit*

A SymbolicConstant specifying whether the step has an explicit procedure type (*procedureType*=ANNEAL, DYNAMIC_EXPLICIT, or DYNAMIC_TEMP_DISPLACEMENT).

*perturbation*

A Boolean specifying whether the step has a perturbation procedure type.

*nonmechanical*

A Boolean specifying whether the step has a mechanical procedure type.

*procedureType*

A SymbolicConstant specifying the Abaqus procedure. Possible values are:
- ANNEAL
- BUCKLE
- COMPLEX_FREQUENCY
- COUPLED_TEMP_DISPLACEMENT
- COUPLED_THERMAL_ELECTRIC
- DIRECT_CYCLIC
- DYNAMIC_IMPLICIT
- DYNAMIC_EXPLICIT
- DYNAMIC_SUBSPACE
- DYNAMIC_TEMP_DISPLACEMENT
- COUPLED_THERMAL_ELECTRICAL_STRUCTURAL
- FLOW
- FREQUENCY
- GEOSTATIC
- HEAT_TRANSFER
- MASS_DIFFUSION
- MODAL_DYNAMICS
- RANDOM_RESPONSE
- RESPONSE_SPECTRUM
- SOILS
- STATIC_GENERAL
- STATIC_LINEAR_PERTURBATION
- STATIC_RIKS
- STEADY_STATE_DIRECT
- STEADY_STATE_MODAL
- STEADY_STATE_SUBSPACE
- VISCO

*suppressed*

A Boolean specifying whether the step is suppressed or not. The default value is OFF.

*fieldOutputRequestState*

A repository of [FieldOutputRequestState](pt01ch51pyo03.md) objects.

*historyOutputRequestState*

A repository of [HistoryOutputRequestState](pt01ch51pyo05.md) objects.

*diagnosticPrint*

A [DiagnosticPrint](pt01ch51pyo01.md) object.

*monitor*

A [Monitor](pt01ch51pyo07.md) object.

*restart*

A [Restart](pt01ch51pyo08.md) object.

*adaptiveMeshConstraintStates*

A repository of [AdaptiveMeshConstraintState](pt01ch02pyo02.md) objects.

*adaptiveMeshDomains*

A repository of [AdaptiveMeshDomain](pt01ch02pyo04.md) objects.

*control*

A [Control](pt01ch50pyo03.md) object.

*solverControl*

A [SolverControl](pt01ch50pyo16.md) object.

*boundaryConditionStates*

A repository of [BoundaryConditionState](pt01ch09pyo08.md) objects.

*interactionStates*

A repository of [InteractionState](pt01ch25pyo49.md) objects.

*loadStates*

A repository of [LoadState](pt01ch27pyo42.md) objects.

*loadCases*

A repository of [LoadCase](pt01ch28pyo01.md) objects.

*predefinedFieldStates*

A repository of [PredefinedFieldState](pt01ch42pyo12.md) objects.

### 49.31.4 Corresponding analysis keywords

| [*BULK VISCOSITY](../key/key-link.md#usb-kws-hbulkvisco) |
| --- |
| [*DYNAMIC](../key/key-link.md#usb-kws-hdynamic) |
| [*FIXED MASS SCALING](../key/key-link.md#usb-kws-hfixedmassscaling) |
| [*STEP](../key/key-link.md#usb-kws-hstep) |
| [*VARIABLE MASS SCALING](../key/key-link.md#usb-kws-hvariablemassscaling) |




