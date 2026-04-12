# 49.8 CoupledThermalElectricStep object







The CoupledThermalElectricStep object is used to analyze problems where the electrical potential and temperature fields must be solved simultaneously.

The CoupledThermalElectricStep object is derived from the [AnalysisStep](pt01ch49pyo02.md) object.

**Access**

```
import step
mdb.models[*name*].steps[*name*]
```

### 49.8.1 CoupledThermalElectricStep(...)

This method creates a CoupledThermalElectricStep object. 

**Path**

```
mdb.models[*name*].CoupledThermalElectricStep
```

**Required arguments**

*name*

A String specifying the repository key.

*previous*

A String specifying the name of the previous step. The new step appears after this step in the list of analysis steps.

**Optional arguments**

*description*

A String specifying a description of the new step. The default value is an empty string.

*response*

A SymbolicConstant specifying the analysis type. Possible values are STEADY_STATE and TRANSIENT. The default value is TRANSIENT.

*timePeriod*

A Float specifying the total time period for the step. The default value is 1.0.

*timeIncrementationMethod*

A SymbolicConstant specifying the time incrementation method to be used. Possible values are FIXED and AUTOMATIC. The default value is AUTOMATIC.

*maxNumInc*

An Int specifying the maximum number of increments in a step. The default value is 100.

*initialInc*

A Float specifying the initial time increment. The default value is the total time period for the step.

*minInc*

A Float specifying the minimum time increment allowed. The default value is the smaller of the suggested initial time increment or 105 times the total time period.

*maxInc*

A Float specifying the maximum time increment allowed. The default value is the total time period for the step.

*end*

A SymbolicConstant specifying the time period to be analyzed in a transient analysis. Possible values are PERIOD and SS. The default value is PERIOD.

*deltmx*

A Float specifying the maximum temperature change to be allowed in an increment in a transient analysis. The default value is 0.0.

*mxdem*

A Float specifying the maximum allowable emissivity change with temperature and field variables during an increment. The default value is 0.1.

*solutionTechnique*

A SymbolicConstant specifying the type of solution technique. Possible values are FULL_NEWTON and SEPARATED. The default value is FULL_NEWTON.

*matrixStorage*

A SymbolicConstant specifying the type of matrix storage. Possible values are SYMMETRIC, UNSYMMETRIC, and SOLVER_DEFAULT. The default value is SOLVER_DEFAULT.

*amplitude*

A SymbolicConstant specifying the amplitude variation for loading magnitudes during the step. The default value is STEP. Possible values are STEP and RAMP.

*extrapolation*

A SymbolicConstant specifying the type of extrapolation to use in determining the incremental solution for a nonlinear analysis. Possible values are NONE, LINEAR, and PARABOLIC. The default value is LINEAR.

*maintainAttributes*

A Boolean specifying whether to retain attributes from an existing step with the same name. The default value is False.

*convertSDI*

A SymbolicConstant specifying whether to force a new iteration if severe discontinuities occur during an iteration. Possible values are PROPAGATED, CONVERT_SDI_OFF, and CONVERT_SDI_ON. The default value is PROPAGATED.

**Return value**

A CoupledThermalElectricStep object.

**Exceptions**

RangeError.

### 49.8.2 setValues(...)

This method modifies the CoupledThermalElectricStep object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [CoupledThermalElectricStep](pt01ch49pyo08.md#ker-coupledthermalelectricstep-coupledthermalelectricste-pyc) method, except for the *name*, *previous*, and *maintainAttributes* arguments.

**Return value**

None

**Exceptions**

RangeError.

### 49.8.3 Members

The CoupledThermalElectricStep object can have the following members:

*name*

A String specifying the repository key.

*response*

A SymbolicConstant specifying the analysis type. Possible values are STEADY_STATE and TRANSIENT. The default value is TRANSIENT.

*timePeriod*

A Float specifying the total time period for the step. The default value is 1.0.

*timeIncrementationMethod*

A SymbolicConstant specifying the time incrementation method to be used. Possible values are FIXED and AUTOMATIC. The default value is AUTOMATIC.

*maxNumInc*

An Int specifying the maximum number of increments in a step. The default value is 100.

*initialInc*

A Float specifying the initial time increment. The default value is the total time period for the step.

*minInc*

A Float specifying the minimum time increment allowed. The default value is the smaller of the suggested initial time increment or 105 times the total time period.

*maxInc*

A Float specifying the maximum time increment allowed. The default value is the total time period for the step.

*end*

A SymbolicConstant specifying the time period to be analyzed in a transient analysis. Possible values are PERIOD and SS. The default value is PERIOD.

*deltmx*

A Float specifying the maximum temperature change to be allowed in an increment in a transient analysis. The default value is 0.0.

*mxdem*

A Float specifying the maximum allowable emissivity change with temperature and field variables during an increment. The default value is 0.1.

*solutionTechnique*

A SymbolicConstant specifying the type of solution technique. Possible values are FULL_NEWTON and SEPARATED. The default value is FULL_NEWTON.

*matrixStorage*

A SymbolicConstant specifying the type of matrix storage. Possible values are SYMMETRIC, UNSYMMETRIC, and SOLVER_DEFAULT. The default value is SOLVER_DEFAULT.

*amplitude*

A SymbolicConstant specifying the amplitude variation for loading magnitudes during the step. The default value is STEP. Possible values are STEP and RAMP.

*extrapolation*

A SymbolicConstant specifying the type of extrapolation to use in determining the incremental solution for a nonlinear analysis. Possible values are NONE, LINEAR, and PARABOLIC. The default value is LINEAR.

*convertSDI*

A SymbolicConstant specifying whether to force a new iteration if severe discontinuities occur during an iteration. Possible values are PROPAGATED, CONVERT_SDI_OFF, and CONVERT_SDI_ON. The default value is PROPAGATED.

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

### 49.8.4 Corresponding analysis keywords

| [*COUPLED THERMAL-ELECTRICAL](../key/key-link.md#usb-kws-hthermalelectric) |
| --- |
| [*SOLUTION TECHNIQUE](../key/key-link.md#usb-kws-hsolutiontech) |
| [*STEP](../key/key-link.md#usb-kws-hstep) |




