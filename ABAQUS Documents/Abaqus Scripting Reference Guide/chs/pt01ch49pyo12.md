# 49.12 FlowStep object







The FlowStep object is used to create an analysis step for use in a CFD analysis.

The FlowStep object is derived from the [AnalysisStep](pt01ch49pyo02.md) object.

**Access**

```
import step
mdb.models[*name*].steps[*name*]
```

### 49.12.1 FlowStep(...)

This method creates a FlowStep object.

**Path**

```
mdb.models[*name*].FlowStep
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

A Float specifying the total time period for the step. The default value is 1.0.

*energyEquation*

A SymbolicConstant specifying the energy equation method to be used. Possible values are ENERGY_NONE and TEMPERATURE. The default value is ENERGY_NONE.

*incrementation*

A SymbolicConstant specifying the time incrementation method to be used. Possible values are FIXED_TIME and FIXED_CFL. The default value is FIXED_TIME.

*initialInc*

A Float specifying the time increment for the step, or the initial time increment when *incrementation*=FIXED_CFL. The default value is 0.01.

*divergenceTol*

A Float specifying the divergence tolerance.. The default value is 10–10.

*maximumCFL*

A Float specifying the maximum Courant-Friedrichs-Levy increment. This member is applicable only when *incrementation*=FIXED_CFL. The default value is 0.45.

*incAdjustmentFreq*

An Int specifying the increment adjustment frequency. This member is applicable only when *incrementation*=FIXED_CFL. The default value is 1.

*stepGrowthFactor*

A Float specifying the time step growth scale factor. This member is applicable only when *incrementation*=FIXED_CFL. The default value is 0.025.

*viscousFactor*

A SymbolicConstant specifying the viscous time integration parameter. Possible values are TRAPEZOID, GALERKIN, and BACKWARD_EULER. The default value is TRAPEZOID.

*boundaryFactor*

A SymbolicConstant specifying the load and boundary condition time integration parameter. Possible values are TRAPEZOID, GALERKIN, and BACKWARD_EULER. The default value is TRAPEZOID.

*advectionFactor*

A SymbolicConstant specifying the advection parameter. Possible values are TRAPEZOID, GALERKIN, and BACKWARD_EULER. The default value is TRAPEZOID.

*momOutputDiagnostics*

A Boolean specifying whether or not to output diagnostics for the momentum equation solver. The default value is OFF.

*momOutputConvergence*

A Boolean specifying whether or not to output convergence data for the momentum equation solver. The default value is OFF.

*momIterationLimit*

An Int specifying the iteration limit for the momentum equation solver. The default value is 50.

*momCheckingFreq*

An Int specifying the momentum equation solver checking frequency. The default value is 2.

*momConvergenceLimit*

A Float specifying the linear convergence limit for the momentum equation solver. The default value is 10–5.

*pressureType*

A SymbolicConstant specifying the pressure equation preconditioner type. Possible values are AMG and SSOR. The default value is AMG.

*pressSolverType*

A SymbolicConstant specifying the pressure equation solver type. This member cannot be changed from the default value when *pressureType*=SSOR. Possible values are CG, BCGS, and FGMRES. The default value is CG.

*pressSmootherType*

A SymbolicConstant specifying the pressure equation residual smoother type. This member is applicable only when *pressureType*=AMG. Possible values are ICC and CHEBYCHEV. The default value is ICC.

*pressPreSweeps*

An Int specifying the pre-sweeps used by the residual smoother. This member is applicable only when *pressureType*=AMG. The default value is 1.

*pressPostSweeps*

An Int specifying the post-sweeps used by the residual smoother. This member is applicable only when *pressureType*=AMG. The default value is 1.

*pressOutputDiagnostics*

A Boolean specifying whether or not to output diagnostics for the pressure equation solver. The default value is OFF.

*pressOutputConvergence*

A Boolean specifying whether or not to output convergence data for the pressure equation solver. The default value is OFF.

*pressIterationLimit*

An Int specifying the iteration limit for the pressure equation solver. This default value is 250 when *pressureType*=AMG and 1000 when *pressureType*=SSOR.

*pressCheckingFreq*

An Int specifying the pressure equation solver checking frequency. The default value is 2.

*pressConvergenceLimit*

A Float specifying the linear convergence limit for the pressure equation solver. The default value is 10–5.

*transOutputDiagnostics*

A Boolean specifying whether or not to output diagnostics for the transport equation solver. The default value is OFF.

*transOutputConvergence*

A Boolean specifying whether or not to output convergence data for the transport equation solver. The default value is OFF.

*transIterationLimit*

An Int specifying the iteration limit for the transport equation solver. The default value is 50.

*transCheckingFreq*

An Int specifying the transport equation solver checking frequency. The default value is 2.

*transConvergenceLimit*

A Float specifying the linear convergence limit for the transport equation solver. The default value is 10–5.

*turbulenceModel*

A SymbolicConstant specifying the turbulence model. Possible values are TURB_NONE, SPALART, and KEPS_RNG. The default value is TURB_NONE.

*turbPrandtlNumber*

A Float specifying the turbulent Prandtl number. This member is applicable only when *energyEquation*=TEMPERATURE and when *turbulenceModel*!=TURB_NONE. The default value is 0.8889.

*turbCb1*

A Float specifying the turbulence constant Cb1. This member is applicable only when *turbulenceModel*=SPALART. The default value is 0.1355.

*turbCb2*

A Float specifying the turbulence constant Cb2. This member is applicable only when *turbulenceModel*=SPALART. The default value is 0.622.

*turbCv1*

A Float specifying the turbulence constant Cv1. This member is applicable only when *turbulenceModel*=SPALART. The default value is 7.1.

*turbCv2*

A Float specifying the turbulence constant Cv2. This member is applicable only when *turbulenceModel*=SPALART. The default value is 5.0.

*turbCw1*

A Float specifying the turbulence constant Cw1. This member is applicable only when *turbulenceModel*=SPALART. The default value is 3.2391.

*turbCw2*

A Float specifying the turbulence constant Cw2. This member is applicable only when *turbulenceModel*=SPALART. The default value is 0.3.

*turbCw3*

A Float specifying the turbulence constant Cw3. This member is applicable only when *turbulenceModel*=SPALART. The default value is 2.0.

*turbSigma*

A Float specifying the turbulence constant Sigma. This member is applicable only when *turbulenceModel*=SPALART. The default value is 0.6667.

*turbKappa*

A Float specifying the turbulence constant Kappa. This member is applicable only when *turbulenceModel*=SPALART. The default value is 0.41.

*turbCmu*

A Float specifying the turbulence constant Cmu. This member is applicable only when *turbulenceModel*=KEPS_RNG. The default value is 0.085.

*turbCeps1*

A Float specifying the turbulence constant cps1. This member is applicable only when *turbulenceModel*=KEPS_RNG. The default value is 1.42.

*turbCeps2t*

A Float specifying the turbulence constant cps2t. This member is applicable only when *turbulenceModel*=KEPS_RNG. The default value is 1.68.

*turbSigma_k*

A Float specifying the turbulence constant sigma_k. This member is applicable only when *turbulenceModel*=KEPS_RNG. The default value is 0.72.

*turbSigma_eps*

A Float specifying the turbulence constant sigma_eps. This member is applicable only when *turbulenceModel*=KEPS_RNG. The default value is 0.72.

*turbBeta*

A Float specifying the turbulence constant beta. This member is applicable only when *turbulenceModel*=KEPS_RNG. The default value is 0.012.

*turbLambda0*

A Float specifying the turbulence constant lambda0. This member is applicable only when *turbulenceModel*=KEPS_RNG. The default value is 4.38.

**Return value**

A FlowStep object.

**Exceptions**

RangeError.

### 49.12.2 setValues(...)

This method modifies the FlowStep object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [FlowStep](pt01ch49pyo12.md#ker-flowstep-flowstep-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 49.12.3 Members

The FlowStep object has members with the same names and descriptions as the arguments to the [FlowStep](pt01ch49pyo12.md#ker-flowstep-flowstep-pyc) method.

In addition, the FlowStep object can have the following members:

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

### 49.12.4 Corresponding analysis keywords

| [*CFD](../key/key-link.md#usb-kws-hcfd) |
| --- |
| [*STEP](../key/key-link.md#usb-kws-hstep) |




