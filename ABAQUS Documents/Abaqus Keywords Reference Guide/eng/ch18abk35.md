# *STEADY STATE TRANSPORT







### *STEADY STATE TRANSPORTSteady-state transport analysis.

This option is used to indicate that the step should be analyzed as a steady-state transport analysis.

**Product: **Abaqus/Standard  

**Type: **History data 

**Level: **Step

##### **References:**

- ["Steady-state transport analysis," Section 6.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asteadystatetransport)
- ["Symmetric model generation," Section 10.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aaximodelgen)

### **Optional parameters: **

ALLSDTOL

Include this parameter to indicate that an adaptive automatic damping algorithm will be activated in this step. Set this parameter equal to the maximum allowable ratio of the stabilization energy to the total strain energy.  The initial damping factor is specified via the STABILIZE parameter or the FACTOR parameter. This damping factor will then be adjusted through the step based on the convergence history and the value of ALLSDTOL. If this parameter is set equal to zero, the adaptive automatic damping algorithm is not activated; a constant damping factor will be used throughout the step. If this parameter is included without a specified value, the default value is 0.05.  If this parameter is omitted but the STABILIZE parameter is included with the default value of dissipated energy fraction, the adaptive automatic damping algorithm will be activated automatically with ALLSDTOL=0.05.

This parameter must be used in conjunction with the STABILIZE parameter (see ["Solving nonlinear problems," Section 7.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-anonlineareqns)).

CONTINUE

Set CONTINUE=NO (default) to specify that this step is not to carry over the damping factors from the results of the preceding general step. In this case the initial damping factors will be recalculated based on the declared damping intensity and on the solution of the first increment of the step or can be specified directly.

Set CONTINUE=YES to specify that this step is to carry over the damping factors from the end of the immediately preceding general step.

This parameter must be used in conjunction with the ALLSDTOL and the STABILIZE parameters.

DIRECT

This parameter selects direct user control of the incrementation through the step. If this parameter is used, constant increments of the size defined by the first item on the data line are used. If this parameter is omitted, Abaqus/Standard will choose the increments (after trying the user's initial time increment for the first attempt at the first increment).

The parameter can have the value NO STOP. If this value is included, the solution to an increment is accepted after the maximum number of iterations allowed has been completed (as defined by the [*CONTROLS](ch03abk75.md) option), even if the equilibrium tolerances are not satisfied. Very small increments and a minimum of two iterations are usually necessary if this value is used. *This approach is not recommended; it should be used only in special cases when the analyst has a thorough understanding of how to interpret results obtained in this way.*

ELSET

Set this parameter equal to the name of an element set for which the rigid body motion will be described in a spatial or Eulerian manner. The rest of the elements in the model will be treated in a classical Lagrangian manner. Only one Eulerian element set can be specified in the whole model.

If this parameter is omitted, the rigid body motion in the whole model will be described in a spatial or Eulerian manner.

FACTOR

Set this parameter equal to the damping factor to be used in the automatic damping algorithm (see ["Solving nonlinear problems," Section 7.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-anonlineareqns)) if the problem is expected to be unstable due to local instabilities and the damping factor calculated by Abaqus is not suitable. This parameter must be used in conjunction with the STABILIZE parameter and overrides the automatic calculation of the damping factor based on a value of the dissipated energy fraction.

INERTIA

Include this parameter to indicate that inertia effects must be accounted for.

Set INERTIA=NO (default) to ignore inertia effects.

Set INERTIA=YES to include inertia effects.

LONG TERM

Include this parameter to indicate that there is no viscoelastic or viscoplastic material response during this step. The solution must be based on the long-term elastic moduli if the material description includes viscoelastic material properties or be based on the long-term response of the elastic-plastic network alone if the two-layer viscoplastic material model is used. 

MULLINS

Include this parameter when the Mullins effect material model is used to indicate how the Mullins effect should be applied over the step.

Set MULLINS=RAMP to indicate that the Mullins effect should be ramped up over the time period of the current step.

Set MULLINS=STEP (default) to indicate that the Mullins effect should be applied instantaneously at the beginning of the current step.

PASS BY PASS

Include this parameter to indicate that a quasi-steady-state (pass-by-pass) procedure will be used to obtain the steady-state solution.

If this parameter is omitted, the steady-state solution will be obtained directly.

STABILIZE

Include this parameter to use automatic stabilization if the problem is expected to be unstable due to local instabilities. Set this parameter equal to the dissipated energy fraction of the automatic damping algorithm (see ["Solving nonlinear problems," Section 7.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-anonlineareqns)). If this parameter is omitted, the stabilization algorithm is not activated. If this parameter is included without a specified value, the default value of the dissipated energy fraction is ![](../graphics/key_eqn01084.gif) and the adaptive automatic damping algorithm will be activated by default with ALLSDTOL =0.05 in this step; set ALLSDTOL=0 to deactivate the adaptive automatic damping algorithm. If the FACTOR parameter is used, any value of the dissipated energy fraction will be overridden by the damping factor.

### **Data line to define a steady-state transport analysis: **

**First (and only) line:**




