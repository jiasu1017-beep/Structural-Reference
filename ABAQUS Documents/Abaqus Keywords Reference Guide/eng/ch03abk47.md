# *CONNECTOR MOTION







### *CONNECTOR MOTIONSpecify the motion of available components of relative motion in connector elements.

This option is used to prescribe the motion of available components of relative motion in connector elements.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model or history data  

**Level: **Model,  Step

**Abaqus/CAE: **Load module

##### **References:**

- ["Connection-type library," Section 31.1.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnectortypelibrary)
- ["DISP," Section 1.1.4 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-udisp)

### **Optional parameters (history data only): **

AMPLITUDE

This parameter is relevant only when some of the variables being prescribed have nonzero magnitudes. Set this parameter equal to the name of the amplitude curve defining the magnitude of the prescribed connector motions (["Amplitude curves," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude)).

If this parameter is omitted in an Abaqus/Standard analysis, either the reference magnitude is applied linearly over the step (a RAMP function) or it is applied immediately at the beginning of the step and subsequently held constant (a STEP function). The choice of RAMP or STEP function depends on the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option (["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)). Two exceptions are displacement or rotation components given with TYPE=DISPLACEMENT, for which the default is always a RAMP function, and displacement or rotation components in a static step given with TYPE=VELOCITY, for which the default is always a STEP function.

If this parameter is omitted in an Abaqus/Explicit analysis, the reference magnitude is applied immediately at the beginning of the step and subsequently held constant (a STEP function). 

In an Abaqus/Standard dynamic procedure, amplitude curves specified for TYPE=DISPLACEMENT or TYPE=VELOCITY will be smoothed automatically. In an explicit dynamic analysis using Abaqus/Explicit, the user must request that such amplitude curves are smoothed. For more information, see ["Amplitude curves," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude).

LOAD CASE

This parameter applies only to Abaqus/Standard analyses.

This parameter is ignored in all procedures except [*BUCKLE](ch02abk16.md). The parameter can be set equal to 1 (default) or 2. 

LOAD CASE=1 can be used to define the connector motion for the applied loads and LOAD CASE=2 can be used to define antisymmetry connector motion for the buckling modes.

OP

Set OP=MOD (default) to modify existing connector motions or to add connector motions to available components of relative motion that were previously unconstrained.

Set OP=NEW if all connector motions that are currently in effect should be removed. To remove only selected connector motions, use OP=NEW and respecify all connector motions that are to be retained.

If a connector motion is removed in a stress/displacement analysis, it will be replaced by a concentrated force equal to the reaction force calculated at the restrained degree of freedom at the end of the previous step. If the step is a general nonlinear analysis step, this concentrated force will then be removed according to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option. Therefore, by default the concentrated force will be reduced linearly to zero over the period of the step in a static analysis and immediately in a dynamic analysis.

### **Optional, mutually exclusive parameters (history data only): **

FIXED

Include this parameter to indicate that the values of the variables being prescribed with this [*CONNECTOR MOTION](ch03abk47.md) option should remain fixed at their current values at the start of the step. If this parameter is used, any magnitudes given on the data lines are ignored.

TYPE

This parameter is used in a stress/displacement analysis to specify whether the magnitude is in the form of a displacement history, a velocity history, or an acceleration history.

Set TYPE=DISPLACEMENT (default) to give a displacement history.

Set TYPE=VELOCITY to give a velocity history. Velocity histories can be specified in static analyses. In this case the default variation is STEP.

Set TYPE=ACCELERATION to give an acceleration history. Acceleration histories should not be used in static analysis steps.

USER

This parameter applies only to Abaqus/Standard analyses.

Include this parameter to indicate that any nonzero magnitudes associated with variables prescribed through this option will be defined in user subroutine [`DISP`](../sub/sub-link.md#sub-xsl-disp). If this parameter is used, any magnitudes defined by the data lines of the option (and possibly modified by the AMPLITUDE parameter) can be redefined in subroutine [`DISP`](../sub/sub-link.md#sub-xsl-disp). The value of the TYPE parameter is ignored when this option is used.

### **Optional, mutually exclusive parameters for matrix generation and direct-solution steady-state dynamics analysis (history data only): **

IMAGINARY

Include this parameter to define the imaginary (out-of-phase) part of the connector motion.

REAL

Include this parameter (default) to define the real (in-phase) part of the connector motion.

### **Data lines to prescribe connector motion: **

**First line:**

Repeat this data line as often as necessary to specify connector motion for different connector elements and available components of relative motion.




