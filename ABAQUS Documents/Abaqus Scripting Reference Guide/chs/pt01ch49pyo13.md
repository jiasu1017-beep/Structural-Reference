# 49.13 FrequencyStep object







The FrequencyStep object is used to perform eigenvalue extraction to calculate the natural frequencies and corresponding mode shapes of a system.

The FrequencyStep object is derived from the [AnalysisStep](pt01ch49pyo02.md) object.

**Access**

```
import step
mdb.models[*name*].steps[*name*]
```

### 49.13.1 FrequencyStep(...)

This method creates a FrequencyStep object. 

**Path**

```
mdb.models[*name*].FrequencyStep
```

**Required arguments**

*name*

A String specifying the repository key.

*previous*

A String specifying the name of the previous step. The new step appears after this step in the list of analysis steps.

*eigensolver*

A SymbolicConstant specifying the eigensolver. Possible values are LANCZOS, SUBSPACE, and AMS.

The following optional arguments are ignored unless *eigensolver*=LANCZOS: *blockSize*, *maxBlocks*, *normalization*, *propertyEvaluationFrequency*.

The following optional arguments are ignored unless *eigensolver*=LANCZOS or AMS: *minEigen*, *maxEigen*, and *acousticCoupling*.

The following optional arguments are ignored unless *eigensolver*=AMS: *projectDamping*, *acousticRangeFactor*, *substructureCutoffMultiplier*, *firstCutoffMultiplier*, *secondCutoffMultiplier*, *residualModeRegion*, *regionalModeDof*, and *limitSavedEigenvectorRegion*.

**Optional arguments**

*numEigen*

The SymbolicConstant ALL or an Int specifying the number of eigenvalues to be calculated or ALL. The default value is ALL.

*description*

A String specifying a description of the new step. The default value is an empty string.

*shift*

A Float specifying the shift point in cycles per time. The default value is 0.0.

*minEigen*

 `None` or a Float specifying the minimum frequency of interest in cycles per time. The default value is `None`.

*maxEigen*

 `None` or a Float specifying the maximum frequency of interest in cycles per time. The default value is `None`.

*vectors*

 `None` or an Int specifying the number of vectors used in the iteration. The default is the minimum of (2*n*, *n* + 8), where *n* is the number of eigenvalues requested. The default value is `None`.

*maxIterations*

An Int specifying the maximum number of iterations. The default value is 30.

*blockSize*

A SymbolicConstant specifying the size of the Lanczos block steps. The default value is DEFAULT.

*maxBlocks*

A SymbolicConstant specifying the maximum number of Lanczos block steps within each Lanczos run. The default value is DEFAULT.

*normalization*

A SymbolicConstant specifying the method for normalizing eigenvectors. Possible values are DISPLACEMENT and MASS. The default value is DISPLACEMENT.

A value of DISPLACEMENT indicates normalizing the eigenvectors so that the largest displacement entry in each vector is unity. A value of MASS indicates normalizing the eigenvectors with respect to the structure's mass matrix, which results in scaling the eigenvectors so that the generalized mass for each vector is unity.

*propertyEvaluationFrequency*

 `None` or a Float specifying the frequency at which to evaluate frequency-dependent properties for viscoelasticity, springs, and dashpots during the eigenvalue extraction. If the value is `None`, the analysis product will evaluate the stiffness associated with frequency-dependent springs and dashpots at zero frequency and will not consider the stiffness contributions from frequency-domain viscoelasticity in the step. The default value is `None`.

*projectDamping*

A Boolean specifying whether to include projection of viscous and structural damping operators during *AMS* eigenvalue extraction.  Valid only when *eigenSolver*=AMS. The default value is ON.

*acousticCoupling*

