# 49.25 StaticStep object







The StaticStep object is used to indicate that the step should be analyzed as a static load step.

The StaticStep object is derived from the [AnalysisStep](pt01ch49pyo02.md) object.

**Access**

```
import step
mdb.models[*name*].steps[*name*]
```

### 49.25.1 StaticStep(...)

This method creates a StaticStep object.

**Path**

```
mdb.models[*name*].StaticStep
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

A Float specifying the total time period. The default value is 1.0.

*nlgeom*

A Boolean specifying whether to allow for geometric nonlinearity. The default value is OFF.

*stabilizationMethod*

A SymbolicConstant specifying the stabilization type. Possible values are NONE, DISSIPATED_ENERGY_FRACTION, and DAMPING_FACTOR. The default value is NONE.

*stabilizationMagnitude*

A Float specifying the damping intensity of the automatic damping algorithm if the problem is expected to be unstable, and *stabilizationMethod* is not NONE. The default value is 210–4.

*adiabatic*

A Boolean specifying whether to perform an adiabatic stress analysis. The default value is OFF.

*timeIncrementationMethod*

A SymbolicConstant specifying the time incrementation method to be used. Possible values are FIXED and AUTOMATIC. The default value is AUTOMATIC.

*maxNumInc*

An Int specifying the maximum number of increments in a step. The default value is 100.

*initialInc*

A Float specifying the initial time increment. The default value is the total time period for the step.

*minInc*

A Float specifying the minimum time increment allowed. The default value is the smaller of the suggested initial time increment or 10–5 times the total time period.

*maxInc*

A Float specifying the maximum time increment allowed. The default value is the total time period for the step.

*matrixSolver*

A SymbolicConstant specifying the type of solver. Possible values are DIRECT and ITERATIVE. The default value is DIRECT.

*matrixStorage*

A SymbolicConstant specifying the type of matrix storage. Possible values are SYMMETRIC, UNSYMMETRIC, and SOLVER_DEFAULT. The default value is SOLVER_DEFAULT.

*amplitude*

A SymbolicConstant specifying the amplitude variation for loading magnitudes during the step. Possible values are STEP and RAMP. The default value is RAMP.

*extrapolation*

A SymbolicConstant specifying the type of extrapolation to use in determining the incremental solution for a nonlinear analysis. Possible values are NONE, LINEAR, and PARABOLIC. The default value is LINEAR.

*fullyPlastic*

A String specifying the region being monitored for fully plastic behavior. The default value is an empty string.

*noStop*

A Boolean specifying whether to accept the solution to an increment after the maximum number of iterations allowed has been completed, even if the equilibrium tolerances are not satisfied. The default value is OFF.

**Warning:**You should set *noStop*=ON only in special cases when you have a thorough understanding of how to interpret the results.

*maintainAttributes*

A Boolean specifying whether to retain attributes from an existing step with the same name. The default value is False.

*useLongTermSolution*

A Boolean specifying wether to obtain the fully relaxed long-term elastic solution with time-domain viscoelasticity or the long-term elastic-plastic solution for two-layer viscoplasticity. The default value is OFF.

*solutionTechnique*

A SymbolicConstant specifying the technique used to for solving nonlinear equations. Possible values are FULL_NEWTON and QUASI_NEWTON. The default value is FULL_NEWTON.

*reformKernel*

An Int specifying the number of quasi-Newton iterations allowed before the kernel matrix is reformed.. The default value is 8.

*convertSDI*

A SymbolicConstant specifying whether to force a new iteration if severe discontinuities occur during an iteration. Possible values are PROPAGATED, CONVERT_SDI_OFF, and CONVERT_SDI_ON. The default value is PROPAGATED.

*adaptiveDampingRatio*

A Float specifying the maximum allowable ratio of the stabilization energy to the total strain energy and can be used only if *stabilizationMethod* is not NONE. The default value is 0.05.

*continueDampingFactors*

A Boolean specifying whether this step will carry over the damping factors from the results of the preceding general step. This parameter must be used in conjunction with the *adaptiveDampingRatio* parameter. The default value is OFF.

**Return value**

A StaticStep object.

**Exceptions**

RangeError.

### 49.25.2 setValues(...)

This method modifies the StaticStep object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [StaticStep](pt01ch49pyo25.md#ker-staticstep-staticstep-pyc) method, except for the *name*, *previous*, and *maintainAttributes* arguments.

**Return value**

None

**Exceptions**

RangeError.

### 49.25.3 Members

The StaticStep object can have the following members:

*name*

A String specifying the repository key.

*timePeriod*

A Float specifying the total time period. The default value is 1.0.

*nlgeom*

A Boolean specifying whether to allow for geometric nonlinearity. The default value is OFF.

*stabilizationMethod*

A SymbolicConstant specifying the stabilization type. Possible values are NONE, DISSIPATED_ENERGY_FRACTION, and DAMPING_FACTOR. The default value is NONE.

*stabilizationMagnitude*

A Float specifying the damping intensity of the automatic damping algorithm if the problem is expected to be unstable, and *stabilizationMethod* is not NONE. The default value is 210–4.

*adiabatic*

A Boolean specifying whether to perform an adiabatic stress analysis. The default value is OFF.

*timeIncrementationMethod*

A SymbolicConstant specifying the time incrementation method to be used. Possible values are FIXED and AUTOMATIC. The default value is AUTOMATIC.

*maxNumInc*

An Int specifying the maximum number of increments in a step. The default value is 100.

*initialInc*

A Float specifying the initial time increment. The default value is the total time period for the step.

*minInc*

A Float specifying the minimum time increment allowed. The default value is the smaller of the suggested initial time increment or 10–5 times the total time period.

*maxInc*

A Float specifying the maximum time increment allowed. The default value is the total time period for the step.

*matrixSolver*

A SymbolicConstant specifying the type of solver. Possible values are DIRECT and ITERATIVE. The default value is DIRECT.

*matrixStorage*

A SymbolicConstant specifying the type of matrix storage. Possible values are SYMMETRIC, UNSYMMETRIC, and SOLVER_DEFAULT. The default value is SOLVER_DEFAULT.

*amplitude*

A SymbolicConstant specifying the amplitude variation for loading magnitudes during the step. Possible values are STEP and RAMP. The default value is RAMP.

*extrapolation*

A SymbolicConstant specifying the type of extrapolation to use in determining the incremental solution for a nonlinear analysis. Possible values are NONE, LINEAR, and PARABOLIC. The default value is LINEAR.

*noStop*

A Boolean specifying whether to accept the solution to an increment after the maximum number of iterations allowed has been completed, even if the equilibrium tolerances are not satisfied. The default value is OFF.

**Warning:**You should set *noStop*=ON only in special cases when you have a thorough understanding of how to interpret the results.

*useLongTermSolution*

A Boolean specifying wether to obtain the fully relaxed long-term elastic solution with time-domain viscoelasticity or the long-term elastic-plastic solution for two-layer viscoplasticity. The default value is OFF.

*solutionTechnique*

A SymbolicConstant specifying the technique used to for solving nonlinear equations. Possible values are FULL_NEWTON and QUASI_NEWTON. The default value is FULL_NEWTON.

*reformKernel*

An Int specifying the number of quasi-Newton iterations allowed before the kernel matrix is reformed.. The default value is 8.

*convertSDI*

A SymbolicConstant specifying whether to force a new iteration if severe discontinuities occur during an iteration. Possible values are PROPAGATED, CONVERT_SDI_OFF, and CONVERT_SDI_ON. The default value is PROPAGATED.

*adaptiveDampingRatio*

A Float specifying the maximum allowable ratio of the stabilization energy to the total strain energy and can be used only if *stabilizationMethod* is not NONE. The default value is 0.05.

*continueDampingFactors*

A Boolean specifying whether this step will carry over the damping factors from the results of the preceding general step. This parameter must be used in conjunction with the *adaptiveDampingRatio* parameter. The default value is OFF.

*previous*

A String specifying the name of the previous step. The new step appears after this step in the list of analysis steps.

*description*

A String specifying a description of the new step. The default value is an empty string.

*fullyPlastic*

A String specifying the region being monitored for fully plastic behavior. The default value is an empty string.

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

### 49.25.4 Corresponding analysis keywords

| [*STATIC](../key/key-link.md#usb-kws-hstatic) |
| --- |
| [*STEP](../key/key-link.md#usb-kws-hstep) |




