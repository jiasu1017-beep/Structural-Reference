# 49.26 SteadyStateDirectStep object







The SteadyStateDirectStep object is used to calculate the linearized steady-state response of the system to harmonic excitation in terms of the physical degrees of freedom of the model. 

The SteadyStateDirectStep object is derived from the [AnalysisStep](pt01ch49pyo02.md) object.

**Access**

```
import step
mdb.models[*name*].steps[*name*]
```

### 49.26.1 SteadyStateDirectStep(...)

This method creates a SteadyStateDirectStep object.

**Path**

```
mdb.models[*name*].SteadyStateDirectStep
```

**Required arguments**

*name*

A String specifying the repository key.

*previous*

A String specifying the name of the previous step. The new step appears after this step in the list of analysis steps.

*frequencyRange*

A [SteadyStateDirectFrequencyArray](pt01ch50pyo17.md) object.

**Optional arguments**

*description*

A String specifying a description of the new step. The default value is an empty string.

*factorization*

A SymbolicConstant specifying whether damping terms are to be ignored so that a real, rather than a complex, system matrix is factored. Possible values are REAL_ONLY and COMPLEX. The default value is COMPLEX.

*scale*

A SymbolicConstant specifying whether a logarithmic or linear scale is used for output. Possible values are LOGARITHMIC and LINEAR. The default value is LOGARITHMIC.

*matrixStorage*

A SymbolicConstant specifying the type of matrix storage. Possible values are SYMMETRIC, UNSYMMETRIC, and SOLVER_DEFAULT. The default value is SOLVER_DEFAULT.

*maintainAttributes*

A Boolean specifying whether to retain attributes from an existing step with the same name. The default value is False.

*subdivideUsingEigenfrequencies*

A Boolean specifying whether to subdivide each frequency range using the eigenfrequencies of the system. The default value is OFF.

*frictionDamping*

A Boolean specifying whether to add to the damping matrix contributions due to friction effects. The default value is OFF.

**Return value**

A SteadyStateDirectStep object.

**Exceptions**

RangeError.

### 49.26.2 setValues(...)

This method modifies the SteadyStateDirectStep object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [SteadyStateDirectStep](pt01ch49pyo26.md#ker-steadystatedirectstep-steadystatedirectstep-pyc) method, except for the *name*, *previous*, and *maintainAttributes* arguments.

**Return value**

None

**Exceptions**

RangeError.

### 49.26.3 Members

The SteadyStateDirectStep object can have the following members:

*name*

A String specifying the repository key.

*factorization*

A SymbolicConstant specifying whether damping terms are to be ignored so that a real, rather than a complex, system matrix is factored. Possible values are REAL_ONLY and COMPLEX. The default value is COMPLEX.

*scale*

A SymbolicConstant specifying whether a logarithmic or linear scale is used for output. Possible values are LOGARITHMIC and LINEAR. The default value is LOGARITHMIC.

*matrixStorage*

A SymbolicConstant specifying the type of matrix storage. Possible values are SYMMETRIC, UNSYMMETRIC, and SOLVER_DEFAULT. The default value is SOLVER_DEFAULT.

*subdivideUsingEigenfrequencies*

A Boolean specifying whether to subdivide each frequency range using the eigenfrequencies of the system. The default value is OFF.

*frictionDamping*

A Boolean specifying whether to add to the damping matrix contributions due to friction effects. The default value is OFF.

*previous*

A String specifying the name of the previous step. The new step appears after this step in the list of analysis steps.

*description*

A String specifying a description of the new step. The default value is an empty string.

*frequencyRange*

A [SteadyStateDirectFrequencyArray](pt01ch50pyo17.md) object.

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

### 49.26.4 Corresponding analysis keywords

| [*STEADY STATE DYNAMICS](../key/key-link.md#usb-kws-hsteadystdyn) |
| --- |
| [*STEP](../key/key-link.md#usb-kws-hstep) |




