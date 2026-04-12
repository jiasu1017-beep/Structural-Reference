# 49.19 ModalDynamicsStep object







The ModalDynamicsStep object is used to provide dynamic time history response as a linear perturbation procedure using modal superposition.

The ModalDynamicsStep object is derived from the [AnalysisStep](pt01ch49pyo02.md) object.

**Access**

```
import step
mdb.models[*name*].steps[*name*]
```

### 49.19.1 ModalDynamicsStep(...)

This method creates a ModalDynamicsStep object. 

**Path**

```
mdb.models[*name*].ModalDynamicsStep
```

**Required arguments**

*name*

A String specifying the repository key.

*previous*

A String specifying the name of the previous step. The new step appears after this step in the list of analysis steps.

**Optional arguments**

*description*

A String specifying a description of the new step. The default value is an empty string.

*continueAnalysis*

A Boolean specifying that the step starts with zero initial conditions. The default value is OFF.

*timePeriod*

A Float specifying the total time period. The default value is 1.0.

*incSize*

A Float specifying the time increment to be used. The default value is 1.0.

*directDamping*

A [DirectDamping](pt01ch50pyo04.md) object.

*compositeDamping*

A [CompositeDamping](pt01ch50pyo01.md) object.

*rayleighDamping*

A [RayleighDamping](pt01ch50pyo11.md) object.

*amplitude*

A SymbolicConstant specifying the amplitude variation for loading magnitudes during the step. Possible values are STEP and RAMP. The default value is STEP.

*maintainAttributes*

A Boolean specifying whether to retain attributes from an existing step with the same name. The default value is False.

*directDampingByFrequency*

A [DirectDampingByFrequency](pt01ch50pyo05.md) object.

*rayleighDampingByFrequency*

A [RayleighDampingByFrequency](pt01ch50pyo12.md) object.

**Return value**

A ModalDynamicsStep object.

**Exceptions**

RangeError.

### 49.19.2 setValues(...)

This method modifies the ModalDynamicsStep object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ModalDynamicsStep](pt01ch49pyo19.md#ker-modaldynamicsstep-modaldynamicsstep-pyc) method, except for the *name*, *previous*, and *maintainAttributes* arguments.

**Return value**

None

**Exceptions**

RangeError.

### 49.19.3 Members

The ModalDynamicsStep object can have the following members:

*name*

A String specifying the repository key.

*continueAnalysis*

A Boolean specifying that the step starts with zero initial conditions. The default value is OFF.

*timePeriod*

A Float specifying the total time period. The default value is 1.0.

*incSize*

A Float specifying the time increment to be used. The default value is 1.0.

*amplitude*

A SymbolicConstant specifying the amplitude variation for loading magnitudes during the step. Possible values are STEP and RAMP. The default value is STEP.

*previous*

A String specifying the name of the previous step. The new step appears after this step in the list of analysis steps.

*description*

A String specifying a description of the new step. The default value is an empty string.

*directDamping*

A [DirectDamping](pt01ch50pyo04.md) object.

*compositeDamping*

A [CompositeDamping](pt01ch50pyo01.md) object.

*rayleighDamping*

A [RayleighDamping](pt01ch50pyo11.md) object.

*directDampingByFrequency*

A [DirectDampingByFrequency](pt01ch50pyo05.md) object.

*rayleighDampingByFrequency*

A [RayleighDampingByFrequency](pt01ch50pyo12.md) object.

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

### 49.19.4 Corresponding analysis keywords

| [*DAMPING](../key/key-link.md#usb-kws-mdamping) |
| --- |
| [*MODAL DAMPING](../key/key-link.md#usb-kws-hmodaldamp) |
| [*MODAL DYNAMIC](../key/key-link.md#usb-kws-hmodaldyn) |
| [*STEP](../key/key-link.md#usb-kws-hstep) |




