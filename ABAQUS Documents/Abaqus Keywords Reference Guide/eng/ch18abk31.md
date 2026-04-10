# *STATIC







### *STATICStatic stress/displacement analysis.

This option is used to indicate that the step should be analyzed as a static load step.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **References:**

- ["Static stress analysis," Section 6.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-astatic)
- ["Unstable collapse and postbuckling analysis," Section 6.2.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-apostbuckling)
- ["Adiabatic analysis," Section 6.5.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aadiabaticanal)
- ["Solving nonlinear problems," Section 7.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-anonlineareqns)
- ["Deformation plasticity," Section 23.2.13 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cdeformationplast)

### **No parameters or data lines are used in a linear perturbation analysis. **

### **Optional parameters for a general static analysis: **

ADIABATIC

Include this parameter to perform an adiabatic stress analysis. This parameter is relevant only for isotropic metal plasticity materials with a Mises yield surface and when the [*INELASTIC HEAT FRACTION](ch09abk16.md) option has been specified.

ALLSDTOL

Include this parameter to indicate that an adaptive automatic damping algorithm will be activated in this step. Set this parameter equal to the maximum allowable ratio of the stabilization energy to the total strain energy. The initial damping factor is specified via the STABILIZE parameter or the FACTOR parameter. This damping factor will then be adjusted through the step based on the convergence history and the value of ALLSDTOL. If this parameter is set equal to zero, the adaptive automatic damping algorithm is not activated; a constant damping factor will be used throughout the step. If this parameter is included without a specified value, the default value is 0.05. If this parameter is omitted but the STABILIZE parameter is included with the default value of dissipated energy fraction, the adaptive automatic damping algorithm will be activated automatically with ALLSDTOL=0.05.

This parameter must be used in conjunction with the STABILIZE parameter (see ["Solving nonlinear problems," Section 7.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-anonlineareqns)).

CONTINUE

Set CONTINUE=NO (default) to specify that this step will not carry over the damping factors from the results of the preceding general step. In this case the initial damping factors will be recalculated based on the declared damping intensity and on the solution of the first increment of the step or can be specified directly.

Set CONTINUE=YES to specify that this step will carry over the damping factors from the end of the immediately preceding general step.

This parameter must be used in conjunction with the ALLSDTOL and the STABILIZE parameters.

DIRECT

This parameter selects direct user control of the incrementation through the step. If this parameter is used, constant increments of the size defined by the first item on the data line are used. If this parameter is omitted, Abaqus/Standard will choose the increments (after trying the user's initial time increment for the first attempt at the first increment).

The parameter can have the value NO STOP. If this value is included, the solution to an increment is accepted after the maximum number of iterations allowed has been completed (as defined by the [*CONTROLS](ch03abk75.md) option), even if the equilibrium tolerances are not satisfied. Very small increments and a minimum of two iterations are usually necessary if this value is used. *This approach is not recommended; it should be used only in special cases when the analyst has a thorough understanding of how to interpret results obtained in this way.*

FACTOR

Set this parameter equal to the damping factor to be used in the automatic damping algorithm (see ["Solving nonlinear problems," Section 7.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-anonlineareqns)) if the problem is expected to be unstable due to local instabilities and the damping factor calculated by Abaqus is not suitable. This parameter must be used in conjunction with the STABILIZE parameter and overrides the automatic calculation of the damping factor based on a value of the dissipated energy fraction.

This parameter cannot be used if the RIKS parameter is included.

FULLY PLASTIC

This parameter is relevant only for cases where “fully plastic” analysis is required with deformation theory plasticity. For that purpose set this parameter equal to the name of the element set being monitored for fully plastic behavior.

The step will end when the solutions at all constitutive calculation points in the element set are fully plastic (defined by the equivalent strain being 10 times the offset yield strain). The step will end before this occurs if either the maximum number of increments given on the [*STEP](ch18abk36.md) option or the time period given on the data line of [*STATIC](ch18abk31.md) is exceeded.

LONG TERM

Include this parameter to obtain the fully relaxed long-term elastic solution with time-domain viscoelasticity or the long-term elastic-plastic solution for two-layer viscoplasticity. If the LONG TERM parameter is omitted, the instantaneous elastic solution is obtained for time-domain viscoelasticity and the combined response of the elastic-plastic and elastic-viscous networks is obtained for two-layer viscoplasticity. The parameter is relevant only for time-domain viscoelastic and two-layer viscoplastic materials.

RIKS

Include this parameter to use the modified Riks method for proportional loading cases (["Unstable collapse and postbuckling analysis," Section 6.2.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-apostbuckling)).

STABILIZE

Include this parameter to use automatic stabilization if the problem is expected to be unstable due to local instabilities. Set this parameter equal to the dissipated energy fraction of the automatic damping algorithm (see ["Solving nonlinear problems," Section 7.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-anonlineareqns)). If this parameter is omitted, the stabilization algorithm is not activated. If this parameter is included without a specified value, the default value of the dissipated energy fraction is ![](../graphics/key_eqn01084.gif) and the adaptive automatic damping algorithm will be activated by default with ALLSDTOL =0.05 in this step; set ALLSDTOL=0 to deactivate the adaptive automatic damping algorithm. If the FACTOR parameter is used, any value of the dissipated energy fraction will be overridden by the damping factor.

This parameter cannot be used if the RIKS parameter is included.

### **Data line for a general static analysis: **

**First (and only) line:**

### **Data line for the Riks method: **

**First (and only) line:**




