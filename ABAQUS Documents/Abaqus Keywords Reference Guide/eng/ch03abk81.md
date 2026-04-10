# *COUPLED TEMPERATURE-DISPLACEMENT







### *COUPLED TEMPERATURE-DISPLACEMENTFully coupled, simultaneous heat transfer and stress analysis.

This option is used to analyze problems where the simultaneous solution of the temperature and stress/displacement fields is necessary.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **References:**

- ["Fully coupled thermal-stress analysis," Section 6.5.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acouptempdisp)
- ["Rate-dependent plasticity: creep and swelling," Section 23.2.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cratedepcreep)

### **Optional parameters: **

ALLSDTOL

Include this parameter to indicate that an adaptive automatic damping algorithm will be activated in this step. Set this parameter equal to the maximum allowable ratio of the stabilization energy to the total strain energy.  The initial damping factor is specified via the STABILIZE parameter or the FACTOR parameter. This damping factor will then be adjusted through the step based on the convergence history and the value of ALLSDTOL. If this parameter is set equal to zero, the adaptive automatic damping algorithm is not activated; a constant damping factor will be used throughout the step. If this parameter is included without a specified value, the default value is 0.05.  If this parameter is omitted but the STABILIZE parameter is included with the default value of dissipated energy fraction, the adaptive automatic damping algorithm will be activated automatically with ALLSDTOL=0.05.

This parameter must be used in conjunction with the STABILIZE parameter (see ["Solving nonlinear problems," Section 7.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-anonlineareqns)).

CONTINUE

Set CONTINUE=NO (default) to specify that this step will not carry over the damping factors from the results of the preceding general step. In this case the initial damping factors will be recalculated based on the declared damping intensity and on the solution of the first increment of the step or can be specified directly.

Set CONTINUE=YES to specify that this step will carry over the damping factors from the end of the immediately preceding general step.

This parameter must be used in conjunction with the ALLSDTOL and the STABILIZE parameters.

CREEP

Set CREEP=EXPLICIT to use explicit integration for creep and swelling effects throughout the step, which may sometimes be computationally less expensive. When CREEP=EXPLICIT, the time increment will be limited by the accuracy tolerances (CETOL and DELTMX) and also by the stability limit of the forward difference operator. See ["Rate-dependent plasticity: creep and swelling," Section 23.2.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cratedepcreep) for details on the integration scheme.

Set CREEP=NONE to specify that there is no creep or viscoelastic response occurring during this step even if creep or viscoelastic material properties have been defined.

ELECTRICAL

Include this parameter to specify that electrical conduction will be modeled in regions of the model that use thermal-electrical-structural elements.

 In this case Abaqus/Standard solves the heat transfer equations in conjunction with the mechanical equilibrium and the electrical conduction equations.

Omit this parameter to specify that the electrical conduction will not be modeled in these regions.

FACTOR

Set this parameter equal to the damping factor to be used in the automatic damping algorithm (see ["Solving nonlinear problems," Section 7.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-anonlineareqns)) if the problem is expected to be unstable due to local instabilities and the damping factor calculated by Abaqus/Standard is not suitable. This parameter must be used in conjunction with the STABILIZE parameter and overrides the automatic calculation of the damping factor based on a value of the dissipated energy fraction.

STABILIZE

Include this parameter to use automatic stabilization if the problem is expected to be unstable due to local instabilities. Set this parameter equal to the dissipated energy fraction of the automatic damping algorithm (see ["Solving nonlinear problems," Section 7.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-anonlineareqns)). If this parameter is omitted, the stabilization algorithm is not activated. If this parameter is included without a specified value, the default value of the dissipated energy fraction is 2  104 and the adaptive automatic damping algorithm will be activated by default with ALLSDTOL =0.05 in this step; set ALLSDTOL=0 to deactivate the adaptive automatic damping algorithm. If the FACTOR parameter is used, any value of the dissipated energy fraction will be overriden by the damping factor.

STEADY STATE

Include this parameter to choose steady-state analysis. If this parameter is omitted, the step is assumed to involve transient response. If this parameter is included, automatic time incrementation will be used.

### **Optional parameters to control time incrementation in transient analysis: **

CETOL

Set this parameter equal to the maximum difference in the creep strain increment calculated from the creep strain rates at the beginning and at the end of the increment, thus controlling the accuracy of the creep integration. The tolerance is sometimes calculated by choosing an acceptable stress error tolerance and dividing by a typical elastic modulus. This parameter is meaningful only when the material response is time dependent (creep and swelling). If both this parameter and the DELTMX parameter are omitted in a transient analysis, fixed time increments will be used, with a constant time increment equal to the initial time increment.

DELTMX

Set this parameter equal to the maximum temperature change allowed within an increment. Abaqus/Standard will restrict the time step to ensure that this value is not exceeded at any node during any increment of the step. If both this and the CETOL parameter are omitted in a transient analysis, fixed time increments will be used, with a constant time increment equal to the initial time increment.

### **Data line to control incrementation in a fully coupled thermal-stress analysis: **

**First (and only) line:**




