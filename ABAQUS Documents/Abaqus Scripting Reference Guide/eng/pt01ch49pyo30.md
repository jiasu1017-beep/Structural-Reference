# 49.30 SubstructureGenerateStep object







TheSubstructureGenerateStep               object is used to generate a substructure.

The SubstructureGenerateStep object is derived from the [AnalysisStep](pt01ch49pyo02.md) object.

**Access**

```
import step
mdb.models[*name*].steps[*name*]
```

### 49.30.1 SubstructureGenerateStep(...)

This method creates a SubstructureGenerateStep object.

**Path**

```
mdb.models[*name*].SubstructureGenerateStep
```

**Required arguments**

*name*

A String specifying the repository key.

*previous*

A String specifying the name of the previous step. The new step appears after this step in the list of analysis steps.

*substructureIdentifier*

A String specifying a unique identifier for the substructure. The default value is an empty string.

**Optional arguments**

*description*

A String specifying a description of the new step. The default value is an empty string.

*recoveryMatrix*

A SymbolicConstant specifying the subtructure recovery to be computed. Possible values are WHOLE_MODEL, REGION, and NONE. The default value is WHOLE_MODEL.

*recoveryRegion*

A [Region](pt01ch45pyo03.md) object specifying the region for substructure recovery. This argument is required when *recoveryMatrix*=REGION.

*computeGravityLoadVectors*

A Boolean specifying whether to compute the gravity load vectors. The default value is False.

*computeReducedMassMatrix*

A Boolean specifying whether to compute the reduced mass matrix. The default value is False.

*computeReducedStructuralDampingMatrix*

A Boolean specifying whether to compute the reduced structural damping matrix. The default value is False.

*computeReducedViscousDampingMatrix*

A Boolean specifying whether to compute the reduced viscous damping matrix. The default value is False.

*evaluateFrequencyDependentProperties*

A Boolean specifying whether to evaluate the frequency dependent properties. The default value is False.

*frequency*

A Float specifying the frequency at which to evaluate the frequency dependent properties. The default value is 0.0.

*retainedEigenmodesMethod*

A SymbolicConstant specifying the eigenmodes to be retained. Possible values are MODE_RANGE, FREQUENCY_RANGE, and NONE. The default value is NONE.

*modeRange*

A [SubstructureGenerateModesArray](pt01ch50pyo25.md) object.

*frequencyRange*

A [SubstructureGenerateFrequencyArray](pt01ch50pyo24.md) object.

*globalDampingField*

A SymbolicConstant specifying the field to which the global damping factors should be applied. Possible values are ALL, ACOUSTIC, MECHANICAL, and NONE. The default value is NONE.

*alphaDampingRatio*

A Float specifying the factor to create global Rayleigh mass proportional damping. The default value is 0.0.

*betaDampingRatio*

A Float specifying the factor to create global Rayleigh stiffness proportional damping. The default value is 0.0.

*structuralDampingRatio*

A Float specifying the factor to create frequency-independent stiffness proportional structural damping. The default value is 0.0.

*viscousDampingControl*

A SymbolicConstant specifying the damping control to include the viscous damping matrix. Possible values are ELEMENT, FACTOR, COMBINED, and NONE. The default value is NONE.

*structuralDampingControl*

A SymbolicConstant specifying the damping control to include the structural damping matrix. Possible values are ELEMENT, FACTOR, COMBINED, and NONE. The default value is NONE.

**Return value**

A SubstructureGenerateStep object.

**Exceptions**

RangeError.

### 49.30.2 setValues(...)

This method modifies the SubstructureGenerateStep object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [SubstructureGenerateStep](pt01ch49pyo30.md#ker-substructuregeneratestep-substructuregeneratestep-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 49.30.3 Members

The SubstructureGenerateStep object can have the following members:

*name*

A String specifying the repository key.

*recoveryMatrix*

A SymbolicConstant specifying the subtructure recovery to be computed. Possible values are WHOLE_MODEL, REGION, and NONE. The default value is WHOLE_MODEL.

*frequency*

A Float specifying the frequency at which to evaluate the frequency dependent properties. The default value is 0.0.

*retainedEigenmodesMethod*

A SymbolicConstant specifying the eigenmodes to be retained. Possible values are MODE_RANGE, FREQUENCY_RANGE, and NONE. The default value is NONE.

*globalDampingField*

A SymbolicConstant specifying the field to which the global damping factors should be applied. Possible values are ALL, ACOUSTIC, MECHANICAL, and NONE. The default value is NONE.

*alphaDampingRatio*

A Float specifying the factor to create global Rayleigh mass proportional damping. The default value is 0.0.

*betaDampingRatio*

A Float specifying the factor to create global Rayleigh stiffness proportional damping. The default value is 0.0.

*structuralDampingRatio*

A Float specifying the factor to create frequency-independent stiffness proportional structural damping. The default value is 0.0.

*viscousDampingControl*

A SymbolicConstant specifying the damping control to include the viscous damping matrix. Possible values are ELEMENT, FACTOR, COMBINED, and NONE. The default value is NONE.

*structuralDampingControl*

A SymbolicConstant specifying the damping control to include the structural damping matrix. Possible values are ELEMENT, FACTOR, COMBINED, and NONE. The default value is NONE.

*previous*

A String specifying the name of the previous step. The new step appears after this step in the list of analysis steps.

*description*

A String specifying a description of the new step. The default value is an empty string.

*substructureIdentifier*

A String specifying a unique identifier for the substructure. The default value is an empty string.

*recoveryRegion*

A [Region](pt01ch45pyo03.md) object specifying the region for substructure recovery. This argument is required when *recoveryMatrix*=REGION.

*frequencyRange*

A [SubstructureGenerateFrequencyArray](pt01ch50pyo24.md) object.

*modeRange*

A [SubstructureGenerateModesArray](pt01ch50pyo25.md) object.

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

### 49.30.4 Corresponding analysis keywords

| [*SUBSTRUCTURE GENERATE](../key/key-link.md#usb-kws-ssubgenerate) |
| --- |
| [*STEP](../key/key-link.md#usb-kws-hstep) |




