# 49.4 BuckleStep object







The BuckleStep object controls eigenvalue buckling estimation.

The BuckleStep object is derived from the [AnalysisStep](pt01ch49pyo02.md) object.

**Access**

```
import step
mdb.models[*name*].steps[*name*]
```

### 49.4.1 BuckleStep(...)

This method creates a BuckleStep object.

**Path**

```
mdb.models[*name*].BuckleStep
```

**Required arguments**

*name*

A String specifying the repository key.

*previous*

A String specifying the name of the previous step. The new step appears after this step in the list of analysis steps.

*numEigen*

An Int specifying the number of eigenvalues to be estimated.

**Optional arguments**

*description*

A String specifying a description of the new step. The default value is an empty string.

*eigensolver*

A SymbolicConstant specifying the eigensolver. Possible values are SUBSPACE and LANCZOS. The default value is SUBSPACE.

*minEigen*

 `None` or a Float specifying the minimum eigenvalue of interest. The default value is `None`.

*maxEigen*

 `None` or a Float specifying the maximum eigenvalue of interest. The default value is `None`.

*vectors*

An Int specifying the number of vectors used in the iteration. The default value is the minimum of (2*n*, *n* + 8), where *n* is the number of eigenvalues requested.

*maxIterations*

An Int specifying the maximum number of iterations. The default value is 30.

*blockSize*

The SymbolicConstant DEFAULT or an Int specifying the size of the Lanczos block steps. The default value is DEFAULT.

*maxBlocks*

The SymbolicConstant DEFAULT or an Int specifying the maximum number of Lanczos block steps within each Lanczos run. The default value is DEFAULT.

**Note:** *minEigen*, *blockSize*, and *maxBlocks* are ignored unless *eigensolver*=LANCZOS.

*matrixStorage*

A SymbolicConstant specifying the type of matrix storage. Possible values are SYMMETRIC, UNSYMMETRIC, and SOLVER_DEFAULT. The default value is SOLVER_DEFAULT.

*maintainAttributes*

A Boolean specifying whether to retain attributes from an existing step with the same name. The default value is False.

**Return value**

A BuckleStep object.

**Exceptions**

RangeError.

### 49.4.2 setValues(...)

This method modifies the BuckleStep object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [BuckleStep](pt01ch49pyo04.md#ker-bucklestep-bucklestep-pyc) method, except for the *name*, *previous*, and *maintainAttributes* arguments.

**Return value**

None

**Exceptions**

RangeError.

### 49.4.3 Members

The BuckleStep object can have the following members:

*name*

A String specifying the repository key.

*numEigen*

An Int specifying the number of eigenvalues to be estimated.

*eigensolver*

A SymbolicConstant specifying the eigensolver. Possible values are SUBSPACE and LANCZOS. The default value is SUBSPACE.

*minEigen*

 `None` or a Float specifying the minimum eigenvalue of interest. The default value is `None`.

*maxEigen*

 `None` or a Float specifying the maximum eigenvalue of interest. The default value is `None`.

*vectors*

An Int specifying the number of vectors used in the iteration. The default value is the minimum of (2*n*, *n* + 8), where *n* is the number of eigenvalues requested.

*maxIterations*

An Int specifying the maximum number of iterations. The default value is 30.

*blockSize*

The SymbolicConstant DEFAULT or an Int specifying the size of the Lanczos block steps. The default value is DEFAULT.

*maxBlocks*

The SymbolicConstant DEFAULT or an Int specifying the maximum number of Lanczos block steps within each Lanczos run. The default value is DEFAULT.

**Note:** *minEigen*, *blockSize*, and *maxBlocks* are ignored unless *eigensolver*=LANCZOS.

*matrixStorage*

A SymbolicConstant specifying the type of matrix storage. Possible values are SYMMETRIC, UNSYMMETRIC, and SOLVER_DEFAULT. The default value is SOLVER_DEFAULT.

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

### 49.4.4 Corresponding analysis keywords

| [*BUCKLE](../key/key-link.md#usb-kws-hbuckle) |
| --- |
| [*STEP](../key/key-link.md#usb-kws-hstep) |




