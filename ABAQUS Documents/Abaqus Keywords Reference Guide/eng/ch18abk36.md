# *STEP







### *STEPBegin a step.

This option is used to begin each step definition. It must be followed by a procedure definition option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **History data 

**Level: **Model  

**Abaqus/CAE: **Step module

##### **References:**

- ["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)
- ["Convergence criteria for nonlinear problems," Section 7.2.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aconvergcriteria)
- ["Design sensitivity analysis," Section 19.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-adsa)
- [*END STEP](ch05abk20.md)

### Beginning a step in an Abaqus/Standard analysis

### **Optional parameters: **

AMPLITUDE

This parameter defines the default amplitude variation for loading magnitudes during the step. 

Set AMPLITUDE=STEP if the load is to be applied instantaneously at the start of the step and remain constant throughout the step.

Set AMPLITUDE=RAMP if the load magnitude is to vary linearly over the step, from the value at the end of the previous step (or zero, at the start of the analysis) to the value given on the loading option.

If this parameter is omitted, the default amplitude choice depends on the procedure chosen, as shown in ["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover). The default amplitude variation can be overwritten for individual loadings by using the AMPLITUDE parameter on the loading options (["Amplitude curves," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude)).

This parameter is rarely needed, and changing the defaults may cause problems. For example, the automatic load incrementation scheme in procedures without a real time scale (such as the [*STATIC](ch18abk31.md) option) applies the loads gradually by incrementing the normalized time scale. The use of AMPLITUDE=STEP specifies that the entire load will be applied immediately, so Abaqus/Standard may not be able to choose suitable small increments if the loading causes strongly nonlinear response.

CONVERT SDI

This parameter determines how severe discontinuities (such as contact changes) are accounted for during nonlinear analysis.

Set CONVERT SDI=YES (default) to use local convergence criteria to determine whether a new iteration is needed. Abaqus/Standard will determine the maximum penetration and estimated force errors associated with severe discontinuities and check whether these errors are within the tolerances. Hence, a solution may converge if the severe discontinuities are small. 

Set CONVERT SDI=NO to force a new iteration if severe discontinuities occur during an iteration, regardless of the magnitude of the penetration and force errors. This option also changes some time incrementation parameters and uses different criteria to determine whether to do another iteration or to make a new attempt with a smaller increment size.

If the CONVERT SDI parameter is omitted, Abaqus/Standard will use the value specified in the previous general analysis step. An exception is the first new step of a restart analysis, which will use CONVERT SDI=YES by default regardless of the setting in the previous step.

This parameter has no relevance and will be ignored for heat transfer analysis and linear perturbation steps.

DSA

This parameter applies only to Abaqus/Design.

Set DSA=YES to activate design sensitivity analysis for the step. Once DSA is activated in a general step, it remains active in all subsequent general steps until it is deactivated in a subsequent general step by setting DSA=NO. Once DSA is activated in a perturbation step, it remains active in all subsequent consecutive perturbation steps until it is deactivated in a subsequent consecutive perturbation step. However, if DSA is activated in a step whose procedure is not supported for DSA, DSA will be deactivated until it is activated again by setting DSA=YES.

EXTRAPOLATION

This parameter is useful only for nonlinear analyses.

Set EXTRAPOLATION=LINEAR (default for procedures other than [*DYNAMIC](ch04abk43.md), APPLICATION=TRANSIENT FIDELITY) to indicate that the process is essentially monotonic, so that Abaqus/Standard should use a 100% linear extrapolation, in time, of the previous incremental solution to begin the nonlinear equation solution for the current increment (a 1% extrapolation is used with the Riks method).

Set EXTRAPOLATION=PARABOLIC to indicate that the process should use a quadratic displacement-based extrapolation, in time, of the previous two incremental solutions to begin the nonlinear equation solution for the current increment.

Set EXTRAPOLATION=VELOCITY PARABOLIC  (available for [*DYNAMIC](ch04abk43.md) procedure only and default for the [*DYNAMIC](ch04abk43.md) APPLICATION=TRANSIENT FIDELITY procedure) to indicate that the process should use a quadratic velocity-based extrapolation, in time, of the previous incremental solutions to begin the nonlinear equation solution for the current increment.

Set EXTRAPOLATION=NO to suppress any extrapolation.

INC

Set this parameter equal to the maximum number of increments in a step (or in a single loading cycle for direct cyclic analysis). This value is only an upper bound. The default value is 100.

The INC parameter has no effect in procedures where automatic incrementation cannot be used (for example, [*BUCKLE](ch02abk16.md), [*STEADY STATE DYNAMICS](ch18abk34.md), and [*MODAL DYNAMIC](ch13abk18.md)).

NAME

Set this parameter equal to a label that will be used to refer to the step on the output database. Step names in the same input file must be unique. Step names from the original input file can be reused in a restart input file.

NLGEOM

Omit this parameter or set NLGEOM=NO to perform a geometrically linear analysis during the current step. Include this parameter or set NLGEOM=YES to indicate that geometric nonlinearity should be accounted for during the step (stress analysis, fully coupled thermal-stress analysis, and coupled thermal-electrical-stress analysis only). Once the NLGEOM option has been switched on, it will be active during all subsequent steps in the analysis.

PERTURBATION

Include this parameter to indicate that this is a linear perturbation step. For this type of analysis Abaqus/Standard expects that load, boundary, and temperature changes should be given and that the results will be changes relative to the previous step. *Please read the discussions in ["General and linear perturbation procedures," Section 6.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-alinearnonlinear), ["Mesh-to-mesh solution mapping," Section 12.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-amapsolution), and ["Applying loads: overview," Section 34.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-ploading), before using this option.*

SOLVER

Set SOLVER=ITERATIVE to use the iterative linear equation solver. *Please read the discussion in ["Iterative linear equation solver," Section 6.1.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aitrsolveroverview), before using this option.*

If this parameter is omitted, the default direct sparse solver is used.

UNSYMM

Set UNSYMM=YES to indicate that unsymmetric matrix storage and solution should be used.

Set UNSYMM=NO to indicate that symmetric storage and solution should be used.

The default value for this parameter depends on the model and procedure options used. The user is allowed to change the default value only in certain cases. If the UNSYMM parameter is not used in such cases, Abaqus/Standard will use the value specified in the previous general analysis step. See ["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover), for a more detailed discussion of the use of this parameter.

### **Optional data lines: **

**First line:**

The subheading can be several lines long, but only the first 80 characters of the first line will be saved and printed as a subheading.

### Beginning a step in an Abaqus/Explicit analysis

### **Optional parameters: **

NAME

Set this parameter equal to the name used to identify the step on the output database. Step names in the same input file must be unique.

NLGEOM

Set NLGEOM=YES (default) to indicate that geometric nonlinearity should be accounted for during the step (stress analysis and fully coupled thermal-stress analysis only). Once the NLGEOM option has been switched on, it will be active during all subsequent steps in the analysis. Set NLGEOM=NO to perform a geometrically linear analysis during the current step. 

The default value for the NLGEOM parameter in an Abaqus/Explicit analysis is YES unless the Abaqus/Explicit analysis is an import analysis, in which case the default value of the NLGEOM parameter is the same as the value of the parameter at the time of import.

### **Optional data lines: **

**First line:**

The subheading can be several lines long, but only the first 80 characters of the first line will be saved and printed as a subheading. 

### Beginning a step in an Abaqus/CFD analysis

### **Optional parameter: **

NAME

Set this parameter equal to the name used to identify the step on the output database. Step names in the same input file must be unique.

### **Optional data lines: **

**First line:**

The subheading can be several lines long, but only the first 80 characters of the first line will be saved and printed as a subheading. 




