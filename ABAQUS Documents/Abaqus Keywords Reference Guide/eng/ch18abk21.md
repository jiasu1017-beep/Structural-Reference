# *SOILS







### *SOILSEffective stress analysis for fluid-filled porous media.

This option is used to specify transient (consolidation) or steady-state response analysis of partially or fully saturated fluid-filled porous media.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **References:**

- ["Coupled pore fluid diffusion and stress analysis," Section 6.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acoupdiffstress)
- ["Rate-dependent plasticity: creep and swelling," Section 23.2.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cratedepcreep)

### **Optional parameters: **

ALLSDTOL

Include this parameter to indicate that an adaptive automatic damping algorithm will be activated in this step. Set this parameter equal to the maximum allowable ratio of the stabilization energy to the total strain energy.  The initial damping factor is specified via the STABILIZE parameter or the FACTOR parameter. This damping factor will then be adjusted through the step based on the convergence history and the value of ALLSDTOL. If this parameter is set equal to zero, the adaptive automatic damping algorithm is not activated; a constant damping factor will be used throughout the step. If this parameter is included without a specified value, the default value is 0.05.  If this parameter is omitted but the STABILIZE parameter is included with the default value of dissipated energy fraction, the adaptive automatic damping algorithm will be activated automatically with ALLSDTOL=0.05.

This parameter must be used in conjunction with the STABILIZE parameter (see ["Solving nonlinear problems," Section 7.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-anonlineareqns)).

CETOL

This parameter will invoke automatic time incrementation. If the UTOL, DELTMX, and CETOL parameters are omitted, fixed time increments will be used.

This parameter is meaningful only when the material response includes time-dependent creep behavior; CETOL controls the accuracy of the creep integration. Set this parameter equal to the maximum allowable difference in the creep strain increment calculated from the creep strain rates at the beginning and at the end of the increment (see ["Rate-dependent plasticity: creep and swelling," Section 23.2.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cratedepcreep)).

The tolerance can be calculated by choosing an acceptable stress error tolerance and dividing by a typical elastic modulus.

CONSOLIDATION

Include this parameter to choose transient (consolidation) analysis. Omit this parameter to choose steady-state analysis.

CONTINUE

Set CONTINUE=NO (default) to specify that this step will not carry over the damping factors from the results of the preceding general step. In this case the initial damping factors will be recalculated based on the declared damping intensity and on the solution of the first increment of the step or can be specified directly.

Set CONTINUE=YES to specify that this step will carry over the damping factors from the end of the immediately preceding general step.

This parameter must be used in conjunction with the ALLSDTOL and the STABILIZE parameters.

DELTMX

This parameter will invoke automatic time incrementation. Set this parameter equal to the maximum temperature change allowed within an increment. Abaqus/Standard will restrict the time step to ensure that this value is not exceeded at any node during any increment of the step. If this parameter, the CETOL parameter, and the UTOL parameter are all omitted in a transient analysis, fixed time increments will be used, with a constant time increment equal to the initial time increment.

END

This parameter is meaningful only for transient analysis. Set END=PERIOD (default) to analyze a specified time period. Set END=SS to end the step when steady state is reached.

CREEP

Set CREEP=NONE to specify that there is no creep or viscoelastic response occurring during this step even if creep or viscoelastic material properties have been defined.

FACTOR

Set this parameter equal to the damping factor to be used in the automatic damping algorithm (see ["Solving nonlinear problems," Section 7.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-anonlineareqns)) if the problem is expected to be unstable due to local instabilities and the damping factor calculated by Abaqus/Standard is not suitable. This parameter must be used in conjunction with the STABILIZE and CONSOLIDATION parameters and overrides the automatic calculation of the damping factor based on a value of the dissipated energy fraction.

HEAT

This parameter is relevant if there are regions in the model that use coupled temperature–pore pressure elements; it specifies whether heat transfer effects are to be modeled in these regions.

This parameter is not relevant if only coupled pore pressure–displacement elements are used in a model.

Set HEAT=YES (default) to specify that heat transfer effects are to be modeled in these regions. In this case Abaqus/Standard solves the heat transfer equation in conjunction with the mechanical equilibrium and the fluid flow continuity equations.

Set HEAT=NO to specify that heat transfer will not be modeled in these regions.

STABILIZE

Include this parameter to use automatic stabilization if the problem is expected to be unstable due to local instabilities. Set this parameter equal to the dissipated energy fraction of the automatic damping algorithm (see ["Solving nonlinear problems," Section 7.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-anonlineareqns)). If this parameter is omitted, the stabilization algorithm is not activated. If this parameter is included without a specified value, the default value of the dissipated energy fraction is 2  104  and the adaptive automatic damping algorithm will be activated by default with ALLSDTOL =0.05 in this step; set ALLSDTOL=0 to deactivate the adaptive automatic damping algorithm. If the FACTOR parameter is used, any value of the dissipated energy fraction will be overridden by the damping factor.

This parameter can be used only in conjunction with the CONSOLIDATION parameter.

UTOL

This parameter will invoke automatic time incrementation. If the UTOL, DELTMX, and the CETOL parameters are omitted, fixed time increments will be used.

Set this parameter equal to the maximum pore pressure change permitted in any increment (in pressure units) in a transient consolidation analysis. Abaqus/Standard will restrict the time step to ensure that this value will not be exceeded at any node (except nodes with boundary conditions) during any increment of the analysis.

Set this value equal to any nonzero value in a steady-state analysis (to activate automatic time incrementation).

### **Data line to define incrementation for a soils analysis: **

**First (and only) line:**