A SymbolicConstant specifying the type of acoustic-structural coupling in models with acoustic and structural elements coupled using the [*TIE](../key/key-link.md#usb-kws-mtie) option or in models with ASI-type elements. Possible values are AC_ON, AC_OFF, and AC_PROJECTION. The default value is AC_ON.

*acousticRangeFactor*

A Float specifying the ratio of the maximum acoustic frequency to the maximum structural frequency. The default value is 1.0.

*frictionDamping*

A Boolean specifying whether to add to the damping matrix contributions due to friction effects. The default value is OFF.

*matrixStorage*

A SymbolicConstant specifying the type of matrix storage. Possible values are SYMMETRIC, UNSYMMETRIC, and SOLVER_DEFAULT. The default value is SOLVER_DEFAULT.

*maintainAttributes*

A Boolean specifying whether to retain attributes from an existing step with the same name. The default value is False.

*simLinearDynamics*

A Boolean specifying whether to activate the SIM-based linear dynamics procedures. The default value is OFF.

*residualModes*

A Boolean specifying whether to include residual modes from an immediately preceding Static, Linear Perturbation step. The default value is OFF.

*substructureCutoffMultiplier*

A Float specifying the cutoff frequency for substructure eigenproblems, defined as a multiplier of the maximum frequency of interest. The default value is 5.0.

*firstCutoffMultiplier*

A Float specifying the first cutoff frequency for a reduced eigenproblem, defined as a multiplier of the maximum frequency of interest. The default value is 1.7.

*secondCutoffMultiplier*

A Float specifying the second cutoff frequency for a reduced eigenproblem defined as a multiplier of the maximum frequency of interest. The default value is 1.1.

*residualModeRegion*

 `None` or a sequence of Strings specifying the name of a region for which residual modes are requested. The default value is `None`.

*residualModeDof*

 `None` or a sequence of Ints specifying the degree of freedom for which residual modes are requested. The default value is `None`.

*limitSavedEigenvectorRegion*

 `None` or a [Region](pt01ch45pyo03.md) object specifying a region for which eigenvectors should be saved or the SymbolicConstant None representing the whole model. The default value is `None`.

**Return value**

A FrequencyStep object.

**Exceptions**

RangeError.

### 49.13.2 setValues(...)

This method modifies the FrequencyStep object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [FrequencyStep](pt01ch49pyo13.md#ker-frequencystep-frequencystep-pyc) method, except for the *name*, *previous*, and *maintainAttributes* arguments.

**Return value**

None

**Exceptions**

RangeError.

### 49.13.3 Members

The FrequencyStep object can have the following members:

*name*

A String specifying the repository key.

*eigensolver*

A SymbolicConstant specifying the eigensolver. Possible values are LANCZOS, SUBSPACE, and AMS.

The following optional arguments are ignored unless *eigensolver*=LANCZOS: *blockSize*, *maxBlocks*, *normalization*, *propertyEvaluationFrequency*.

The following optional arguments are ignored unless *eigensolver*=LANCZOS or AMS: *minEigen*, *maxEigen*, and *acousticCoupling*.

The following optional arguments are ignored unless *eigensolver*=AMS: *projectDamping*, *acousticRangeFactor*, *substructureCutoffMultiplier*, *firstCutoffMultiplier*, *secondCutoffMultiplier*, *residualModeRegion*, *regionalModeDof*, and *limitSavedEigenvectorRegion*.

*numEigen*

The SymbolicConstant ALL or an Int specifying the number of eigenvalues to be calculated or ALL. The default value is ALL.

*shift*

A Float specifying the shift point in cycles per time. The default value is 0.0.

*minEigen*

 `None` or a Float specifying the minimum frequency of interest in cycles per time. The default value is `None`.

*maxEigen*

 `None` or a Float specifying the maximum frequency of interest in cycles per time. The default value is `None`.

*vectors*

 `None` or an Int specifying the number of vectors used in the iteration. The default is the minimum of (2*n*, *n* + 8), where *n* is the number of eigenvalues requested. The default value is `None`.

*maxIterations*

An Int specifying the maximum number of iterations. The default value is 30.

*blockSize*

A SymbolicConstant specifying the size of the Lanczos block steps. The default value is DEFAULT.

*maxBlocks*

A SymbolicConstant specifying the maximum number of Lanczos block steps within each Lanczos run. The default value is DEFAULT.

*normalization*

A SymbolicConstant specifying the method for normalizing eigenvectors. Possible values are DISPLACEMENT and MASS. The default value is DISPLACEMENT.

A value of DISPLACEMENT indicates normalizing the eigenvectors so that the largest displacement entry in each vector is unity. A value of MASS indicates normalizing the eigenvectors with respect to the structure's mass matrix, which results in scaling the eigenvectors so that the generalized mass for each vector is unity.

*propertyEvaluationFrequency*

 `None` or a Float specifying the frequency at which to evaluate frequency-dependent properties for viscoelasticity, springs, and dashpots during the eigenvalue extraction. If the value is `None`, the analysis product will evaluate the stiffness associated with frequency-dependent springs and dashpots at zero frequency and will not consider the stiffness contributions from frequency-domain viscoelasticity in the step. The default value is `None`.

*projectDamping*

A Boolean specifying whether to include projection of viscous and structural damping operators during *AMS* eigenvalue extraction.  Valid only when *eigenSolver*=AMS. The default value is ON.

*acousticCoupling*

A SymbolicConstant specifying the type of acoustic-structural coupling in models with acoustic and structural elements coupled using the [*TIE](../key/key-link.md#usb-kws-mtie) option or in models with ASI-type elements. Possible values are AC_ON, AC_OFF, and AC_PROJECTION. The default value is AC_ON.

*acousticRangeFactor*

A Float specifying the ratio of the maximum acoustic frequency to the maximum structural frequency. The default value is 1.0.

*frictionDamping*

A Boolean specifying whether to add to the damping matrix contributions due to friction effects. The default value is OFF.

*matrixStorage*

A SymbolicConstant specifying the type of matrix storage. Possible values are SYMMETRIC, UNSYMMETRIC, and SOLVER_DEFAULT. The default value is SOLVER_DEFAULT.

*simLinearDynamics*

A Boolean specifying whether to activate the SIM-based linear dynamics procedures. The default value is OFF.

*residualModes*

A Boolean specifying whether to include residual modes from an immediately preceding Static, Linear Perturbation step. The default value is OFF.

*substructureCutoffMultiplier*

A Float specifying the cutoff frequency for substructure eigenproblems, defined as a multiplier of the maximum frequency of interest. The default value is 5.0.

*firstCutoffMultiplier*

A Float specifying the first cutoff frequency for a reduced eigenproblem, defined as a multiplier of the maximum frequency of interest. The default value is 1.7.

*secondCutoffMultiplier*

A Float specifying the second cutoff frequency for a reduced eigenproblem defined as a multiplier of the maximum frequency of interest. The default value is 1.1.

*previous*

A String specifying the name of the previous step. The new step appears after this step in the list of analysis steps.

*description*

A String specifying a description of the new step. The default value is an empty string.

*residualModeRegion*

 `None` or a tuple of Strings specifying the name of a region for which residual modes are requested. The default value is `None`.

*residualModeDof*

 `None` or a tuple of Ints specifying the degree of freedom for which residual modes are requested. The default value is `None`.

*limitSavedEigenvectorRegion*

 `None` or a [Region](pt01ch45pyo03.md) object specifying a region for which eigenvectors should be saved or the SymbolicConstant None representing the whole model. The default value is `None`.

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

### 49.13.4 Corresponding analysis keywords

| [*FREQUENCY](../key/key-link.md#usb-kws-hfrequency) |
| --- |
| [*STEP](../key/key-link.md#usb-kws-hstep) |




