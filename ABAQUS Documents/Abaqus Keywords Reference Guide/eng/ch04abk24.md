# *DIRECT CYCLIC







### *DIRECT CYCLICObtain the stabilized cyclic response of a structure directly.

This option is used to provide a direct cyclic procedure for nonlinear, non-isothermal quasi-static analysis in Abaqus/Standard.  It can also be used to predict progressive damage and failure for ductile bulk materials and/or to predict delamination/debonding growth at the interfaces in laminated composites in a low-cycle fatigue analysis.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **References:**

- ["Direct cyclic analysis," Section 6.2.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-adirectcyclic)
- ["Low-cycle fatigue analysis using the direct cyclic approach," Section 6.2.7 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-adirectcyclicfatigue)
- [*TIME POINTS](ch19abk07.md)

### **Optional parameters: **

CETOL

Set this parameter equal to the maximum difference in the creep strain increment calculated from the creep strain rates based on conditions at the beginning and on conditions at the end of the increment, thus controlling the time integration accuracy of the creep integration.

This parameter can be used in conjunction with the [*TIME POINTS](ch19abk07.md) option. In this case Abaqus/Standard will ensure the response will also be evaluated at each time point specified on the [*TIME POINTS](ch19abk07.md) option.

If both this parameter and the DELTMX parameter are omitted, fixed time stepping will be used, with a constant time increment equal to the initial time increment or by following precisely the time points specified on the [*TIME POINTS](ch19abk07.md) option.

CONTINUE

Set CONTINUE=YES to specify that the current [*DIRECT CYCLIC](ch04abk24.md) step is a continuation of the previous direct cyclic step. The displacement solution in the Fourier series obtained in the previous [*DIRECT CYCLIC](ch04abk24.md) step is then used as the starting values for the current step.

Set CONTINUE=NO (default) to reset all the displacement Fourier coefficients to zero, thus allowing application of cyclic loading conditions that are very different from those in the previous direct cyclic step.

DELTMX

Set this parameter equal to the maximum temperature change to be allowed in an increment during a direct cyclic analysis. Abaqus/Standard will restrict the time increment to ensure that this value will not be exceeded at any node during any increment of the step.

This parameter can be used in conjunction with the [*TIME POINTS](ch19abk07.md) option. In this case Abaqus/Standard will ensure the response will also be evaluated at each time point specified on the [*TIME POINTS](ch19abk07.md) option.

If both this parameter and the CETOL parameter are omitted, fixed time stepping will be used, with a constant time increment equal to the initial time increment or by following precisely the time points specified on the [*TIME POINTS](ch19abk07.md) option.

FATIGUE

Include this parameter to perform a low-cycle fatigue analysis using a direct cyclic approach in conjunction with the damage extrapolation technique. Multiple cycles can be included in a single direct cyclic analysis. The analysis models progressive damage and failure on constitutive points in the bulk materials based on a continuum damage approach. It can also be used to model delamination/debonding growth at the interfaces in laminated composites.

TIME POINTS

Set this parameter equal to the name of the [*TIME POINTS](ch19abk07.md) option that defines the time points at which the response of the structure will be evaluated.

### **Data line to control incrementation and Fourier representation in a direct cyclic analysis without the FATIGUE parameter: **

**First (and only) line:**

### **Data lines for a low-cycle fatigue analysis using the direct cyclic approach: **

**First line:**

**Second line:**




