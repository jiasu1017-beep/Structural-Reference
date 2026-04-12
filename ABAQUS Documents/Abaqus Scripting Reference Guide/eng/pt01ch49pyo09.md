# 49.9 DirectCyclicStep object







The DirectCyclicStep object is used to provide a direct cyclic procedure for nonlinear, non-isothermal quasi-static analysis. It can also be used to predict progressive damage and failure for ductile bulk materials and/or to predict delamination/debonding growth at the interfaces in laminated composites in a low-cycle fatigue analysis.

The DirectCyclicStep object is derived from the [AnalysisStep](pt01ch49pyo02.md) object.

**Access**

```
import step
mdb.models[*name*].steps[*name*]
```

### 49.9.1 DirectCyclicStep(...)

This method creates a DirectCyclicStep object.

**Path**

```
mdb.models[*name*].DirectCyclicStep
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

A Float specifying the time of single loading cycle. The default value is 1.0.

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

*maxNumIterations*

An Int specifying the maximum number of iterations in a step. The default value is 200.

*initialTerms*

An Int specifying the initial number of terms in the Fourier series. The default value is 11.

*maxTerms*

An Int specifying the maximum number of terms in the Fourier series. The default value is 25.

*termsIncrement*

An Int specifying the increment in number of terms in the Fourier series. The default value is 5.

*deltmx*

A Float specifying the maximum temperature change to be allowed in an increment. The default value is 0.0.

*cetol*

A Float specifying the maximum difference in the creep strain increment calculated from the creep strain rates at the beginning and end of the increment. The default value is 0.0.

*timePoints*

 `None` or a String specifying a String specifying the name of a time point object used to determine at which times the response of the structure will be evaluated. The default value is NONE.

*fatigue*

A Boolean specifying whether to include low-cycle fatigue analysis. The default value is OFF.

*continueAnalysis*

A Boolean specifying whether the displacement solution in the Fourier series obtained in the previous direct cyclic step is used as the starting values for the current step. The default value is OFF.

*minCycleInc*

An Int specifying the minimum number of cycles over which the damage is extrapolated forward. The default value is 100.

*maxCycleInc*

An Int specifying the maximum number of cycles over which the damage is extrapolated forward. The default value is 1000.

*maxNumCycles*

The SymbolicConstant DEFAULT or an Int specifying the maximum number of cycles allowed in a step or DEFAULT.  A value of 1 plus half of the maximum number of cycles will be used if DEFAULT is specified. The default value is DEFAULT.

*damageExtrapolationTolerance*

A Float specifying the maximum extrapolated damage increment. The default value is 1.0.

*matrixStorage*

A SymbolicConstant specifying the type of matrix storage. Possible values are SYMMETRIC, UNSYMMETRIC, and SOLVER_DEFAULT. The default value is SOLVER_DEFAULT.

*extrapolation*

A SymbolicConstant specifying the type of extrapolation to use in determining the incremental solution for a nonlinear analysis. Possible values are NONE, LINEAR, and PARABOLIC. The default value is LINEAR.

*maintainAttributes*

A Boolean specifying whether to retain attributes from an existing step with the same name. The default value is False.

*convertSDI*

A SymbolicConstant specifying whether to force a new iteration if severe discontinuities occur during an iteration. Possible values are PROPAGATED, CONVERT_SDI_OFF, and CONVERT_SDI_ON. The default value is PROPAGATED.

**Return value**

A DirectCyclicStep object.

**Exceptions**

RangeError.

### 49.9.2 setValues(...)

This method modifies the DirectCyclicStep object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [DirectCyclicStep](pt01ch49pyo09.md#ker-directcyclicstep-directcyclicstep-pyc) method, except for the *name*, *previous*, and *maintainAttributes* arguments.

**Return value**

None

**Exceptions**

RangeError.

### 49.9.3 Members

The DirectCyclicStep object can have the following members:

*name*

A String specifying the repository key.

*timePeriod*

A Float specifying the time of single loading cycle. The default value is 1.0.

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

*maxNumIterations*

An Int specifying the maximum number of iterations in a step. The default value is 200.

*initialTerms*

An Int specifying the initial number of terms in the Fourier series. The default value is 11.

*maxTerms*

An Int specifying the maximum number of terms in the Fourier series. The default value is 25.

*termsIncrement*

An Int specifying the increment in number of terms in the Fourier series. The default value is 5.

*deltmx*

A Float specifying the maximum temperature change to be allowed in an increment. The default value is 0.0.

*cetol*

A Float specifying the maximum difference in the creep strain increment calculated from the creep strain rates at the beginning and end of the increment. The default value is 0.0.

*fatigue*

A Boolean specifying whether to include low-cycle fatigue analysis. The default value is OFF.

*continueAnalysis*

A Boolean specifying whether the displacement solution in the Fourier series obtained in the previous direct cyclic step is used as the starting values for the current step. The default value is OFF.

*minCycleInc*

An Int specifying the minimum number of cycles over which the damage is extrapolated forward. The default value is 100.

*maxCycleInc*

An Int specifying the maximum number of cycles over which the damage is extrapolated forward. The default value is 1000.

*maxNumCycles*

The SymbolicConstant DEFAULT or an Int specifying the maximum number of cycles allowed in a step or DEFAULT.  A value of 1 plus half of the maximum number of cycles will be used if DEFAULT is specified. The default value is DEFAULT.

*damageExtrapolationTolerance*

A Float specifying the maximum extrapolated damage increment. The default value is 1.0.

*matrixStorage*

A SymbolicConstant specifying the type of matrix storage. Possible values are SYMMETRIC, UNSYMMETRIC, and SOLVER_DEFAULT. The default value is SOLVER_DEFAULT.

*extrapolation*

A SymbolicConstant specifying the type of extrapolation to use in determining the incremental solution for a nonlinear analysis. Possible values are NONE, LINEAR, and PARABOLIC. The default value is LINEAR.

*convertSDI*

A SymbolicConstant specifying whether to force a new iteration if severe discontinuities occur during an iteration. Possible values are PROPAGATED, CONVERT_SDI_OFF, and CONVERT_SDI_ON. The default value is PROPAGATED.

*previous*

A String specifying the name of the previous step. The new step appears after this step in the list of analysis steps.

*description*

A String specifying a description of the new step. The default value is an empty string.

*timePoints*

 `None` or a String specifying a String specifying the name of a time point object used to determine at which times the response of the structure will be evaluated. The default value is NONE.

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

### 49.9.4 Corresponding analysis keywords

| [*DIRECT CYCLIC](../key/key-link.md#usb-kws-hdirectcyclic) |
| --- |
| [*STEP](../key/key-link.md#usb-kws-hstep) |




