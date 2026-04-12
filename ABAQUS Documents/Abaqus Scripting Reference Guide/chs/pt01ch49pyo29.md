# 49.29 SubspaceDynamicsStep object







The SubspaceDynamicsStep object is used to calculate the linearized steady-state response of the system to harmonic excitation on the basis of the subspace projection method.

The SubspaceDynamicsStep object is derived from the [AnalysisStep](pt01ch49pyo02.md) object.

**Access**

```
import step
mdb.models[*name*].steps[*name*]
```

### 49.29.1 SubspaceDynamicsStep(...)

This method creates a SubspaceDynamicsStep object.

**Path**

```
mdb.models[*name*].SubspaceDynamicsStep
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

A Float specifying the total time period of the step. The default value is 1.0.

*vectors*

The SymbolicConstant ALL or an Int specifying the number of modes to be used for subspace projection. The possible value for the SymbolicConstant is ALL. The default value is ALL.

*nlgeom*

A Boolean specifying whether to allow for geometric nonlinearity. The default value is OFF.

*maxNumInc*

An Int specifying the maximum number of increments in a step. The default value is 100.

*incSize*

A Float specifying the suggested time increment. The default value is 0.0.

*amplitude*

A SymbolicConstant specifying the amplitude variation for loading magnitudes during the step. Possible values are STEP and RAMP. The default value is STEP.

*maintainAttributes*

A Boolean specifying whether to retain attributes from an existing step with the same name. The default value is False.

**Return value**

A SubspaceDynamicsStep object.

**Exceptions**

RangeError.

### 49.29.2 setValues(...)

This method modifies the SubspaceDynamicsStep object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [SubspaceDynamicsStep](pt01ch49pyo29.md#ker-subspacedynamicsstep-subspacedynamicsstep-pyc) method, except for the *name*, *previous*, and *maintainAttributes* arguments.

**Return value**

None

**Exceptions**

RangeError.

### 49.29.3 Members

The SubspaceDynamicsStep object can have the following members:

*name*

A String specifying the repository key.

*timePeriod*

A Float specifying the total time period of the step. The default value is 1.0.

*vectors*

The SymbolicConstant ALL or an Int specifying the number of modes to be used for subspace projection. The possible value for the SymbolicConstant is ALL. The default value is ALL.

*nlgeom*

A Boolean specifying whether to allow for geometric nonlinearity. The default value is OFF.

*maxNumInc*

An Int specifying the maximum number of increments in a step. The default value is 100.

*incSize*

A Float specifying the suggested time increment. The default value is 0.0.

*amplitude*

A SymbolicConstant specifying the amplitude variation for loading magnitudes during the step. Possible values are STEP and RAMP. The default value is STEP.

*previous*

A String specifying the name of the previous step. The new step appears after this step in the list of analysis steps.

*description*

A String specifying a description of the new step. The default value is an empty string.

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

### 49.29.4 Corresponding analysis keywords

| [*DYNAMIC](../key/key-link.md#usb-kws-hdynamic) |
| --- |
| [*STEP](../key/key-link.md#usb-kws-hstep) |




