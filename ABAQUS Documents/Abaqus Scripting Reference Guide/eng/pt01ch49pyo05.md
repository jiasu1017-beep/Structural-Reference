# 49.5 ComplexFrequencyStep object







The ComplexFrequencyStep object is used to perform eigenvalue extraction to calculate the complex eigenvalues and corresponding complex mode shapes of a system.

The ComplexFrequencyStep object is derived from the [AnalysisStep](pt01ch49pyo02.md) object.

**Access**

```
import step
mdb.models[*name*].steps[*name*]
```

### 49.5.1 ComplexFrequencyStep(...)

This method creates a ComplexFrequencyStep object. 

**Path**

```
mdb.models[*name*].ComplexFrequencyStep
```

**Required arguments**

*name*

A String specifying the repository key.

*previous*

A String specifying the name of the previous step. The new step appears after this step in the list of analysis steps.

**Optional arguments**

*numEigen*

The SymbolicConstant ALL or an Int specifying the number of complex eigenmodes to be calculated or a SymbolicConstant ALL. The default value is ALL.

*description*

A String specifying a description of the new step. The default value is an empty string.

*shift*

 `None` or a Float specifying the shift point in cycles per time. The default value is `None`.

*frictionDamping*

A Boolean specifying whether to add to the damping matrix contributions due to friction effects. The default value is OFF.

*matrixStorage*

A SymbolicConstant specifying the type of matrix storage. Possible values are SYMMETRIC, UNSYMMETRIC, and SOLVER_DEFAULT. The default value is SOLVER_DEFAULT.

*maintainAttributes*

A Boolean specifying whether to retain attributes from an existing step with the same name. The default value is False.

*minEigen*

 `None` or a Float specifying the minimum frequency of interest in cycles per time. The default value is `None`.

*maxEigen*

 `None` or a Float specifying the maximum frequency of interest in cycles per time. The default value is `None`.

*propertyEvaluationFrequency*

 `None` or a Float specifying the frequency at which to evaluate frequency-dependent properties for viscoelasticity, springs, and dashpots during the eigenvalue extraction. If the value is `None`, the analysis product will evaluate the stiffness associated with frequency-dependent springs and dashpots at zero frequency and will not consider the stiffness contributions from frequency-domain viscoelasticity in the step. The default value is `None`.

**Return value**

A ComplexFrequencyStep object.

**Exceptions**

RangeError.

### 49.5.2 setValues(...)

This method modifies the ComplexFrequencyStep object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ComplexFrequencyStep](pt01ch49pyo05.md#ker-complexfrequencystep-complexfrequencystep-pyc) method, except for the *name*, *previous*, and *maintainAttributes* arguments.

**Return value**

None

**Exceptions**

RangeError.

### 49.5.3 Members

The ComplexFrequencyStep object can have the following members:

*name*

A String specifying the repository key.

*numEigen*

The SymbolicConstant ALL or an Int specifying the number of complex eigenmodes to be calculated or a SymbolicConstant ALL. The default value is ALL.

*shift*

 `None` or a Float specifying the shift point in cycles per time. The default value is `None`.

*frictionDamping*

A Boolean specifying whether to add to the damping matrix contributions due to friction effects. The default value is OFF.

*matrixStorage*

A SymbolicConstant specifying the type of matrix storage. Possible values are SYMMETRIC, UNSYMMETRIC, and SOLVER_DEFAULT. The default value is SOLVER_DEFAULT.

*minEigen*

 `None` or a Float specifying the minimum frequency of interest in cycles per time. The default value is `None`.

*maxEigen*

 `None` or a Float specifying the maximum frequency of interest in cycles per time. The default value is `None`.

*propertyEvaluationFrequency*

 `None` or a Float specifying the frequency at which to evaluate frequency-dependent properties for viscoelasticity, springs, and dashpots during the eigenvalue extraction. If the value is `None`, the analysis product will evaluate the stiffness associated with frequency-dependent springs and dashpots at zero frequency and will not consider the stiffness contributions from frequency-domain viscoelasticity in the step. The default value is `None`.

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

### 49.5.4 Corresponding analysis keywords

| [*COMPLEX FREQUENCY](../key/key-link.md#usb-kws-hcomplexfrequency) |
| --- |
| [*STEP](../key/key-link.md#usb-kws-hstep) |




